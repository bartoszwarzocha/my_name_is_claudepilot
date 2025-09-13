---
description: Design and implement scalable, secure REST APIs following best practices with comprehensive validation, error handling, and documentation. Adapts to project specifications defined in copilot.instructions.md.
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

# REST API Design and Implementation

Create robust, well-documented REST APIs that serve as the backbone for frontend applications and external integrations, following RESTful principles and industry standards while adapting to the technology stack specified in copilot.instructions.md.

## Context Adaptation

**IMPORTANT**: Always read the `copilot.instructions.md` file in the project root directory at the beginning of your work to adapt your implementation to:

- Backend framework and primary language (Spring Boot, .NET Core, NestJS, FastAPI, etc.)
- Business domain requirements and API patterns
- Authentication and authorization requirements
- Database technology and ORM preferences
- Performance and scalability expectations

## Mission

Create robust, well-documented REST APIs that serve as the backbone for frontend applications and external integrations, following RESTful principles and industry standards.

## API Design Process

### Step 1: Requirements Analysis

**Technology Stack Detection:**
```bash
# Read project configuration to determine backend technology
cat copilot.instructions.md | grep -A 5 "primary_language\|Backend\|Technologies"

# Analyze existing project structure
find . -name "*.csproj" -o -name "pom.xml" -o -name "package.json" -o -name "requirements.txt" | head -3
ls -la Controllers/ Models/ Services/ src/ api/ 2>/dev/null | head -10
```

**Requirements Gathering:**
- **Functional requirements** from business logic analysis
- **Data models** and entity relationships mapping
- **Integration needs** with external systems
- **Performance requirements** and expected load patterns
- **Security requirements** and compliance standards

### Step 2: API Contract Design

**Resource Identification:**
```yaml
# Example API Resource Mapping
resources:
  users:
    base_url: "/api/v1/users"
    operations:
      - GET /users (list with pagination)
      - POST /users (create)
      - GET /users/{id} (get by id)
      - PUT /users/{id} (update)
      - PATCH /users/{id} (partial update)
      - DELETE /users/{id} (delete)
    
  user_orders:
    base_url: "/api/v1/users/{userId}/orders"
    operations:
      - GET /users/{userId}/orders (nested resource)
      - POST /users/{userId}/orders (create order for user)
```

**HTTP Methods Mapping:**
- **GET** - Retrieve resources (safe, idempotent)
- **POST** - Create new resources (not idempotent)
- **PUT** - Update entire resources (idempotent)
- **PATCH** - Partial resource updates (not necessarily idempotent)
- **DELETE** - Remove resources (idempotent)

**URL Structure Design:**
```
/api/v1/users                    # Collection of users
/api/v1/users/{id}              # Specific user
/api/v1/users/{id}/orders       # User's orders (nested resource)
/api/v1/orders?status=pending   # Filtered collection
/api/v1/search/users?q=john     # Search endpoint
```

### Step 3: Technology-Adaptive Implementation

