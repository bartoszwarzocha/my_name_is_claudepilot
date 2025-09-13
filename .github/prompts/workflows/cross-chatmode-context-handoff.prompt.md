---
name: cross-chatmode-context-handoff
description: Intelligent context preservation and handoff system for seamless transitions between GitHub Copilot chatmodes with comprehensive state management
tools: [github-copilot, context-management, state-preservation, workflow-coordination, intelligent-routing]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# Cross-Chatmode Context Handoff Workflow

## Context Analysis Framework

This workflow manages intelligent context preservation and seamless transitions between GitHub Copilot chatmodes:

```markdown
## Context Handoff Intelligence
1. Read `copilot.instructions.md` for chatmode ecosystem and transition patterns
2. Analyze current development context, active tasks, and conversation history
3. Extract critical information, decisions made, and work in progress
4. Map optimal next chatmode based on task complexity and requirements
5. Generate comprehensive context handoff with preserved state and guidance
```

## GitHub Integration Points

### 1. Context State Management

```typescript
// Comprehensive context state management for chatmode transitions
interface ChatmodeContext {
  currentChatmode: string;
  taskContext: TaskContext;
  technicalContext: TechnicalContext;
  businessContext: BusinessContext;
  workflowState: WorkflowState;
  conversationHistory: ConversationEntry[];
  sharedResources: SharedResource[];
  pendingDecisions: PendingDecision[];
}

interface TaskContext {
  primaryTask: Task;
  subtasks: Task[];
  completedTasks: Task[];
  blockers: Blocker[];
  dependencies: Dependency[];
  timeline: Timeline;
  priorities: Priority[];
}

interface TechnicalContext {
  codebaseState: CodebaseState;
  architectureDecisions: ArchitectureDecision[];
  technologyStack: TechnologyStack;
  developmentEnvironment: DevelopmentEnvironment;
  performanceMetrics: PerformanceMetrics;
  securityConsiderations: SecurityConsideration[];
}

class CrossChatmodeContextManager {
  async captureCurrentContext(chatmode: string): Promise<ChatmodeContext> {
    const taskContext = await this.extractTaskContext();
    const technicalContext = await this.extractTechnicalContext();
    const businessContext = await this.extractBusinessContext();
    const conversationHistory = await this.extractConversationHistory();

    return {
      currentChatmode: chatmode,
      taskContext,
      technicalContext,
      businessContext,
      workflowState: await this.captureWorkflowState(),
      conversationHistory,
      sharedResources: await this.identifySharedResources(),
      pendingDecisions: await this.extractPendingDecisions()
    };
  }

  async recommendNextChatmode(context: ChatmodeContext): Promise<ChatmodeRecommendation> {
    const taskAnalysis = this.analyzeCurrentTasks(context.taskContext);
    const complexityAssessment = this.assessComplexity(context);
    const expertiseRequirement = this.identifyRequiredExpertise(context);

    return {
      recommendedChatmode: this.selectOptimalChatmode(taskAnalysis, complexityAssessment, expertiseRequirement),
      confidence: this.calculateConfidence(taskAnalysis, expertiseRequirement),
      reasoning: this.generateRecommendationReasoning(taskAnalysis, expertiseRequirement),
      alternativeChatmodes: this.identifyAlternatives(taskAnalysis, expertiseRequirement),
      transitionStrategy: this.planTransitionStrategy(context)
    };
  }

  private selectOptimalChatmode(
    taskAnalysis: TaskAnalysis,
    complexity: ComplexityAssessment,
    expertise: ExpertiseRequirement
  ): string {
    const chatmodeScoring = {
      'business-analyst': this.scoreBusinessAnalyst(taskAnalysis, expertise),
      'software-architect': this.scoreSoftwareArchitect(taskAnalysis, complexity, expertise),
      'frontend-engineer': this.scoreFrontendEngineer(taskAnalysis, expertise),
      'backend-engineer': this.scoreBackendEngineer(taskAnalysis, expertise),
      'api-engineer': this.scoreApiEngineer(taskAnalysis, expertise),
      'data-engineer': this.scoreDataEngineer(taskAnalysis, expertise),
      'security-engineer': this.scoreSecurityEngineer(taskAnalysis, expertise),
      'qa-engineer': this.scoreQAEngineer(taskAnalysis, expertise),
      'deployment-engineer': this.scoreDeploymentEngineer(taskAnalysis, expertise),
      'ux-designer': this.scoreUXDesigner(taskAnalysis, expertise),
      'product-manager': this.scoreProductManager(taskAnalysis, expertise),
      'reviewer': this.scoreReviewer(taskAnalysis, expertise)
    };

    return Object.entries(chatmodeScoring)
      .sort(([, scoreA], [, scoreB]) => scoreB - scoreA)[0][0];
  }
}
```

