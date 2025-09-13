---
name: application-performance-optimization
description: Comprehensive application performance optimization and monitoring implementation across full technology stack
tools: [all]
model: claude-sonnet-4
---

# Application Performance Optimization

**Purpose: Comprehensive application performance optimization, testing, and monitoring implementation with technology-adaptive strategies and continuous performance improvement**

## Context Adaptation Framework

Read and understand project specifications from `copilot.instructions.md` file. Adapt all performance optimization approaches to match:

- **Primary Technology Stack**: Frontend, backend, and database technologies
- **Project Scale and Requirements**: Performance targets based on startup/SME/enterprise scale
- **Business Domain Criticality**: Performance-critical areas (e-commerce, fintech, real-time systems)
- **Development Stage**: Current optimization needs (MVP/basic, production/advanced)
- **Infrastructure Constraints**: Deployment environment and resource limitations
- **User Base and Load**: Expected traffic patterns and scalability requirements

All performance optimization strategies must align with project-specific context while maintaining scalability, reliability, and cost-effectiveness.

---

## 🎯 Mission

Implement comprehensive performance optimization strategies across the entire application stack, establish robust monitoring systems, and create sustainable performance improvement processes that scale with business growth.

## 📊 Performance Optimization Framework

### Technology-Adaptive Frontend Performance

#### React Performance Optimization
```typescript
// Advanced memoization and optimization patterns
import React, { memo, useMemo, useCallback, lazy, Suspense, startTransition } from 'react';
import { FixedSizeList as List, VariableSizeList } from 'react-window';
import { debounce } from 'lodash-es';

// Smart component memoization with custom comparison
const ProductCard = memo(({ product, onSelect, isSelected }) => {
  const handleClick = useCallback(() => {
    onSelect(product.id);
  }, [product.id, onSelect]);

  const cardStyles = useMemo(() => ({
    backgroundColor: isSelected ? '#e3f2fd' : '#ffffff',
    border: isSelected ? '2px solid #1976d2' : '1px solid #e0e0e0',
    transition: 'all 0.2s ease-in-out'
  }), [isSelected]);

  return (
    <div style={cardStyles} onClick={handleClick}>
      <img
        src={product.thumbnail}
        alt={product.name}
        loading="lazy"
        width="150"
        height="150"
      />
      <h3>{product.name}</h3>
      <span>${product.price}</span>
    </div>
  );
}, (prevProps, nextProps) => {
  return prevProps.product.id === nextProps.product.id &&
         prevProps.isSelected === nextProps.isSelected;
});

// Virtual scrolling with dynamic item sizing
const DynamicProductList = ({ products, onProductSelect }) => {
  const getItemSize = useCallback((index) => {
    const product = products[index];
    return product.hasDescription ? 200 : 150;
  }, [products]);

  const Row = ({ index, style }) => {
    const product = products[index];
    return (
      <div style={style}>
        <ProductCard
          product={product}
          onSelect={onProductSelect}
          isSelected={false}
        />
      </div>
    );
  };

  return (
    <VariableSizeList
      height={600}
      itemCount={products.length}
      itemSize={getItemSize}
      itemData={products}
      overscanCount={5}
    >
      {Row}
    </VariableSizeList>
  );
};

// Code splitting with intelligent preloading
const ProductDetails = lazy(() =>
  import('./ProductDetails').then(module => ({
    default: module.ProductDetails
  }))
);

const CategoryPage = lazy(() => {
  const modulePromise = import('./CategoryPage');
  // Preload after initial render
  setTimeout(() => modulePromise, 100);
  return modulePromise;
});

// Performance monitoring with React DevTools Profiler
import { Profiler } from 'react';

function onRenderCallback(id, phase, actualDuration, baseDuration, startTime, commitTime) {
  // Send performance data to analytics
  if (actualDuration > 16) { // Flag slow renders
    console.warn(`Slow render detected in ${id}: ${actualDuration}ms`);
    // Send to monitoring service
    window.analytics?.track('slow_render', {
      component: id,
      duration: actualDuration,
      phase
    });
  }
}

const App = () => (
  <Profiler id="App" onRender={onRenderCallback}>
    <Router>
      <Suspense fallback={<LoadingSpinner />}>
        <Routes>
          <Route path="/products/:id" element={<ProductDetails />} />
          <Route path="/category/:slug" element={<CategoryPage />} />
        </Routes>
      </Suspense>
    </Router>
  </Profiler>
);

// Web Vitals monitoring with advanced metrics
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals';
import { Metric } from 'web-vitals/types';

interface PerformanceMetrics {
  cls: number;
  fid: number;
  fcp: number;
  lcp: number;
  ttfb: number;
  customMetrics: Record<string, number>;
}

class PerformanceTracker {
  private metrics: Partial<PerformanceMetrics> = {};

  constructor() {
    this.initializeWebVitalsTracking();
    this.trackCustomMetrics();
  }

  private initializeWebVitalsTracking() {
    const sendToAnalytics = (metric: Metric) => {
      this.metrics[metric.name.toLowerCase() as keyof PerformanceMetrics] = metric.value;

      // Send to analytics service
      window.gtag?.('event', metric.name, {
        value: Math.round(metric.name === 'CLS' ? metric.value * 1000 : metric.value),
        event_category: 'Web Vitals',
        event_label: metric.id,
        non_interaction: true,
      });

      // Log poor performance
      if (this.isPoorPerformance(metric)) {
        console.warn(`Poor ${metric.name} detected:`, metric.value);
        this.reportPerformanceIssue(metric);
      }
    };

    getCLS(sendToAnalytics);
    getFID(sendToAnalytics);
    getFCP(sendToAnalytics);
    getLCP(sendToAnalytics);
    getTTFB(sendToAnalytics);
  }

  private isPoorPerformance(metric: Metric): boolean {
    const thresholds = {
      CLS: 0.25,
      FID: 300,
      FCP: 3000,
      LCP: 4000,
      TTFB: 800
    };

    return metric.value > thresholds[metric.name as keyof typeof thresholds];
  }

  private trackCustomMetrics() {
    // Track bundle size impact
    if ('performance' in window) {
      window.addEventListener('load', () => {
        const navigation = performance.getEntriesByType('navigation')[0] as PerformanceNavigationTiming;
        this.metrics.customMetrics = {
          domContentLoaded: navigation.domContentLoadedEventEnd - navigation.domContentLoadedEventStart,
          loadComplete: navigation.loadEventEnd - navigation.loadEventStart,
          totalPageLoad: navigation.loadEventEnd - navigation.fetchStart
        };
      });
    }
  }
}

// Resource optimization with service worker
// sw.js - Service Worker for caching and performance
self.addEventListener('install', event => {
  event.waitUntil(
    caches.open('app-v1').then(cache => {
      return cache.addAll([
        '/',
        '/static/css/main.css',
        '/static/js/main.js',
        '/manifest.json'
      ]);
    })
  );
});

self.addEventListener('fetch', event => {
  if (event.request.destination === 'image') {
    event.respondWith(
      caches.open('images').then(cache => {
        return cache.match(event.request).then(response => {
          if (response) {
            return response;
          }
          return fetch(event.request).then(fetchResponse => {
            cache.put(event.request, fetchResponse.clone());
            return fetchResponse;
          });
        });
      })
    );
  }
});
```

