---
name: architecture-evolution-guidance
description: Strategic architecture evolution and modernization guidance with incremental migration planning and risk assessment
tools: [github-copilot, architecture-analysis, modernization-planning, migration-tools, dependency-analysis]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# Architecture Evolution Guidance Workflow

## Context Analysis Framework

This workflow provides strategic guidance for architecture evolution, modernization, and large-scale system transformations:

```markdown
## Architecture Evolution Context Analysis
1. Read `copilot.instructions.md` for current architecture standards and technology preferences
2. Analyze existing system architecture, dependencies, and technical debt
3. Assess business drivers for change, performance requirements, and scalability needs
4. Understand team capabilities, timeline constraints, and risk tolerance
5. Map current state to desired future architecture with incremental migration path
```

## GitHub Integration Points

### 1. Architecture Assessment & Analysis

```typescript
// Comprehensive architecture analysis and assessment
interface ArchitectureAnalysis {
  currentState: {
    systemArchitecture: SystemArchitecture;
    technologyStack: TechnologyStack;
    dependencies: DependencyMap;
    performanceMetrics: PerformanceMetrics;
    scalabilityLimitations: ScalabilityLimitation[];
    technicalDebt: TechnicalDebtAssessment;
  };
  businessDrivers: {
    performanceRequirements: PerformanceRequirement[];
    scalabilityTargets: ScalabilityTarget[];
    complianceNeeds: ComplianceRequirement[];
    businessGrowthProjections: GrowthProjection[];
  };
  evolutionOpportunities: {
    modernizationCandidates: ModernizationCandidate[];
    cloudMigrationOpportunities: CloudMigrationOpportunity[];
    performanceOptimizations: PerformanceOptimization[];
    securityEnhancements: SecurityEnhancement[];
  };
}

class ArchitectureEvolutionAnalyzer {
  async analyzeCurrentArchitecture(systemId: string): Promise<ArchitectureAnalysis> {
    const codebaseAnalysis = await this.analyzeCodebase(systemId);
    const dependencyAnalysis = await this.analyzeDependencies(systemId);
    const performanceAnalysis = await this.analyzePerformance(systemId);
    const businessAnalysis = await this.analyzeBusinessDrivers(systemId);

    return {
      currentState: {
        systemArchitecture: await this.mapSystemArchitecture(codebaseAnalysis),
        technologyStack: this.analyzeTechnologyStack(codebaseAnalysis),
        dependencies: dependencyAnalysis,
        performanceMetrics: performanceAnalysis.currentMetrics,
        scalabilityLimitations: this.identifyScalabilityLimitations(performanceAnalysis),
        technicalDebt: await this.assessTechnicalDebt(codebaseAnalysis)
      },
      businessDrivers: businessAnalysis,
      evolutionOpportunities: await this.identifyEvolutionOpportunities(codebaseAnalysis, businessAnalysis)
    };
  }

  private async assessTechnicalDebt(codebase: CodebaseAnalysis): Promise<TechnicalDebtAssessment> {
    return {
      codeQualityIssues: await this.analyzeCodeQuality(codebase),
      architecturalSmells: await this.detectArchitecturalSmells(codebase),
      outdatedDependencies: await this.findOutdatedDependencies(codebase),
      securityVulnerabilities: await this.scanSecurityVulnerabilities(codebase),
      performanceBottlenecks: await this.identifyPerformanceBottlenecks(codebase),
      maintenanceComplexity: this.calculateMaintenanceComplexity(codebase)
    };
  }

  private async identifyEvolutionOpportunities(
    codebase: CodebaseAnalysis,
    business: BusinessDrivers
  ): Promise<EvolutionOpportunities> {
    return {
      modernizationCandidates: await this.identifyModernizationCandidates(codebase),
      cloudMigrationOpportunities: this.assessCloudMigrationOpportunities(codebase, business),
      performanceOptimizations: this.identifyPerformanceOptimizations(codebase),
      securityEnhancements: this.identifySecurityEnhancements(codebase)
    };
  }
}
```

### 2. Migration Planning & Strategy

