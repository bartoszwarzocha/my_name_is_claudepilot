---
name: pr-review-to-deployment
description: Complete workflow from Pull Request review through production deployment with automated quality gates and rollback capabilities
tools: [github-copilot, github-actions, deployment-automation, monitoring-integration, rollback-management]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# Pull Request Review to Deployment Workflow

## Context Analysis Framework

This workflow automatically manages the complete deployment pipeline from PR review to production:

```markdown
## Intelligent Deployment Context Detection
1. Read `copilot.instructions.md` for deployment specifications and standards
2. Analyze Pull Request details (changes, tests, reviews, approvals)
3. Detect deployment environment configuration and infrastructure
4. Understand current production state and health metrics
5. Map changes to deployment risk assessment and rollback strategy
```

## GitHub Integration Points

### 1. Pull Request Analysis & Review Automation

```typescript
// Comprehensive PR analysis for deployment readiness
interface PRAnalysis {
  prDetails: {
    number: number;
    title: string;
    author: string;
    reviewers: string[];
    approvals: number;
    changes: FileChange[];
    baseBranch: string;
    headBranch: string;
  };
  riskAssessment: 'low' | 'medium' | 'high' | 'critical';
  deploymentReadiness: DeploymentReadiness;
  qualityGates: QualityGateResult[];
  securityValidation: SecurityValidation;
  performanceImpact: PerformanceImpact;
}

class PullRequestAnalyzer {
  async analyzePR(prNumber: number): Promise<PRAnalysis> {
    const pr = await this.fetchPRDetails(prNumber);
    const changes = await this.analyzeCodeChanges(pr);

    return {
      prDetails: this.extractPRDetails(pr),
      riskAssessment: this.assessDeploymentRisk(changes),
      deploymentReadiness: await this.checkDeploymentReadiness(pr),
      qualityGates: await this.validateQualityGates(pr),
      securityValidation: await this.performSecurityValidation(changes),
      performanceImpact: await this.assessPerformanceImpact(changes)
    };
  }

  private assessDeploymentRisk(changes: FileChange[]): 'low' | 'medium' | 'high' | 'critical' {
    const riskFactors = {
      databaseChanges: changes.some(c => c.path.includes('migration') || c.path.includes('schema')),
      configChanges: changes.some(c => c.path.includes('config') || c.path.includes('.env')),
      coreLogicChanges: changes.some(c => c.linesChanged > 100),
      externalDependencies: changes.some(c => c.path.includes('package.json') || c.path.includes('requirements.txt')),
      infrastructureChanges: changes.some(c => c.path.includes('Dockerfile') || c.path.includes('k8s'))
    };

    const riskScore = Object.values(riskFactors).filter(Boolean).length;

    if (riskScore >= 4) return 'critical';
    if (riskScore >= 3) return 'high';
    if (riskScore >= 2) return 'medium';
    return 'low';
  }
}
```

### 2. Automated Code Review Enhancement

```typescript
// GitHub Copilot enhanced code review
interface CodeReviewEnhancement {
  automatedChecks: AutomatedCheck[];
  securitySuggestions: SecuritySuggestion[];
  performanceRecommendations: PerformanceRecommendation[];
  codeQualityImprovements: CodeQualityImprovement[];
  deploymentConsiderations: DeploymentConsideration[];
}

class CopilotCodeReviewer {
  async enhanceCodeReview(prNumber: number): Promise<CodeReviewEnhancement> {
    const prChanges = await this.getPRChanges(prNumber);

    return {
      automatedChecks: await this.runAutomatedChecks(prChanges),
      securitySuggestions: await this.generateSecuritySuggestions(prChanges),
      performanceRecommendations: await this.analyzePerformanceImpact(prChanges),
      codeQualityImprovements: await this.suggestQualityImprovements(prChanges),
      deploymentConsiderations: await this.assessDeploymentImpact(prChanges)
    };
  }

  private async runAutomatedChecks(changes: FileChange[]): Promise<AutomatedCheck[]> {
    return [
      await this.checkTestCoverage(changes),
      await this.validateCodeStyle(changes),
      await this.checkDependencyVulnerabilities(changes),
      await this.validateDocumentation(changes),
      await this.checkBreakingChanges(changes)
    ];
  }

  private async generateSecuritySuggestions(changes: FileChange[]): Promise<SecuritySuggestion[]> {
    const suggestions: SecuritySuggestion[] = [];

    for (const change of changes) {
      // SQL injection detection
      if (this.detectSQLInjectionRisk(change.content)) {
        suggestions.push({
          type: 'sql-injection-risk',
          severity: 'high',
          file: change.path,
          line: change.lineNumber,
          suggestion: 'Use parameterized queries to prevent SQL injection',
          example: this.generateParameterizedQueryExample(change.content)
        });
      }

      // Secrets detection
      if (this.detectHardcodedSecrets(change.content)) {
        suggestions.push({
          type: 'hardcoded-secrets',
          severity: 'critical',
          file: change.path,
          line: change.lineNumber,
          suggestion: 'Move secrets to environment variables or secure vault',
          example: this.generateSecureConfigExample()
        });
      }
    }

    return suggestions;
  }
}
```