#### Angular Performance Optimization
```typescript
// Advanced change detection and optimization
import {
  Component,
  ChangeDetectionStrategy,
  OnPush,
  TrackByFunction,
  Inject,
  PLATFORM_ID
} from '@angular/core';
import { isPlatformBrowser } from '@angular/common';
import { Observable, BehaviorSubject, combineLatest } from 'rxjs';
import { map, shareReplay, distinctUntilChanged, debounceTime } from 'rxjs/operators';

@Component({
  selector: 'app-optimized-product-list',
  changeDetection: ChangeDetectionStrategy.OnPush,
  template: `
    <div class="search-container">
      <input
        #searchInput
        (input)="onSearchChange(searchInput.value)"
        placeholder="Search products..."
        [value]="searchTerm$ | async"
      />
    </div>

    <cdk-virtual-scroll-viewport
      itemSize="200"
      class="product-viewport"
      (scrolledIndexChange)="onScrollChange($event)"
    >
      <div
        *cdkVirtualFor="let product of filteredProducts$ | async;
                        trackBy: trackByProductId;
                        templateCacheSize: 20"
        class="product-item"
      >
        <app-product-card
          [product]="product"
          [isVisible]="isProductVisible(product.id)"
          (productClick)="onProductSelect($event)"
        ></app-product-card>
      </div>
    </cdk-virtual-scroll-viewport>
  `,
  styleUrls: ['./optimized-product-list.component.scss']
})
export class OptimizedProductListComponent implements OnInit {
  private searchSubject = new BehaviorSubject<string>('');
  private visibleProductIds = new Set<string>();

  searchTerm$ = this.searchSubject.asObservable();

  products$ = this.productService.getProducts().pipe(
    shareReplay({ bufferSize: 1, refCount: true })
  );

  filteredProducts$ = combineLatest([
    this.products$,
    this.searchTerm$.pipe(
      debounceTime(300),
      distinctUntilChanged()
    )
  ]).pipe(
    map(([products, searchTerm]) =>
      this.filterProducts(products, searchTerm)
    ),
    shareReplay({ bufferSize: 1, refCount: true })
  );

  trackByProductId: TrackByFunction<Product> = (index, item) => item.id;

  constructor(
    private productService: ProductService,
    private cdr: ChangeDetectorRef,
    @Inject(PLATFORM_ID) private platformId: Object
  ) {}

  ngOnInit() {
    // Preload critical data
    if (isPlatformBrowser(this.platformId)) {
      this.preloadCriticalData();
    }
  }

  onSearchChange(searchTerm: string) {
    this.searchSubject.next(searchTerm);
  }

  onScrollChange(scrolledIndex: number) {
    // Update visible products for lazy loading
    const startIndex = Math.max(0, scrolledIndex - 5);
    const endIndex = scrolledIndex + 15;

    this.filteredProducts$.pipe(take(1)).subscribe(products => {
      this.visibleProductIds.clear();
      products.slice(startIndex, endIndex).forEach(product => {
        this.visibleProductIds.add(product.id);
      });
    });
  }

  isProductVisible(productId: string): boolean {
    return this.visibleProductIds.has(productId);
  }

  onProductSelect(product: Product) {
    // Use router for navigation to enable preloading
    this.router.navigate(['/products', product.id]);
  }

  private filterProducts(products: Product[], searchTerm: string): Product[] {
    if (!searchTerm.trim()) {
      return products;
    }

    const lowerSearchTerm = searchTerm.toLowerCase();
    return products.filter(product =>
      product.name.toLowerCase().includes(lowerSearchTerm) ||
      product.description.toLowerCase().includes(lowerSearchTerm)
    );
  }

  private preloadCriticalData() {
    // Preload next likely routes
    this.router.preload();

    // Preload critical images
    this.products$.pipe(take(1)).subscribe(products => {
      products.slice(0, 10).forEach(product => {
        const img = new Image();
        img.src = product.imageUrl;
      });
    });
  }
}

// Lazy loading with preloading strategy
import { PreloadingStrategy, Route } from '@angular/router';
import { Observable, of } from 'rxjs';

export class CustomPreloadingStrategy implements PreloadingStrategy {
  preload(route: Route, fn: () => Observable<any>): Observable<any> {
    // Preload routes marked for preloading
    if (route.data && route.data['preload']) {
      return fn();
    }

    // Preload high-priority routes after a delay
    if (route.data && route.data['priority'] === 'high') {
      return timer(2000).pipe(switchMap(() => fn()));
    }

    return of(null);
  }
}

// Performance monitoring service
@Injectable({
  providedIn: 'root'
})
export class PerformanceMonitoringService {
  private performanceObserver?: PerformanceObserver;

  constructor(@Inject(PLATFORM_ID) private platformId: Object) {
    if (isPlatformBrowser(this.platformId)) {
      this.initializePerformanceMonitoring();
    }
  }

  private initializePerformanceMonitoring() {
    // Monitor long tasks
    if ('PerformanceObserver' in window) {
      this.performanceObserver = new PerformanceObserver((list) => {
        list.getEntries().forEach((entry) => {
          if (entry.entryType === 'longtask') {
            console.warn('Long task detected:', entry.duration);
            this.reportLongTask(entry);
          }
        });
      });

      this.performanceObserver.observe({ entryTypes: ['longtask'] });
    }

    // Monitor navigation timing
    window.addEventListener('load', () => {
      setTimeout(() => {
        const navigation = performance.getEntriesByType('navigation')[0] as PerformanceNavigationTiming;
        this.reportNavigationTiming(navigation);
      }, 0);
    });
  }

  private reportLongTask(entry: PerformanceEntry) {
    // Send to analytics service
    window.gtag?.('event', 'long_task', {
      value: Math.round(entry.duration),
      event_category: 'Performance',
      custom_map: { 'metric1': 'duration' }
    });
  }

  private reportNavigationTiming(navigation: PerformanceNavigationTiming) {
    const metrics = {
      dns: navigation.domainLookupEnd - navigation.domainLookupStart,
      tcp: navigation.connectEnd - navigation.connectStart,
      ssl: navigation.connectEnd - navigation.secureConnectionStart,
      ttfb: navigation.responseStart - navigation.requestStart,
      download: navigation.responseEnd - navigation.responseStart,
      dom: navigation.domContentLoadedEventEnd - navigation.domContentLoadedEventStart,
      load: navigation.loadEventEnd - navigation.loadEventStart
    };

    Object.entries(metrics).forEach(([name, value]) => {
      if (value > 0) {
        window.gtag?.('event', 'timing_complete', {
          name: name,
          value: Math.round(value),
          event_category: 'Navigation Timing'
        });
      }
    });
  }
}
```