**Java + Spring Boot Pattern:**
```java
// Entity Layer with JPA
@Entity
@Table(name = "users")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(unique = true, nullable = false)
    @Email
    private String email;
    
    @Column(nullable = false)
    @Size(min = 2, max = 100)
    private String name;
    
    @Enumerated(EnumType.STRING)
    private UserStatus status = UserStatus.ACTIVE;
    
    @CreationTimestamp
    private LocalDateTime createdAt;
    
    @UpdateTimestamp
    private LocalDateTime updatedAt;
    
    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Order> orders = new ArrayList<>();
}

// Repository Layer
@Repository
public interface UserRepository extends JpaRepository<User, Long>, JpaSpecificationExecutor<User> {
    Optional<User> findByEmail(String email);
    
    @Query("SELECT u FROM User u WHERE u.status = :status")
    Page<User> findByStatus(@Param("status") UserStatus status, Pageable pageable);
    
    @Query("SELECT u FROM User u WHERE u.name ILIKE %:searchTerm% OR u.email ILIKE %:searchTerm%")
    Page<User> searchUsers(@Param("searchTerm") String searchTerm, Pageable pageable);
}

// Service Layer with Business Logic
@Service
@Transactional
@RequiredArgsConstructor
public class UserService {
    private final UserRepository userRepository;
    private final UserMapper userMapper;
    private final PasswordEncoder passwordEncoder;

    public UserResponseDto createUser(CreateUserRequestDto request) {
        // Business validation
        if (userRepository.findByEmail(request.getEmail()).isPresent()) {
            throw new UserAlreadyExistsException("User with email already exists");
        }
        
        // Map and save
        User user = userMapper.toEntity(request);
        user.setPassword(passwordEncoder.encode(request.getPassword()));
        User savedUser = userRepository.save(user);
        
        return userMapper.toResponseDto(savedUser);
    }
    
    public Page<UserResponseDto> getUsers(UserFilterCriteria criteria, Pageable pageable) {
        Specification<User> spec = UserSpecifications.withCriteria(criteria);
        return userRepository.findAll(spec, pageable)
                .map(userMapper::toResponseDto);
    }
    
    public UserResponseDto getUserById(Long id) {
        return userRepository.findById(id)
                .map(userMapper::toResponseDto)
                .orElseThrow(() -> new UserNotFoundException("User not found with id: " + id));
    }
}

// Controller Layer with Comprehensive Documentation
@RestController
@RequestMapping("/api/v1/users")
@RequiredArgsConstructor
@Validated
@Tag(name = "Users", description = "User management operations")
public class UserController {
    private final UserService userService;
    
    @PostMapping
    @Operation(summary = "Create new user", description = "Creates a new user account with the provided information")
    @ApiResponses({
        @ApiResponse(responseCode = "201", description = "User created successfully"),
        @ApiResponse(responseCode = "400", description = "Invalid request data"),
        @ApiResponse(responseCode = "409", description = "User already exists")
    })
    public ResponseEntity<ApiResponse<UserResponseDto>> createUser(
            @Valid @RequestBody CreateUserRequestDto request) {
        
        UserResponseDto user = userService.createUser(request);
        
        return ResponseEntity.status(HttpStatus.CREATED)
                .location(URI.create("/api/v1/users/" + user.getId()))
                .body(ApiResponse.success(user, "User created successfully"));
    }
    
    @GetMapping
    @Operation(summary = "Get users", description = "Retrieve users with filtering and pagination")
    public ResponseEntity<ApiResponse<PagedResult<UserResponseDto>>> getUsers(
            @Valid UserFilterCriteria criteria,
            @PageableDefault(size = 20, sort = "name") Pageable pageable) {
        
        Page<UserResponseDto> users = userService.getUsers(criteria, pageable);
        return ResponseEntity.ok(ApiResponse.success(PagedResult.of(users)));
    }
    
    @GetMapping("/{id}")
    @Operation(summary = "Get user by ID", description = "Retrieve specific user by their ID")
    public ResponseEntity<ApiResponse<UserResponseDto>> getUserById(
            @PathVariable @Positive Long id) {
        
        UserResponseDto user = userService.getUserById(id);
        return ResponseEntity.ok(ApiResponse.success(user));
    }
}

// Global Exception Handler
@ControllerAdvice
@Slf4j
public class GlobalExceptionHandler {
    
    @ExceptionHandler(UserNotFoundException.class)
    public ResponseEntity<ApiResponse<Void>> handleUserNotFound(UserNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
                .body(ApiResponse.error("USER_NOT_FOUND", ex.getMessage()));
    }
    
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<ApiResponse<Void>> handleValidationException(
            MethodArgumentNotValidException ex) {
        
        List<ValidationError> errors = ex.getBindingResult().getFieldErrors()
                .stream()
                .map(error -> ValidationError.builder()
                        .field(error.getField())
                        .message(error.getDefaultMessage())
                        .rejectedValue(error.getRejectedValue())
                        .build())
                .collect(Collectors.toList());
        
        return ResponseEntity.status(HttpStatus.BAD_REQUEST)
                .body(ApiResponse.validationError("Request validation failed", errors));
    }
}
```