```typescript
// Strategic migration planning with risk assessment
interface MigrationStrategy {
  targetArchitecture: TargetArchitecture;
  migrationApproach: 'big-bang' | 'strangler-fig' | 'parallel-run' | 'incremental';
  migrationPhases: MigrationPhase[];
  riskAssessment: RiskAssessment;
  rollbackStrategy: RollbackStrategy;
  successMetrics: SuccessMetric[];
}

class ArchitectureMigrationPlanner {
  async planMigration(
    current: ArchitectureAnalysis,
    target: TargetArchitectureGoals
  ): Promise<MigrationStrategy> {

    const targetArchitecture = await this.designTargetArchitecture(current, target);
    const migrationApproach = this.selectMigrationApproach(current, targetArchitecture);
    const phases = await this.planMigrationPhases(current, targetArchitecture, migrationApproach);

    return {
      targetArchitecture,
      migrationApproach,
      migrationPhases: phases,
      riskAssessment: await this.assessMigrationRisks(phases),
      rollbackStrategy: this.planRollbackStrategy(phases),
      successMetrics: this.defineSuccessMetrics(target)
    };
  }

  private selectMigrationApproach(
    current: ArchitectureAnalysis,
    target: TargetArchitecture
  ): MigrationApproach {
    const factors = {
      systemSize: current.currentState.systemArchitecture.complexity,
      businessCriticality: current.businessDrivers.businessGrowthProjections.length,
      riskTolerance: this.assessRiskTolerance(current),
      timeConstraints: this.assessTimeConstraints(current),
      teamCapabilities: this.assessTeamCapabilities(current)
    };

    // Strangler Fig pattern for large, critical systems
    if (factors.systemSize === 'large' && factors.businessCriticality === 'high') {
      return 'strangler-fig';
    }

    // Incremental for moderate complexity systems
    if (factors.systemSize === 'medium' && factors.riskTolerance === 'moderate') {
      return 'incremental';
    }

    // Big Bang for small, non-critical systems
    if (factors.systemSize === 'small' && factors.riskTolerance === 'high') {
      return 'big-bang';
    }

    // Default to incremental for safety
    return 'incremental';
  }
}
```

## Workflow Stages

### Stage 1: Architecture Assessment & Planning

```typescript
interface ArchitectureAssessmentStage {
  activities: [
    'Current architecture documentation and analysis',
    'Technology stack assessment and gap analysis',
    'Performance and scalability bottleneck identification',
    'Business requirements and growth projections analysis',
    'Target architecture design and validation',
    'Migration strategy and roadmap development'
  ];
  chatmodes: ['software-architect', 'business-analyst', 'security-engineer'];
  deliverables: [
    'Current state architecture documentation',
    'Technical debt assessment report',
    'Target architecture blueprint',
    'Migration strategy and roadmap',
    'Risk assessment and mitigation plan'
  ];
}

// Architecture assessment implementation patterns
const architectureAssessmentPatterns = {
  monolithToMicroservices: {
    chatmode: 'software-architect',
    assessment: `
// Monolith to Microservices Migration Assessment
interface MonolithAnalysis {
  codebaseStructure: CodebaseStructure;
  domainBoundaries: DomainBoundary[];
  dataAccessPatterns: DataAccessPattern[];
  transactionBoundaries: TransactionBoundary[];
  communicationPatterns: CommunicationPattern[];
}

class MonolithToMicroservicesAnalyzer {
  async analyzeMonolith(codebasePath: string): Promise<MonolithAnalysis> {
    return {
      codebaseStructure: await this.analyzeCodebaseStructure(codebasePath),
      domainBoundaries: await this.identifyDomainBoundaries(codebasePath),
      dataAccessPatterns: await this.analyzeDataAccess(codebasePath),
      transactionBoundaries: await this.identifyTransactions(codebasePath),
      communicationPatterns: await this.analyzeCommunication(codebasePath)
    };
  }

  private async identifyDomainBoundaries(codebasePath: string): Promise<DomainBoundary[]> {
    // Analyze code structure to identify potential service boundaries
    const packageAnalysis = await this.analyzePackageStructure(codebasePath);
    const dependencyGraph = await this.buildDependencyGraph(codebasePath);
    const databaseAnalysis = await this.analyzeDatabaseSchema(codebasePath);

    return this.identifyBoundariesFromAnalysis({
      packages: packageAnalysis,
      dependencies: dependencyGraph,
      database: databaseAnalysis
    });
  }

  private async analyzeDataAccess(codebasePath: string): Promise<DataAccessPattern[]> {
    // Identify data access patterns that might complicate microservices separation
    return [
      await this.findSharedDatabaseAccess(codebasePath),
      await this.findTransactionalBoundaries(codebasePath),
      await this.findDataConsistencyRequirements(codebasePath)
    ].flat();
  }