### Backend Performance Optimization

#### Node.js/TypeScript Performance
```typescript
// Advanced clustering and worker management
import cluster from 'cluster';
import os from 'os';
import { EventEmitter } from 'events';

class ClusterManager extends EventEmitter {
  private workers: Map<number, cluster.Worker> = new Map();
  private readonly numCPUs = os.cpus().length;

  constructor() {
    super();
    this.setupMaster();
  }

  private setupMaster() {
    if (cluster.isMaster) {
      console.log(`Master ${process.pid} is running`);

      // Fork workers
      for (let i = 0; i < this.numCPUs; i++) {
        this.forkWorker();
      }

      // Handle worker events
      cluster.on('exit', (worker, code, signal) => {
        console.log(`Worker ${worker.process.pid} died`);
        this.workers.delete(worker.id);
        this.forkWorker(); // Restart worker
      });

      // Graceful shutdown
      process.on('SIGTERM', () => {
        this.gracefulShutdown();
      });

    } else {
      // Worker process
      this.startWorker();
    }
  }

  private forkWorker() {
    const worker = cluster.fork();
    this.workers.set(worker.id, worker);

    worker.on('message', (message) => {
      this.handleWorkerMessage(worker, message);
    });
  }

  private startWorker() {
    const app = require('./app').default;
    const port = process.env.PORT || 3000;

    app.listen(port, () => {
      console.log(`Worker ${process.pid} started on port ${port}`);
    });
  }

  private gracefulShutdown() {
    console.log('Gracefully shutting down workers...');

    this.workers.forEach(worker => {
      worker.send('shutdown');
      worker.disconnect();

      setTimeout(() => {
        worker.kill();
      }, 5000);
    });
  }
}

// Memory-efficient data processing
import { Transform, Readable, Writable } from 'stream';
import { pipeline } from 'stream/promises';

class DataProcessor {
  async processLargeDataset(inputPath: string, outputPath: string) {
    const inputStream = fs.createReadStream(inputPath);
    const outputStream = fs.createWriteStream(outputPath);

    const transformer = new Transform({
      objectMode: true,
      transform(chunk: any, encoding: string, callback: Function) {
        try {
          const processed = this.processChunk(chunk);
          callback(null, processed);
        } catch (error) {
          callback(error);
        }
      }
    });

    await pipeline(inputStream, transformer, outputStream);
  }

  private processChunk(chunk: Buffer): Buffer {
    // Efficient chunk processing
    return chunk;
  }
}

// Advanced caching with Redis and memory tiers
import Redis from 'ioredis';
import LRU from 'lru-cache';

class MultiTierCache {
  private redis: Redis;
  private memoryCache: LRU<string, any>;

  constructor() {
    this.redis = new Redis({
      host: process.env.REDIS_HOST || 'localhost',
      port: parseInt(process.env.REDIS_PORT || '6379'),
      retryDelayOnFailover: 100,
      enableOfflineQueue: false,
      maxRetriesPerRequest: 3,
      lazyConnect: true
    });

    this.memoryCache = new LRU({
      max: 1000,
      maxAge: 1000 * 60 * 5 // 5 minutes
    });
  }

  async get<T>(key: string): Promise<T | null> {
    // Try memory cache first
    const memoryResult = this.memoryCache.get(key);
    if (memoryResult !== undefined) {
      return memoryResult;
    }

    // Try Redis cache
    try {
      const redisResult = await this.redis.get(key);
      if (redisResult) {
        const parsed = JSON.parse(redisResult);
        this.memoryCache.set(key, parsed);
        return parsed;
      }
    } catch (error) {
      console.warn('Redis cache error:', error);
    }

    return null;
  }

  async set(key: string, value: any, ttl: number = 3600): Promise<void> {
    // Set in memory cache
    this.memoryCache.set(key, value);

    // Set in Redis cache
    try {
      await this.redis.setex(key, ttl, JSON.stringify(value));
    } catch (error) {
      console.warn('Redis cache set error:', error);
    }
  }

  async invalidate(pattern: string): Promise<void> {
    // Clear memory cache
    this.memoryCache.reset();

    // Clear Redis cache
    try {
      const keys = await this.redis.keys(pattern);
      if (keys.length > 0) {
        await this.redis.del(...keys);
      }
    } catch (error) {
      console.warn('Redis cache invalidation error:', error);
    }
  }
}

// Database connection pooling and optimization
import { Pool, PoolConfig } from 'pg';

class DatabaseManager {
  private pool: Pool;

  constructor() {
    const config: PoolConfig = {
      connectionString: process.env.DATABASE_URL,
      max: 20, // Maximum connections
      min: 5,  // Minimum connections
      idleTimeoutMillis: 30000,
      connectionTimeoutMillis: 2000,
      keepAlive: true,
      keepAliveInitialDelayMillis: 10000
    };

    this.pool = new Pool(config);
    this.setupEventListeners();
  }

  private setupEventListeners() {
    this.pool.on('connect', (client) => {
      console.log('New database connection established');
    });

    this.pool.on('error', (err, client) => {
      console.error('Database pool error:', err);
    });
  }

  async query(text: string, params?: any[]): Promise<any> {
    const start = Date.now();

    try {
      const result = await this.pool.query(text, params);
      const duration = Date.now() - start;

      // Log slow queries
      if (duration > 1000) {
        console.warn(`Slow query detected (${duration}ms):`, text);
      }

      return result;
    } catch (error) {
      console.error('Database query error:', error);
      throw error;
    }
  }

  async getClient() {
    return await this.pool.connect();
  }

  async close() {
    await this.pool.end();
  }
}

// API response optimization
import compression from 'compression';
import helmet from 'helmet';
import rateLimit from 'express-rate-limit';

class APIOptimizer {
  static configureMiddleware(app: Express) {
    // Compression
    app.use(compression({
      level: 6,
      threshold: 1024,
      filter: (req, res) => {
        if (req.headers['x-no-compression']) {
          return false;
        }
        return compression.filter(req, res);
      }
    }));

    // Security headers
    app.use(helmet({
      contentSecurityPolicy: {
        directives: {
          defaultSrc: ["'self'"],
          styleSrc: ["'self'", "'unsafe-inline'"],
          scriptSrc: ["'self'"],
          imgSrc: ["'self'", "data:", "https:"]
        }
      }
    }));

    // Rate limiting
    const limiter = rateLimit({
      windowMs: 15 * 60 * 1000, // 15 minutes
      max: 1000, // Limit each IP to 1000 requests per windowMs
      message: 'Too many requests from this IP',
      standardHeaders: true,
      legacyHeaders: false
    });
    app.use('/api/', limiter);

    // Request/Response optimization
    app.use((req, res, next) => {
      // Enable keep-alive
      res.setHeader('Connection', 'keep-alive');

      // Cache control for static assets
      if (req.url.match(/\.(css|js|png|jpg|jpeg|gif|ico|svg)$/)) {
        res.setHeader('Cache-Control', 'public, max-age=31536000');
      }

      next();
    });
  }
}
```

