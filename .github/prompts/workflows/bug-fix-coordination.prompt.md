---
name: bug-fix-coordination
description: Comprehensive bug fix coordination workflow from incident detection through resolution with priority-based triage and post-incident analysis
tools: [github-copilot, incident-management, debugging-tools, monitoring-integration, root-cause-analysis]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# Bug Fix Coordination Workflow

## Context Analysis Framework

This workflow provides intelligent coordination for bug fixes from detection through resolution with comprehensive incident management:

```markdown
## Incident Context Analysis
1. Read `copilot.instructions.md` for incident response procedures and escalation paths
2. Analyze bug reports, error logs, and monitoring alerts for severity assessment
3. Detect impact scope, affected systems, and user impact metrics
4. Understand current system state, recent deployments, and configuration changes
5. Map incident to optimal response strategy and resource allocation
```

## GitHub Integration Points

### 1. Incident Detection & Triage

```typescript
// Comprehensive bug analysis and prioritization system
interface BugAnalysis {
  incidentDetails: {
    reportId: string;
    title: string;
    description: string;
    reporter: string;
    timestamp: Date;
    source: 'user-report' | 'monitoring-alert' | 'automated-detection' | 'internal-discovery';
  };
  severityAssessment: {
    severity: 'critical' | 'high' | 'medium' | 'low';
    impact: 'system-down' | 'feature-broken' | 'performance-degraded' | 'minor-issue';
    urgency: 'immediate' | 'high' | 'medium' | 'low';
    userImpact: UserImpact;
    businessImpact: BusinessImpact;
  };
  technicalAnalysis: {
    affectedSystems: string[];
    potentialCauses: PotentialCause[];
    reproducibility: 'always' | 'intermittent' | 'rare' | 'unknown';
    environment: 'production' | 'staging' | 'development' | 'all';
  };
}

class BugTriageSystem {
  async analyzeBugReport(reportId: string): Promise<BugAnalysis> {
    const incident = await this.fetchIncidentDetails(reportId);
    const systemMetrics = await this.gatherSystemMetrics(incident.timestamp);
    const historicalData = await this.analyzeHistoricalPatterns(incident);

    return {
      incidentDetails: this.extractIncidentDetails(incident),
      severityAssessment: await this.assessSeverity(incident, systemMetrics),
      technicalAnalysis: await this.performTechnicalAnalysis(incident, systemMetrics, historicalData)
    };
  }

  private async assessSeverity(
    incident: Incident,
    systemMetrics: SystemMetrics
  ): Promise<SeverityAssessment> {
    const impactFactors = {
      systemAvailability: this.calculateAvailabilityImpact(systemMetrics),
      userAffected: this.estimateAffectedUsers(incident, systemMetrics),
      revenueImpact: this.calculateRevenueImpact(incident, systemMetrics),
      dataIntegrity: this.assessDataIntegrityRisk(incident),
      securityImplications: this.assessSecurityRisk(incident)
    };

    const severityScore = this.calculateSeverityScore(impactFactors);

    return {
      severity: this.mapScoreToSeverity(severityScore),
      impact: this.determineImpactLevel(impactFactors),
      urgency: this.calculateUrgency(severityScore, incident.timestamp),
      userImpact: this.analyzeUserImpact(impactFactors),
      businessImpact: this.analyzeBusinessImpact(impactFactors)
    };
  }

  private calculateSeverityScore(factors: ImpactFactors): number {
    const weights = {
      systemAvailability: 0.3,
      userAffected: 0.25,
      revenueImpact: 0.2,
      dataIntegrity: 0.15,
      securityImplications: 0.1
    };

    return Object.entries(factors).reduce((score, [factor, value]) => {
      return score + (value * weights[factor]);
    }, 0);
  }
}
```

### 2. Intelligent Bug Assignment & Team Coordination

```typescript
// Smart bug assignment and team coordination
interface BugAssignmentStrategy {
  primaryAssignee: TeamMember;
  supportingTeam: TeamMember[];
  escalationPath: EscalationLevel[];
  communicationPlan: CommunicationPlan;
  resourceAllocation: ResourceAllocation;
}

class BugAssignmentEngine {
  async assignBugToTeam(bugAnalysis: BugAnalysis): Promise<BugAssignmentStrategy> {
    const teamAvailability = await this.getTeamAvailability();
    const expertiseMatch = await this.matchExpertiseToIssue(bugAnalysis);
    const currentWorkload = await this.analyzeCurrentWorkload();

    return {
      primaryAssignee: this.selectPrimaryAssignee(expertiseMatch, teamAvailability, currentWorkload),
      supportingTeam: this.selectSupportingTeam(bugAnalysis, expertiseMatch),
      escalationPath: this.defineEscalationPath(bugAnalysis),
      communicationPlan: this.createCommunicationPlan(bugAnalysis),
      resourceAllocation: this.planResourceAllocation(bugAnalysis, teamAvailability)
    };
  }

  private selectPrimaryAssignee(
    expertiseMatch: ExpertiseMatch[],
    availability: TeamAvailability,
    workload: WorkloadAnalysis
  ): TeamMember {
    // Score team members based on expertise, availability, and current load
    const candidates = expertiseMatch.map(match => ({
      member: match.member,
      score: this.calculateAssignmentScore(match, availability, workload)
    }));

    return candidates.sort((a, b) => b.score - a.score)[0].member;
  }

  private calculateAssignmentScore(
    match: ExpertiseMatch,
    availability: TeamAvailability,
    workload: WorkloadAnalysis
  ): number {
    const expertiseScore = match.expertiseLevel * 0.4;
    const availabilityScore = availability.getAvailability(match.member.id) * 0.3;
    const workloadScore = (1 - workload.getCurrentLoad(match.member.id)) * 0.3;

    return expertiseScore + availabilityScore + workloadScore;
  }
}
```