## Workflow Stages

### Stage 1: Pre-Deployment Validation

```typescript
interface PreDeploymentValidation {
  reviewStatus: {
    requiredApprovals: number;
    currentApprovals: number;
    reviewCompletion: boolean;
    conflictResolution: boolean;
  };
  qualityGates: {
    codeQuality: QualityGateStatus;
    testCoverage: QualityGateStatus;
    securityScan: QualityGateStatus;
    performanceTest: QualityGateStatus;
  };
  deploymentReadiness: {
    environmentHealth: 'healthy' | 'degraded' | 'unhealthy';
    dependencyStatus: 'available' | 'degraded' | 'unavailable';
    resourceCapacity: 'sufficient' | 'limited' | 'insufficient';
  };
  chatmode: 'reviewer' | 'security-engineer' | 'qa-engineer';
}

// Pre-deployment validation implementation
class PreDeploymentValidator {
  async validateDeploymentReadiness(prNumber: number): Promise<PreDeploymentValidation> {
    const [reviewStatus, qualityGates, environmentStatus] = await Promise.all([
      this.checkReviewStatus(prNumber),
      this.validateQualityGates(prNumber),
      this.checkEnvironmentHealth()
    ]);

    return {
      reviewStatus,
      qualityGates,
      deploymentReadiness: environmentStatus,
      chatmode: this.determineChatmode(reviewStatus, qualityGates)
    };
  }

  private async validateQualityGates(prNumber: number): Promise<any> {
    return {
      codeQuality: await this.runSonarQubeAnalysis(prNumber),
      testCoverage: await this.validateTestCoverage(prNumber),
      securityScan: await this.runSecurityScan(prNumber),
      performanceTest: await this.runPerformanceTests(prNumber)
    };
  }

  private async runSonarQubeAnalysis(prNumber: number): Promise<QualityGateStatus> {
    // SonarQube integration for code quality analysis
    const analysis = await this.sonarQubeClient.analyzePR(prNumber);

    return {
      status: analysis.qualityGate.status === 'OK' ? 'passed' : 'failed',
      metrics: {
        coverage: analysis.measures.coverage,
        duplicatedLines: analysis.measures.duplicatedLinesDensity,
        maintainabilityRating: analysis.measures.maintainabilityRating,
        reliabilityRating: analysis.measures.reliabilityRating,
        securityRating: analysis.measures.securityRating
      },
      issues: analysis.issues.filter(issue => issue.severity === 'BLOCKER' || issue.severity === 'CRITICAL')
    };
  }
}
```

### Stage 2: Deployment Strategy Selection

```typescript
// Technology-adaptive deployment strategies
interface DeploymentStrategy {
  type: 'blue-green' | 'canary' | 'rolling' | 'recreate';
  configuration: DeploymentConfiguration;
  rollbackPlan: RollbackPlan;
  monitoringStrategy: MonitoringStrategy;
  healthChecks: HealthCheck[];
}

class DeploymentStrategySelector {
  selectOptimalStrategy(
    prAnalysis: PRAnalysis,
    projectContext: ProjectContext
  ): DeploymentStrategy {

    // Risk-based strategy selection
    if (prAnalysis.riskAssessment === 'critical') {
      return this.createBlueGreenStrategy(prAnalysis, projectContext);
    }

    if (prAnalysis.riskAssessment === 'high') {
      return this.createCanaryStrategy(prAnalysis, projectContext);
    }

    if (projectContext.scale === 'enterprise') {
      return this.createRollingStrategy(prAnalysis, projectContext);
    }

    return this.createRecreateStrategy(prAnalysis, projectContext);
  }

  private createCanaryStrategy(
    prAnalysis: PRAnalysis,
    context: ProjectContext
  ): DeploymentStrategy {
    return {
      type: 'canary',
      configuration: {
        initialTrafficPercentage: 5,
        trafficIncrements: [10, 25, 50, 100],
        incrementInterval: '5m',
        successCriteria: {
          errorRateThreshold: 0.1,
          responseTimeThreshold: 200,
          successRateThreshold: 99.5
        },
        rollbackCriteria: {
          errorRateThreshold: 1.0,
          responseTimeThreshold: 1000,
          successRateThreshold: 95.0
        }
      },
      rollbackPlan: this.createAutomatedRollbackPlan(),
      monitoringStrategy: this.createEnhancedMonitoring(),
      healthChecks: this.createComprehensiveHealthChecks()
    };
  }
}
```