#### Python/FastAPI Performance
```python
# Advanced async processing and optimization
import asyncio
import asyncpg
from typing import List, Optional, Dict, Any
from fastapi import FastAPI, BackgroundTasks, Depends
from fastapi.middleware.gzip import GZipMiddleware
from fastapi.middleware.cors import CORSMiddleware
import aioredis
import aioboto3
from contextlib import asynccontextmanager
import time
import logging

# Database connection pooling
class DatabaseManager:
    def __init__(self):
        self.pool: Optional[asyncpg.Pool] = None

    async def create_pool(self):
        self.pool = await asyncpg.create_pool(
            dsn=DATABASE_URL,
            min_size=10,
            max_size=50,
            max_queries=50000,
            max_inactive_connection_lifetime=300,
            server_settings={
                'jit': 'off',  # Disable JIT for faster connection
                'application_name': 'fastapi_app'
            }
        )

    async def close_pool(self):
        if self.pool:
            await self.pool.close()

    @asynccontextmanager
    async def get_connection(self):
        async with self.pool.acquire() as connection:
            yield connection

# Redis caching with connection pooling
class CacheManager:
    def __init__(self):
        self.redis: Optional[aioredis.Redis] = None

    async def initialize(self):
        self.redis = aioredis.from_url(
            REDIS_URL,
            max_connections=20,
            retry_on_timeout=True,
            health_check_interval=30
        )

    async def get(self, key: str) -> Optional[str]:
        try:
            return await self.redis.get(key)
        except Exception as e:
            logging.warning(f"Cache get error: {e}")
            return None

    async def set(self, key: str, value: str, ttl: int = 3600):
        try:
            await self.redis.setex(key, ttl, value)
        except Exception as e:
            logging.warning(f"Cache set error: {e}")

# Performance monitoring middleware
import time
from starlette.middleware.base import BaseHTTPMiddleware
from starlette.requests import Request
from starlette.responses import Response

class PerformanceMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next):
        start_time = time.time()

        # Add request ID for tracking
        request_id = str(uuid.uuid4())
        request.state.request_id = request_id

        response = await call_next(request)

        process_time = time.time() - start_time

        # Log slow requests
        if process_time > 1.0:
            logging.warning(
                f"Slow request: {request.method} {request.url.path} "
                f"took {process_time:.4f}s"
            )

        # Add performance headers
        response.headers["X-Process-Time"] = str(process_time)
        response.headers["X-Request-ID"] = request_id

        # Record metrics
        await self.record_metrics(request, response, process_time)

        return response

    async def record_metrics(self, request: Request, response: Response, duration: float):
        # Send metrics to monitoring service
        metrics = {
            'method': request.method,
            'path': request.url.path,
            'status_code': response.status_code,
            'duration': duration,
            'timestamp': time.time()
        }

        # Async send to monitoring service
        asyncio.create_task(self.send_metrics(metrics))

    async def send_metrics(self, metrics: Dict[str, Any]):
        # Implementation for sending metrics to monitoring service
        pass

# Efficient data processing with generators
async def process_large_dataset(data_source: str) -> AsyncGenerator[Dict, None]:
    """Process large datasets efficiently using async generators"""

    async with aiofiles.open(data_source, 'r') as file:
        async for line in file:
            try:
                data = json.loads(line)
                processed_data = await process_data_item(data)
                yield processed_data
            except Exception as e:
                logging.error(f"Error processing line: {e}")
                continue

async def process_data_item(data: Dict) -> Dict:
    """Process individual data items with async operations"""

    # Simulate async processing
    await asyncio.sleep(0.001)

    return {
        'id': data.get('id'),
        'processed_at': time.time(),
        'result': data.get('value', 0) * 2
    }

# Background task processing
from celery import Celery

celery_app = Celery(
    'fastapi_app',
    broker='redis://localhost:6379/0',
    backend='redis://localhost:6379/0'
)

@celery_app.task
def process_heavy_computation(data: Dict) -> Dict:
    """Heavy computation task processed in background"""

    # CPU-intensive processing
    import time
    start = time.time()

    # Simulate heavy computation
    result = sum(i**2 for i in range(data.get('iterations', 10000)))

    duration = time.time() - start

    return {
        'result': result,
        'duration': duration,
        'processed_at': time.time()
    }

# Optimized FastAPI application
@asynccontextmanager
async def lifespan(app: FastAPI):
    # Startup
    await db_manager.create_pool()
    await cache_manager.initialize()

    yield

    # Shutdown
    await db_manager.close_pool()
    await cache_manager.redis.close()

app = FastAPI(
    title="High Performance API",
    lifespan=lifespan
)

# Add middleware
app.add_middleware(GZipMiddleware, minimum_size=1000)
app.add_middleware(PerformanceMiddleware)
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# Dependency for database connection
async def get_db_connection():
    async with db_manager.get_connection() as connection:
        yield connection

# Optimized API endpoints
@app.get("/api/products/{product_id}")
async def get_product(
    product_id: int,
    connection=Depends(get_db_connection)
):
    # Try cache first
    cache_key = f"product:{product_id}"
    cached_result = await cache_manager.get(cache_key)

    if cached_result:
        return json.loads(cached_result)

    # Query database
    query = """
        SELECT p.*, c.name as category_name
        FROM products p
        LEFT JOIN categories c ON p.category_id = c.id
        WHERE p.id = $1 AND p.active = true
    """

    result = await connection.fetchrow(query, product_id)

    if result:
        product_data = dict(result)
        # Cache result
        await cache_manager.set(
            cache_key,
            json.dumps(product_data, default=str),
            ttl=300
        )
        return product_data

    raise HTTPException(status_code=404, detail="Product not found")

@app.post("/api/products/batch-process")
async def batch_process_products(
    product_ids: List[int],
    background_tasks: BackgroundTasks,
    connection=Depends(get_db_connection)
):
    # Process in batches for efficiency
    batch_size = 100
    results = []

    for i in range(0, len(product_ids), batch_size):
        batch = product_ids[i:i + batch_size]

        query = """
            SELECT id, name, price
            FROM products
            WHERE id = ANY($1::int[]) AND active = true
        """

        batch_results = await connection.fetch(query, batch)
        results.extend([dict(row) for row in batch_results])

    # Schedule background processing
    background_tasks.add_task(
        process_heavy_computation.delay,
        {'product_count': len(results)}
    )

    return {'products': results, 'total': len(results)}
```

