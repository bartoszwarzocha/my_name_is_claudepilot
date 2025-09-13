---
description: Design and implement scalable microservices architecture with proper service decomposition, inter-service communication, and resilience patterns. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
  - vscodeAPI
---

# Microservices Architecture Patterns

Design and implement scalable microservices architecture following domain-driven design principles, with proper service decomposition, inter-service communication patterns, and resilience mechanisms.

## Context Adaptation

**IMPORTANT**: Always read the `copilot.instructions.md` file in the project root directory at the beginning of your work to adapt your implementation to:

- Backend technologies and frameworks specified in the project
- Business domains and service boundaries
- Infrastructure preferences and deployment targets
- Security requirements and compliance needs
- Performance and scalability expectations

## Mission

Create a well-architected microservices ecosystem that promotes loose coupling, high cohesion, and independent deployability while maintaining data consistency and system resilience.

## Architecture Design Process

### Step 1: Service Decomposition Strategy

**Domain-Driven Design Approach:**
```bash
# Analyze business domains from project configuration
cat copilot.instructions.md | grep -A 10 "Business domains\|business_domain"

# Identify service boundaries
find . -name "*.md" -o -name "*.txt" | xargs grep -l "business\|domain\|service" | head -5
```

**Service Identification Patterns:**
- **Business Capability Decomposition**: Services aligned with business functions
- **Data Decomposition**: Services owning specific data domains
- **Transaction Boundary Analysis**: Services managing consistent transactions
- **Team Conway's Law**: Services aligned with team structures

**Service Boundary Design:**
```yaml
# Example Service Map
services:
  user-service:
    domain: "User Management"
    responsibilities:
      - User registration and authentication
      - Profile management
      - User preferences
    data_ownership:
      - users
      - user_profiles
      - user_sessions
    
  order-service:
    domain: "Order Processing"
    responsibilities:
      - Order creation and management
      - Order status tracking
      - Order history
    data_ownership:
      - orders
      - order_items
      - order_status
    
  product-service:
    domain: "Product Catalog"
    responsibilities:
      - Product information management
      - Inventory tracking
      - Product categories
    data_ownership:
      - products
      - categories
      - inventory
```

### Step 2: Inter-Service Communication Patterns

**Synchronous Communication (REST/GraphQL):**
```typescript
// Service-to-Service REST Communication
interface ServiceClient {
  baseUrl: string;
  timeout: number;
  retries: number;
  circuitBreaker: CircuitBreakerConfig;
}

class UserServiceClient implements ServiceClient {
  constructor(
    public baseUrl: string = process.env.USER_SERVICE_URL,
    public timeout: number = 5000,
    public retries: number = 3,
    public circuitBreaker: CircuitBreakerConfig = defaultCircuitBreaker
  ) {}

  async getUserById(id: string): Promise<User> {
    const response = await this.httpClient.get(`/users/${id}`, {
      timeout: this.timeout,
      headers: {
        'Authorization': `Bearer ${this.getServiceToken()}`,
        'X-Correlation-ID': this.getCorrelationId(),
        'X-Service-Name': 'order-service'
      }
    });
    
    return response.data;
  }

  async getUsersInBatch(ids: string[]): Promise<User[]> {
    return await this.httpClient.post('/users/batch', { ids }, {
      timeout: this.timeout * 2 // Longer timeout for batch operations
    });
  }
}
```

**Asynchronous Communication (Event-Driven):**
```typescript
// Event-Driven Communication with Message Queues
interface DomainEvent {
  eventId: string;
  eventType: string;
  aggregateId: string;
  aggregateType: string;
  eventData: any;
  timestamp: Date;
  version: number;
}

class OrderCreatedEvent implements DomainEvent {
  constructor(
    public eventId: string,
    public aggregateId: string, // orderId
    public eventData: {
      customerId: string;
      orderItems: OrderItem[];
      totalAmount: number;
      currency: string;
    },
    public timestamp: Date = new Date(),
    public version: number = 1
  ) {}

  eventType = 'OrderCreated';
  aggregateType = 'Order';
}

// Event Publisher
class EventPublisher {
  constructor(
    private messageQueue: MessageQueue,
    private eventStore: EventStore
  ) {}

  async publishEvent(event: DomainEvent): Promise<void> {
    // Store event for replay capability
    await this.eventStore.saveEvent(event);
    
    // Publish to message queue
    await this.messageQueue.publish(event.eventType, event, {
      persistent: true,
      headers: {
        'event-type': event.eventType,
        'aggregate-id': event.aggregateId,
        'correlation-id': this.getCorrelationId()
      }
    });
  }
}

// Event Consumer
class InventoryEventHandler {
  @EventHandler('OrderCreated')
  async handleOrderCreated(event: OrderCreatedEvent): Promise<void> {
    try {
      // Reserve inventory for order items
      await this.inventoryService.reserveItems(
        event.eventData.orderItems,
        event.aggregateId
      );
      
      // Publish inventory reserved event
      const inventoryReservedEvent = new InventoryReservedEvent(
        generateId(),
        event.aggregateId,
        { reservationId: generateId(), items: event.eventData.orderItems }
      );
      
      await this.eventPublisher.publishEvent(inventoryReservedEvent);
      
    } catch (error) {
      // Publish compensation event
      const inventoryReservationFailedEvent = new InventoryReservationFailedEvent(
        generateId(),
        event.aggregateId,
        { reason: error.message, orderItems: event.eventData.orderItems }
      );
      
      await this.eventPublisher.publishEvent(inventoryReservationFailedEvent);
    }
  }
}
```

### Step 3: Data Management Patterns