  generateMigrationStrategy(analysis: MonolithAnalysis): MicroservicesMigrationStrategy {
    const serviceExtractionOrder = this.planServiceExtractionOrder(analysis.domainBoundaries);
    const dataStrategy = this.planDataSeparationStrategy(analysis.dataAccessPatterns);

    return {
      approach: 'strangler-fig',
      phases: serviceExtractionOrder.map((boundary, index) => ({
        phase: index + 1,
        serviceName: boundary.name,
        extractionComplexity: boundary.complexity,
        dataStrategy: dataStrategy[boundary.name],
        estimatedDuration: this.estimateMigrationDuration(boundary),
        prerequisites: this.identifyPrerequisites(boundary, analysis),
        successCriteria: this.defineServiceSuccessCriteria(boundary)
      })),
      riskMitigation: this.planRiskMitigation(analysis)
    };
  }
}
    `,

    implementation: `
// Strangler Fig Implementation Pattern
class StranglerFigMigration {
  constructor(
    private legacySystem: LegacySystem,
    private targetArchitecture: MicroservicesArchitecture
  ) {}

  async implementStranglerFig(): Promise<void> {
    // Phase 1: Set up proxy/gateway layer
    await this.setupApiGateway();

    // Phase 2: Implement monitoring and observability
    await this.setupObservability();

    // Phase 3: Begin service extraction
    for (const service of this.targetArchitecture.services) {
      await this.extractService(service);
    }

    // Phase 4: Decommission legacy components
    await this.decommissionLegacyComponents();
  }

  private async setupApiGateway(): Promise<void> {
    // API Gateway configuration for routing
    const gatewayConfig = {
      routes: [
        {
          path: '/api/users/*',
          target: 'legacy-system', // Initially route to legacy
          canary: {
            enabled: false,
            newTarget: 'user-service',
            percentage: 0
          }
        },
        {
          path: '/api/orders/*',
          target: 'legacy-system',
          canary: {
            enabled: false,
            newTarget: 'order-service',
            percentage: 0
          }
        }
      ]
    };

    await this.deployApiGateway(gatewayConfig);
  }

  private async extractService(service: ServiceDefinition): Promise<void> {
    // 1. Implement new service
    const newService = await this.implementNewService(service);

    // 2. Set up data synchronization
    await this.setupDataSync(service, newService);

    // 3. Gradually shift traffic
    await this.performCanaryMigration(service, newService);

    // 4. Remove legacy code
    await this.removeLegacyCode(service);
  }