## 🔧 Infrastructure Performance Optimization

### Database Performance Optimization
```sql
-- PostgreSQL performance optimization
-- Index strategies for common query patterns
CREATE INDEX CONCURRENTLY idx_products_category_active
ON products (category_id, active)
WHERE active = true;

CREATE INDEX CONCURRENTLY idx_products_search_text
ON products USING gin(to_tsvector('english', name || ' ' || description));

CREATE INDEX CONCURRENTLY idx_orders_user_date
ON orders (user_id, created_at DESC)
WHERE status IN ('completed', 'processing');

-- Partial indexes for specific use cases
CREATE INDEX CONCURRENTLY idx_products_featured
ON products (featured_rank)
WHERE featured = true AND active = true;

-- Query optimization examples
EXPLAIN (ANALYZE, BUFFERS, FORMAT JSON)
SELECT p.*, c.name as category_name
FROM products p
JOIN categories c ON p.category_id = c.id
WHERE p.active = true
  AND p.price BETWEEN $1 AND $2
  AND c.active = true
ORDER BY p.created_at DESC
LIMIT 20;

-- Connection pooling configuration
-- postgresql.conf optimizations
shared_buffers = 256MB                  # 25% of RAM for small instances
effective_cache_size = 1GB              # 75% of RAM
work_mem = 4MB                          # Per connection work memory
maintenance_work_mem = 64MB             # Maintenance operations
checkpoint_completion_target = 0.9      # Spread checkpoints
wal_buffers = 16MB                      # WAL buffer size
default_statistics_target = 100         # Query planner statistics

-- Connection pooling with PgBouncer
# pgbouncer.ini
[databases]
app_db = host=localhost port=5432 dbname=app_production

[pgbouncer]
listen_port = 6432
listen_addr = 127.0.0.1
auth_type = md5
auth_file = /etc/pgbouncer/userlist.txt
pool_mode = transaction
max_client_conn = 1000
default_pool_size = 100
reserve_pool_size = 25
server_lifetime = 3600
server_idle_timeout = 600
```