### Stage 3: Technology-Specific Deployment Implementation

#### React/TypeScript Frontend Deployment

```typescript
// React application deployment with GitHub Actions
const reactDeploymentWorkflow = {
  chatmode: 'deployment-engineer',
  pipeline: `
name: React Frontend Deployment

on:
  pull_request:
    types: [closed]
    branches: [main]

jobs:
  deploy-staging:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    environment: staging

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run build with staging config
        run: |
          npm run build:staging
        env:
          REACT_APP_API_URL: \${{ secrets.STAGING_API_URL }}
          REACT_APP_ENV: staging

      - name: Run lighthouse CI
        run: |
          npm install -g @lhci/cli@0.12.x
          lhci autorun
        env:
          LHCI_GITHUB_APP_TOKEN: \${{ secrets.LHCI_GITHUB_APP_TOKEN }}

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: \${{ secrets.VERCEL_TOKEN }}
          github-token: \${{ secrets.GITHUB_TOKEN }}
          vercel-args: '--prod'
          vercel-org-id: \${{ secrets.ORG_ID }}
          vercel-project-id: \${{ secrets.PROJECT_ID }}

      - name: Run E2E tests against staging
        run: |
          npm run test:e2e:staging
        env:
          STAGING_URL: \${{ steps.vercel.outputs.preview-url }}

      - name: Comment deployment status
        uses: actions/github-script@v7
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '🚀 Staging deployment successful! Preview: \${{ steps.vercel.outputs.preview-url }}'
            });

  deploy-production:
    needs: deploy-staging
    runs-on: ubuntu-latest
    environment: production
    if: github.event.pull_request.merged == true

    steps:
      - uses: actions/checkout@v4

      - name: Production deployment with blue-green strategy
        run: |
          # Deploy to blue environment
          vercel --prod --name=\${PROJECT_NAME}-blue

          # Health check on blue environment
          ./scripts/health-check.sh \${BLUE_URL}

          # Switch traffic to blue (becomes new green)
          vercel alias \${BLUE_URL} \${PRODUCTION_URL}

          # Keep old environment as blue for rollback
          echo "Deployment completed. Old environment available for rollback."
  `,

  rollbackScript: `
#!/bin/bash
# React Frontend Rollback Script

set -e

PREVIOUS_VERSION=\${1:-"latest-stable"}
ROLLBACK_REASON=\${2:-"Performance degradation detected"}

echo "🔄 Starting rollback to version: \$PREVIOUS_VERSION"
echo "Reason: \$ROLLBACK_REASON"

# Switch traffic back to previous version
vercel alias \${PREVIOUS_VERSION_URL} \${PRODUCTION_URL}

# Verify rollback success
./scripts/health-check.sh \${PRODUCTION_URL}

# Notify team
curl -X POST \${SLACK_WEBHOOK_URL} \
  -H 'Content-type: application/json' \
  --data "{\"text\":\"🔄 Production rollback completed. Version: \$PREVIOUS_VERSION. Reason: \$ROLLBACK_REASON\"}"

echo "✅ Rollback completed successfully"
  `,

  monitoring: `
// Frontend monitoring and alerting
const monitoringConfig = {
  metrics: [
    'core-web-vitals',
    'error-rate',
    'page-load-time',
    'user-interactions',
    'api-response-times'
  ],

  alerts: {
    'high-error-rate': {
      threshold: '> 1%',
      window: '5m',
      action: 'trigger-rollback'
    },
    'slow-page-load': {
      threshold: '> 3s',
      window: '10m',
      action: 'notify-team'
    },
    'core-web-vitals-degradation': {
      threshold: 'CLS > 0.25 OR LCP > 2.5s',
      window: '15m',
      action: 'performance-review'
    }
  }
};
  `
};
```