**Database per Service Pattern:**
```typescript
// Each service owns its data
interface ServiceDataAccess {
  database: Database;
  repository: Repository;
  migrationRunner: MigrationRunner;
}

class UserServiceDataLayer implements ServiceDataAccess {
  constructor(
    public database: Database,
    public repository: UserRepository,
    public migrationRunner: MigrationRunner
  ) {}

  // Service-specific schema management
  async initializeSchema(): Promise<void> {
    await this.migrationRunner.runMigrations([
      'create_users_table',
      'create_user_profiles_table',
      'create_user_sessions_table'
    ]);
  }

  // Encapsulated data access
  async findUserWithProfile(id: string): Promise<UserWithProfile | null> {
    return await this.repository.findUserWithProfile(id);
  }
}
```

**Saga Pattern for Distributed Transactions:**
```typescript
// Choreography-based Saga
class OrderProcessingSaga {
  private steps: SagaStep[] = [
    {
      action: 'validatePayment',
      compensation: 'cancelPaymentValidation'
    },
    {
      action: 'reserveInventory',
      compensation: 'releaseInventory'
    },
    {
      action: 'createShipment',
      compensation: 'cancelShipment'
    },
    {
      action: 'confirmOrder',
      compensation: 'cancelOrder'
    }
  ];

  async executeStep(stepIndex: number, context: SagaContext): Promise<void> {
    const step = this.steps[stepIndex];
    
    try {
      await this.executeAction(step.action, context);
      
      if (stepIndex < this.steps.length - 1) {
        // Continue to next step
        await this.executeStep(stepIndex + 1, context);
      } else {
        // Saga completed successfully
        await this.completeSaga(context);
      }
    } catch (error) {
      // Execute compensation actions in reverse order
      await this.compensate(stepIndex, context, error);
    }
  }

  private async compensate(failedStepIndex: number, context: SagaContext, error: Error): Promise<void> {
    for (let i = failedStepIndex; i >= 0; i--) {
      const step = this.steps[i];
      try {
        await this.executeAction(step.compensation, context);
      } catch (compensationError) {
        // Log compensation failure but continue
        console.error(`Compensation failed for step ${i}:`, compensationError);
      }
    }
    
    await this.failSaga(context, error);
  }
}
```

### Step 4: Service Resilience Patterns

**Circuit Breaker Pattern:**
```typescript
interface CircuitBreakerConfig {
  failureThreshold: number;
  timeout: number;
  resetTimeout: number;
}

enum CircuitBreakerState {
  CLOSED = 'CLOSED',
  OPEN = 'OPEN',
  HALF_OPEN = 'HALF_OPEN'
}

class CircuitBreaker {
  private state: CircuitBreakerState = CircuitBreakerState.CLOSED;
  private failureCount: number = 0;
  private lastFailureTime: number = 0;

  constructor(private config: CircuitBreakerConfig) {}

  async execute<T>(operation: () => Promise<T>): Promise<T> {
    if (this.state === CircuitBreakerState.OPEN) {
      if (Date.now() - this.lastFailureTime >= this.config.resetTimeout) {
        this.state = CircuitBreakerState.HALF_OPEN;
        this.failureCount = 0;
      } else {
        throw new Error('Circuit breaker is OPEN');
      }
    }

    try {
      const result = await Promise.race([
        operation(),
        this.createTimeoutPromise()
      ]);

      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      throw error;
    }
  }

  private onSuccess(): void {
    this.failureCount = 0;
    this.state = CircuitBreakerState.CLOSED;
  }

  private onFailure(): void {
    this.failureCount++;
    this.lastFailureTime = Date.now();

    if (this.failureCount >= this.config.failureThreshold) {
      this.state = CircuitBreakerState.OPEN;
    }
  }

  private createTimeoutPromise(): Promise<never> {
    return new Promise((_, reject) => {
      setTimeout(() => reject(new Error('Operation timeout')), this.config.timeout);
    });
  }
}
```

**Retry Pattern with Exponential Backoff:**
```typescript
interface RetryConfig {
  maxAttempts: number;
  baseDelay: number;
  maxDelay: number;
  backoffMultiplier: number;
  jitter: boolean;
}

class RetryHandler {
  constructor(private config: RetryConfig) {}

  async executeWithRetry<T>(
    operation: () => Promise<T>,
    predicate: (error: Error) => boolean = () => true
  ): Promise<T> {
    let lastError: Error;

    for (let attempt = 1; attempt <= this.config.maxAttempts; attempt++) {
      try {
        return await operation();
      } catch (error) {
        lastError = error;

        if (!predicate(error) || attempt === this.config.maxAttempts) {
          throw error;
        }

        const delay = this.calculateDelay(attempt);
        await this.sleep(delay);
      }
    }

    throw lastError!;
  }

  private calculateDelay(attempt: number): number {
    const exponentialDelay = this.config.baseDelay * 
      Math.pow(this.config.backoffMultiplier, attempt - 1);
    
    const cappedDelay = Math.min(exponentialDelay, this.config.maxDelay);
    
    if (this.config.jitter) {
      // Add random jitter to prevent thundering herd
      return cappedDelay * (0.5 + Math.random() * 0.5);
    }
    
    return cappedDelay;
  }

  private sleep(ms: number): Promise<void> {
    return new Promise(resolve => setTimeout(resolve, ms));
  }
}
```

### Step 5: Service Discovery and Configuration