### CDN and Caching Strategy
```typescript
// CloudFront configuration for optimal performance
const cloudFrontConfig = {
  origins: [
    {
      domainName: 'api.example.com',
      originPath: '/api/v1',
      customOriginConfig: {
        httpPort: 80,
        httpsPort: 443,
        originProtocolPolicy: 'https-only',
        originSslProtocols: ['TLSv1.2']
      }
    }
  ],

  cacheBehaviors: [
    {
      pathPattern: '/api/products/*',
      targetOriginId: 'api-origin',
      viewerProtocolPolicy: 'redirect-to-https',
      cachePolicyId: 'custom-api-cache-policy',
      compress: true,
      ttl: {
        defaultTTL: 300,  // 5 minutes
        maxTTL: 3600      // 1 hour
      }
    },
    {
      pathPattern: '/static/*',
      targetOriginId: 'static-origin',
      viewerProtocolPolicy: 'redirect-to-https',
      compress: true,
      ttl: {
        defaultTTL: 86400,  // 1 day
        maxTTL: 31536000    // 1 year
      }
    }
  ]
};

// Edge caching with service workers
class EdgeCacheManager {
  private cacheNames = {
    static: 'static-v1',
    api: 'api-v1',
    images: 'images-v1'
  };

  async cacheStaticAssets() {
    const cache = await caches.open(this.cacheNames.static);
    const urlsToCache = [
      '/',
      '/static/css/main.css',
      '/static/js/main.js',
      '/manifest.json'
    ];

    await cache.addAll(urlsToCache);
  }

  async handleFetch(request: Request): Promise<Response> {
    const url = new URL(request.url);

    // Handle API requests
    if (url.pathname.startsWith('/api/')) {
      return this.handleAPIRequest(request);
    }

    // Handle static assets
    if (url.pathname.startsWith('/static/')) {
      return this.handleStaticRequest(request);
    }

    // Handle images
    if (this.isImageRequest(request)) {
      return this.handleImageRequest(request);
    }

    return fetch(request);
  }

  private async handleAPIRequest(request: Request): Promise<Response> {
    const cache = await caches.open(this.cacheNames.api);

    // Check cache first for GET requests
    if (request.method === 'GET') {
      const cachedResponse = await cache.match(request);
      if (cachedResponse && this.isCacheValid(cachedResponse)) {
        return cachedResponse;
      }
    }

    // Fetch from network
    try {
      const response = await fetch(request);

      // Cache successful GET responses
      if (request.method === 'GET' && response.ok) {
        const responseToCache = response.clone();
        await cache.put(request, responseToCache);
      }

      return response;
    } catch (error) {
      // Return cached version on network failure
      const cachedResponse = await cache.match(request);
      if (cachedResponse) {
        return cachedResponse;
      }
      throw error;
    }
  }

  private isCacheValid(response: Response): boolean {
    const cacheDate = response.headers.get('date');
    if (!cacheDate) return false;

    const cacheTime = new Date(cacheDate).getTime();
    const now = Date.now();
    const maxAge = 5 * 60 * 1000; // 5 minutes

    return (now - cacheTime) < maxAge;
  }
}
```

## 📊 Performance Monitoring and Testing

### Load Testing with K6
```javascript
// Advanced load testing scenarios
import http from 'k6/http';
import { check, sleep } from 'k6';
import { Rate, Trend, Counter } from 'k6/metrics';

// Custom metrics
const errorRate = new Rate('errors');
const apiResponseTime = new Trend('api_response_time');
const apiCalls = new Counter('api_calls');

// Test configuration
export const options = {
  stages: [
    { duration: '30s', target: 10 },   // Ramp up to 10 users
    { duration: '1m', target: 50 },    // Stay at 50 users
    { duration: '2m', target: 100 },   // Ramp up to 100 users
    { duration: '2m', target: 100 },   // Stay at 100 users
    { duration: '1m', target: 200 },   // Ramp up to 200 users
    { duration: '2m', target: 200 },   // Stay at 200 users
    { duration: '30s', target: 0 },    // Ramp down to 0 users
  ],

  thresholds: {
    http_req_duration: ['p(95)<500'], // 95% of requests must complete below 500ms
    http_req_failed: ['rate<0.1'],    // Error rate must be below 10%
    api_response_time: ['p(90)<300'], // 90% of API calls below 300ms
  }
};

// Test data
const products = Array.from({ length: 1000 }, (_, i) => ({
  id: i + 1,
  name: `Product ${i + 1}`,
  price: Math.floor(Math.random() * 1000) + 10
}));

// Main test function
export default function () {
  const baseUrl = 'https://api.example.com';

  // Test scenarios with weighted distribution
  const scenarios = [
    { weight: 40, test: testProductListing },
    { weight: 30, test: testProductDetails },
    { weight: 20, test: testProductSearch },
    { weight: 10, test: testProductCreation }
  ];

  const randomScenario = scenarios[
    Math.floor(Math.random() * 100) < scenarios[0].weight ? 0 :
    Math.floor(Math.random() * 100) < scenarios[0].weight + scenarios[1].weight ? 1 :
    Math.floor(Math.random() * 100) < scenarios[0].weight + scenarios[1].weight + scenarios[2].weight ? 2 : 3
  ];

  randomScenario.test(baseUrl);

  sleep(Math.random() * 2 + 1); // Random sleep between 1-3 seconds
}

function testProductListing(baseUrl) {
  const response = http.get(`${baseUrl}/api/products?page=1&limit=20`);

  check(response, {
    'product listing status is 200': (r) => r.status === 200,
    'product listing response time < 300ms': (r) => r.timings.duration < 300,
    'product listing has products': (r) => JSON.parse(r.body).data.length > 0
  });

  apiResponseTime.add(response.timings.duration);
  apiCalls.add(1);
  errorRate.add(response.status !== 200);
}

function testProductDetails(baseUrl) {
  const productId = Math.floor(Math.random() * 1000) + 1;
  const response = http.get(`${baseUrl}/api/products/${productId}`);

  check(response, {
    'product details status is 200': (r) => r.status === 200,
    'product details response time < 200ms': (r) => r.timings.duration < 200,
    'product details has required fields': (r) => {
      const product = JSON.parse(r.body);
      return product.id && product.name && product.price;
    }
  });

  apiResponseTime.add(response.timings.duration);
  apiCalls.add(1);
  errorRate.add(response.status !== 200);
}

function testProductSearch(baseUrl) {
  const searchTerms = ['laptop', 'phone', 'tablet', 'watch', 'camera'];
  const term = searchTerms[Math.floor(Math.random() * searchTerms.length)];

  const response = http.get(`${baseUrl}/api/products/search?q=${term}`);

  check(response, {
    'search status is 200': (r) => r.status === 200,
    'search response time < 400ms': (r) => r.timings.duration < 400,
    'search returns results': (r) => JSON.parse(r.body).total >= 0
  });

  apiResponseTime.add(response.timings.duration);
  apiCalls.add(1);
  errorRate.add(response.status !== 200);
}

function testProductCreation(baseUrl) {
  const product = products[Math.floor(Math.random() * products.length)];

  const response = http.post(`${baseUrl}/api/products`, JSON.stringify(product), {
    headers: { 'Content-Type': 'application/json' }
  });

  check(response, {
    'product creation status is 201': (r) => r.status === 201,
    'product creation response time < 500ms': (r) => r.timings.duration < 500
  });

  apiResponseTime.add(response.timings.duration);
  apiCalls.add(1);
  errorRate.add(response.status !== 201);
}

// Stress testing scenario
export function stressTest() {
  const response = http.get('https://api.example.com/api/products');
  check(response, { 'status is 200': (r) => r.status === 200 });
}

export const stressOptions = {
  executor: 'ramping-arrival-rate',
  startRate: 1,
  timeUnit: '1s',
  preAllocatedVUs: 50,
  maxVUs: 1000,
  stages: [
    { target: 10, duration: '1m' },
    { target: 50, duration: '2m' },
    { target: 100, duration: '3m' },
    { target: 200, duration: '2m' },
    { target: 0, duration: '1m' }
  ]
};
```