## Workflow Stages

### Stage 1: Incident Response & Investigation

```typescript
interface IncidentResponseStage {
  immediateActions: [
    'Acknowledge incident and set status',
    'Assess severity and impact',
    'Notify stakeholders per escalation matrix',
    'Begin initial investigation',
    'Implement immediate mitigation if available'
  ];
  investigationActivities: [
    'Reproduce issue in controlled environment',
    'Analyze logs and monitoring data',
    'Review recent code changes and deployments',
    'Identify potential root causes',
    'Document findings and hypotheses'
  ];
  chatmodes: ['software-architect', 'backend-engineer', 'frontend-engineer', 'security-engineer'];
}

// Critical Bug Investigation Implementation
class CriticalBugInvestigation {
  async executeIncidentResponse(bugAnalysis: BugAnalysis): Promise<IncidentResponse> {
    // Immediate response based on severity
    const immediateActions = await this.executeImmediateResponse(bugAnalysis);

    // Technical investigation
    const investigation = await this.conductTechnicalInvestigation(bugAnalysis);

    // Mitigation planning
    const mitigationPlan = await this.planImmediateMitigation(bugAnalysis, investigation);

    return {
      immediateActions,
      investigation,
      mitigationPlan,
      nextSteps: this.planNextSteps(bugAnalysis, investigation)
    };
  }

  private async executeImmediateResponse(bugAnalysis: BugAnalysis): Promise<ImmediateResponse> {
    const actions: ImmediateAction[] = [];

    // Critical severity requires immediate escalation
    if (bugAnalysis.severityAssessment.severity === 'critical') {
      actions.push(await this.notifyIncidentCommander());
      actions.push(await this.activateWarRoom());
      actions.push(await this.implementEmergencyMitigation());
    }

    // High severity requires rapid response
    if (bugAnalysis.severityAssessment.severity === 'high') {
      actions.push(await this.notifyOnCallTeam());
      actions.push(await this.escalateToTeamLead());
    }

    // All severities require status tracking
    actions.push(await this.createIncidentTicket(bugAnalysis));
    actions.push(await this.updateStatusPage(bugAnalysis));

    return {
      actions,
      timestamp: new Date(),
      responseTime: this.calculateResponseTime(bugAnalysis.incidentDetails.timestamp)
    };
  }

  private async conductTechnicalInvestigation(bugAnalysis: BugAnalysis): Promise<TechnicalInvestigation> {
    const investigation = {
      logAnalysis: await this.analyzeLogs(bugAnalysis),
      metricsAnalysis: await this.analyzeMetrics(bugAnalysis),
      codeAnalysis: await this.analyzeRecentChanges(bugAnalysis),
      environmentAnalysis: await this.analyzeEnvironment(bugAnalysis),
      dependencyAnalysis: await this.analyzeDependencies(bugAnalysis)
    };

    return {
      ...investigation,
      rootCauseHypotheses: this.generateRootCauseHypotheses(investigation),
      reproductionSteps: await this.defineReproductionSteps(bugAnalysis, investigation),
      impactAssessment: this.assessDetailedImpact(bugAnalysis, investigation)
    };
  }
}
```

### Stage 2: Technology-Specific Bug Investigation

#### Frontend Bug Investigation (React/TypeScript)

```typescript
// React-specific bug investigation and debugging
const reactBugInvestigation = {
  chatmode: 'frontend-engineer',
  investigationTools: [
    'React DevTools for component state analysis',
    'Browser Developer Tools for network and performance',
    'Error boundary logs for component errors',
    'Redux DevTools for state management issues',
    'Lighthouse for performance issues'
  ],

  commonBugPatterns: {
    'state-management-issues': {
      symptoms: ['Inconsistent UI state', 'State not updating', 'Race conditions'],
      investigation: `