#### Node.js/Express Backend Deployment

```typescript
// Node.js backend deployment with Kubernetes
const nodeBackendDeploymentWorkflow = {
  chatmode: 'deployment-engineer',
  pipeline: `
name: Node.js Backend Deployment

on:
  pull_request:
    types: [closed]
    branches: [main]

jobs:
  deploy:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build Docker image
        run: |
          docker build -t \${{ github.repository }}:\${{ github.sha }} .
          docker tag \${{ github.repository }}:\${{ github.sha }} \${{ github.repository }}:latest

      - name: Security scan with Trivy
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: \${{ github.repository }}:\${{ github.sha }}
          format: 'sarif'
          output: 'trivy-results.sarif'

      - name: Push to registry
        run: |
          echo \${{ secrets.DOCKER_PASSWORD }} | docker login -u \${{ secrets.DOCKER_USERNAME }} --password-stdin
          docker push \${{ github.repository }}:\${{ github.sha }}
          docker push \${{ github.repository }}:latest

      - name: Deploy to staging with Helm
        run: |
          helm upgrade --install backend-staging ./helm/backend \\
            --namespace staging \\
            --set image.tag=\${{ github.sha }} \\
            --set environment=staging \\
            --set replicas=2

      - name: Run integration tests
        run: |
          kubectl wait --for=condition=ready pod -l app=backend-staging -n staging --timeout=300s
          npm run test:integration:staging

      - name: Production deployment with canary strategy
        run: |
          # Deploy canary version (5% traffic)
          helm upgrade --install backend-canary ./helm/backend \\
            --namespace production \\
            --set image.tag=\${{ github.sha }} \\
            --set environment=production \\
            --set canary.enabled=true \\
            --set canary.weight=5

      - name: Monitor canary deployment
        run: |
          # Wait for canary metrics
          sleep 300

          # Check canary health
          CANARY_SUCCESS_RATE=\$(kubectl get --raw "/api/v1/namespaces/production/services/prometheus:9090/proxy/api/v1/query?query=rate(http_requests_total{job='backend-canary',code='200'}[5m])" | jq -r '.data.result[0].value[1]')

          if (( \$(echo "\$CANARY_SUCCESS_RATE > 0.995" | bc -l) )); then
            echo "✅ Canary deployment successful, proceeding with full rollout"
            helm upgrade backend-production ./helm/backend \\
              --namespace production \\
              --set image.tag=\${{ github.sha }} \\
              --set environment=production \\
              --set canary.enabled=false
          else
            echo "❌ Canary deployment failed, rolling back"
            helm rollback backend-canary -n production
            exit 1
          fi
  `,

  kubernetesManifests: `
# Kubernetes deployment with rolling update strategy
apiVersion: apps/v1
kind: Deployment
metadata:
  name: backend-api
  namespace: production
spec:
  replicas: 5
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 2
      maxUnavailable: 1
  selector:
    matchLabels:
      app: backend-api
  template:
    metadata:
      labels:
        app: backend-api
        version: {{ .Values.image.tag }}
    spec:
      containers:
      - name: backend
        image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
        ports:
        - containerPort: 3000
        env:
        - name: NODE_ENV
          value: "production"
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: backend-secrets
              key: database-url
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
            path: /ready
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5

---
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  selector:
    app: backend-api
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: ClusterIP
  `,

  rollbackScript: `
#!/bin/bash
# Node.js Backend Rollback Script

set -e

NAMESPACE=\${1:-"production"}
REASON=\${2:-"Performance issues detected"}

echo "🔄 Starting backend rollback in namespace: \$NAMESPACE"
echo "Reason: \$REASON"

# Get current revision
CURRENT_REVISION=\$(helm history backend-\$NAMESPACE -n \$NAMESPACE --max 1 -o json | jq -r '.[0].revision')
PREVIOUS_REVISION=\$((CURRENT_REVISION - 1))

# Rollback to previous version
helm rollback backend-\$NAMESPACE \$PREVIOUS_REVISION -n \$NAMESPACE

# Wait for rollback to complete
kubectl rollout status deployment/backend-api -n \$NAMESPACE --timeout=300s

# Verify health
kubectl wait --for=condition=ready pod -l app=backend-api -n \$NAMESPACE --timeout=120s