**.NET Core + Clean Architecture Pattern:**
```csharp
// Domain Entity
public class User : BaseEntity
{
    public string Email { get; private set; }
    public string Name { get; private set; }
    public UserStatus Status { get; private set; }
    public string PasswordHash { get; private set; }
    
    private readonly List<Order> _orders = new();
    public IReadOnlyCollection<Order> Orders => _orders.AsReadOnly();

    public User(string email, string name, string passwordHash)
    {
        Email = email ?? throw new ArgumentNullException(nameof(email));
        Name = name ?? throw new ArgumentNullException(nameof(name));
        PasswordHash = passwordHash ?? throw new ArgumentNullException(nameof(passwordHash));
        Status = UserStatus.Active;
    }

    public void UpdateProfile(string name)
    {
        Name = name ?? throw new ArgumentNullException(nameof(name));
        UpdatedAt = DateTime.UtcNow;
    }

    public void Deactivate()
    {
        Status = UserStatus.Inactive;
        UpdatedAt = DateTime.UtcNow;
    }
}

// Application Command/Query
public record CreateUserCommand(string Email, string Name, string Password) : IRequest<ApiResult<UserDto>>;

public record GetUserByIdQuery(long Id) : IRequest<ApiResult<UserDto>>;

public record GetUsersQuery(UserFilterCriteria Criteria, int Page, int PageSize) : IRequest<ApiResult<PagedResult<UserDto>>>;

// Command Handler
public class CreateUserHandler : IRequestHandler<CreateUserCommand, ApiResult<UserDto>>
{
    private readonly IUserRepository _repository;
    private readonly IPasswordService _passwordService;
    private readonly IMapper _mapper;

    public CreateUserHandler(IUserRepository repository, IPasswordService passwordService, IMapper mapper)
    {
        _repository = repository;
        _passwordService = passwordService;
        _mapper = mapper;
    }

    public async Task<ApiResult<UserDto>> Handle(CreateUserCommand request, CancellationToken cancellationToken)
    {
        // Check if user exists
        if (await _repository.ExistsByEmailAsync(request.Email))
        {
            return ApiResult<UserDto>.Failure("User with this email already exists");
        }

        // Create user entity
        var passwordHash = _passwordService.HashPassword(request.Password);
        var user = new User(request.Email, request.Name, passwordHash);

        // Save to repository
        await _repository.AddAsync(user, cancellationToken);
        await _repository.SaveChangesAsync(cancellationToken);

        // Return mapped result
        var userDto = _mapper.Map<UserDto>(user);
        return ApiResult<UserDto>.Success(userDto);
    }
}

// API Controller
[ApiController]
[Route("api/v1/[controller]")]
[Produces("application/json")]
public class UsersController : ControllerBase
{
    private readonly IMediator _mediator;

    public UsersController(IMediator mediator)
    {
        _mediator = mediator;
    }

    /// <summary>
    /// Creates a new user account
    /// </summary>
    /// <param name="command">User creation data</param>
    /// <returns>Created user information</returns>
    [HttpPost]
    [ProducesResponseType(typeof(ApiResponse<UserDto>), StatusCodes.Status201Created)]
    [ProducesResponseType(typeof(ApiResponse<object>), StatusCodes.Status400BadRequest)]
    [ProducesResponseType(typeof(ApiResponse<object>), StatusCodes.Status409Conflict)]
    public async Task<ActionResult<ApiResponse<UserDto>>> CreateUser([FromBody] CreateUserCommand command)
    {
        var result = await _mediator.Send(command);

        if (result.IsSuccess)
        {
            return CreatedAtAction(
                nameof(GetUserById), 
                new { id = result.Data.Id }, 
                ApiResponse<UserDto>.Success(result.Data, "User created successfully"));
        }

        return BadRequest(ApiResponse<object>.Error(result.ErrorMessage));
    }

    /// <summary>
    /// Retrieves a user by their ID
    /// </summary>
    /// <param name="id">User ID</param>
    /// <returns>User information</returns>
    [HttpGet("{id:long}")]
    [ProducesResponseType(typeof(ApiResponse<UserDto>), StatusCodes.Status200OK)]
    [ProducesResponseType(typeof(ApiResponse<object>), StatusCodes.Status404NotFound)]
    public async Task<ActionResult<ApiResponse<UserDto>>> GetUserById(long id)
    {
        var result = await _mediator.Send(new GetUserByIdQuery(id));

        if (result.IsSuccess)
        {
            return Ok(ApiResponse<UserDto>.Success(result.Data));
        }

        return NotFound(ApiResponse<object>.Error("User not found"));
    }
}
```