// React State Management Bug Investigation
const investigateStateIssues = {
  // Check for common state anti-patterns
  checkStateAntiPatterns: () => {
    // 1. Direct state mutation
    console.warn('Checking for direct state mutations...');
    // Look for: state.someProperty = newValue

    // 2. Missing dependency arrays in useEffect
    console.warn('Checking useEffect dependency arrays...');

    // 3. Stale closures in event handlers
    console.warn('Checking for stale closures...');
  },

  // Debug component re-render issues
  debugRerenderIssues: () => {
    // Use React.memo() and useMemo() analysis
    const ComponentWithDebug = React.memo((props) => {
      console.log('Component rerendered with props:', props);
      return <YourComponent {...props} />;
    });

    // Track prop changes
    const usePrevious = (value) => {
      const ref = useRef();
      useEffect(() => {
        ref.current = value;
      });
      return ref.current;
    };
  },

  // Analyze async state updates
  debugAsyncStateUpdates: async () => {
    // Check for race conditions in async operations
    let isCancelled = false;

    try {
      const data = await fetchData();
      if (!isCancelled) {
        setState(data);
      }
    } catch (error) {
      if (!isCancelled) {
        setError(error);
      }
    }

    return () => {
      isCancelled = true;
    };
  }
};
      `,

      resolution: `
// React State Management Bug Fix Patterns
const fixStateIssues = {
  // Fix direct state mutations
  fixDirectMutations: () => {
    // WRONG: state.items.push(newItem)
    // CORRECT: setState(prev => [...prev.items, newItem])

    const [items, setItems] = useState([]);

    const addItem = (newItem) => {
      setItems(prevItems => [...prevItems, newItem]);
    };

    const updateItem = (id, updates) => {
      setItems(prevItems =>
        prevItems.map(item =>
          item.id === id ? { ...item, ...updates } : item
        )
      );
    };
  },

  // Fix useEffect dependency issues
  fixEffectDependencies: () => {
    const [data, setData] = useState(null);
    const [filter, setFilter] = useState('');

    // Include all dependencies
    useEffect(() => {
      const fetchFilteredData = async () => {
        const result = await api.getData(filter);
        setData(result);
      };

      fetchFilteredData();
    }, [filter]); // Include filter in dependencies

    // Use callback to avoid dependency issues
    const stableCallback = useCallback(
      (value) => api.processData(value, filter),
      [filter]
    );
  },

  // Fix async race conditions
  fixRaceConditions: () => {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(false);

    useEffect(() => {
      let isCancelled = false;
      setLoading(true);

      const fetchData = async () => {
        try {
          const result = await api.getData();
          if (!isCancelled) {
            setData(result);
            setLoading(false);
          }
        } catch (error) {
          if (!isCancelled) {
            setError(error);
            setLoading(false);
          }
        }
      };

      fetchData();

      return () => {
        isCancelled = true;
      };
    }, []);
  }
};
      `
    },

    'performance-issues': {
      symptoms: ['Slow rendering', 'Janky animations', 'Memory leaks', 'Large bundle size'],
      investigation: `
// React Performance Bug Investigation
import { Profiler } from 'react';