**Service Registry Pattern:**
```typescript
interface ServiceInstance {
  serviceId: string;
  serviceName: string;
  host: string;
  port: number;
  metadata: Record<string, string>;
  healthCheckUrl: string;
  registrationTime: Date;
}

class ServiceRegistry {
  private services: Map<string, ServiceInstance[]> = new Map();

  async registerService(instance: ServiceInstance): Promise<void> {
    const serviceName = instance.serviceName;
    
    if (!this.services.has(serviceName)) {
      this.services.set(serviceName, []);
    }
    
    const instances = this.services.get(serviceName)!;
    
    // Remove any existing instance with the same serviceId
    const filteredInstances = instances.filter(
      inst => inst.serviceId !== instance.serviceId
    );
    
    filteredInstances.push(instance);
    this.services.set(serviceName, filteredInstances);
    
    // Start health checking
    this.startHealthCheck(instance);
  }

  async discoverService(serviceName: string): Promise<ServiceInstance[]> {
    const instances = this.services.get(serviceName) || [];
    return instances.filter(instance => this.isHealthy(instance));
  }

  async getServiceUrl(serviceName: string): Promise<string> {
    const instances = await this.discoverService(serviceName);
    
    if (instances.length === 0) {
      throw new Error(`No healthy instances found for service: ${serviceName}`);
    }
    
    // Simple round-robin load balancing
    const instance = this.selectInstance(instances);
    return `http://${instance.host}:${instance.port}`;
  }

  private selectInstance(instances: ServiceInstance[]): ServiceInstance {
    const index = Math.floor(Math.random() * instances.length);
    return instances[index];
  }

  private async startHealthCheck(instance: ServiceInstance): Promise<void> {
    const healthCheck = setInterval(async () => {
      try {
        const response = await fetch(instance.healthCheckUrl, {
          timeout: 5000
        });
        
        if (!response.ok) {
          this.markUnhealthy(instance);
        }
      } catch (error) {
        this.markUnhealthy(instance);
      }
    }, 30000); // Check every 30 seconds

    // Store interval ID for cleanup
    instance.metadata.healthCheckInterval = healthCheck.toString();
  }

  private markUnhealthy(instance: ServiceInstance): void {
    instance.metadata.healthy = 'false';
    instance.metadata.lastHealthCheck = new Date().toISOString();
  }

  private isHealthy(instance: ServiceInstance): boolean {
    return instance.metadata.healthy !== 'false';
  }
}
```

## Technology-Specific Implementation

### Docker Containerization
```dockerfile
# Multi-stage build for microservice
FROM node:18-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

FROM node:18-alpine AS runtime

# Create non-root user
RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001

WORKDIR /app

# Copy built application
COPY --from=builder --chown=nextjs:nodejs /app/node_modules ./node_modules
COPY --chown=nextjs:nodejs ./dist ./dist
COPY --chown=nextjs:nodejs ./package.json ./package.json

USER nextjs

EXPOSE 3000

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000/health || exit 1

CMD ["npm", "start"]
```

### Kubernetes Deployment
```yaml
# Service deployment with proper resource limits and health checks
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-service
  labels:
    app: user-service
    version: v1
spec:
  replicas: 3
  selector:
    matchLabels:
      app: user-service
  template:
    metadata:
      labels:
        app: user-service
        version: v1
    spec:
      containers:
      - name: user-service
        image: user-service:v1.2.0
        ports:
        - containerPort: 3000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: user-service-secrets
              key: database-url
        - name: REDIS_URL
          valueFrom:
            configMapKeyRef:
              name: user-service-config
              key: redis-url
        resources:
          requests:
            memory: "256Mi"
            cpu: "100m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5
---
apiVersion: v1
kind: Service
metadata:
  name: user-service
spec:
  selector:
    app: user-service
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: ClusterIP
```

## Monitoring and Observability

### Distributed Tracing
```typescript
// OpenTelemetry integration for microservices
import { NodeSDK } from '@opentelemetry/sdk-node';
import { getNodeAutoInstrumentations } from '@opentelemetry/auto-instrumentations-node';
import { Resource } from '@opentelemetry/resources';
import { SemanticResourceAttributes } from '@opentelemetry/semantic-conventions';

const sdk = new NodeSDK({
  resource: new Resource({
    [SemanticResourceAttributes.SERVICE_NAME]: process.env.SERVICE_NAME,
    [SemanticResourceAttributes.SERVICE_VERSION]: process.env.SERVICE_VERSION,
  }),
  instrumentations: [getNodeAutoInstrumentations()],
});

sdk.start();

// Custom span creation
class UserService {
  async createUser(userData: CreateUserRequest): Promise<User> {
    const span = trace.getActiveSpan();
    span?.setAttributes({
      'user.email': userData.email,
      'operation.type': 'create_user'
    });

    try {
      const user = await this.userRepository.create(userData);
      span?.setStatus({ code: SpanStatusCode.OK });
      return user;
    } catch (error) {
      span?.setStatus({
        code: SpanStatusCode.ERROR,
        message: error.message
      });
      throw error;
    }
  }
}
```

### Service Mesh Integration
```yaml
# Istio service mesh configuration
apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: user-service
spec:
  hosts:
  - user-service
  http:
  - timeout: 10s
    retries:
      attempts: 3
      perTryTimeout: 3s
    route:
    - destination:
        host: user-service
        subset: v1
      weight: 90
    - destination:
        host: user-service
        subset: v2
      weight: 10
---
apiVersion: networking.istio.io/v1beta1
kind: DestinationRule
metadata:
  name: user-service
spec:
  host: user-service
  trafficPolicy:
    circuitBreaker:
      consecutiveErrors: 3
      interval: 30s
      baseEjectionTime: 30s
  subsets:
  - name: v1
    labels:
      version: v1
  - name: v2
    labels:
      version: v2