**Node.js + TypeScript + Express Pattern:**
```typescript
// Entity/Model Definition
import { Entity, PrimaryGeneratedColumn, Column, CreateDateColumn, UpdateDateColumn, OneToMany } from 'typeorm';
import { Order } from './Order';

export enum UserStatus {
  ACTIVE = 'active',
  INACTIVE = 'inactive',
  SUSPENDED = 'suspended'
}

@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ unique: true })
  email: string;

  @Column()
  name: string;

  @Column()
  passwordHash: string;

  @Column({
    type: 'enum',
    enum: UserStatus,
    default: UserStatus.ACTIVE
  })
  status: UserStatus;

  @CreateDateColumn()
  createdAt: Date;

  @UpdateDateColumn()
  updatedAt: Date;

  @OneToMany(() => Order, order => order.user)
  orders: Order[];
}

// DTOs with Validation
import { IsEmail, IsString, Length, IsEnum, IsOptional } from 'class-validator';
import { ApiProperty, ApiPropertyOptional } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ description: 'User email address', example: 'user@example.com' })
  @IsEmail({}, { message: 'Please provide a valid email address' })
  email: string;

  @ApiProperty({ description: 'User full name', example: 'John Doe' })
  @IsString()
  @Length(2, 100, { message: 'Name must be between 2 and 100 characters' })
  name: string;

  @ApiProperty({ description: 'User password', example: 'SecurePassword123!' })
  @IsString()
  @Length(8, 128, { message: 'Password must be between 8 and 128 characters' })
  password: string;
}

export class UserResponseDto {
  @ApiProperty({ description: 'User ID', example: 1 })
  id: number;

  @ApiProperty({ description: 'User email', example: 'user@example.com' })
  email: string;

  @ApiProperty({ description: 'User name', example: 'John Doe' })
  name: string;

  @ApiProperty({ description: 'User status', enum: UserStatus })
  status: UserStatus;

  @ApiProperty({ description: 'Creation date' })
  createdAt: Date;

  @ApiProperty({ description: 'Last update date' })
  updatedAt: Date;
}

// Service Layer
import { Injectable, ConflictException, NotFoundException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import * as bcrypt from 'bcrypt';

@Injectable()
export class UserService {
  constructor(
    @InjectRepository(User)
    private userRepository: Repository<User>
  ) {}

  async createUser(createUserDto: CreateUserDto): Promise<UserResponseDto> {
    // Check if user exists
    const existingUser = await this.userRepository.findOne({
      where: { email: createUserDto.email }
    });

    if (existingUser) {
      throw new ConflictException('User with this email already exists');
    }

    // Hash password and create user
    const passwordHash = await bcrypt.hash(createUserDto.password, 12);
    const user = this.userRepository.create({
      email: createUserDto.email,
      name: createUserDto.name,
      passwordHash
    });

    const savedUser = await this.userRepository.save(user);
    return this.mapToResponseDto(savedUser);
  }

  async findUserById(id: number): Promise<UserResponseDto> {
    const user = await this.userRepository.findOne({ where: { id } });
    
    if (!user) {
      throw new NotFoundException('User not found');
    }

    return this.mapToResponseDto(user);
  }

  async findUsers(page: number = 1, limit: number = 20): Promise<{ users: UserResponseDto[], total: number }> {
    const [users, total] = await this.userRepository.findAndCount({
      skip: (page - 1) * limit,
      take: limit,
      order: { createdAt: 'DESC' }
    });

    return {
      users: users.map(user => this.mapToResponseDto(user)),
      total
    };
  }

  private mapToResponseDto(user: User): UserResponseDto {
    return {
      id: user.id,
      email: user.email,
      name: user.name,
      status: user.status,
      createdAt: user.createdAt,
      updatedAt: user.updatedAt
    };
  }
}

// Controller
import { Controller, Get, Post, Put, Delete, Body, Param, Query, ParseIntPipe, ValidationPipe, UseGuards } from '@nestjs/common';
import { ApiTags, ApiOperation, ApiResponse, ApiParam, ApiQuery, ApiBearerAuth } from '@nestjs/swagger';
import { JwtAuthGuard } from '../auth/jwt-auth.guard';

@ApiTags('users')
@Controller('api/v1/users')
@UseGuards(JwtAuthGuard)
@ApiBearerAuth()
export class UserController {
  constructor(private readonly userService: UserService) {}

  @Post()
  @ApiOperation({ summary: 'Create a new user' })
  @ApiResponse({ status: 201, description: 'User created successfully', type: UserResponseDto })
  @ApiResponse({ status: 400, description: 'Invalid input data' })
  @ApiResponse({ status: 409, description: 'User already exists' })
  async createUser(@Body(ValidationPipe) createUserDto: CreateUserDto): Promise<ApiResponse<UserResponseDto>> {
    const user = await this.userService.createUser(createUserDto);
    return ApiResponse.success(user, 'User created successfully');
  }

  @Get(':id')
  @ApiOperation({ summary: 'Get user by ID' })
  @ApiParam({ name: 'id', description: 'User ID', type: 'number' })
  @ApiResponse({ status: 200, description: 'User found', type: UserResponseDto })
  @ApiResponse({ status: 404, description: 'User not found' })
  async getUserById(@Param('id', ParseIntPipe) id: number): Promise<ApiResponse<UserResponseDto>> {
    const user = await this.userService.findUserById(id);
    return ApiResponse.success(user);
  }

  @Get()
  @ApiOperation({ summary: 'Get users with pagination' })
  @ApiQuery({ name: 'page', required: false, type: Number, description: 'Page number' })
  @ApiQuery({ name: 'limit', required: false, type: Number, description: 'Items per page' })
  @ApiResponse({ status: 200, description: 'Users retrieved successfully' })
  async getUsers(
    @Query('page', ParseIntPipe) page: number = 1,
    @Query('limit', ParseIntPipe) limit: number = 20
  ): Promise<ApiResponse<{ users: UserResponseDto[], pagination: any }>> {
    const { users, total } = await this.userService.findUsers(page, limit);
    
    const pagination = {
      page,
      limit,
      total,
      totalPages: Math.ceil(total / limit),
      hasNext: page * limit < total,
      hasPrevious: page > 1
    };

    return ApiResponse.success({ users, pagination });
  }
}
```