### 2. Intelligent Context Handoff Generation

```typescript
// Smart context handoff generation with preserved state
interface ContextHandoff {
  handoffSummary: HandoffSummary;
  preservedState: PreservedState;
  actionableItems: ActionableItem[];
  transitionGuidance: TransitionGuidance;
  continuityInstructions: ContinuityInstruction[];
  qualityChecks: QualityCheck[];
}

class IntelligentHandoffGenerator {
  async generateContextHandoff(
    fromChatmode: string,
    toChatmode: string,
    context: ChatmodeContext
  ): Promise<ContextHandoff> {

    return {
      handoffSummary: this.generateHandoffSummary(fromChatmode, toChatmode, context),
      preservedState: this.preserveState(context),
      actionableItems: this.extractActionableItems(context, toChatmode),
      transitionGuidance: this.generateTransitionGuidance(fromChatmode, toChatmode, context),
      continuityInstructions: this.generateContinuityInstructions(context, toChatmode),
      qualityChecks: this.generateQualityChecks(context, toChatmode)
    };
  }

  private generateHandoffSummary(
    fromChatmode: string,
    toChatmode: string,
    context: ChatmodeContext
  ): HandoffSummary {
    return {
      transition: `${fromChatmode} → ${toChatmode}`,
      primaryObjective: this.extractPrimaryObjective(context),
      workCompleted: this.summarizeCompletedWork(context),
      currentStatus: this.assessCurrentStatus(context),
      nextSteps: this.identifyNextSteps(context, toChatmode),
      criticalInformation: this.extractCriticalInformation(context),
      timeContext: this.captureTimeContext(context)
    };
  }

  private preserveState(context: ChatmodeContext): PreservedState {
    return {
      // Technical state preservation
      codeChanges: this.preserveCodeChanges(context.technicalContext),
      architecturalDecisions: context.technicalContext.architectureDecisions,
      configurationChanges: this.preserveConfigurationChanges(context.technicalContext),

      // Business state preservation
      requirementDecisions: this.preserveRequirementDecisions(context.businessContext),
      stakeholderInputs: this.preserveStakeholderInputs(context.businessContext),
      businessConstraints: this.preserveBusinessConstraints(context.businessContext),

      // Workflow state preservation
      taskProgress: this.preserveTaskProgress(context.taskContext),
      dependencyMap: this.preserveDependencyMap(context.taskContext),
      riskAssessments: this.preserveRiskAssessments(context),
      qualityMetrics: this.preserveQualityMetrics(context)
    };
  }

  private extractActionableItems(
    context: ChatmodeContext,
    targetChatmode: string
  ): ActionableItem[] {
    const items: ActionableItem[] = [];

    // Extract incomplete tasks relevant to target chatmode
    const relevantTasks = context.taskContext.subtasks.filter(task =>
      this.isTaskRelevantToChatmode(task, targetChatmode)
    );

    for (const task of relevantTasks) {
      items.push({
        type: 'task-completion',
        priority: task.priority,
        description: task.description,
        context: this.generateTaskContext(task, context),
        estimatedEffort: task.estimatedEffort,
        dependencies: task.dependencies,
        successCriteria: task.successCriteria
      });
    }

    // Extract pending decisions
    for (const decision of context.pendingDecisions) {
      if (this.isDecisionRelevantToChatmode(decision, targetChatmode)) {
        items.push({
          type: 'decision-required',
          priority: decision.priority,
          description: decision.description,
          context: decision.context,
          options: decision.options,
          implications: decision.implications,
          deadline: decision.deadline
        });
      }
    }

    // Extract blockers that target chatmode can resolve
    for (const blocker of context.taskContext.blockers) {
      if (this.canChatmodeResolveBlocker(blocker, targetChatmode)) {
        items.push({
          type: 'blocker-resolution',
          priority: 'high',
          description: blocker.description,
          context: blocker.context,
          impact: blocker.impact,
          suggestedResolution: blocker.suggestedResolution
        });
      }
    }

    return items.sort((a, b) => this.priorityScore(b.priority) - this.priorityScore(a.priority));
  }
}
```