```

## Quality Gates

### ✅ Architecture Compliance
- [ ] Services follow single responsibility principle
- [ ] Data ownership clearly defined per service
- [ ] Inter-service communication patterns implemented correctly
- [ ] Service boundaries align with business domains

### ✅ Resilience Implementation
- [ ] Circuit breaker pattern implemented for external calls
- [ ] Retry logic with exponential backoff configured
- [ ] Timeout handling implemented across all operations
- [ ] Graceful degradation strategies defined

### ✅ Observability Setup
- [ ] Distributed tracing implemented across services
- [ ] Health check endpoints configured
- [ ] Metrics collection enabled
- [ ] Centralized logging configured

## Transition to Specialized Chatmodes

After completing microservices architecture design:

- **For Service Implementation**: Switch to **@api-engineer** chatmode to implement individual service endpoints and business logic
- **For Data Layer Design**: Switch to **@data-engineer** chatmode to design service databases and data access patterns
- **For Infrastructure Setup**: Switch to **@deployment-engineer** chatmode to implement container orchestration and service mesh
- **For Service Testing**: Switch to **@qa-engineer** chatmode to implement comprehensive testing strategies for distributed systems

## 📊 Performance and Scaling Patterns

### Step 8: Caching Strategies

**Multi-Level Caching:**
```typescript
// Cache hierarchy implementation
interface CacheConfig {
  l1_cache: MemoryCacheConfig;
  l2_cache: RedisCacheConfig;
  l3_cache: CdnCacheConfig;
}

class MultilevelCache {
  private memory_cache: MemoryCache;
  private redis_cache: RedisCache;
  private cdn_cache: CdnCache;
  
  constructor(config: CacheConfig) {
    this.memory_cache = new MemoryCache(config.l1_cache);
    this.redis_cache = new RedisCache(config.l2_cache);
    this.cdn_cache = new CdnCache(config.l3_cache);
  }
  
  async get<T>(key: string): Promise<T | null> {
    // L1: In-memory cache
    let value = await this.memory_cache.get<T>(key);
    if (value) {
      return value;
    }
    
    // L2: Redis cache
    value = await this.redis_cache.get<T>(key);
    if (value) {
      // Populate L1 cache
      await this.memory_cache.set(key, value, 300); // 5 min TTL
      return value;
    }
    
    // L3: CDN/Distributed cache
    value = await this.cdn_cache.get<T>(key);
    if (value) {
      // Populate L2 and L1 caches
      await this.redis_cache.set(key, value, 3600); // 1 hour TTL
      await this.memory_cache.set(key, value, 300);  // 5 min TTL
      return value;
    }
    
    return null;
  }
  
  async set(key: string, value: any, ttl?: number): Promise<void> {
    // Set in all cache levels
    await Promise.all([
      this.memory_cache.set(key, value, Math.min(ttl || 300, 300)),
      this.redis_cache.set(key, value, ttl || 3600),
      this.cdn_cache.set(key, value, ttl || 86400)
    ]);
  }
  
  async invalidate(key: string): Promise<void> {
    await Promise.all([
      this.memory_cache.delete(key),
      this.redis_cache.delete(key),
      this.cdn_cache.delete(key)
    ]);
  }
}
```

## Technology-Adaptive Implementation

### Java + Spring Cloud Microservices

**Recommended Pattern:** Spring Cloud ecosystem with Eureka, Gateway, and Config Server

```java
// Service Discovery with Eureka
@SpringBootApplication
@EnableEurekaServer
public class DiscoveryServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(DiscoveryServerApplication.class, args);
    }
}

// API Gateway with Spring Cloud Gateway
@SpringBootApplication
@EnableEurekaClient
public class GatewayApplication {
    
    @Bean
    public RouteLocator customRouteLocator(RouteLocatorBuilder builder) {
        return builder.routes()
            .route("customer-service", r -> r.path("/api/customers/**")
                .filters(f -> f
                    .circuitBreaker(config -> config
                        .setName("customer-service-cb")
                        .setFallbackUri("/fallback/customers"))
                    .retry(retryConfig -> retryConfig.setRetries(3)))
                .uri("lb://customer-service"))
            .route("order-service", r -> r.path("/api/orders/**")
                .filters(f -> f
                    .circuitBreaker(config -> config
                        .setName("order-service-cb")
                        .setFallbackUri("/fallback/orders"))
                    .rateLimit(config -> config
                        .setRateLimiter(RedisRateLimiter.class)
                        .setKeyResolver(exchange -> Mono.just("global"))))
                .uri("lb://order-service"))
            .build();
    }
}

// Microservice Implementation
@RestController
@RequestMapping("/api/customers")
@Slf4j
public class CustomerController {
    
    private final CustomerService customerService;
    private final OrderServiceClient orderServiceClient;
    
    @GetMapping("/{id}")
    @CircuitBreaker(name = "customer-service", fallbackMethod = "getCustomerFallback")
    @TimeLimiter(name = "customer-service")
    @Retry(name = "customer-service")
    public CompletableFuture<ResponseEntity<CustomerDto>> getCustomer(@PathVariable String id) {
        return CompletableFuture.supplyAsync(() -> {
            CustomerDto customer = customerService.findById(id);
            List<OrderDto> orders = orderServiceClient.getOrdersByCustomerId(id);
            customer.setOrders(orders);
            return ResponseEntity.ok(customer);
        });
    }
    
    public CompletableFuture<ResponseEntity<CustomerDto>> getCustomerFallback(
            String id, Exception ex) {
        log.warn("Fallback triggered for customer {}: {}", id, ex.getMessage());
        CustomerDto fallbackCustomer = new CustomerDto();
        fallbackCustomer.setId(id);
        fallbackCustomer.setName("Service Unavailable");
        return CompletableFuture.completedFuture(ResponseEntity.ok(fallbackCustomer));
    }
}