### Step 4: Advanced API Patterns

**Pagination Implementation:**
```typescript
// Cursor-based pagination for large datasets
interface PaginationOptions {
  limit: number;
  cursor?: string;
  direction: 'forward' | 'backward';
}

interface PaginatedResult<T> {
  data: T[];
  pagination: {
    hasNext: boolean;
    hasPrevious: boolean;
    nextCursor?: string;
    previousCursor?: string;
    total?: number;
  };
}

class PaginationService {
  static async paginateQuery<T>(
    query: SelectQueryBuilder<T>,
    options: PaginationOptions,
    cursorField: string = 'id'
  ): Promise<PaginatedResult<T>> {
    
    const { limit, cursor, direction } = options;
    const actualLimit = Math.min(limit, 100) + 1; // +1 to check for hasNext
    
    if (cursor) {
      const operator = direction === 'forward' ? '>' : '<';
      query.andWhere(`${cursorField} ${operator} :cursor`, { cursor });
    }
    
    const orderDirection = direction === 'forward' ? 'ASC' : 'DESC';
    query.orderBy(cursorField, orderDirection).limit(actualLimit);
    
    const results = await query.getMany();
    const hasMore = results.length > limit;
    
    if (hasMore) {
      results.pop(); // Remove the extra item
    }
    
    const hasNext = direction === 'forward' ? hasMore : cursor !== undefined;
    const hasPrevious = direction === 'backward' ? hasMore : cursor !== undefined;
    
    return {
      data: results,
      pagination: {
        hasNext,
        hasPrevious,
        nextCursor: hasNext ? results[results.length - 1][cursorField] : undefined,
        previousCursor: hasPrevious ? results[0][cursorField] : undefined
      }
    };
  }
}
```