## Workflow Stages

### Stage 1: Context Capture & Analysis

```typescript
interface ContextCaptureStage {
  activities: [
    'Current chatmode state extraction',
    'Conversation history analysis',
    'Technical context preservation',
    'Business context documentation',
    'Workflow state capture',
    'Quality metrics assessment'
  ];
  outcomes: [
    'Complete context snapshot',
    'Critical information identification',
    'State preservation package',
    'Transition readiness assessment'
  ];
}

// Context capture implementation patterns
const contextCapturePatterns = {
  technicalContextCapture: `
// Technical Context Capture for Development Tasks
class TechnicalContextCapture {
  async captureCodebaseState(): Promise<CodebaseState> {
    return {
      changedFiles: await this.getChangedFiles(),
      branchState: await this.getBranchState(),
      uncommittedChanges: await this.getUncommittedChanges(),
      testResults: await this.getLatestTestResults(),
      buildStatus: await this.getBuildStatus(),
      dependencyChanges: await this.getDependencyChanges()
    };
  }

  async captureArchitecturalDecisions(): Promise<ArchitectureDecision[]> {
    return [
      {
        decision: 'Selected React over Vue for frontend framework',
        rationale: 'Team expertise and ecosystem maturity',
        implications: ['Component architecture', 'State management approach'],
        timestamp: new Date(),
        decisionMaker: 'software-architect'
      },
      {
        decision: 'Implemented microservices pattern for user management',
        rationale: 'Scalability and team autonomy requirements',
        implications: ['Service boundaries', 'Data consistency patterns'],
        timestamp: new Date(),
        decisionMaker: 'software-architect'
      }
    ];
  }

  async capturePerformanceMetrics(): Promise<PerformanceMetrics> {
    return {
      responseTime: await this.measureResponseTime(),
      throughput: await this.measureThroughput(),
      errorRate: await this.calculateErrorRate(),
      resourceUtilization: await this.getResourceUtilization(),
      userExperienceMetrics: await this.getUserExperienceMetrics()
    };
  }

  private async getChangedFiles(): Promise<FileChange[]> {
    // Git analysis for changed files
    const gitDiff = await this.executeCommand('git diff --name-status HEAD~1');

    return gitDiff.split('\\n').map(line => {
      const [status, path] = line.split('\\t');
      return {
        path,
        changeType: this.mapGitStatus(status),
        linesChanged: this.calculateLinesChanged(path)
      };
    });
  }
}
  `,

  businessContextCapture: `
// Business Context Capture for Requirements and Decisions
class BusinessContextCapture {
  async captureRequirementDecisions(): Promise<RequirementDecision[]> {
    return [
      {
        requirement: 'User authentication system',
        decision: 'Implement OAuth2 with social login options',
        stakeholder: 'Product Manager',
        businessJustification: 'Reduce user friction and improve conversion rates',
        acceptanceCriteria: [
          'Support Google and GitHub OAuth',
          'Maintain user session for 30 days',
          'Provide account linking functionality'
        ],
        impact: 'high',
        timestamp: new Date()
      }
    ];
  }

  async captureStakeholderInputs(): Promise<StakeholderInput[]> {
    return [
      {
        stakeholder: 'VP Engineering',
        input: 'Performance requirements: 99.9% uptime, <200ms response time',
        category: 'performance-requirement',
        priority: 'critical',
        timestamp: new Date()
      },
      {
        stakeholder: 'Security Team',
        input: 'Must comply with SOC2 Type II requirements',
        category: 'compliance-requirement',
        priority: 'critical',
        timestamp: new Date()
      }
    ];
  }