### Application Performance Monitoring
```typescript
// Comprehensive APM implementation
class ApplicationPerformanceMonitor {
  private metrics: Map<string, PerformanceMetric[]> = new Map();
  private alerts: AlertManager;

  constructor() {
    this.alerts = new AlertManager();
    this.setupPerformanceObservers();
    this.setupCustomMetrics();
  }

  private setupPerformanceObservers() {
    if ('PerformanceObserver' in window) {
      // Monitor long tasks
      const longTaskObserver = new PerformanceObserver((list) => {
        list.getEntries().forEach((entry) => {
          this.recordLongTask(entry);
        });
      });
      longTaskObserver.observe({ entryTypes: ['longtask'] });

      // Monitor navigation timing
      const navObserver = new PerformanceObserver((list) => {
        list.getEntries().forEach((entry) => {
          this.recordNavigationTiming(entry as PerformanceNavigationTiming);
        });
      });
      navObserver.observe({ entryTypes: ['navigation'] });

      // Monitor resource timing
      const resourceObserver = new PerformanceObserver((list) => {
        list.getEntries().forEach((entry) => {
          this.recordResourceTiming(entry as PerformanceResourceTiming);
        });
      });
      resourceObserver.observe({ entryTypes: ['resource'] });
    }
  }

  private recordLongTask(entry: PerformanceEntry) {
    const metric: PerformanceMetric = {
      name: 'long_task',
      value: entry.duration,
      timestamp: Date.now(),
      metadata: {
        startTime: entry.startTime,
        attribution: (entry as any).attribution
      }
    };

    this.addMetric('long_tasks', metric);

    // Alert on excessive long tasks
    if (entry.duration > 100) {
      this.alerts.sendAlert('performance', `Long task detected: ${entry.duration}ms`);
    }
  }

  private recordNavigationTiming(entry: PerformanceNavigationTiming) {
    const metrics = {
      dns_lookup: entry.domainLookupEnd - entry.domainLookupStart,
      tcp_connection: entry.connectEnd - entry.connectStart,
      ssl_handshake: entry.connectEnd - entry.secureConnectionStart,
      ttfb: entry.responseStart - entry.requestStart,
      dom_content_loaded: entry.domContentLoadedEventEnd - entry.domContentLoadedEventStart,
      page_load: entry.loadEventEnd - entry.loadEventStart
    };

    Object.entries(metrics).forEach(([name, value]) => {
      if (value > 0) {
        this.addMetric('navigation_timing', {
          name,
          value,
          timestamp: Date.now(),
          metadata: { url: window.location.href }
        });
      }
    });
  }

  private recordResourceTiming(entry: PerformanceResourceTiming) {
    const loadTime = entry.responseEnd - entry.startTime;

    this.addMetric('resource_timing', {
      name: 'resource_load_time',
      value: loadTime,
      timestamp: Date.now(),
      metadata: {
        url: entry.name,
        type: this.getResourceType(entry.name),
        size: entry.transferSize
      }
    });

    // Alert on slow resource loads
    if (loadTime > 2000) {
      this.alerts.sendAlert('performance', `Slow resource load: ${entry.name} (${loadTime}ms)`);
    }
  }

  public recordCustomMetric(name: string, value: number, metadata?: any) {
    this.addMetric('custom', {
      name,
      value,
      timestamp: Date.now(),
      metadata
    });
  }

  public startTimer(operation: string): () => void {
    const start = performance.now();

    return () => {
      const duration = performance.now() - start;
      this.recordCustomMetric(`${operation}_duration`, duration, { operation });
    };
  }

  private addMetric(category: string, metric: PerformanceMetric) {
    if (!this.metrics.has(category)) {
      this.metrics.set(category, []);
    }

    const categoryMetrics = this.metrics.get(category)!;
    categoryMetrics.push(metric);

    // Keep only last 1000 metrics per category
    if (categoryMetrics.length > 1000) {
      categoryMetrics.shift();
    }
  }

  public getMetrics(category?: string): PerformanceMetric[] {
    if (category) {
      return this.metrics.get(category) || [];
    }

    const allMetrics: PerformanceMetric[] = [];
    this.metrics.forEach(metrics => allMetrics.push(...metrics));
    return allMetrics;
  }

  public generateReport(): PerformanceReport {
    const now = Date.now();
    const oneHourAgo = now - (60 * 60 * 1000);

    const recentMetrics = this.getMetrics().filter(
      metric => metric.timestamp > oneHourAgo
    );

    return {
      timestamp: now,
      summary: this.calculateSummary(recentMetrics),
      details: this.groupMetricsByName(recentMetrics),
      alerts: this.alerts.getRecentAlerts()
    };
  }

  private calculateSummary(metrics: PerformanceMetric[]): PerformanceSummary {
    const groupedMetrics = this.groupMetricsByName(metrics);

    return Object.entries(groupedMetrics).reduce((summary, [name, values]) => {
      const numbers = values.map(m => m.value);
      summary[name] = {
        count: numbers.length,
        avg: numbers.reduce((a, b) => a + b, 0) / numbers.length,
        min: Math.min(...numbers),
        max: Math.max(...numbers),
        p95: this.calculatePercentile(numbers, 95)
      };
      return summary;
    }, {} as PerformanceSummary);
  }

  private groupMetricsByName(metrics: PerformanceMetric[]): Record<string, PerformanceMetric[]> {
    return metrics.reduce((groups, metric) => {
      if (!groups[metric.name]) {
        groups[metric.name] = [];
      }
      groups[metric.name].push(metric);
      return groups;
    }, {} as Record<string, PerformanceMetric[]>);
  }

  private calculatePercentile(values: number[], percentile: number): number {
    const sorted = values.sort((a, b) => a - b);
    const index = Math.ceil((percentile / 100) * sorted.length) - 1;
    return sorted[index];
  }

  private getResourceType(url: string): string {
    if (url.match(/\.(css)$/)) return 'stylesheet';
    if (url.match(/\.(js)$/)) return 'script';
    if (url.match(/\.(png|jpg|jpeg|gif|svg|webp)$/)) return 'image';
    if (url.match(/\.(woff|woff2|ttf|eot)$/)) return 'font';
    return 'other';
  }
}

interface PerformanceMetric {
  name: string;
  value: number;
  timestamp: number;
  metadata?: any;
}

interface PerformanceSummary {
  [metricName: string]: {
    count: number;
    avg: number;
    min: number;
    max: number;
    p95: number;
  };
}

interface PerformanceReport {
  timestamp: number;
  summary: PerformanceSummary;
  details: Record<string, PerformanceMetric[]>;
  alerts: Alert[];
}

// Alert management system
class AlertManager {
  private alerts: Alert[] = [];
  private thresholds: Map<string, number> = new Map([
    ['response_time', 1000],
    ['error_rate', 0.05],
    ['memory_usage', 0.8]
  ]);

  sendAlert(category: string, message: string, severity: 'low' | 'medium' | 'high' = 'medium') {
    const alert: Alert = {
      id: Date.now().toString(),
      category,
      message,
      severity,
      timestamp: Date.now(),
      acknowledged: false
    };

    this.alerts.push(alert);

    // Send to external monitoring service
    this.sendToMonitoringService(alert);

    console.warn(`Performance Alert [${severity.toUpperCase()}]: ${message}`);
  }

  private sendToMonitoringService(alert: Alert) {
    // Implementation for sending alerts to external monitoring
    fetch('/api/monitoring/alerts', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(alert)
    }).catch(console.error);
  }

  getRecentAlerts(hours: number = 24): Alert[] {
    const cutoff = Date.now() - (hours * 60 * 60 * 1000);
    return this.alerts.filter(alert => alert.timestamp > cutoff);
  }
}

interface Alert {
  id: string;
  category: string;
  message: string;
  severity: 'low' | 'medium' | 'high';
  timestamp: number;
  acknowledged: boolean;
}
```