**Rate Limiting Implementation:**
```typescript
import Redis from 'ioredis';

interface RateLimitConfig {
  windowMs: number;
  maxRequests: number;
  keyGenerator: (req: Request) => string;
}

class RateLimiter {
  constructor(
    private redis: Redis,
    private config: RateLimitConfig
  ) {}

  async checkLimit(req: Request): Promise<{ allowed: boolean; resetTime: number; remaining: number }> {
    const key = this.config.keyGenerator(req);
    const window = Math.floor(Date.now() / this.config.windowMs);
    const redisKey = `rate_limit:${key}:${window}`;
    
    const current = await this.redis.incr(redisKey);
    
    if (current === 1) {
      await this.redis.expire(redisKey, Math.ceil(this.config.windowMs / 1000));
    }
    
    const resetTime = (window + 1) * this.config.windowMs;
    const remaining = Math.max(0, this.config.maxRequests - current);
    
    return {
      allowed: current <= this.config.maxRequests,
      resetTime,
      remaining
    };
  }
}

// Middleware usage
const rateLimiter = new RateLimiter(redis, {
  windowMs: 15 * 60 * 1000, // 15 minutes
  maxRequests: 100,
  keyGenerator: (req) => req.ip + ':' + (req.user?.id || 'anonymous')
});

const rateLimitMiddleware = async (req: Request, res: Response, next: NextFunction) => {
  const result = await rateLimiter.checkLimit(req);
  
  res.set({
    'X-RateLimit-Limit': rateLimiter.config.maxRequests.toString(),
    'X-RateLimit-Remaining': result.remaining.toString(),
    'X-RateLimit-Reset': new Date(result.resetTime).toISOString()
  });
  
  if (!result.allowed) {
    return res.status(429).json({
      error: 'RATE_LIMIT_EXCEEDED',
      message: 'Too many requests, please try again later',
      retryAfter: Math.ceil((result.resetTime - Date.now()) / 1000)
    });
  }
  
  next();
};
```

## Quality Gates

### ✅ API Design Compliance
- [ ] RESTful principles correctly applied
- [ ] HTTP methods used appropriately
- [ ] Resource URLs follow conventions
- [ ] Response status codes are appropriate

### ✅ Security Implementation
- [ ] Authentication and authorization implemented
- [ ] Input validation and sanitization active
- [ ] Rate limiting configured
- [ ] HTTPS enforcement and security headers set

### ✅ Documentation Quality
- [ ] OpenAPI/Swagger specification complete
- [ ] All endpoints documented with examples
- [ ] Error responses documented
- [ ] Authentication requirements clear

### ✅ Performance & Reliability
- [ ] Pagination implemented for collections
- [ ] Database queries optimized
- [ ] Caching strategy implemented
- [ ] Error handling comprehensive

## Transition to Specialized Chatmodes

After completing REST API design and implementation:

- **For Frontend Integration**: Switch to **@frontend-engineer** chatmode to integrate with the implemented APIs
- **For Security Implementation**: Switch to **@security-engineer** chatmode to implement API security controls and vulnerability assessments
- **For Database Optimization**: Switch to **@data-engineer** chatmode to optimize database queries and implement efficient data access patterns
- **For API Testing**: Switch to **@qa-engineer** chatmode to implement comprehensive API testing strategies and automated test suites

## 📊 API Quality Standards

### Performance Requirements
- **Response time** targets (e.g., < 200ms for simple queries)
- **Throughput** handling (requests per second)
- **Caching strategies** (Redis, CDN, HTTP caching)
- **Database optimization** (indexing, query tuning)

### Documentation Standards
- **OpenAPI/Swagger** specification
- **Interactive API documentation** with examples
- **Authentication guide** and setup instructions
- **Error code reference** with explanations
- **SDK/client library** generation support

### Testing Strategy
- **Unit tests** for business logic and validations
- **Integration tests** for database interactions
- **Contract tests** for API compatibility
- **Load tests** for performance validation
- **Security tests** for vulnerability assessment

## 🔄 Common API Patterns

### CRUD Operations
```javascript
// Create
POST /api/v1/users
Content-Type: application/json
{ "name": "John Doe", "email": "john@example.com" }

// Read
GET /api/v1/users/123
GET /api/v1/users?page=1&limit=20&sort=name

// Update
PUT /api/v1/users/123
PATCH /api/v1/users/123

// Delete  
DELETE /api/v1/users/123
```