  async captureBusinessConstraints(): Promise<BusinessConstraint[]> {
    return [
      {
        constraint: 'Budget limitation for third-party services',
        impact: 'Technology selection limited to open-source or existing subscriptions',
        workaround: 'Prioritize self-hosted solutions where feasible',
        timeline: 'Affects Q4 roadmap planning'
      },
      {
        constraint: 'Regulatory compliance deadlines',
        impact: 'Security features must be implemented by end of quarter',
        workaround: 'Parallel development streams for compliance features',
        timeline: 'Hard deadline: December 31st'
      }
    ];
  }
}
  `,

  workflowStateCapture: `
// Workflow State Capture for Task and Process Management
class WorkflowStateCapture {
  async captureTaskProgress(): Promise<TaskProgress> {
    return {
      completedTasks: await this.getCompletedTasks(),
      inProgressTasks: await this.getInProgressTasks(),
      pendingTasks: await this.getPendingTasks(),
      blockedTasks: await this.getBlockedTasks(),
      overallProgress: this.calculateOverallProgress()
    };
  }

  async captureDependencyMap(): Promise<DependencyMap> {
    const tasks = await this.getAllTasks();
    const dependencies = new Map();

    for (const task of tasks) {
      dependencies.set(task.id, {
        dependsOn: task.dependencies,
        blockedBy: await this.findBlockingTasks(task),
        enables: await this.findEnabledTasks(task),
        criticalPath: await this.isOnCriticalPath(task)
      });
    }

    return dependencies;
  }

  async captureQualityMetrics(): Promise<QualityMetrics> {
    return {
      codeQuality: {
        testCoverage: await this.getTestCoverage(),
        codeComplexity: await this.getCodeComplexity(),
        technicalDebt: await this.getTechnicalDebtMetrics(),
        codeReviewCompletion: await this.getCodeReviewMetrics()
      },
      processQuality: {
        velocityTrend: await this.getVelocityTrend(),
        defectRate: await this.getDefectRate(),
        cycleTime: await this.getCycleTime(),
        leadTime: await this.getLeadTime()
      }
    };
  }
}
  `
};
```

### Stage 2: Chatmode Selection & Routing

```typescript
interface ChatmodeSelectionStage {
  selectionCriteria: [
    'Task complexity and domain expertise requirements',
    'Current workflow phase and next logical steps',
    'Team availability and workload distribution',
    'Business priority and timeline constraints',
    'Technical dependencies and prerequisite completion'
  ];
  routingLogic: [
    'Expertise-based routing for specialized tasks',
    'Workflow-based routing for process continuity',
    'Load-based routing for team optimization',
    'Priority-based routing for urgent tasks'
  ];
}

// Intelligent chatmode selection system
const chatmodeSelectionSystem = {
  expertiseBasedRouting: `
// Expertise-Based Chatmode Selection
class ExpertiseBasedRouter {
  selectChatmodeByExpertise(taskRequirements: TaskRequirement[]): ChatmodeSelection {
    const expertiseMap = {
      'database-design': ['data-engineer', 'backend-engineer'],
      'api-design': ['api-engineer', 'backend-engineer'],
      'ui-components': ['frontend-engineer', 'ux-designer'],
      'performance-optimization': ['qa-engineer', 'backend-engineer', 'frontend-engineer'],
      'security-audit': ['security-engineer'],
      'deployment-automation': ['deployment-engineer'],
      'business-requirements': ['business-analyst', 'product-manager'],
      'architecture-decisions': ['software-architect'],
      'code-review': ['reviewer', 'senior-engineer'],
      'user-experience': ['ux-designer', 'product-manager']
    };

    const scores = new Map<string, number>();

    for (const requirement of taskRequirements) {
      const candidateChatmodes = expertiseMap[requirement.domain] || [];

      for (const chatmode of candidateChatmodes) {
        const currentScore = scores.get(chatmode) || 0;
        scores.set(chatmode, currentScore + requirement.weight);
      }
    }

    const sortedChatmodes = Array.from(scores.entries())
      .sort(([, scoreA], [, scoreB]) => scoreB - scoreA);

    return {
      primaryChatmode: sortedChatmodes[0][0],
      confidence: this.calculateConfidence(sortedChatmodes[0][1], taskRequirements),
      alternatives: sortedChatmodes.slice(1, 3).map(([chatmode]) => chatmode),
      reasoning: this.generateExpertiseReasoning(taskRequirements, sortedChatmodes[0])
    };
  }