// Feign Client for Inter-Service Communication
@FeignClient(name = "order-service", fallback = OrderServiceClientFallback.class)
public interface OrderServiceClient {
    
    @GetMapping("/api/orders/customer/{customerId}")
    List<OrderDto> getOrdersByCustomerId(@PathVariable("customerId") String customerId);
}

@Component
public class OrderServiceClientFallback implements OrderServiceClient {
    
    @Override
    public List<OrderDto> getOrdersByCustomerId(String customerId) {
        log.warn("Order service unavailable for customer: {}", customerId);
        return Collections.emptyList();
    }
}

// Configuration Properties
@ConfigurationProperties(prefix = "app.microservices")
@Data
public class MicroservicesConfig {
    private Resilience4j resilience4j;
    private ServiceDiscovery serviceDiscovery;
    
    @Data
    public static class Resilience4j {
        private CircuitBreaker circuitBreaker;
        private Retry retry;
        private RateLimiter rateLimiter;
        
        @Data
        public static class CircuitBreaker {
            private int failureRateThreshold = 50;
            private int waitDurationInOpenState = 30000;
            private int slidingWindowSize = 10;
        }
    }
}
```

### .NET Core + Dapr Microservices

**Recommended Pattern:** Dapr sidecar pattern with service mesh capabilities

```csharp
// Startup Configuration for Dapr
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddDaprClient();
        
        // Service registration
        services.AddScoped<ICustomerService, CustomerService>();
        services.AddScoped<IOrderService, OrderService>();
        
        // Health checks
        services.AddHealthChecks()
            .AddCheck<DatabaseHealthCheck>("database")
            .AddDapr();
    }
    
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();
        app.UseCloudEvents();
        
        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllers();
            endpoints.MapSubscribeHandler();
            endpoints.MapHealthChecks("/health");
        });
    }
}

// Customer Service with Dapr State Management
[ApiController]
[Route("api/[controller]")]
public class CustomersController : ControllerBase
{
    private readonly DaprClient _daprClient;
    private readonly ILogger<CustomersController> _logger;
    
    public CustomersController(DaprClient daprClient, ILogger<CustomersController> logger)
    {
        _daprClient = daprClient;
        _logger = logger;
    }
    
    [HttpGet("{id}")]
    public async Task<ActionResult<CustomerDto>> GetCustomer(string id)
    {
        try
        {
            // Get customer from state store
            var customer = await _daprClient.GetStateAsync<CustomerDto>("statestore", id);
            
            if (customer == null)
            {
                return NotFound();
            }
            
            // Call order service via Dapr service invocation
            var orders = await _daprClient.InvokeMethodAsync<List<OrderDto>>(
                "order-service", 
                $"api/orders/customer/{id}", 
                HttpMethod.Get);
                
            customer.Orders = orders;
            return Ok(customer);
        }
        catch (DaprException ex)
        {
            _logger.LogError(ex, "Dapr error occurred while getting customer {CustomerId}", id);
            return StatusCode(500, "Service unavailable");
        }
    }
    
    [HttpPost]
    public async Task<ActionResult<CustomerDto>> CreateCustomer([FromBody] CreateCustomerRequest request)
    {
        var customer = new CustomerDto
        {
            Id = Guid.NewGuid().ToString(),
            Name = request.Name,
            Email = request.Email,
            CreatedAt = DateTime.UtcNow
        };
        
        // Save to state store
        await _daprClient.SaveStateAsync("statestore", customer.Id, customer);
        
        // Publish event
        await _daprClient.PublishEventAsync("pubsub", "customer.created", new CustomerCreatedEvent
        {
            CustomerId = customer.Id,
            Name = customer.Name,
            Email = customer.Email,
            Timestamp = DateTime.UtcNow
        });
        
        return CreatedAtAction(nameof(GetCustomer), new { id = customer.Id }, customer);
    }
    
    // Event handler for order events
    [HttpPost("events/order.completed")]
    [Topic("pubsub", "order.completed")]
    public async Task HandleOrderCompleted([FromBody] OrderCompletedEvent orderEvent)
    {
        _logger.LogInformation("Processing order completed event for customer {CustomerId}", 
            orderEvent.CustomerId);
        
        // Update customer statistics
        var customer = await _daprClient.GetStateAsync<CustomerDto>("statestore", orderEvent.CustomerId);
        if (customer != null)
        {
            customer.TotalOrders += 1;
            customer.TotalSpent += orderEvent.Amount;
            customer.LastOrderDate = orderEvent.CompletedAt;
            
            await _daprClient.SaveStateAsync("statestore", customer.Id, customer);
        }
    }
}

// Dapr Configuration (components/statestore.yaml)
/*
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
*/

// Dapr Pub/Sub Configuration (components/pubsub.yaml)
/*
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    value: ""
*/
```

### Node.js + NestJS + Kubernetes

**Recommended Pattern:** NestJS microservices with Kubernetes native patterns

```typescript
// Main Application with Microservices
@Module({
  imports: [
    ClientsModule.register([
      {
        name: 'ORDER_SERVICE',
        transport: Transport.REDIS,
        options: {
          host: 'redis',
          port: 6379,
        },
      },
      {
        name: 'NOTIFICATION_SERVICE',
        transport: Transport.KAFKA,
        options: {
          client: {
            clientId: 'customer-service',
            brokers: ['kafka:9092'],
          },
          consumer: {
            groupId: 'customer-service-group',
          },
        },
      },
    ]),
    ConfigModule.forRoot(),
    TypeOrmModule.forRoot({
      type: 'postgres',
      host: process.env.DB_HOST,
      port: parseInt(process.env.DB_PORT),
      username: process.env.DB_USERNAME,
      password: process.env.DB_PASSWORD,
      database: process.env.DB_NAME,
      entities: [Customer],
      synchronize: process.env.NODE_ENV !== 'production',
    }),
    TypeOrmModule.forFeature([Customer]),
  ],
  controllers: [CustomerController],
  providers: [CustomerService, HealthController],
})
export class AppModule {}