### Pagination Pattern
```javascript
GET /api/v1/users?page=2&limit=20

Response:
{
  "data": [...],
  "meta": {
    "page": 2,
    "limit": 20, 
    "total": 150,
    "totalPages": 8
  },
  "links": {
    "first": "/api/v1/users?page=1&limit=20",
    "prev": "/api/v1/users?page=1&limit=20", 
    "next": "/api/v1/users?page=3&limit=20",
    "last": "/api/v1/users?page=8&limit=20"
  }
}
```

### Filtering and Searching
```javascript
// Simple filtering
GET /api/v1/users?status=active&role=admin

// Text search
GET /api/v1/users?search=john

// Advanced filtering
GET /api/v1/orders?created_after=2023-01-01&amount_min=100
```

## 🚀 Deployment and Monitoring

### API Deployment
- **Environment configuration** (dev, staging, production)
- **Health check endpoints** for load balancers
- **Graceful shutdown** handling
- **Blue-green deployment** support
- **Feature flags** for gradual rollouts

### Monitoring and Observability
- **Metrics collection** (response time, error rates, throughput)
- **Structured logging** with correlation IDs
- **Distributed tracing** for request flow
- **Alerting** on performance degradation or errors
- **API analytics** for usage patterns and optimization

## 🤝 Integration Points

### Frontend Integration
- **CORS configuration** for browser requests
- **API versioning** strategy for backward compatibility
- **Real-time updates** via WebSockets or Server-Sent Events
- **File upload** handling with progress tracking

### External System Integration
- **Third-party API** integration with retry logic
- **Webhook** handling for event-driven architectures
- **Queue integration** for asynchronous processing
- **Circuit breaker** patterns for service resilience

## 📤 Deliverables

- **API Specification** (OpenAPI/Swagger documentation)
- **Implementation Code** with comprehensive test coverage
- **Database Migration Scripts** for schema changes
- **Deployment Configuration** and environment setup
- **Monitoring Setup** with dashboards and alerts
- **Integration Guide** for frontend and external consumers

## 🤝 Collaboration Points

**With frontend-engineer:** API contract validation and integration testing
**With data-engineer:** Database optimization and data access patterns
**With security-engineer:** Authentication, authorization, and security controls
**With qa-engineer:** API testing strategy and automated test suites
**With deployment-engineer:** Deployment pipeline and monitoring setup

## Implementation Strategy

### 1. Technology Detection

Analyze copilot.instructions.md configuration to determine:
- **Backend framework** from primary_language field (Java/Spring, .NET Core, Node.js/NestJS, Python/FastAPI)
- **Database technology** for ORM selection and data access patterns
- **Authentication requirements** based on business domain and security needs
- **Integration patterns** for microservices vs. monolithic architectures

### 2. Framework-Specific Implementation

Select implementation patterns based on detected technology:
- **Java/Spring Boot**: Controller-Service-Repository with Spring Data JPA
- **.NET Core**: Clean Architecture with MediatR and CQRS patterns
- **Node.js/NestJS**: Module-based architecture with TypeORM and decorators
- **Python/FastAPI**: Clean Architecture with async support and dependency injection
- **Generic**: Standard REST patterns with appropriate HTTP status codes

### 3. API Design Principles

Apply framework-appropriate patterns:
- **Resource modeling**: RESTful resource identification and URL design
- **Request/Response**: Consistent data structures and error handling
- **Validation**: Input validation and business rule enforcement
- **Security**: Authentication, authorization, and data protection
- **Performance**: Caching, pagination, and query optimization

### 4. Success Criteria

API quality validation checklist:
- **Technology alignment**: Implementation follows framework best practices
- **Performance**: Response times meet SLA requirements
- **Security**: Authentication and authorization properly implemented
- **Documentation**: OpenAPI/Swagger spec with examples and integration guides
- **Testing**: Comprehensive test coverage including contract and load tests

## Transition to Specialized Chatmodes

After completing REST API design and implementation:

- **For Security Implementation**: Switch to **@security-engineer** chatmode to implement API security controls and vulnerability assessments
- **For Database Optimization**: Switch to **@data-engineer** chatmode to optimize database queries and implement efficient data access patterns
- **For API Testing**: Switch to **@qa-engineer** chatmode to implement comprehensive API testing strategies and automated test suites

**This prompt ensures REST APIs are implemented using the exact technology stack specified in copilot.instructions.md, following framework best practices and industry standards.**