const performanceInvestigation = {
  // Profile component rendering
  profileComponent: (id, phase, actualDuration, baseDuration, startTime, commitTime, interactions) => {
    console.log('Performance Profile:', {
      id,
      phase, // "mount" or "update"
      actualDuration, // Time spent rendering
      baseDuration, // Time without memoization
      startTime,
      commitTime,
      interactions
    });

    // Flag slow components
    if (actualDuration > 16) { // More than one frame (60fps)
      console.warn(\`Slow component detected: \${id} took \${actualDuration}ms\`);
    }
  },

  // Check for unnecessary re-renders
  checkUnnecessaryRerenders: () => {
    // Use React DevTools Profiler
    // Look for components that re-render without prop changes

    // Debug with useWhyDidYouUpdate hook
    const useWhyDidYouUpdate = (name, props) => {
      const previous = useRef();

      useEffect(() => {
        if (previous.current) {
          const allKeys = Object.keys({...previous.current, ...props});
          const changedKeys = {};

          allKeys.forEach(key => {
            if (previous.current[key] !== props[key]) {
              changedKeys[key] = {
                from: previous.current[key],
                to: props[key]
              };
            }
          });

          if (Object.keys(changedKeys).length) {
            console.log('[why-did-you-update]', name, changedKeys);
          }
        }

        previous.current = props;
      });
    };
  },

  // Memory leak detection
  detectMemoryLeaks: () => {
    // Check for event listeners not being cleaned up
    useEffect(() => {
      const handleResize = () => {
        // Handle window resize
      };

      window.addEventListener('resize', handleResize);

      return () => {
        window.removeEventListener('resize', handleResize);
      };
    }, []);

    // Check for timers not being cleared
    useEffect(() => {
      const timer = setInterval(() => {
        // Do something
      }, 1000);

      return () => {
        clearInterval(timer);
      };
    }, []);
  }
};
      `
    }
  }
};
```

#### Backend Bug Investigation (Node.js/Express)

```typescript
// Node.js backend bug investigation patterns
const nodeBugInvestigation = {
  chatmode: 'backend-engineer',
  investigationTools: [
    'Application logs and error tracking',
    'Performance monitoring (APM)',
    'Database query analysis',
    'Memory and CPU profiling',
    'Network trace analysis'
  ],

  commonBugPatterns: {
    'memory-leaks': {
      investigation: `
// Node.js Memory Leak Investigation
const memoryLeakInvestigation = {
  // Monitor memory usage
  monitorMemoryUsage: () => {
    const memoryUsage = process.memoryUsage();
    console.log('Memory Usage:', {
      rss: \`\${Math.round(memoryUsage.rss / 1024 / 1024)} MB\`, // Resident Set Size
      heapTotal: \`\${Math.round(memoryUsage.heapTotal / 1024 / 1024)} MB\`,
      heapUsed: \`\${Math.round(memoryUsage.heapUsed / 1024 / 1024)} MB\`,
      external: \`\${Math.round(memoryUsage.external / 1024 / 1024)} MB\`
    });

    // Set up periodic monitoring
    setInterval(() => {
      const usage = process.memoryUsage();
      if (usage.heapUsed > 500 * 1024 * 1024) { // 500MB threshold
        console.warn('High memory usage detected:', usage);
      }
    }, 30000); // Check every 30 seconds
  },

  // Check for common leak sources
  checkCommonLeakSources: () => {
    // 1. Event listeners not removed
    const EventEmitter = require('events');
    const emitter = new EventEmitter();

    // Monitor event listener count
    emitter.on('newListener', (event, listener) => {
      const count = emitter.listenerCount(event);
      if (count > 10) { // Threshold for potential leak
        console.warn(\`Potential memory leak: \${count} listeners for event '\${event}'\`);
      }
    });

    // 2. Timers not cleared
    const activeTimers = new Set();

    const setIntervalWithTracking = (callback, delay) => {
      const timer = setInterval(callback, delay);
      activeTimers.add(timer);
      return timer;
    };

    const clearIntervalWithTracking = (timer) => {
      clearInterval(timer);
      activeTimers.delete(timer);
    };

    // 3. Database connections not closed
    const activeDatabaseConnections = new Set();

    const trackDatabaseConnection = (connection) => {
      activeDatabaseConnections.add(connection);

      connection.on('close', () => {
        activeDatabaseConnections.delete(connection);
      });
    };
  },

  // Heap dump analysis
  createHeapDump: () => {
    const heapdump = require('heapdump');

    // Create heap dump on demand
    const createDump = () => {
      const filename = \`heapdump-\${Date.now()}.heapsnapshot\`;
      heapdump.writeSnapshot(filename, (err, filename) => {
        if (err) {
          console.error('Failed to create heap dump:', err);
        } else {
          console.log('Heap dump created:', filename);
        }
      });
    };

    // Automatic heap dump on high memory usage
    setInterval(() => {
      const usage = process.memoryUsage();
      if (usage.heapUsed > 1024 * 1024 * 1024) { // 1GB threshold
        createDump();
      }
    }, 60000);
  }
};
      `,

      resolution: `
// Memory Leak Resolution Patterns
const memoryLeakFixes = {
  // Fix event listener leaks
  fixEventListenerLeaks: () => {
    class RequestHandler {
      constructor() {
        this.activeRequests = new Map();
        this.handleRequest = this.handleRequest.bind(this);

        // Proper cleanup on process termination
        process.on('SIGTERM', this.cleanup.bind(this));
        process.on('SIGINT', this.cleanup.bind(this));
      }

      handleRequest(req, res) {
        const requestId = req.id;

        // Track active requests
        this.activeRequests.set(requestId, { req, res, startTime: Date.now() });

        // Clean up on response completion
        res.on('finish', () => {
          this.activeRequests.delete(requestId);
        });

        res.on('close', () => {
          this.activeRequests.delete(requestId);
        });
      }

      cleanup() {
        // Clean up all active requests
        for (const [requestId, request] of this.activeRequests) {
          if (!request.res.headersSent) {
            request.res.status(503).send('Server shutting down');
          }
        }
        this.activeRequests.clear();
      }
    }
  },

  // Fix database connection leaks
  fixDatabaseLeaks: () => {
    const mysql = require('mysql2/promise');

    class DatabaseManager {
      constructor() {
        this.pool = mysql.createPool({
          host: 'localhost',
          user: 'user',
          password: 'password',
          database: 'mydb',
          waitForConnections: true,
          connectionLimit: 10,
          queueLimit: 0,
          acquireTimeout: 60000,
          timeout: 60000
        });

        // Monitor pool status
        setInterval(() => {
          console.log('Pool status:', {
            totalConnections: this.pool.pool._allConnections.length,
            freeConnections: this.pool.pool._freeConnections.length,
            queuedRequests: this.pool.pool._connectionQueue.length
          });
        }, 30000);
      }

      async executeQuery(sql, params) {
        let connection;
        try {
          connection = await this.pool.getConnection();
          const [results] = await connection.execute(sql, params);
          return results;
        } finally {
          if (connection) connection.release(); // Always release connection
        }
      }

      async closePool() {
        await this.pool.end();
      }
    }
  },

  // Fix timer and callback leaks
  fixTimerLeaks: () => {
    class TimerManager {
      constructor() {
        this.activeTimers = new Set();
        this.activeTimeouts = new Set();
      }

      setInterval(callback, delay) {
        const timer = setInterval(callback, delay);
        this.activeTimers.add(timer);
        return timer;
      }

      setTimeout(callback, delay) {
        const timeout = setTimeout(() => {
          callback();
          this.activeTimeouts.delete(timeout);
        }, delay);
        this.activeTimeouts.add(timeout);
        return timeout;
      }

      clearInterval(timer) {
        clearInterval(timer);
        this.activeTimers.delete(timer);
      }

      clearTimeout(timeout) {
        clearTimeout(timeout);
        this.activeTimeouts.delete(timeout);
      }

      clearAllTimers() {
        for (const timer of this.activeTimers) {
          clearInterval(timer);
        }
        for (const timeout of this.activeTimeouts) {
          clearTimeout(timeout);
        }
        this.activeTimers.clear();
        this.activeTimeouts.clear();
      }
    }
  }
};
      `
    },

    'database-performance': {
      investigation: `
// Database Performance Issue Investigation
const databaseInvestigation = {
  // Query performance analysis
  analyzeSlowQueries: async () => {
    // Enable query logging
    const mysql = require('mysql2/promise');

    const connection = await mysql.createConnection({
      host: 'localhost',
      user: 'root',
      password: 'password',
      database: 'test'
    });

    // Log slow queries
    const originalQuery = connection.query;
    connection.query = function(...args) {
      const startTime = Date.now();
      const result = originalQuery.apply(this, args);

      result.then(() => {
        const duration = Date.now() - startTime;
        if (duration > 1000) { // Log queries taking more than 1 second
          console.warn('Slow query detected:', {
            sql: args[0],
            duration: \`\${duration}ms\`,
            params: args[1]
          });
        }
      });

      return result;
    };
  },

  // Connection pool analysis
  analyzeConnectionPool: () => {
    const poolAnalyzer = {
      monitorConnections: (pool) => {
        setInterval(() => {
          const stats = {
            total: pool.pool._allConnections.length,
            free: pool.pool._freeConnections.length,
            used: pool.pool._allConnections.length - pool.pool._freeConnections.length,
            pending: pool.pool._connectionQueue.length
          };

          console.log('Connection Pool Stats:', stats);

          // Alert on potential issues
          if (stats.used / stats.total > 0.9) {
            console.warn('High connection pool usage:', stats);
          }

          if (stats.pending > 0) {
            console.warn('Queued connection requests:', stats.pending);
          }
        }, 10000);
      },

      detectConnectionLeaks: (pool) => {
        const connectionAcquisitionTimes = new Map();

        pool.on('acquire', (connection) => {
          connectionAcquisitionTimes.set(connection.threadId, Date.now());
        });

        pool.on('release', (connection) => {
          connectionAcquisitionTimes.delete(connection.threadId);
        });

        // Check for long-held connections
        setInterval(() => {
          const now = Date.now();
          for (const [threadId, acquisitionTime] of connectionAcquisitionTimes) {
            const holdTime = now - acquisitionTime;
            if (holdTime > 30000) { // 30 seconds
              console.warn(\`Long-held connection detected: Thread \${threadId} held for \${holdTime}ms\`);
            }
          }
        }, 15000);
      }
    };
  }
};
      `
    }
  }
};
```

### Stage 3: Bug Resolution & Testing

```typescript
interface BugResolutionStage {
  resolutionStrategy: {
    quickFix: 'Immediate hotfix for critical issues';
    comprehensiveFix: 'Complete solution with thorough testing';
    workaround: 'Temporary mitigation while developing proper fix';
    architecturalChange: 'Requires significant system changes';
  };
  testingStrategy: {
    reproductionTests: 'Verify the bug can be consistently reproduced';
    fixValidation: 'Confirm the fix resolves the issue';
    regressionTesting: 'Ensure the fix doesnt break existing functionality';
    performanceImpact: 'Validate performance implications of the fix';
  };
  chatmode: 'qa-engineer' | 'backend-engineer' | 'frontend-engineer';
}

// Bug fix validation and testing
const bugFixValidation = {
  chatmode: 'qa-engineer',
  validationProcess: {
    preFixValidation: `
// Pre-fix validation tests
describe('Bug Reproduction Tests', () => {
  test('should consistently reproduce the reported bug', async () => {
    // Set up the exact conditions that cause the bug
    const testConditions = setupBugConditions();

    // Execute the steps that trigger the bug
    const result = await executeStepsThatTriggerBug(testConditions);

    // Verify the bug manifests as expected
    expect(result).toMatchBugSymptoms();
  });

  test('should reproduce bug across different environments', async () => {
    const environments = ['development', 'staging', 'production-like'];

    for (const env of environments) {
      const testEnv = await setupEnvironment(env);
      const result = await executeBugScenario(testEnv);

      expect(result.bugReproduced).toBe(true);
    }
  });

  test('should reproduce bug with different data sets', async () => {
    const testDataSets = generateTestDataSets();

    for (const dataSet of testDataSets) {
      const result = await executeBugScenario(dataSet);

      if (result.bugReproduced) {
        console.log('Bug reproduced with dataset:', dataSet.id);
      }
    }
  });
});
    `,

    postFixValidation: `
// Post-fix validation tests
describe('Bug Fix Validation', () => {
  test('should resolve the original bug scenario', async () => {
    // Use the same conditions that previously caused the bug
    const originalConditions = setupOriginalBugConditions();

    // Execute the same steps that previously triggered the bug
    const result = await executeOriginalBugSteps(originalConditions);

    // Verify the bug is now resolved
    expect(result.bugResolved).toBe(true);
    expect(result.errorMessages).toHaveLength(0);
  });

  test('should handle edge cases properly', async () => {
    const edgeCases = generateEdgeCases();

    for (const edgeCase of edgeCases) {
      const result = await executeEdgeCaseTest(edgeCase);

      expect(result.handledCorrectly).toBe(true);
      expect(result.errors).toHaveLength(0);
    }
  });

  test('should maintain performance within acceptable limits', async () => {
    const performanceTest = new PerformanceTest();

    const results = await performanceTest.run({
      scenario: 'bug-fix-scenario',
      iterations: 100,
      concurrency: 10
    });

    expect(results.averageResponseTime).toBeLessThan(200); // ms
    expect(results.p95ResponseTime).toBeLessThan(500); // ms
    expect(results.errorRate).toBeLessThan(0.01); // 1%
  });
});
    `,

    regressionTesting: `
// Regression testing to ensure fix doesn't break existing functionality
describe('Regression Testing', () => {
  test('should not affect existing user workflows', async () => {
    const criticalUserFlows = getCriticalUserFlows();

    for (const flow of criticalUserFlows) {
      const result = await executeUserFlow(flow);

      expect(result.successful).toBe(true);
      expect(result.errors).toHaveLength(0);
      expect(result.performanceMetrics.responseTime).toBeLessThan(flow.maxResponseTime);
    }
  });

  test('should not introduce new security vulnerabilities', async () => {
    const securityTests = getSecurityTestSuite();

    for (const test of securityTests) {
      const result = await executeSecurityTest(test);

      expect(result.vulnerabilitiesFound).toHaveLength(0);
      expect(result.securityScore).toBeGreaterThan(90);
    }
  });

  test('should maintain backward compatibility', async () => {
    const compatibilityTests = getBackwardCompatibilityTests();

    for (const test of compatibilityTests) {
      const result = await executeCompatibilityTest(test);

      expect(result.compatible).toBe(true);
      expect(result.deprecationWarnings).toHaveLength(0);
    }
  });
});
    `
  }
};
```

### Stage 4: Deployment & Monitoring

```typescript
interface BugFixDeploymentStage {
  deploymentStrategy: {
    hotfix: 'Immediate deployment for critical production issues';
    scheduledDeployment: 'Planned deployment for non-critical fixes';
    canaryDeployment: 'Gradual rollout for complex fixes';
    rollbackPlan: 'Comprehensive rollback strategy if issues arise';
  };
  monitoringStrategy: {
    errorRateMonitoring: 'Track error rates post-deployment';
    performanceMonitoring: 'Monitor performance impact';
    userImpactMonitoring: 'Track user experience metrics';
    businessImpactMonitoring: 'Monitor business metric recovery';
  };
  chatmode: 'deployment-engineer';
}

// Bug fix deployment and monitoring
const bugFixDeployment = {
  chatmode: 'deployment-engineer',
  deploymentStrategies: {
    criticalHotfix: `
# Critical Bug Hotfix Deployment Strategy
name: Critical Bug Hotfix Deployment

on:
  push:
    branches: [hotfix/*]

jobs:
  emergency-deployment:
    runs-on: ubuntu-latest
    environment: production

    steps:
      - uses: actions/checkout@v4

      - name: Validate hotfix branch
        run: |
          if [[ ! "${{ github.ref }}" =~ ^refs/heads/hotfix/ ]]; then
            echo "Only hotfix branches can trigger emergency deployment"
            exit 1
          fi

      - name: Run critical bug fix tests
        run: |
          # Run only tests related to the bug fix
          npm test -- --testPathPattern=bug-fix-tests
          npm run test:integration -- --grep "bug fix"

      - name: Security scan for hotfix
        run: |
          npm audit --audit-level high
          npx semgrep --config=auto

      - name: Deploy to production with monitoring
        run: |
          # Deploy with enhanced monitoring
          kubectl set image deployment/app app=new-image:${{ github.sha }}

          # Wait for deployment to be ready
          kubectl rollout status deployment/app --timeout=300s

          # Verify deployment health
          sleep 30
          ./scripts/health-check.sh

      - name: Enable enhanced monitoring
        run: |
          # Increase monitoring sensitivity
          ./scripts/enable-enhanced-monitoring.sh

          # Set up alerting for the specific bug metrics
          ./scripts/setup-bug-fix-alerts.sh

      - name: Notify incident response team
        run: |
          curl -X POST $SLACK_WEBHOOK_URL \\
            -H 'Content-type: application/json' \\
            --data "{
              \\"text\\": \\"🚑 Critical bug fix deployed: ${{ github.event.head_commit.message }}\\",
              \\"channel\\": \\"#incidents\\"
            }"
    `,

    canaryBugFix: `
# Canary Deployment for Complex Bug Fixes
name: Canary Bug Fix Deployment

on:
  push:
    branches: [bugfix/*]

jobs:
  canary-deployment:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Run comprehensive tests
        run: |
          npm test
          npm run test:integration
          npm run test:e2e

      - name: Deploy canary version (5% traffic)
        run: |
          helm upgrade app-canary ./helm/app \\
            --set image.tag=${{ github.sha }} \\
            --set canary.enabled=true \\
            --set canary.weight=5 \\
            --namespace production

      - name: Monitor canary for 15 minutes
        run: |
          echo "Monitoring canary deployment..."
          sleep 900 # 15 minutes

          # Check canary metrics
          ERROR_RATE=$(kubectl exec deploy/prometheus -- promtool query instant 'rate(http_requests_total{job="app-canary",status=~"5.."}[5m])')
          RESPONSE_TIME=$(kubectl exec deploy/prometheus -- promtool query instant 'histogram_quantile(0.95, rate(http_request_duration_seconds_bucket{job="app-canary"}[5m]))')

          if (( $(echo "$ERROR_RATE > 0.001" | bc -l) )); then
            echo "❌ Canary failed: High error rate ($ERROR_RATE)"
            exit 1
          fi

          if (( $(echo "$RESPONSE_TIME > 0.5" | bc -l) )); then
            echo "❌ Canary failed: High response time ($RESPONSE_TIME)"
            exit 1
          fi

          echo "✅ Canary metrics look good"

      - name: Gradually increase traffic
        run: |
          # 25% traffic
          helm upgrade app-canary ./helm/app --set canary.weight=25
          sleep 600 # 10 minutes monitoring

          # 50% traffic
          helm upgrade app-canary ./helm/app --set canary.weight=50
          sleep 600 # 10 minutes monitoring

          # 100% traffic (full deployment)
          helm upgrade app-production ./helm/app \\
            --set image.tag=${{ github.sha }} \\
            --set canary.enabled=false
    `
  },

  postDeploymentMonitoring: `
// Post-deployment monitoring for bug fixes
const bugFixMonitoring = {
  // Error rate monitoring specific to the bug
  monitorErrorRates: () => {
    const prometheus = require('prometheus-query');
    const client = new prometheus.PrometheusQuery('http://prometheus:9090');

    const monitorBugSpecificErrors = async () => {
      const query = 'rate(http_requests_total{status=~"5..", job="app"}[5m])';
      const result = await client.query(query);

      const currentErrorRate = parseFloat(result.result[0]?.value?.[1] || '0');
      const errorThreshold = 0.001; // 0.1%

      if (currentErrorRate > errorThreshold) {
        await triggerAlert({
          type: 'high-error-rate',
          value: currentErrorRate,
          threshold: errorThreshold,
          message: 'Error rate increased after bug fix deployment'
        });
      }
    };

    // Monitor every 30 seconds for first hour after deployment
    const intensiveMonitoring = setInterval(monitorBugSpecificErrors, 30000);

    setTimeout(() => {
      clearInterval(intensiveMonitoring);
      // Switch to normal monitoring interval (5 minutes)
      setInterval(monitorBugSpecificErrors, 300000);
    }, 3600000); // 1 hour
  },

  // Monitor business metrics recovery
  monitorBusinessMetrics: () => {
    const monitorRecovery = async () => {
      // Monitor conversion rates
      const conversionQuery = 'rate(successful_transactions_total[5m])';
      const conversionResult = await prometheus.query(conversionQuery);

      // Monitor user engagement
      const engagementQuery = 'rate(user_actions_total[5m])';
      const engagementResult = await prometheus.query(engagementQuery);

      // Compare against baseline metrics
      const baseline = await getBaselineMetrics();

      const recovery = {
        conversion: compareToBaseline(conversionResult, baseline.conversion),
        engagement: compareToBaseline(engagementResult, baseline.engagement)
      };

      if (recovery.conversion < 0.95 || recovery.engagement < 0.95) {
        await triggerAlert({
          type: 'business-metrics-not-recovered',
          recovery,
          message: 'Business metrics have not fully recovered after bug fix'
        });
      }
    };

    // Monitor business metrics recovery
    const businessMonitoring = setInterval(monitorRecovery, 300000); // Every 5 minutes

    // Stop monitoring after 24 hours if metrics have recovered
    setTimeout(() => {
      clearInterval(businessMonitoring);
    }, 86400000); // 24 hours
  }
};
  `
};
```

## Chatmode Transition Framework

### Bug Fix Workflow Transitions

```typescript
interface BugFixTransitionMap {
  incidentTriage: {
    chatmode: 'software-architect';
    nextChatmode: 'backend-engineer' | 'frontend-engineer' | 'security-engineer';
    transitionCriteria: ['Severity assessed', 'Root cause hypotheses formed', 'Team assigned'];
  };
  technicalInvestigation: {
    chatmode: 'backend-engineer' | 'frontend-engineer';
    nextChatmode: 'qa-engineer';
    transitionCriteria: ['Bug reproduced', 'Root cause identified', 'Fix implemented'];
  };
  testing: {
    chatmode: 'qa-engineer';
    nextChatmode: 'deployment-engineer';
    transitionCriteria: ['Fix validated', 'Regression tests passed', 'Performance impact assessed'];
  };
  deployment: {
    chatmode: 'deployment-engineer';
    nextChatmode: 'business-analyst';
    transitionCriteria: ['Fix deployed', 'Monitoring active', 'Metrics recovered'];
  };
}

class BugFixContextManager {
  generateTransitionContext(bugAnalysis: BugAnalysis, currentStage: string, nextStage: string): string {
    return `
## Bug Fix Context Handoff: ${currentStage} → ${nextStage}

### Bug Summary
- **Bug ID**: ${bugAnalysis.incidentDetails.reportId}
- **Severity**: ${bugAnalysis.severityAssessment.severity}
- **Impact**: ${bugAnalysis.severityAssessment.impact}
- **Affected Systems**: ${bugAnalysis.technicalAnalysis.affectedSystems.join(', ')}

### Investigation Findings
${this.summarizeInvestigationFindings(bugAnalysis)}

### Resolution Progress
${this.summarizeResolutionProgress(bugAnalysis)}

### Next Stage Guidance for ${nextStage}
${this.generateNextStageGuidance(nextStage, bugAnalysis)}

### Monitoring & Validation Requirements
${this.generateMonitoringRequirements(bugAnalysis)}
    `;
  }
}
```

## Quality Gates & Standards

### Bug Fix Quality Framework

```typescript
const bugFixQualityGates: QualityGate[] = [
  {
    name: 'Root Cause Validation',
    criteria: [
      { metric: 'reproduction-success-rate', threshold: 95, unit: 'percentage' },
      { metric: 'root-cause-confidence', threshold: 80, unit: 'percentage' },
      { metric: 'impact-assessment-completeness', threshold: 100, unit: 'percentage' }
    ],
    automationLevel: 'semi-automated',
    blockingLevel: 'error'
  },
  {
    name: 'Fix Validation',
    criteria: [
      { metric: 'bug-resolution-verified', threshold: 1, unit: 'boolean' },
      { metric: 'regression-tests-passed', threshold: 100, unit: 'percentage' },
      { metric: 'performance-impact-acceptable', threshold: 1, unit: 'boolean' },
      { metric: 'security-impact-assessed', threshold: 1, unit: 'boolean' }
    ],
    automationLevel: 'fully-automated',
    blockingLevel: 'critical'
  }
];
```

## Examples & Use Cases

### Example 1: Critical Production Database Connection Issue

```bash
# Bug: "Database connections timing out causing 500 errors"
# Severity: CRITICAL (Production system affected)
# Investigation: Memory leak in connection pool management
# Resolution: Implement proper connection cleanup and pool monitoring

# Workflow:
# 1. Immediate Response (software-architect)
#    - Implement temporary connection limit increase
#    - Enable enhanced monitoring and alerting
#    - Notify incident commander and stakeholders

# 2. Investigation (backend-engineer)
#    - Analyze connection pool metrics and memory usage
#    - Identify connection leak in error handling paths
#    - Develop comprehensive fix with proper cleanup

# 3. Testing (qa-engineer)
#    - Load testing with connection leak scenarios
#    - Memory usage validation under stress
#    - Regression testing of database operations

# 4. Deployment (deployment-engineer)
#    - Emergency hotfix deployment with rollback plan
#    - Enhanced monitoring for connection metrics
#    - Gradual traffic restoration with validation
```

### Example 2: React Component State Bug

```bash
# Bug: "User interface not updating after API calls"
# Severity: HIGH (Core functionality affected)
# Investigation: State update race condition in async operations
# Resolution: Implement proper async state management with cleanup

# Technology-specific investigation and resolution:
# - React DevTools component state analysis
# - Network timing analysis for race conditions
# - Implementation of proper async state patterns
# - Comprehensive component testing with async scenarios
```

### Example 3: Security Vulnerability Fix

```bash
# Bug: "SQL injection vulnerability in search endpoint"
# Severity: CRITICAL (Security vulnerability)
# Investigation: Unsanitized user input in dynamic query construction
# Resolution: Implement parameterized queries and input validation

# Security-focused workflow:
# - Immediate endpoint isolation if possible
# - Security audit of all similar code patterns
# - Penetration testing of the fix
# - Security monitoring enhancement post-deployment
```

This comprehensive bug fix coordination workflow provides systematic approach to incident response, investigation, resolution, and deployment with technology-specific guidance and enterprise-grade quality standards.