  private calculateConfidence(score: number, requirements: TaskRequirement[]): number {
    const maxPossibleScore = requirements.reduce((sum, req) => sum + req.weight, 0);
    return Math.min(score / maxPossibleScore, 1.0);
  }
}
  `,

  workflowBasedRouting: `
// Workflow-Based Chatmode Selection
class WorkflowBasedRouter {
  selectChatmodeByWorkflow(
    currentPhase: WorkflowPhase,
    completedTasks: Task[],
    pendingTasks: Task[]
  ): ChatmodeSelection {

    const workflowTransitions = {
      'requirements-gathering': {
        completed: ['business-analyst', 'product-manager'],
        next: this.determineRequirementsNext(completedTasks, pendingTasks)
      },
      'design-phase': {
        completed: ['software-architect', 'ux-designer'],
        next: this.determineDesignNext(completedTasks, pendingTasks)
      },
      'implementation-phase': {
        completed: ['frontend-engineer', 'backend-engineer', 'api-engineer'],
        next: this.determineImplementationNext(completedTasks, pendingTasks)
      },
      'testing-phase': {
        completed: ['qa-engineer', 'security-engineer'],
        next: this.determineTestingNext(completedTasks, pendingTasks)
      },
      'deployment-phase': {
        completed: ['deployment-engineer'],
        next: this.determineDeploymentNext(completedTasks, pendingTasks)
      }
    };

    const currentTransition = workflowTransitions[currentPhase];

    return {
      primaryChatmode: currentTransition.next.primary,
      confidence: currentTransition.next.confidence,
      alternatives: currentTransition.next.alternatives,
      reasoning: \`Workflow phase '\${currentPhase}' naturally transitions to '\${currentTransition.next.primary}'\`
    };
  }

  private determineRequirementsNext(completed: Task[], pending: Task[]): ChatmodeNext {
    const hasCompleteRequirements = completed.some(task =>
      task.type === 'requirements-documentation' && task.status === 'completed'
    );

    if (hasCompleteRequirements) {
      const hasArchitecturalTasks = pending.some(task =>
        task.domain === 'architecture' || task.domain === 'system-design'
      );

      return {
        primary: hasArchitecturalTasks ? 'software-architect' : 'frontend-engineer',
        confidence: 0.9,
        alternatives: ['ux-designer', 'backend-engineer']
      };
    }

    return {
      primary: 'business-analyst',
      confidence: 0.8,
      alternatives: ['product-manager']
    };
  }
}
  `,

  contextAwareRouting: `
// Context-Aware Chatmode Selection
class ContextAwareRouter {
  selectChatmodeByContext(
    context: ChatmodeContext,
    urgency: 'low' | 'medium' | 'high' | 'critical'
  ): ChatmodeSelection {

    // Emergency routing for critical issues
    if (urgency === 'critical') {
      return this.selectEmergencyChatmode(context);
    }

    // Multi-factor selection for normal operations
    const factors = {
      expertise: this.assessExpertiseNeeds(context),
      workflow: this.assessWorkflowPosition(context),
      availability: this.assessTeamAvailability(context),
      dependencies: this.assessDependencies(context),
      businessPriority: this.assessBusinessPriority(context)
    };

    const weightedScores = this.calculateWeightedScores(factors);

    return {
      primaryChatmode: weightedScores[0].chatmode,
      confidence: weightedScores[0].score,
      alternatives: weightedScores.slice(1, 3).map(ws => ws.chatmode),
      reasoning: this.generateContextualReasoning(factors, weightedScores[0])
    };
  }

  private selectEmergencyChatmode(context: ChatmodeContext): ChatmodeSelection {
    // Emergency chatmode selection based on incident type
    const incidentType = this.classifyIncident(context);

    const emergencyRouting = {
      'production-outage': 'deployment-engineer',
      'security-breach': 'security-engineer',
      'data-corruption': 'data-engineer',
      'performance-crisis': 'qa-engineer',
      'user-facing-bug': 'frontend-engineer',
      'api-failure': 'backend-engineer'
    };

    return {
      primaryChatmode: emergencyRouting[incidentType] || 'software-architect',
      confidence: 0.95,
      alternatives: ['software-architect', 'deployment-engineer'],
      reasoning: \`Emergency incident type '\${incidentType}' requires immediate '\${emergencyRouting[incidentType]}' expertise\`
    };
  }
}
  `
};
```

### Stage 3: Context Handoff Generation

```typescript
interface ContextHandoffStage {
  generationActivities: [
    'Critical information extraction and summarization',
    'State preservation and packaging',
    'Actionable items identification and prioritization',
    'Transition guidance and instruction creation',
    'Quality check and validation setup',
    'Continuity assurance and verification'
  ];
  handoffComponents: [
    'Executive summary of current state',
    'Preserved technical and business context',
    'Prioritized actionable items list',
    'Step-by-step transition guidance',
    'Quality gates and success criteria',
    'Fallback and escalation procedures'
  ];
}

// Context handoff generation patterns
const contextHandoffPatterns = {
  technicalHandoff: `
// Technical Context Handoff for Development Transitions
function generateTechnicalHandoff(
  fromChatmode: string,
  toChatmode: string,
  context: TechnicalContext
): TechnicalHandoff {
  return \`
## Technical Context Handoff: \${fromChatmode} → \${toChatmode}

### Current Technical State
- **Branch**: \${context.codebaseState.currentBranch}
- **Last Commit**: \${context.codebaseState.lastCommit}
- **Build Status**: \${context.codebaseState.buildStatus}
- **Test Coverage**: \${context.performanceMetrics.testCoverage}%

### Architecture Decisions Made
\${context.architectureDecisions.map(decision =>
  \`- **\${decision.decision}**: \${decision.rationale}\`
).join('\\n')}

### Code Changes in Progress
\${context.codebaseState.changedFiles.map(file =>
  \`- \${file.path} (\${file.changeType}): \${file.linesChanged} lines\`
).join('\\n')}

### Technology Stack Context
- **Frontend**: \${context.technologyStack.frontend.join(', ')}
- **Backend**: \${context.technologyStack.backend.join(', ')}
- **Database**: \${context.technologyStack.database.join(', ')}
- **Infrastructure**: \${context.technologyStack.infrastructure.join(', ')}

### Performance Baseline
- **Response Time**: \${context.performanceMetrics.responseTime}ms
- **Throughput**: \${context.performanceMetrics.throughput} req/sec
- **Error Rate**: \${context.performanceMetrics.errorRate}%

### Security Considerations
\${context.securityConsiderations.map(consideration =>
  \`- **\${consideration.category}**: \${consideration.description}\`
).join('\\n')}

### Next Steps for \${toChatmode}
\${generateTechnicalNextSteps(toChatmode, context)}

### Quality Gates
\${generateTechnicalQualityGates(toChatmode, context)}
  \`;
}
  `,

  businessHandoff: `
// Business Context Handoff for Requirements and Strategy Transitions
function generateBusinessHandoff(
  fromChatmode: string,
  toChatmode: string,
  context: BusinessContext
): BusinessHandoff {
  return \`
## Business Context Handoff: \${fromChatmode} → \${toChatmode}

### Business Objectives
- **Primary Goal**: \${context.primaryObjective}
- **Success Metrics**: \${context.successMetrics.join(', ')}
- **Timeline**: \${context.timeline.deadline}
- **Budget**: \${context.budgetConstraints}

### Stakeholder Decisions
\${context.requirementDecisions.map(decision =>
  \`- **\${decision.requirement}**: \${decision.decision} (by \${decision.stakeholder})\`
).join('\\n')}

### Requirements Status
\${context.requirements.map(req =>
  \`- \${req.description}: \${req.status} (Priority: \${req.priority})\`
).join('\\n')}

### Business Constraints
\${context.businessConstraints.map(constraint =>
  \`- **\${constraint.constraint}**: \${constraint.impact}\`
).join('\\n')}

### Stakeholder Inputs
\${context.stakeholderInputs.map(input =>
  \`- **\${input.stakeholder}**: \${input.input} (Priority: \${input.priority})\`
).join('\\n')}

### User Impact Considerations
\${generateUserImpactGuidance(context)}

### Business Value Validation
\${generateBusinessValueCriteria(context)}

### Next Steps for \${toChatmode}
\${generateBusinessNextSteps(toChatmode, context)}
  \`;
}
  `,

  workflowHandoff: `
// Workflow Context Handoff for Process Continuity
function generateWorkflowHandoff(
  fromChatmode: string,
  toChatmode: string,
  context: WorkflowContext
): WorkflowHandoff {
  return \`
## Workflow Context Handoff: \${fromChatmode} → \${toChatmode}

### Current Workflow State
- **Phase**: \${context.currentPhase}
- **Overall Progress**: \${context.overallProgress}%
- **Active Tasks**: \${context.activeTasks.length}
- **Blocked Tasks**: \${context.blockedTasks.length}

### Completed Tasks
\${context.completedTasks.map(task =>
  \`- ✅ \${task.description} (Completed: \${task.completedDate})\`
).join('\\n')}

### Pending Tasks for \${toChatmode}
\${context.pendingTasks
  .filter(task => isTaskRelevantToChatmode(task, toChatmode))
  .map(task => \`- ⏳ \${task.description} (Priority: \${task.priority})\`)
  .join('\\n')}

### Active Blockers
\${context.blockers.map(blocker =>
  \`- 🚫 \${blocker.description}: \${blocker.resolution || 'Resolution needed'}\`
).join('\\n')}

### Dependency Map
\${generateDependencyVisualization(context.dependencies)}

### Quality Metrics
- **Velocity**: \${context.qualityMetrics.velocity} tasks/week
- **Cycle Time**: \${context.qualityMetrics.cycleTime} days
- **Defect Rate**: \${context.qualityMetrics.defectRate}%

### Risk Assessment
\${context.risks.map(risk =>
  \`- **\${risk.category}**: \${risk.description} (Impact: \${risk.impact}, Probability: \${risk.probability})\`
).join('\\n')}

### Handoff Instructions for \${toChatmode}
\${generateWorkflowInstructions(toChatmode, context)}
  \`;
}
  `
};
```

## Chatmode Transition Framework

### Intelligent Transition Orchestration

```typescript
interface TransitionOrchestration {
  transitionTypes: {
    sequential: 'Natural workflow progression between phases';
    parallel: 'Simultaneous work by multiple chatmodes';
    escalation: 'Escalation to higher expertise level';
    collaboration: 'Joint work requiring multiple perspectives';
    emergency: 'Urgent issue requiring immediate expertise switch';
  };
  transitionStrategies: {
    contextPreservation: 'Maintain full context across transitions';
    stateManagement: 'Preserve work state and progress';
    qualityContinuity: 'Ensure quality standards across handoffs';
    knowledgeTransfer: 'Transfer domain knowledge and decisions';
  };
}

class TransitionOrchestrator {
  async orchestrateTransition(
    transitionRequest: TransitionRequest
  ): Promise<TransitionResult> {

    // Capture current context
    const currentContext = await this.contextManager.captureCurrentContext(
      transitionRequest.fromChatmode
    );

    // Determine optimal target chatmode
    const recommendation = await this.contextManager.recommendNextChatmode(
      currentContext
    );

    // Generate context handoff
    const handoff = await this.handoffGenerator.generateContextHandoff(
      transitionRequest.fromChatmode,
      recommendation.recommendedChatmode,
      currentContext
    );

    // Validate transition readiness
    const validation = await this.validateTransitionReadiness(
      transitionRequest,
      currentContext,
      handoff
    );

    if (!validation.isReady) {
      return {
        success: false,
        error: validation.blockers,
        recommendations: validation.recommendations
      };
    }

    // Execute transition
    const transitionResult = await this.executeTransition(
      transitionRequest,
      handoff,
      recommendation
    );

    return transitionResult;
  }

  private async validateTransitionReadiness(
    request: TransitionRequest,
    context: ChatmodeContext,
    handoff: ContextHandoff
  ): Promise<TransitionValidation> {

    const validations = await Promise.all([
      this.validateTaskCompleteness(context),
      this.validateInformationCompleteness(handoff),
      this.validateQualityGates(context),
      this.validateDependencyResolution(context),
      this.validateResourceAvailability(request.toChatmode)
    ]);

    const blockers = validations
      .filter(v => !v.passed)
      .map(v => v.issue);

    return {
      isReady: blockers.length === 0,
      blockers,
      recommendations: this.generateTransitionRecommendations(validations)
    };
  }
}
```

## Quality Gates & Standards

### Context Handoff Quality Framework

```typescript
const contextHandoffQualityGates: QualityGate[] = [
  {
    name: 'Context Completeness Validation',
    criteria: [
      { metric: 'context-information-completeness', threshold: 95, unit: 'percentage' },
      { metric: 'critical-decisions-documented', threshold: 100, unit: 'percentage' },
      { metric: 'state-preservation-integrity', threshold: 100, unit: 'percentage' },
      { metric: 'actionable-items-clarity', threshold: 90, unit: 'percentage' }
    ],
    automationLevel: 'semi-automated',
    blockingLevel: 'error'
  },
  {
    name: 'Transition Readiness Validation',
    criteria: [
      { metric: 'prerequisite-tasks-completed', threshold: 100, unit: 'percentage' },
      { metric: 'blocker-resolution-status', threshold: 100, unit: 'percentage' },
      { metric: 'dependency-satisfaction', threshold: 100, unit: 'percentage' },
      { metric: 'target-chatmode-availability', threshold: 1, unit: 'boolean' }
    ],
    automationLevel: 'fully-automated',
    blockingLevel: 'critical'
  },
  {
    name: 'Handoff Quality Validation',
    criteria: [
      { metric: 'transition-guidance-clarity', threshold: 85, unit: 'percentage' },
      { metric: 'continuity-instruction-completeness', threshold: 90, unit: 'percentage' },
      { metric: 'quality-check-coverage', threshold: 100, unit: 'percentage' },
      { metric: 'fallback-procedure-definition', threshold: 1, unit: 'boolean' }
    ],
    automationLevel: 'manual',
    blockingLevel: 'warning'
  }
];
```

## Examples & Use Cases

### Example 1: Frontend to Backend Transition

```bash
# Scenario: React component completed, need API implementation
# Transition: frontend-engineer → backend-engineer

# Context Captured:
# - Component specifications and interface requirements
# - API contract definitions and data models
# - Authentication and authorization requirements
# - Performance and caching considerations

# Handoff Generated:
# - Frontend component ready for integration
# - API endpoints needed: GET /users, POST /users, PUT /users/:id
# - Data validation rules and business logic requirements
# - Integration testing scenarios and acceptance criteria

# Next Steps for backend-engineer:
# 1. Implement user management API endpoints
# 2. Add request validation and error handling
# 3. Integrate with database and caching layer
# 4. Create integration tests with frontend component
```

### Example 2: Development to Deployment Transition

```bash
# Scenario: Feature implementation complete, ready for deployment
# Transition: backend-engineer → deployment-engineer

# Context Captured:
# - Feature implementation details and dependencies
# - Database migrations and configuration changes
# - Environment variables and secrets needed
# - Performance impact and monitoring requirements

# Handoff Generated:
# - Code changes ready for deployment
# - Infrastructure requirements and scaling considerations
# - Deployment strategy and rollback procedures
# - Monitoring and alerting configuration needs

# Next Steps for deployment-engineer:
# 1. Review deployment strategy and risk assessment
# 2. Prepare infrastructure and environment configuration
# 3. Execute deployment with monitoring and validation
# 4. Configure post-deployment monitoring and alerting
```

### Example 3: Emergency Security Issue Escalation

```bash
# Scenario: Security vulnerability discovered during code review
# Transition: reviewer → security-engineer (Emergency)

# Context Captured:
# - Vulnerability details and potential impact
# - Affected code components and data flows
# - Current security measures and gaps
# - Business impact and urgency assessment

# Handoff Generated:
# - Critical security vulnerability requiring immediate attention
# - Affected systems and potential attack vectors
# - Immediate mitigation steps and long-term fix requirements
# - Compliance and disclosure considerations

# Next Steps for security-engineer:
# 1. Assess vulnerability severity and exploit potential
# 2. Implement immediate security patches and mitigations
# 3. Conduct security audit of related components
# 4. Develop comprehensive security improvement plan
```

This comprehensive cross-chatmode context handoff workflow ensures seamless transitions between GitHub Copilot chatmodes with complete context preservation, intelligent routing, and enterprise-grade quality assurance.