  private async performCanaryMigration(
    serviceDefinition: ServiceDefinition,
    newService: Service
  ): Promise<void> {
    const trafficPercentages = [5, 10, 25, 50, 100];

    for (const percentage of trafficPercentages) {
      // Update gateway routing
      await this.updateGatewayRouting(serviceDefinition.path, percentage);

      // Monitor for issues
      const monitoring = await this.monitorCanaryDeployment(
        serviceDefinition,
        percentage,
        { duration: '15m', errorThreshold: 0.01 }
      );

      if (!monitoring.successful) {
        await this.rollbackCanary(serviceDefinition);
        throw new Error(\`Canary deployment failed at \${percentage}%: \${monitoring.error}\`);
      }

      // Wait between traffic increases
      await this.sleep(900000); // 15 minutes
    }
  }
}
    `,

    transition: 'Switch to `deployment-engineer` chatmode for infrastructure planning'
  },

  cloudMigration: {
    chatmode: 'software-architect',
    assessment: `
// Cloud Migration Assessment (On-premise to Cloud)
interface CloudMigrationAnalysis {
  currentInfrastructure: InfrastructureAssessment;
  cloudReadiness: CloudReadinessAssessment;
  migrationCandidates: MigrationCandidate[];
  costAnalysis: CostAnalysis;
  securityConsiderations: SecurityConsideration[];
}

class CloudMigrationAnalyzer {
  async assessCloudMigration(
    currentInfrastructure: Infrastructure
  ): Promise<CloudMigrationAnalysis> {

    return {
      currentInfrastructure: await this.assessCurrentInfrastructure(currentInfrastructure),
      cloudReadiness: await this.assessCloudReadiness(currentInfrastructure),
      migrationCandidates: await this.identifyMigrationCandidates(currentInfrastructure),
      costAnalysis: await this.performCostAnalysis(currentInfrastructure),
      securityConsiderations: await this.analyzeSecurityRequirements(currentInfrastructure)
    };
  }

  private async assessCurrentInfrastructure(
    infrastructure: Infrastructure
  ): Promise<InfrastructureAssessment> {
    return {
      servers: await this.analyzeServers(infrastructure.servers),
      databases: await this.analyzeDatabases(infrastructure.databases),
      storage: await this.analyzeStorage(infrastructure.storage),
      networking: await this.analyzeNetworking(infrastructure.networking),
      monitoring: await this.analyzeMonitoring(infrastructure.monitoring),
      backup: await this.analyzeBackupSystems(infrastructure.backup)
    };
  }

  private async identifyMigrationCandidates(
    infrastructure: Infrastructure
  ): Promise<MigrationCandidate[]> {
    const applications = infrastructure.applications;

    return applications.map(app => ({
      applicationName: app.name,
      migrationStrategy: this.determineMigrationStrategy(app),
      cloudService: this.recommendCloudService(app),
      complexity: this.assessMigrationComplexity(app),
      dependencies: this.mapDependencies(app),
      estimatedEffort: this.estimateEffort(app),
      businessPriority: this.assessBusinessPriority(app)
    }));
  }

  private determineMigrationStrategy(application: Application): MigrationStrategy {
    // 6 R's of Cloud Migration
    if (application.architecture.isLegacy && !application.businessCriticality.isHigh) {
      return 'retire'; // Retire applications that are no longer needed
    }

    if (application.licensing.isProblematic || application.architecture.isObsolete) {
      return 'replace'; // Replace with SaaS solutions
    }

    if (application.architecture.isCloudNative || application.complexity.isLow) {
      return 'rehost'; // Lift and shift
    }

    if (application.performance.needsImprovement || application.scalability.isLimited) {
      return 'replatform'; // Lift, tinker, and shift
    }

    if (application.businessValue.isHigh && application.customization.isExtensive) {
      return 'refactor'; // Re-architect for cloud
    }

    return 'retain'; // Keep on-premises for now
  }
}
    `,

    implementation: `
// Cloud Migration Implementation (AWS Example)
class AWSCloudMigration {
  async implementCloudMigration(migrationPlan: CloudMigrationPlan): Promise<void> {
    // Phase 1: Set up cloud foundation
    await this.setupCloudFoundation();

    // Phase 2: Migrate data and databases
    await this.migrateData(migrationPlan.dataMigration);

    // Phase 3: Migrate applications
    for (const app of migrationPlan.applications) {
      await this.migrateApplication(app);
    }

    // Phase 4: Optimize and modernize
    await this.optimizeCloudResources();
  }

  private async setupCloudFoundation(): Promise<void> {
    // Set up VPC and networking
    const vpc = await this.createVPC({
      cidr: '10.0.0.0/16',
      subnets: [
        { cidr: '10.0.1.0/24', type: 'public', az: 'us-west-2a' },
        { cidr: '10.0.2.0/24', type: 'private', az: 'us-west-2a' },
        { cidr: '10.0.3.0/24', type: 'public', az: 'us-west-2b' },
        { cidr: '10.0.4.0/24', type: 'private', az: 'us-west-2b' }
      ]
    });

    // Set up security groups and NACLs
    await this.setupSecurity(vpc);

    // Set up monitoring and logging
    await this.setupCloudWatch();
    await this.setupCloudTrail();
  }

  private async migrateApplication(app: ApplicationMigration): Promise<void> {
    switch (app.strategy) {
      case 'rehost':
        await this.performLiftAndShift(app);
        break;
      case 'replatform':
        await this.performLiftTinkerShift(app);
        break;
      case 'refactor':
        await this.performRefactor(app);
        break;
      case 'replace':
        await this.performReplace(app);
        break;
    }
  }

  private async performLiftAndShift(app: ApplicationMigration): Promise<void> {
    // Create EC2 instances matching current infrastructure
    const instances = await this.createEC2Instances({
      imageId: app.currentImage,
      instanceType: this.mapInstanceType(app.currentSpecs),
      securityGroupIds: app.securityGroups,
      subnetId: app.targetSubnet
    });

    // Set up load balancer
    const loadBalancer = await this.createApplicationLoadBalancer({
      name: \`\${app.name}-alb\`,
      scheme: 'internet-facing',
      type: 'application',
      subnets: app.publicSubnets
    });

    // Configure auto scaling
    await this.setupAutoScaling({
      minSize: app.scaling.min,
      maxSize: app.scaling.max,
      desiredCapacity: app.scaling.desired,
      targetGroupArn: loadBalancer.targetGroup.arn
    });
  }

  private async performRefactor(app: ApplicationMigration): Promise<void> {
    // Convert to containerized architecture
    const containerDef = await this.containerizeApplication(app);

    // Deploy to ECS/EKS
    if (app.orchestration === 'kubernetes') {
      await this.deployToEKS(containerDef);
    } else {
      await this.deployToECS(containerDef);
    }

    // Set up managed services
    await this.setupManagedServices(app.services);
  }
}
    `,

    transition: 'Switch to `deployment-engineer` chatmode for cloud infrastructure setup'
  },

  performanceOptimization: {
    chatmode: 'software-architect',
    assessment: `
// Performance Architecture Assessment and Optimization
interface PerformanceAnalysis {
  currentPerformance: PerformanceMetrics;
  bottleneckAnalysis: BottleneckAnalysis;
  scalabilityAssessment: ScalabilityAssessment;
  optimizationOpportunities: OptimizationOpportunity[];
}

class PerformanceArchitectureAnalyzer {
  async analyzePerformance(system: SystemArchitecture): Promise<PerformanceAnalysis> {
    return {
      currentPerformance: await this.measureCurrentPerformance(system),
      bottleneckAnalysis: await this.identifyBottlenecks(system),
      scalabilityAssessment: await this.assessScalability(system),
      optimizationOpportunities: await this.identifyOptimizations(system)
    };
  }

  private async identifyBottlenecks(system: SystemArchitecture): Promise<BottleneckAnalysis> {
    const bottlenecks = await Promise.all([
      this.analyzeApplicationBottlenecks(system),
      this.analyzeDatabaseBottlenecks(system),
      this.analyzeNetworkBottlenecks(system),
      this.analyzeInfrastructureBottlenecks(system)
    ]);

    return {
      application: bottlenecks[0],
      database: bottlenecks[1],
      network: bottlenecks[2],
      infrastructure: bottlenecks[3],
      priority: this.prioritizeBottlenecks(bottlenecks)
    };
  }

  private async analyzeApplicationBottlenecks(
    system: SystemArchitecture
  ): Promise<ApplicationBottleneck[]> {
    return [
      await this.findSlowEndpoints(system),
      await this.findMemoryLeaks(system),
      await this.findCPUIntensiveOperations(system),
      await this.findBlockingOperations(system),
      await this.findInefficinetAlgorithms(system)
    ].flat();
  }

  private async identifyOptimizations(
    system: SystemArchitecture
  ): Promise<OptimizationOpportunity[]> {
    return [
      // Caching opportunities
      {
        type: 'caching',
        description: 'Implement Redis cache for frequent database queries',
        impact: 'high',
        effort: 'medium',
        implementation: await this.planCachingStrategy(system)
      },

      // Database optimizations
      {
        type: 'database',
        description: 'Add database indexes for slow queries',
        impact: 'high',
        effort: 'low',
        implementation: await this.planDatabaseOptimizations(system)
      },

      // CDN implementation
      {
        type: 'cdn',
        description: 'Implement CDN for static assets',
        impact: 'medium',
        effort: 'low',
        implementation: await this.planCDNImplementation(system)
      },

      // Load balancing improvements
      {
        type: 'load-balancing',
        description: 'Optimize load balancing strategy',
        impact: 'medium',
        effort: 'medium',
        implementation: await this.planLoadBalancingOptimizations(system)
      }
    ];
  }
}
    `,

    implementation: `
// Performance Optimization Implementation Patterns
class PerformanceOptimizationImplementation {
  async implementOptimizations(opportunities: OptimizationOpportunity[]): Promise<void> {
    // Prioritize optimizations by impact/effort ratio
    const prioritized = this.prioritizeOptimizations(opportunities);

    for (const optimization of prioritized) {
      await this.implementOptimization(optimization);
    }
  }

  private async implementCaching(cachingPlan: CachingStrategy): Promise<void> {
    // Redis cache implementation
    const redisConfig = {
      host: process.env.REDIS_HOST,
      port: parseInt(process.env.REDIS_PORT || '6379'),
      password: process.env.REDIS_PASSWORD,
      retryDelayOnFailover: 100,
      enableReadyCheck: false,
      maxRetriesPerRequest: null
    };

    const redis = new Redis(redisConfig);

    // Implement cache-aside pattern
    const cacheAsideImplementation = {
      async get(key: string): Promise<any> {
        // Try cache first
        const cached = await redis.get(key);
        if (cached) {
          return JSON.parse(cached);
        }

        // Fallback to database
        const data = await database.query(key);

        // Cache the result
        await redis.setex(key, 3600, JSON.stringify(data)); // 1 hour TTL

        return data;
      },

      async invalidate(pattern: string): Promise<void> {
        const keys = await redis.keys(pattern);
        if (keys.length > 0) {
          await redis.del(...keys);
        }
      }
    };

    // Implement write-through pattern for critical data
    const writeThroughImplementation = {
      async set(key: string, value: any): Promise<void> {
        // Write to database first
        await database.save(key, value);

        // Then update cache
        await redis.setex(key, 3600, JSON.stringify(value));
      }
    };
  }

  private async implementDatabaseOptimizations(dbPlan: DatabaseOptimizationPlan): Promise<void> {
    // Add indexes for slow queries
    for (const index of dbPlan.indexes) {
      await this.database.createIndex(index);
    }

    // Optimize query patterns
    for (const query of dbPlan.queryOptimizations) {
      await this.implementQueryOptimization(query);
    }

    // Set up connection pooling
    const poolConfig = {
      min: 5,
      max: 20,
      acquireTimeoutMillis: 60000,
      createTimeoutMillis: 30000,
      destroyTimeoutMillis: 5000,
      idleTimeoutMillis: 30000,
      reapIntervalMillis: 1000,
      createRetryIntervalMillis: 100
    };

    await this.setupConnectionPooling(poolConfig);
  }

  private async implementCDN(cdnPlan: CDNImplementationPlan): Promise<void> {
    // CloudFront distribution setup
    const distribution = await this.createCloudFrontDistribution({
      origins: [{
        id: 'primary-origin',
        domainName: cdnPlan.originDomain,
        customOriginConfig: {
          httpPort: 80,
          httpsPort: 443,
          originProtocolPolicy: 'https-only'
        }
      }],
      defaultCacheBehavior: {
        targetOriginId: 'primary-origin',
        viewerProtocolPolicy: 'redirect-to-https',
        cachePolicyId: 'managed-caching-optimized',
        compress: true
      },
      cacheBehaviors: cdnPlan.cacheBehaviors
    });

    // Update application to serve assets from CDN
    await this.updateAssetURLs(distribution.domainName);
  }
}
    `,

    transition: 'Switch to `qa-engineer` chatmode for performance testing validation'
  }
};
```

### Stage 2: Implementation Planning & Execution

```typescript
interface ImplementationExecutionStage {
  planningActivities: [
    'Detailed implementation roadmap creation',
    'Resource allocation and team assignment',
    'Risk mitigation strategy development',
    'Success metrics and monitoring setup',
    'Communication and change management planning'
  ];
  executionActivities: [
    'Infrastructure setup and preparation',
    'Incremental implementation with validation',
    'Monitoring and observability implementation',
    'Testing and quality assurance',
    'Documentation and knowledge transfer'
  ];
  chatmodes: ['deployment-engineer', 'backend-engineer', 'frontend-engineer', 'data-engineer'];
}

// Implementation execution coordination
const implementationExecutionCoordination = {
  phases: [
    {
      name: 'Foundation Setup',
      chatmode: 'deployment-engineer',
      activities: [
        'Infrastructure provisioning and configuration',
        'Monitoring and observability setup',
        'Security and compliance framework implementation',
        'CI/CD pipeline adaptation for new architecture'
      ]
    },
    {
      name: 'Core Migration',
      chatmodes: ['backend-engineer', 'frontend-engineer', 'data-engineer'],
      activities: [
        'Application component migration/refactoring',
        'Database schema evolution and data migration',
        'API interface evolution and versioning',
        'Integration testing and validation'
      ]
    },
    {
      name: 'Optimization & Validation',
      chatmode: 'qa-engineer',
      activities: [
        'Performance testing and optimization',
        'Load testing and scalability validation',
        'Security testing and compliance verification',
        'User acceptance testing and feedback incorporation'
      ]
    }
  ]
};
```

### Stage 3: Validation & Optimization

```typescript
interface ValidationOptimizationStage {
  validationActivities: [
    'Architecture compliance verification',
    'Performance benchmarking and comparison',
    'Security audit and penetration testing',
    'Business metrics validation',
    'User experience impact assessment'
  ];
  optimizationActivities: [
    'Performance tuning based on real-world usage',
    'Cost optimization and resource rightsizing',
    'Security hardening and compliance updates',
    'Documentation updates and knowledge sharing',
    'Lessons learned capture and process improvement'
  ];
  chatmodes: ['qa-engineer', 'security-engineer', 'business-analyst'];
}

// Validation and optimization implementation
const validationOptimizationPatterns = {
  performanceValidation: `
// Architecture Performance Validation
class ArchitecturePerformanceValidator {
  async validatePerformanceImprovements(
    baseline: PerformanceBaseline,
    current: PerformanceMetrics
  ): Promise<PerformanceValidationResult> {

    const improvements = this.calculateImprovements(baseline, current);
    const regressions = this.identifyRegressions(baseline, current);

    return {
      improvements,
      regressions,
      overallAssessment: this.assessOverallPerformance(improvements, regressions),
      recommendations: this.generateOptimizationRecommendations(current)
    };
  }

  private calculateImprovements(
    baseline: PerformanceBaseline,
    current: PerformanceMetrics
  ): PerformanceImprovement[] {
    return [
      {
        metric: 'response_time',
        baseline: baseline.responseTime,
        current: current.responseTime,
        improvement: ((baseline.responseTime - current.responseTime) / baseline.responseTime) * 100,
        status: current.responseTime < baseline.responseTime ? 'improved' : 'degraded'
      },
      {
        metric: 'throughput',
        baseline: baseline.throughput,
        current: current.throughput,
        improvement: ((current.throughput - baseline.throughput) / baseline.throughput) * 100,
        status: current.throughput > baseline.throughput ? 'improved' : 'degraded'
      },
      {
        metric: 'error_rate',
        baseline: baseline.errorRate,
        current: current.errorRate,
        improvement: ((baseline.errorRate - current.errorRate) / baseline.errorRate) * 100,
        status: current.errorRate < baseline.errorRate ? 'improved' : 'degraded'
      }
    ];
  }
}
  `,

  securityValidation: `
// Architecture Security Validation
class ArchitectureSecurityValidator {
  async validateSecurityPosture(architecture: NewArchitecture): Promise<SecurityValidationResult> {
    const securityAssessment = await Promise.all([
      this.validateNetworkSecurity(architecture),
      this.validateApplicationSecurity(architecture),
      this.validateDataSecurity(architecture),
      this.validateAccessControls(architecture),
      this.validateCompliance(architecture)
    ]);

    return {
      networkSecurity: securityAssessment[0],
      applicationSecurity: securityAssessment[1],
      dataSecurity: securityAssessment[2],
      accessControls: securityAssessment[3],
      compliance: securityAssessment[4],
      overallSecurityScore: this.calculateSecurityScore(securityAssessment)
    };
  }

  private async validateNetworkSecurity(architecture: NewArchitecture): Promise<NetworkSecurityAssessment> {
    return {
      firewallRules: await this.validateFirewallConfiguration(architecture.network),
      segmentation: await this.validateNetworkSegmentation(architecture.network),
      encryption: await this.validateNetworkEncryption(architecture.network),
      monitoring: await this.validateNetworkMonitoring(architecture.network)
    };
  }
}
  `
};
```

## Chatmode Transition Framework

### Architecture Evolution Coordination

```typescript
interface ArchitectureEvolutionTransitions {
  assessment: {
    primary: 'software-architect';
    supporting: ['business-analyst', 'security-engineer'];
    deliverables: ['Architecture analysis', 'Migration strategy', 'Risk assessment'];
    transition: 'Switch to implementation chatmodes based on migration strategy';
  };
  implementation: {
    monolith_to_microservices: ['backend-engineer', 'api-engineer', 'data-engineer'];
    cloud_migration: ['deployment-engineer', 'security-engineer'];
    performance_optimization: ['backend-engineer', 'frontend-engineer', 'qa-engineer'];
    transition: 'Switch to qa-engineer for validation and testing';
  };
  validation: {
    primary: 'qa-engineer';
    supporting: ['security-engineer', 'deployment-engineer'];
    deliverables: ['Performance validation', 'Security audit', 'Compliance verification'];
    transition: 'Switch to business-analyst for business impact assessment';
  };
}

class ArchitectureEvolutionOrchestrator {
  generateTransitionGuidance(
    currentPhase: ArchitecturePhase,
    nextPhase: ArchitecturePhase,
    migrationContext: MigrationContext
  ): string {
    return `
## Architecture Evolution Transition: ${currentPhase} → ${nextPhase}

### Migration Context
- **Migration Type**: ${migrationContext.type}
- **Current Architecture**: ${migrationContext.currentArchitecture}
- **Target Architecture**: ${migrationContext.targetArchitecture}
- **Migration Approach**: ${migrationContext.approach}

### Current Phase Summary
${this.summarizeCurrentPhase(currentPhase, migrationContext)}

### Next Phase Requirements
${this.generateNextPhaseRequirements(nextPhase, migrationContext)}

### Recommended Chatmode: ${this.getOptimalChatmode(nextPhase, migrationContext)}

### Implementation Guidance
${this.generateImplementationGuidance(nextPhase, migrationContext)}

### Success Criteria
${this.generateSuccessCriteria(nextPhase, migrationContext)}

### Risk Mitigation
${this.generateRiskMitigation(nextPhase, migrationContext)}
    `;
  }
}
```

## Quality Gates & Standards

### Architecture Evolution Quality Framework

```typescript
const architectureEvolutionQualityGates: QualityGate[] = [
  {
    name: 'Architecture Design Validation',
    criteria: [
      { metric: 'design-completeness', threshold: 95, unit: 'percentage' },
      { metric: 'scalability-validation', threshold: 1, unit: 'boolean' },
      { metric: 'security-compliance', threshold: 100, unit: 'percentage' },
      { metric: 'performance-requirements-met', threshold: 1, unit: 'boolean' }
    ],
    automationLevel: 'semi-automated',
    blockingLevel: 'critical'
  },
  {
    name: 'Migration Implementation Validation',
    criteria: [
      { metric: 'migration-success-rate', threshold: 99, unit: 'percentage' },
      { metric: 'data-integrity-maintained', threshold: 100, unit: 'percentage' },
      { metric: 'performance-degradation', threshold: 5, unit: 'percentage-max' },
      { metric: 'rollback-capability-verified', threshold: 1, unit: 'boolean' }
    ],
    automationLevel: 'fully-automated',
    blockingLevel: 'critical'
  },
  {
    name: 'Post-Migration Validation',
    criteria: [
      { metric: 'performance-improvement', threshold: 20, unit: 'percentage-min' },
      { metric: 'cost-optimization', threshold: 15, unit: 'percentage-min' },
      { metric: 'security-posture-improvement', threshold: 10, unit: 'percentage-min' },
      { metric: 'maintainability-improvement', threshold: 25, unit: 'percentage-min' }
    ],
    automationLevel: 'manual',
    blockingLevel: 'warning'
  }
];
```

## Examples & Use Cases

### Example 1: E-commerce Platform Microservices Migration

```bash
# Project: "Migrate monolithic e-commerce platform to microservices"
# Current: Ruby on Rails monolith with PostgreSQL
# Target: Node.js microservices with event-driven architecture

# Stage 1: Assessment (software-architect)
# - Domain boundary analysis (User, Product, Order, Payment, Inventory)
# - Data access pattern analysis and transaction boundary identification
# - Performance bottleneck identification and scalability requirements
# - Microservices extraction priority planning

# Stage 2: Implementation (backend-engineer + api-engineer + data-engineer)
# - Strangler Fig pattern implementation with API Gateway
# - Service extraction starting with User Service (lowest coupling)
# - Event sourcing implementation for order management
# - Database per service pattern with eventual consistency

# Stage 3: Validation (qa-engineer + security-engineer)
# - Distributed transaction testing and saga pattern validation
# - Performance testing under peak load conditions
# - Security audit of inter-service communication
# - Business metrics validation (conversion rate, order processing time)
```

### Example 2: Legacy On-Premise to AWS Cloud Migration

```bash
# Project: "Migrate legacy .NET applications to AWS cloud"
# Current: Windows Server, SQL Server, IIS on-premise
# Target: AWS ECS, RDS, Application Load Balancer

# Migration Strategy: Lift-Tinker-Shift approach
# - Containerize .NET applications with minimal changes
# - Migrate SQL Server to RDS with Multi-AZ deployment
# - Implement CloudFront CDN for static assets
# - Set up CloudWatch monitoring and alerting

# Phases:
# 1. Foundation setup with VPC, security groups, and monitoring
# 2. Database migration with DMS and validation
# 3. Application containerization and ECS deployment
# 4. Load balancer and auto-scaling configuration
# 5. Performance optimization and cost analysis
```

### Example 3: Performance Architecture Optimization

```bash
# Project: "Optimize React/Node.js application performance"
# Issues: Slow page load times, high server response times, poor user experience
# Goals: 50% improvement in page load time, 40% reduction in server response time

# Optimization Strategy:
# - Frontend: Code splitting, lazy loading, image optimization, CDN implementation
# - Backend: Database query optimization, Redis caching, API response optimization
# - Infrastructure: Load balancer optimization, auto-scaling improvements

# Implementation:
# 1. Performance baseline establishment and monitoring setup
# 2. Frontend optimizations with bundle analysis and lazy loading
# 3. Backend optimizations with database indexing and caching
# 4. Infrastructure improvements with CDN and load balancing
# 5. Validation and fine-tuning based on real-world metrics
```

This comprehensive architecture evolution workflow provides strategic guidance for large-scale system transformations with risk mitigation, incremental implementation, and thorough validation at enterprise scale.