## 📋 Implementation Strategy and Success Criteria

### Performance Implementation Roadmap

**Phase 1: Foundation and Monitoring (Week 1-2)**
- Establish performance baselines and monitoring
- Implement APM tools and custom metrics collection
- Set up automated performance testing in CI/CD
- Define performance budgets and SLAs

**Phase 2: Backend Optimization (Week 3-4)**
- Implement database query optimization and indexing
- Add caching layers (Redis, application-level)
- Optimize API response times and throughput
- Implement connection pooling and resource management

**Phase 3: Frontend Optimization (Week 5-6)**
- Implement code splitting and lazy loading
- Add virtual scrolling for large datasets
- Optimize bundle sizes and loading strategies
- Implement progressive web app features

**Phase 4: Infrastructure Optimization (Week 7-8)**
- Set up CDN and edge caching
- Implement load balancing and auto-scaling
- Optimize database configuration and maintenance
- Set up monitoring dashboards and alerts

### Success Criteria and KPIs

**Response Time Targets:**
```typescript
interface PerformanceTargets {
  api_response_time: {
    p50: 100,  // 50th percentile < 100ms
    p95: 300,  // 95th percentile < 300ms
    p99: 500   // 99th percentile < 500ms
  };

  page_load_time: {
    first_contentful_paint: 1500,  // < 1.5s
    largest_contentful_paint: 2500, // < 2.5s
    time_to_interactive: 3000       // < 3s
  };

  database_queries: {
    average_query_time: 50,   // < 50ms average
    slow_query_threshold: 100, // Alert on queries > 100ms
    connection_pool_usage: 0.8 // < 80% pool utilization
  };
}
```

**Throughput and Scalability:**
- Handle 1000+ concurrent users without degradation
- Support 10,000+ requests per minute
- Maintain <1% error rate under normal load
- Auto-scale based on CPU/memory thresholds

**Resource Optimization:**
- Frontend bundle size < 500KB gzipped
- Memory usage < 80% of available resources
- CPU usage < 70% under normal load
- Database connection efficiency > 90%

---

## Transition to Implementation

**Next Steps:**
Based on the comprehensive performance optimization strategy, consider switching to specialized chatmodes for implementation:

- Switch to **backend-engineer** chatmode to implement database optimizations and API performance improvements
- Switch to **frontend-engineer** chatmode to implement client-side performance optimizations and monitoring
- Switch to **deployment-engineer** chatmode to set up infrastructure monitoring and auto-scaling
- Switch to **security-engineer** chatmode to ensure performance optimizations maintain security standards

*Comprehensive performance optimization ensures applications deliver exceptional user experiences while maintaining scalability, reliability, and cost-effectiveness across all system components.*