// Microservice Controller with Circuit Breaker
@Controller('customers')
@ApiTags('customers')
export class CustomerController {
  constructor(
    private readonly customerService: CustomerService,
    @Inject('ORDER_SERVICE') private orderClient: ClientProxy,
    @Inject('NOTIFICATION_SERVICE') private notificationClient: ClientProxy,
  ) {}

  @Get(':id')
  @UseInterceptors(CacheInterceptor)
  @CacheTTL(300) // 5 minutes
  @ApiOperation({ summary: 'Get customer by ID' })
  async getCustomer(@Param('id') id: string): Promise<CustomerDto> {
    const customer = await this.customerService.findById(id);
    
    if (!customer) {
      throw new NotFoundException('Customer not found');
    }

    // Use circuit breaker for external service calls
    try {
      const orders = await this.orderClient
        .send('get_customer_orders', { customerId: id })
        .pipe(
          timeout(5000),
          retry(3),
          catchError((error) => {
            console.warn('Order service unavailable:', error.message);
            return of([]);
          }),
        )
        .toPromise();

      return {
        ...customer,
        orders,
      };
    } catch (error) {
      // Return customer without orders if service is down
      return customer;
    }
  }

  @Post()
  @ApiOperation({ summary: 'Create new customer' })
  async createCustomer(@Body() createCustomerDto: CreateCustomerDto): Promise<CustomerDto> {
    const customer = await this.customerService.create(createCustomerDto);

    // Publish event asynchronously
    this.notificationClient.emit('customer.created', {
      customerId: customer.id,
      email: customer.email,
      name: customer.name,
      timestamp: new Date().toISOString(),
    });

    return customer;
  }

  @EventPattern('order.completed')
  async handleOrderCompleted(@Payload() data: OrderCompletedEvent) {
    try {
      await this.customerService.updateOrderStats(data.customerId, {
        totalOrders: 1,
        totalSpent: data.amount,
        lastOrderDate: data.completedAt,
      });

      console.log(`Updated customer ${data.customerId} order statistics`);
    } catch (error) {
      console.error('Failed to update customer order stats:', error);
      // Could republish to dead letter queue here
    }
  }

  @Get('health')
  @ApiExcludeEndpoint()
  getHealth() {
    return { status: 'ok', timestamp: new Date().toISOString() };
  }
}

// Kubernetes Deployment Configuration
const kubernetesConfig = `
apiVersion: apps/v1
kind: Deployment
metadata:
  name: customer-service
  labels:
    app: customer-service
    version: v1
spec:
  replicas: 3
  selector:
    matchLabels:
      app: customer-service
      version: v1
  template:
    metadata:
      labels:
        app: customer-service
        version: v1
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "3000"
        prometheus.io/path: "/metrics"
    spec:
      containers:
      - name: customer-service
        image: customer-service:latest
        ports:
        - containerPort: 3000
        env:
        - name: DB_HOST
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: host
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: password
        - name: REDIS_URL
          value: "redis://redis:6379"
        - name: KAFKA_BROKERS
          value: "kafka:9092"
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5
---
apiVersion: v1
kind: Service
metadata:
  name: customer-service
  labels:
    app: customer-service
spec:
  selector:
    app: customer-service
  ports:
  - port: 80
    targetPort: 3000
    protocol: TCP
  type: ClusterIP
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: customer-service-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: api.example.com
    http:
      paths:
      - path: /api/customers
        pathType: Prefix
        backend:
          service:
            name: customer-service
            port:
              number: 80
`;

// Service Mesh with Istio Configuration
const istioConfig = `
apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: customer-service
spec:
  hosts:
  - customer-service
  http:
  - fault:
      delay:
        percentage:
          value: 0.1
        fixedDelay: 5s
  - match:
    - headers:
        version:
          exact: v2
    route:
    - destination:
        host: customer-service
        subset: v2
      weight: 100
  - route:
    - destination:
        host: customer-service
        subset: v1
      weight: 90
    - destination:
        host: customer-service
        subset: v2
      weight: 10
  timeout: 30s
  retries:
    attempts: 3
    perTryTimeout: 10s
---
apiVersion: networking.istio.io/v1beta1
kind: DestinationRule
metadata:
  name: customer-service
spec:
  host: customer-service
  subsets:
  - name: v1
    labels:
      version: v1
  - name: v2
    labels:
      version: v2
  trafficPolicy:
    outlierDetection:
      consecutiveErrors: 3
      interval: 30s
      baseEjectionTime: 30s
    circuitBreaker:
      http:
        http1MaxPendingRequests: 10
        maxRequestsPerConnection: 2
      connectionPool:
        tcp:
          maxConnections: 10
`;
```

### Python + FastAPI + asyncio

**Recommended Pattern:** Async microservices with message queues and service discovery

```python
# FastAPI Microservice with Async Patterns
from fastapi import FastAPI, HTTPException, Depends, BackgroundTasks
from fastapi.middleware.cors import CORSMiddleware
from fastapi.middleware.trustedhost import TrustedHostMiddleware
import asyncio
import aioredis
from typing import List, Optional
import httpx
from contextlib import asynccontextmanager
import logging
from prometheus_fastapi_instrumentator import Instrumentator