# Check service health
HEALTH_CHECK=\$(kubectl run health-check --rm -i --restart=Never --image=curlimages/curl -- curl -s -o /dev/null -w "%{http_code}" http://backend-service.\$NAMESPACE.svc.cluster.local/health)

if [ "\$HEALTH_CHECK" == "200" ]; then
  echo "✅ Rollback completed successfully"
  # Notify team
  curl -X POST \$SLACK_WEBHOOK_URL \
    -H 'Content-type: application/json' \
    --data "{\"text\":\"🔄 Backend rollback completed in \$NAMESPACE. Revision: \$PREVIOUS_REVISION. Reason: \$REASON\"}"
else
  echo "❌ Rollback failed - service health check failed"
  exit 1
fi
  `
};
```

#### Python/FastAPI Deployment

```typescript
// Python FastAPI deployment with Docker and monitoring
const pythonFastApiDeploymentWorkflow = {
  chatmode: 'deployment-engineer',
  pipeline: `
name: FastAPI Deployment Pipeline

on:
  pull_request:
    types: [closed]
    branches: [main]

jobs:
  test-and-deploy:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_PASSWORD: postgres
          POSTGRES_DB: testdb
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install poetry
          poetry install

      - name: Run tests with coverage
        run: |
          poetry run pytest --cov=app --cov-report=xml --cov-report=html
        env:
          DATABASE_URL: postgresql://postgres:postgres@localhost/testdb

      - name: Security scan with bandit
        run: |
          poetry run bandit -r app/ -f json -o bandit-report.json

      - name: Build Docker image
        run: |
          docker build -f Dockerfile.production -t fastapi-app:\${{ github.sha }} .

      - name: Run container security scan
        uses: anchore/scan-action@v3
        with:
          image: fastapi-app:\${{ github.sha }}
          fail-build: true
          severity-cutoff: high

      - name: Deploy to staging
        run: |
          # Deploy with docker-compose for staging
          DOCKER_TAG=\${{ github.sha }} docker-compose -f docker-compose.staging.yml up -d

          # Wait for health check
          timeout 60 bash -c 'until curl -f http://localhost:8000/health; do sleep 2; done'

      - name: Run API integration tests
        run: |
          poetry run pytest tests/integration/ --base-url=http://localhost:8000

      - name: Production deployment with blue-green
        run: |
          # Deploy to blue environment
          docker tag fastapi-app:\${{ github.sha }} fastapi-app:blue
          docker-compose -f docker-compose.production.yml up -d fastapi-blue

          # Health check blue environment
          timeout 60 bash -c 'until curl -f http://localhost:8001/health; do sleep 2; done'

          # Load test blue environment
          poetry run locust -f tests/load/locustfile.py --host=http://localhost:8001 --users=50 --spawn-rate=10 --run-time=2m --html=load-test-report.html --headless

          # Switch traffic to blue (blue becomes new green)
          docker-compose -f docker-compose.production.yml exec nginx nginx -s reload

          # Clean up old green environment after successful switch
          docker-compose -f docker-compose.production.yml stop fastapi-green
  `,

  dockerFile: `
# Multi-stage Dockerfile for production
FROM python:3.11-slim as builder

WORKDIR /app

# Install poetry
RUN pip install poetry

# Copy dependency files
COPY pyproject.toml poetry.lock ./

# Configure poetry and install dependencies
RUN poetry config virtualenvs.create false \\
    && poetry install --no-dev --no-root

# Production stage
FROM python:3.11-slim as production

WORKDIR /app

# Copy installed dependencies from builder stage
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin

# Copy application code
COPY app/ ./app/
COPY alembic/ ./alembic/
COPY alembic.ini ./

# Create non-root user
RUN groupadd -r appuser && useradd -r -g appuser appuser
RUN chown -R appuser:appuser /app
USER appuser

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \\
  CMD curl -f http://localhost:8000/health || exit 1

# Start application
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--workers", "4"]
  `,

  monitoringSetup: `
# FastAPI monitoring with Prometheus and Grafana
from prometheus_client import Counter, Histogram, generate_latest, CONTENT_TYPE_LATEST
from fastapi import FastAPI, Response
import time

# Metrics
REQUEST_COUNT = Counter('http_requests_total', 'Total HTTP requests', ['method', 'endpoint', 'status'])
REQUEST_LATENCY = Histogram('http_request_duration_seconds', 'HTTP request latency')

class PrometheusMiddleware:
    def __init__(self, app: FastAPI):
        self.app = app

    async def __call__(self, scope, receive, send):
        if scope["type"] == "http":
            start_time = time.time()

            # Process request
            await self.app(scope, receive, send)

            # Record metrics
            duration = time.time() - start_time
            REQUEST_LATENCY.observe(duration)
            REQUEST_COUNT.labels(
                method=scope["method"],
                endpoint=scope["path"],
                status="200"  # Simplified
            ).inc()
        else:
            await self.app(scope, receive, send)

@app.get("/metrics")
async def metrics():
    return Response(generate_latest(), media_type=CONTENT_TYPE_LATEST)

@app.get("/health")
async def health_check():
    # Check database connectivity
    try:
        await database.execute("SELECT 1")
        return {"status": "healthy", "timestamp": time.time()}
    except Exception as e:
        raise HTTPException(status_code=503, detail=f"Database unhealthy: {str(e)}")
  `
};
```

### Stage 4: Monitoring & Rollback Automation

```typescript
interface MonitoringAndRollback {
  monitoringStrategy: {
    metrics: string[];
    alerts: AlertConfiguration[];
    dashboards: DashboardConfiguration[];
    logs: LoggingConfiguration;
  };
  rollbackStrategy: {
    triggers: RollbackTrigger[];
    automationLevel: 'manual' | 'semi-automated' | 'fully-automated';
    rollbackTime: string;
    verificationSteps: VerificationStep[];
  };
  chatmode: 'deployment-engineer' | 'qa-engineer';
}

// Comprehensive monitoring setup
class DeploymentMonitoringSystem {
  async setupMonitoring(deployment: DeploymentStrategy): Promise<MonitoringConfiguration> {
    return {
      realTimeMetrics: await this.configureRealTimeMetrics(deployment),
      alerting: await this.setupAlerting(deployment),
      logAggregation: await this.configureLogAggregation(deployment),
      healthChecks: await this.setupHealthChecks(deployment),
      performanceMonitoring: await this.configurePerformanceMonitoring(deployment)
    };
  }

  private async configureRealTimeMetrics(deployment: DeploymentStrategy): Promise<MetricsConfiguration> {
    return {
      applicationMetrics: {
        responseTime: 'avg(http_request_duration_seconds)',
        errorRate: 'rate(http_requests_total{status=~"5.."}[5m])',
        throughput: 'rate(http_requests_total[5m])',
        activeConnections: 'sum(http_active_connections)'
      },
      infrastructureMetrics: {
        cpuUsage: 'avg(cpu_usage_percent)',
        memoryUsage: 'avg(memory_usage_percent)',
        diskIO: 'rate(disk_io_operations[5m])',
        networkIO: 'rate(network_bytes_total[5m])'
      },
      businessMetrics: {
        userSessions: 'sum(active_user_sessions)',
        conversionRate: 'rate(successful_transactions[5m])',
        revenueImpact: 'sum(transaction_value[5m])'
      }
    };
  }

  private async setupAlerting(deployment: DeploymentStrategy): Promise<AlertConfiguration[]> {
    return [
      {
        name: 'High Error Rate',
        query: 'rate(http_requests_total{status=~"5.."}[5m]) > 0.01',
        severity: 'critical',
        duration: '2m',
        action: 'trigger-automated-rollback',
        notification: ['slack', 'pagerduty', 'email']
      },
      {
        name: 'Response Time Degradation',
        query: 'avg(http_request_duration_seconds) > 0.5',
        severity: 'warning',
        duration: '5m',
        action: 'notify-team',
        notification: ['slack', 'email']
      },
      {
        name: 'Memory Usage High',
        query: 'avg(memory_usage_percent) > 85',
        severity: 'warning',
        duration: '3m',
        action: 'scale-up-resources',
        notification: ['slack']
      },
      {
        name: 'Service Unavailable',
        query: 'up{job="application"} == 0',
        severity: 'critical',
        duration: '1m',
        action: 'immediate-rollback',
        notification: ['slack', 'pagerduty', 'phone']
      }
    ];
  }
}

// Automated rollback system
class AutomatedRollbackSystem {
  async executeRollback(
    trigger: RollbackTrigger,
    deployment: DeploymentStrategy
  ): Promise<RollbackResult> {

    console.log(`🔄 Executing automated rollback due to: ${trigger.reason}`);

    // 1. Immediate traffic switching
    await this.switchTrafficToPreviousVersion(deployment);

    // 2. Verify rollback success
    const verification = await this.verifyRollbackSuccess(deployment);

    if (!verification.success) {
      // 3. Emergency procedures if rollback fails
      await this.executeEmergencyProcedures(deployment);
    }

    // 4. Notify stakeholders
    await this.notifyStakeholders(trigger, verification);

    // 5. Create incident report
    await this.createIncidentReport(trigger, verification);

    return {
      success: verification.success,
      rollbackTime: new Date(),
      previousVersion: deployment.previousVersion,
      reason: trigger.reason,
      verificationResults: verification.results
    };
  }

  private async switchTrafficToPreviousVersion(deployment: DeploymentStrategy): Promise<void> {
    switch (deployment.type) {
      case 'blue-green':
        await this.switchBlueGreenTraffic(deployment);
        break;
      case 'canary':
        await this.rollbackCanaryDeployment(deployment);
        break;
      case 'rolling':
        await this.rollbackRollingDeployment(deployment);
        break;
    }
  }

  private async switchBlueGreenTraffic(deployment: DeploymentStrategy): Promise<void> {
    // Switch load balancer to previous version
    await this.loadBalancer.updateTargets({
      remove: deployment.currentTargets,
      add: deployment.previousTargets
    });

    // Wait for traffic switch
    await this.waitForTrafficSwitch(30000); // 30 seconds
  }
}
```

## Chatmode Transition Framework

### Deployment Workflow Transitions

```typescript
interface DeploymentChatmodeTransition {
  stage: string;
  primaryChatmode: string;
  supportingChatmodes: string[];
  transitionTriggers: string[];
  contextHandoff: ContextHandoff;
}

const deploymentTransitionMap: DeploymentChatmodeTransition[] = [
  {
    stage: 'pr-review',
    primaryChatmode: 'reviewer',
    supportingChatmodes: ['security-engineer', 'qa-engineer'],
    transitionTriggers: [
      'All reviews approved',
      'Quality gates passed',
      'Security validation complete'
    ],
    contextHandoff: {
      information: 'PR details, code changes, review feedback',
      nextStage: 'deployment-planning',
      nextChatmode: 'deployment-engineer'
    }
  },
  {
    stage: 'deployment-planning',
    primaryChatmode: 'deployment-engineer',
    supportingChatmodes: ['software-architect'],
    transitionTriggers: [
      'Deployment strategy selected',
      'Infrastructure validated',
      'Rollback plan prepared'
    ],
    contextHandoff: {
      information: 'Deployment strategy, infrastructure state, risk assessment',
      nextStage: 'deployment-execution',
      nextChatmode: 'deployment-engineer'
    }
  },
  {
    stage: 'deployment-execution',
    primaryChatmode: 'deployment-engineer',
    supportingChatmodes: ['qa-engineer', 'security-engineer'],
    transitionTriggers: [
      'Deployment completed',
      'Health checks passed',
      'Monitoring configured'
    ],
    contextHandoff: {
      information: 'Deployment results, monitoring data, performance metrics',
      nextStage: 'post-deployment-validation',
      nextChatmode: 'qa-engineer'
    }
  }
];

class DeploymentContextManager {
  generateTransitionContext(
    fromStage: string,
    toStage: string,
    deploymentData: DeploymentData
  ): string {
    return `
## Deployment Context Handoff: ${fromStage} → ${toStage}

### Deployment Summary
- **PR #**: ${deploymentData.prNumber}
- **Deployment Strategy**: ${deploymentData.strategy}
- **Environment**: ${deploymentData.environment}
- **Risk Level**: ${deploymentData.riskLevel}

### Changes Deployed
${deploymentData.changes.map(change => `- ${change.type}: ${change.description}`).join('\n')}

### Quality Gates Status
${deploymentData.qualityGates.map(gate => `- ${gate.name}: ${gate.status}`).join('\n')}

### Monitoring & Health
- **Application Health**: ${deploymentData.health.application}
- **Infrastructure Health**: ${deploymentData.health.infrastructure}
- **Performance Metrics**: ${deploymentData.performance.summary}

### Next Steps for ${toStage}
${this.generateNextStepsGuidance(toStage, deploymentData)}

### Rollback Information
- **Previous Version**: ${deploymentData.previousVersion}
- **Rollback Trigger**: Automated if error rate > 1% or response time > 1s
- **Rollback Time**: ~${deploymentData.rollbackTime} minutes
    `;
  }
}
```

## Quality Gates & Standards

### Production Deployment Quality Framework

```typescript
interface ProductionQualityGates {
  preDeployment: QualityGate[];
  duringDeployment: QualityGate[];
  postDeployment: QualityGate[];
  continuousMonitoring: QualityGate[];
}

const productionQualityGates: ProductionQualityGates = {
  preDeployment: [
    {
      name: 'Code Review Approval',
      criteria: [
        { metric: 'required-approvals', threshold: 2, unit: 'count' },
        { metric: 'security-review', threshold: 1, unit: 'boolean' },
        { metric: 'architecture-review', threshold: 1, unit: 'boolean' }
      ],
      automationLevel: 'manual',
      blockingLevel: 'critical'
    },
    {
      name: 'Automated Testing Gate',
      criteria: [
        { metric: 'test-coverage', threshold: 80, unit: 'percentage' },
        { metric: 'unit-tests-passed', threshold: 100, unit: 'percentage' },
        { metric: 'integration-tests-passed', threshold: 100, unit: 'percentage' },
        { metric: 'e2e-tests-passed', threshold: 100, unit: 'percentage' }
      ],
      automationLevel: 'fully-automated',
      blockingLevel: 'critical'
    }
  ],

  duringDeployment: [
    {
      name: 'Deployment Health Gate',
      criteria: [
        { metric: 'deployment-success-rate', threshold: 100, unit: 'percentage' },
        { metric: 'service-availability', threshold: 99.9, unit: 'percentage' },
        { metric: 'health-check-success', threshold: 100, unit: 'percentage' }
      ],
      automationLevel: 'fully-automated',
      blockingLevel: 'critical'
    }
  ],

  postDeployment: [
    {
      name: 'Performance Validation Gate',
      criteria: [
        { metric: 'response-time-p95', threshold: 500, unit: 'milliseconds' },
        { metric: 'error-rate', threshold: 0.1, unit: 'percentage' },
        { metric: 'throughput-degradation', threshold: 5, unit: 'percentage' }
      ],
      automationLevel: 'semi-automated',
      blockingLevel: 'error'
    },
    {
      name: 'Business Metrics Gate',
      criteria: [
        { metric: 'conversion-rate-impact', threshold: -2, unit: 'percentage' },
        { metric: 'user-satisfaction-score', threshold: 4.0, unit: 'rating' },
        { metric: 'revenue-impact', threshold: -1, unit: 'percentage' }
      ],
      automationLevel: 'manual',
      blockingLevel: 'warning'
    }
  ]
};
```

## Examples & Use Cases

### Example 1: High-Risk Database Migration Deployment

```bash
# PR: "Add user preferences table with migration"
# Risk Assessment: HIGH (database schema changes)
# Strategy: Blue-Green deployment with extended monitoring

# Stage 1: Pre-deployment Validation (reviewer chatmode)
# - Database migration review
# - Rollback strategy verification
# - Performance impact assessment

# Stage 2: Deployment Planning (deployment-engineer chatmode)
# - Blue-green strategy with database migration
# - Extended monitoring period (2 hours)
# - Automated rollback triggers

# Stage 3: Deployment Execution
# - Deploy to blue environment
# - Run database migrations
# - Comprehensive health checks
# - Performance validation
# - Gradual traffic switch (5% → 25% → 100%)

# Stage 4: Post-deployment Monitoring
# - Extended monitoring period
# - Business metrics validation
# - User feedback monitoring
```

### Example 2: Frontend Performance Optimization

```bash
# PR: "Optimize React component rendering with React.memo"
# Risk Assessment: MEDIUM (performance changes)
# Strategy: Canary deployment with performance monitoring

# Deployment Flow:
# 1. Staging deployment with Lighthouse CI
# 2. Performance regression testing
# 3. Canary deployment (10% traffic)
# 4. Core Web Vitals monitoring
# 5. Progressive rollout based on metrics
# 6. Full deployment or automated rollback
```

### Example 3: Critical Security Patch

```bash
# PR: "Fix SQL injection vulnerability in user search"
# Risk Assessment: CRITICAL (security fix)
# Strategy: Immediate deployment with comprehensive monitoring

# Expedited Deployment Flow:
# 1. Emergency security review
# 2. Automated security testing
# 3. Immediate blue-green deployment
# 4. Enhanced security monitoring
# 5. Penetration testing validation
# 6. Incident report and post-mortem
```

This comprehensive workflow ensures safe, monitored deployments from PR review through production with automated quality gates, intelligent rollback capabilities, and technology-specific optimization patterns.