# Application Lifespan Management
@asynccontextmanager
async def lifespan(app: FastAPI):
    # Startup
    app.state.redis = await aioredis.from_url("redis://redis:6379")
    app.state.http_client = httpx.AsyncClient()
    app.state.service_registry = ServiceRegistry()
    
    # Register service
    await app.state.service_registry.register_service(
        service_name="customer-service",
        host="customer-service",
        port=8000,
        health_check="/health"
    )
    
    yield
    
    # Shutdown
    await app.state.redis.close()
    await app.state.http_client.aclose()
    await app.state.service_registry.deregister_service("customer-service")

# FastAPI Application
app = FastAPI(
    title="Customer Service",
    version="1.0.0",
    lifespan=lifespan
)

# Middleware
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

app.add_middleware(
    TrustedHostMiddleware,
    allowed_hosts=["customer-service", "*.example.com"]
)

# Metrics
Instrumentator().instrument(app).expose(app)

# Service Discovery
class ServiceRegistry:
    def __init__(self):
        self.services = {}
        
    async def register_service(self, service_name: str, host: str, port: int, health_check: str):
        self.services[service_name] = {
            "host": host,
            "port": port,
            "health_check": health_check,
            "last_seen": asyncio.get_event_loop().time()
        }
        
    async def get_service(self, service_name: str) -> Optional[dict]:
        return self.services.get(service_name)
        
    async def deregister_service(self, service_name: str):
        self.services.pop(service_name, None)

# Circuit Breaker Implementation
class CircuitBreaker:
    def __init__(self, failure_threshold: int = 5, recovery_timeout: int = 30):
        self.failure_threshold = failure_threshold
        self.recovery_timeout = recovery_timeout
        self.failure_count = 0
        self.last_failure_time = None
        self.state = "CLOSED"  # CLOSED, OPEN, HALF_OPEN
        
    async def call(self, func, *args, **kwargs):
        if self.state == "OPEN":
            if asyncio.get_event_loop().time() - self.last_failure_time > self.recovery_timeout:
                self.state = "HALF_OPEN"
            else:
                raise HTTPException(status_code=503, detail="Circuit breaker is OPEN")
                
        try:
            result = await func(*args, **kwargs)
            if self.state == "HALF_OPEN":
                self.state = "CLOSED"
                self.failure_count = 0
            return result
        except Exception as e:
            self.failure_count += 1
            self.last_failure_time = asyncio.get_event_loop().time()
            
            if self.failure_count >= self.failure_threshold:
                self.state = "OPEN"
                
            raise e

# Service Communication with Retry and Circuit Breaker
class ServiceCommunication:
    def __init__(self):
        self.circuit_breakers = {}
        
    def get_circuit_breaker(self, service_name: str) -> CircuitBreaker:
        if service_name not in self.circuit_breakers:
            self.circuit_breakers[service_name] = CircuitBreaker()
        return self.circuit_breakers[service_name]
    
    async def call_service(self, service_name: str, path: str, method: str = "GET", **kwargs):
        circuit_breaker = self.get_circuit_breaker(service_name)
        
        async def make_request():
            service_info = await app.state.service_registry.get_service(service_name)
            if not service_info:
                raise HTTPException(status_code=503, detail=f"Service {service_name} not found")
                
            url = f"http://{service_info['host']}:{service_info['port']}{path}"
            
            # Retry logic with exponential backoff
            max_retries = 3
            base_delay = 1
            
            for attempt in range(max_retries):
                try:
                    async with app.state.http_client as client:
                        response = await client.request(method, url, timeout=5.0, **kwargs)
                        response.raise_for_status()
                        return response.json()
                except httpx.TimeoutException:
                    if attempt == max_retries - 1:
                        raise HTTPException(status_code=504, detail="Service timeout")
                    await asyncio.sleep(base_delay * (2 ** attempt))
                except httpx.HTTPStatusError as e:
                    if e.response.status_code >= 500:
                        if attempt == max_retries - 1:
                            raise HTTPException(status_code=e.response.status_code, 
                                             detail="Service unavailable")
                        await asyncio.sleep(base_delay * (2 ** attempt))
                    else:
                        raise HTTPException(status_code=e.response.status_code, 
                                         detail="Service error")
        
        return await circuit_breaker.call(make_request)

# Dependencies
async def get_redis():
    return app.state.redis

async def get_service_communication():
    return ServiceCommunication()

# API Routes
@app.get("/api/customers/{customer_id}")
async def get_customer(
    customer_id: str, 
    redis: aioredis.Redis = Depends(get_redis),
    service_comm: ServiceCommunication = Depends(get_service_communication)
):
    # Try cache first
    cached_customer = await redis.get(f"customer:{customer_id}")
    if cached_customer:
        customer_data = json.loads(cached_customer)
    else:
        # Get from database (simplified)
        customer_data = await get_customer_from_db(customer_id)
        if not customer_data:
            raise HTTPException(status_code=404, detail="Customer not found")
            
        # Cache for 5 minutes
        await redis.setex(f"customer:{customer_id}", 300, json.dumps(customer_data))
    
    # Get orders from order service with circuit breaker
    try:
        orders = await service_comm.call_service(
            "order-service", 
            f"/api/orders/customer/{customer_id}"
        )
        customer_data["orders"] = orders
    except HTTPException as e:
        logging.warning(f"Failed to get orders for customer {customer_id}: {e.detail}")
        customer_data["orders"] = []
    
    return customer_data

@app.post("/api/customers")
async def create_customer(
    customer_data: CustomerCreateRequest,
    background_tasks: BackgroundTasks,
    redis: aioredis.Redis = Depends(get_redis)
):
    # Create customer (simplified)
    customer = await create_customer_in_db(customer_data)
    
    # Cache the new customer
    await redis.setex(f"customer:{customer['id']}", 300, json.dumps(customer))
    
    # Publish event asynchronously
    background_tasks.add_task(
        publish_customer_created_event, 
        customer['id'], 
        customer['email']
    )
    
    return customer

# Event Publishing
async def publish_customer_created_event(customer_id: str, email: str):
    try:
        # Publish to Redis Streams or message queue
        await app.state.redis.xadd(
            "customer.events",
            {
                "event_type": "customer.created",
                "customer_id": customer_id,
                "email": email,
                "timestamp": datetime.utcnow().isoformat()
            }
        )
        logging.info(f"Published customer.created event for {customer_id}")
    except Exception as e:
        logging.error(f"Failed to publish customer.created event: {e}")

# Health Check
@app.get("/health")
async def health_check():
    return {
        "status": "healthy",
        "timestamp": datetime.utcnow().isoformat(),
        "version": "1.0.0"
    }

# Docker Compose Configuration for Development
docker_compose_config = """
version: '3.8'
services:
  customer-service:
    build: .
    ports:
      - "8000:8000"
    environment:
      - REDIS_URL=redis://redis:6379
      - DATABASE_URL=postgresql://user:pass@postgres:5432/customers
    depends_on:
      - redis
      - postgres
    deploy:
      replicas: 2
      restart_policy:
        condition: on-failure
        delay: 5s
        max_attempts: 3
        
  redis:
    image: redis:alpine
    ports:
      - "6379:6379"
      
  postgres:
    image: postgres:13
    environment:
      POSTGRES_DB: customers
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
"""
```

### Generic/Fallback Implementation

For unsupported technologies, provide generic microservices patterns:

```yaml
# Generic Microservices Configuration
microservices:
  architecture_pattern: "service_per_domain"
  communication:
    sync: "HTTP/REST with API Gateway"
    async: "Message Queue (Redis/RabbitMQ/Kafka)"
  
  service_discovery: "DNS-based or Registry-based"
  load_balancing: "Round-robin or Weighted"
  
  resilience_patterns:
    - circuit_breaker
    - retry_with_exponential_backoff
    - timeout_handling
    - bulkhead_isolation
    
  data_management: "Database-per-service"
  
  observability:
    tracing: "Distributed tracing with correlation IDs"
    metrics: "Prometheus + Grafana"
    logging: "Centralized logging with ELK stack"
    
  deployment: "Containerized with Kubernetes or Docker Swarm"
  
  security:
    authentication: "JWT with shared secret or PKI"
    authorization: "Role-based or Attribute-based"
    communication: "mTLS for service-to-service"
```

## 📤 Deliverables

- **Microservices Architecture Design** with service boundaries and communication patterns
- **Service Implementation** with API specifications and inter-service contracts
- **Event-Driven Architecture** with event schemas and saga implementations
- **Service Mesh Configuration** with traffic management and security policies
- **Observability Stack** with tracing, metrics, and logging infrastructure
- **Resilience Patterns** with circuit breakers, retries, and failover mechanisms
- **Documentation** with architecture diagrams, API docs, and operational runbooks

## 🤝 Collaboration Points

**With software-architect:** Overall system architecture alignment and technology stack decisions
**With data-engineer:** Data consistency patterns, event sourcing, and cross-service queries
**With security-engineer:** Service-to-service authentication, network security, and data protection
**With deployment-engineer:** Container orchestration, service mesh deployment, and infrastructure scaling
**With qa-engineer:** Contract testing, integration testing, and chaos engineering practices

## Implementation Strategy

### 1. Technology Detection

Analyze copilot.instructions.md configuration to determine:
- **Microservices framework** from primary_language field (Java/Spring Cloud, .NET/Dapr, Node.js/NestJS, Python/FastAPI)
- **Communication requirements** for synchronous vs asynchronous patterns
- **Infrastructure preferences** for container orchestration and service mesh
- **Data consistency needs** for event sourcing vs traditional approaches

### 2. Architecture Pattern Selection

Select patterns based on detected technology and scale:
- **Java/Spring Cloud**: Eureka discovery, Config Server, Gateway, Circuit Breaker
- **.NET/Dapr**: Sidecar pattern with state management and pub/sub
- **Node.js/NestJS**: Kubernetes-native with message queues and caching
- **Python/FastAPI**: Async patterns with service discovery and circuit breakers
- **Generic**: Standard microservices patterns with resilience and observability

### 3. Implementation Approach

Apply technology-specific microservices patterns:
- **Service decomposition**: Domain-driven design with bounded contexts
- **Communication**: Framework-appropriate sync/async patterns
- **Data management**: Database-per-service with eventual consistency
- **Resilience**: Circuit breakers, retries, and timeout handling
- **Observability**: Distributed tracing, metrics, and structured logging

### 4. Success Criteria

Microservices architecture validation checklist:
- **Technology alignment**: Implementation follows framework best practices
- **Service boundaries**: Clear domain separation with minimal coupling
- **Scalability**: Independent service scaling and deployment
- **Resilience**: Fault tolerance with graceful degradation
- **Observability**: Comprehensive monitoring and debugging capabilities

## Transition to Specialized Chatmodes

After completing microservices architecture design:

- **For Service Implementation**: Switch to **@api-engineer** chatmode to implement individual service endpoints and business logic
- **For Data Layer Design**: Switch to **@data-engineer** chatmode to design service databases and data access patterns
- **For Infrastructure Setup**: Switch to **@deployment-engineer** chatmode to implement container orchestration and service mesh
- **For Service Testing**: Switch to **@qa-engineer** chatmode to implement comprehensive testing strategies for distributed systems

**This prompt ensures microservices architecture follows best practices for scalability, resilience, and maintainability while adapting to project-specific requirements defined in copilot.instructions.md.**