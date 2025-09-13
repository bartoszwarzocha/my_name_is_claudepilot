---
name: feature-development-lifecycle
description: Complete end-to-end feature development lifecycle from concept to production with intelligent planning, implementation coordination, and quality assurance
tools: [github-copilot, github-integration, project-management, feature-planning, lifecycle-coordination]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# Feature Development Lifecycle Workflow

## Context Analysis Framework

This workflow orchestrates the complete feature development lifecycle with intelligent coordination across all development phases:

```markdown
## Comprehensive Lifecycle Context Detection
1. Read `copilot.instructions.md` for project standards and development processes
2. Analyze feature requirements (epics, user stories, acceptance criteria)
3. Detect current project architecture and technology constraints
4. Understand team capacity, timeline constraints, and business priorities
5. Map feature complexity to optimal development approach and resource allocation
```

## GitHub Integration Points

### 1. Feature Planning & Epic Management

```typescript
// Comprehensive feature analysis and planning
interface FeatureLifecycleAnalysis {
  featureDetails: {
    epic: string;
    userStories: UserStory[];
    acceptanceCriteria: AcceptanceCriteria[];
    businessValue: BusinessValue;
    technicalComplexity: TechnicalComplexity;
  };
  developmentPlan: {
    phases: DevelopmentPhase[];
    timeline: Timeline;
    resourceAllocation: ResourceAllocation;
    riskAssessment: RiskAssessment;
  };
  qualityStrategy: {
    testingApproach: TestingStrategy;
    performanceTargets: PerformanceTargets;
    securityRequirements: SecurityRequirements;
    complianceNeeds: ComplianceRequirements;
  };
}

class FeatureLifecycleManager {
  async planFeatureDevelopment(epic: Epic): Promise<FeatureLifecycleAnalysis> {
    const featureAnalysis = await this.analyzeFeatureRequirements(epic);
    const technicalAssessment = await this.assessTechnicalComplexity(epic);
    const resourcePlanning = await this.planResourceAllocation(epic, technicalAssessment);

    return {
      featureDetails: this.extractFeatureDetails(epic, featureAnalysis),
      developmentPlan: await this.createDevelopmentPlan(epic, technicalAssessment, resourcePlanning),
      qualityStrategy: await this.defineQualityStrategy(epic, technicalAssessment)
    };
  }

  private async assessTechnicalComplexity(epic: Epic): Promise<TechnicalComplexity> {
    return {
      architecturalImpact: this.assessArchitecturalChanges(epic),
      databaseChanges: this.analyzeDatabaseRequirements(epic),
      integrationComplexity: this.assessIntegrationNeeds(epic),
      performanceImpact: this.analyzePerformanceRequirements(epic),
      securityImplications: this.assessSecurityRequirements(epic),
      scalabilityConsiderations: this.analyzeScalabilityNeeds(epic)
    };
  }

  private async createDevelopmentPlan(
    epic: Epic,
    complexity: TechnicalComplexity,
    resources: ResourceAllocation
  ): Promise<DevelopmentPlan> {
    const phases = this.planDevelopmentPhases(epic, complexity);
    const timeline = this.estimateTimeline(phases, resources);
    const risks = this.assessProjectRisks(epic, complexity, timeline);

    return {
      phases,
      timeline,
      resourceAllocation: resources,
      riskAssessment: risks,
      milestones: this.defineMilestones(phases, timeline),
      dependencies: this.mapDependencies(epic, phases)
    };
  }
}
```

### 2. GitHub Issues & Project Automation

```typescript
// GitHub Issues and Projects integration for feature tracking
interface GitHubFeatureTracking {
  epicIssue: {
    title: string;
    description: string;
    labels: string[];
    milestone: string;
    assignees: string[];
    linkedIssues: number[];
  };
  userStoryIssues: UserStoryIssue[];
  taskBreakdown: TaskIssue[];
  projectBoard: {
    columns: ProjectColumn[];
    automation: ProjectAutomation;
    burndownTracking: BurndownConfiguration;
  };
}

class GitHubFeatureCoordinator {
  async setupFeatureTracking(feature: FeatureLifecycleAnalysis): Promise<GitHubFeatureTracking> {
    // Create epic issue
    const epicIssue = await this.createEpicIssue(feature);

    // Break down into user stories
    const userStoryIssues = await this.createUserStoryIssues(feature, epicIssue);

    // Create technical tasks
    const taskIssues = await this.createTaskIssues(feature, userStoryIssues);

    // Setup project board
    const projectBoard = await this.setupProjectBoard(feature, epicIssue);

    return {
      epicIssue,
      userStoryIssues,
      taskBreakdown: taskIssues,
      projectBoard
    };
  }

  private async createEpicIssue(feature: FeatureLifecycleAnalysis): Promise<EpicIssue> {
    const issueBody = `
## Epic Overview
${feature.featureDetails.epic}

## Business Value
- **Priority**: ${feature.featureDetails.businessValue.priority}
- **Impact**: ${feature.featureDetails.businessValue.impact}
- **Success Metrics**: ${feature.featureDetails.businessValue.successMetrics.join(', ')}

## User Stories
${feature.featureDetails.userStories.map(story => `- [ ] ${story.title}`).join('\n')}

## Technical Complexity
- **Architecture Impact**: ${feature.developmentPlan.riskAssessment.architecturalRisk}
- **Estimated Timeline**: ${feature.developmentPlan.timeline.totalDuration}
- **Team Size**: ${feature.developmentPlan.resourceAllocation.teamSize}

## Acceptance Criteria
${feature.featureDetails.acceptanceCriteria.map(criteria => `- [ ] ${criteria.description}`).join('\n')}

## Definition of Done
- [ ] All user stories completed and tested
- [ ] Code review passed
- [ ] Security review completed
- [ ] Performance targets met
- [ ] Documentation updated
- [ ] Deployed to production
    `;

    return await this.githubClient.issues.create({
      title: `Epic: ${feature.featureDetails.epic}`,
      body: issueBody,
      labels: ['epic', 'feature', feature.featureDetails.businessValue.priority],
      milestone: feature.developmentPlan.timeline.milestone
    });
  }
}
```

## Workflow Stages

### Stage 1: Feature Discovery & Planning

```typescript
interface FeatureDiscoveryStage {
  activities: [
    'Business requirements analysis',
    'User research and validation',
    'Technical feasibility assessment',
    'Architecture planning',
    'Resource estimation',
    'Risk analysis and mitigation planning'
  ];
  chatmodes: ['business-analyst', 'product-manager', 'software-architect'];
  deliverables: [
    'Feature specification document',
    'User story mapping',
    'Technical architecture plan',
    'Development timeline',
    'Risk mitigation plan'
  ];
}

// Feature Discovery Implementation
class FeatureDiscoveryEngine {
  async executeDiscoveryPhase(featureRequest: FeatureRequest): Promise<FeatureDiscoveryResult> {
    // Business Analysis Phase
    const businessAnalysis = await this.conductBusinessAnalysis(featureRequest);

    // User Research Phase
    const userResearch = await this.conductUserResearch(featureRequest);

    // Technical Assessment Phase
    const technicalAssessment = await this.conductTechnicalAssessment(featureRequest);

    // Architecture Planning Phase
    const architecturePlan = await this.planArchitecture(featureRequest, technicalAssessment);

    return {
      businessRequirements: businessAnalysis,
      userInsights: userResearch,
      technicalFeasibility: technicalAssessment,
      architectureDesign: architecturePlan,
      implementationPlan: await this.createImplementationPlan(businessAnalysis, technicalAssessment, architecturePlan)
    };
  }

  private async conductBusinessAnalysis(request: FeatureRequest): Promise<BusinessAnalysis> {
    return {
      stakeholderRequirements: await this.gatherStakeholderInput(request),
      competitiveAnalysis: await this.analyzeCompetitiveFeatures(request),
      businessImpactAssessment: await this.assessBusinessImpact(request),
      successMetrics: await this.defineSuccessMetrics(request),
      priorityScoring: await this.calculatePriorityScore(request)
    };
  }

  private async conductUserResearch(request: FeatureRequest): Promise<UserResearch> {
    return {
      userPersonas: await this.identifyTargetPersonas(request),
      userJourneyMapping: await this.mapUserJourneys(request),
      usabilityRequirements: await this.defineUsabilityRequirements(request),
      accessibilityRequirements: await this.defineAccessibilityRequirements(request),
      userAcceptanceTestCriteria: await this.defineUATCriteria(request)
    };
  }

  private async conductTechnicalAssessment(request: FeatureRequest): Promise<TechnicalAssessment> {
    return {
      architecturalImpact: await this.assessArchitecturalImpact(request),
      performanceRequirements: await this.definePerformanceRequirements(request),
      scalabilityConsiderations: await this.assessScalabilityNeeds(request),
      securityRequirements: await this.defineSecurityRequirements(request),
      integrationRequirements: await this.assessIntegrationNeeds(request),
      technologyStackEvaluation: await this.evaluateTechnologyChoices(request)
    };
  }
}
```

### Stage 2: Implementation Coordination

```typescript
// Multi-chatmode implementation coordination
interface ImplementationCoordination {
  frontendDevelopment: {
    chatmode: 'frontend-engineer';
    activities: FrontendActivity[];
    deliverables: FrontendDeliverable[];
  };
  backendDevelopment: {
    chatmode: 'backend-engineer' | 'api-engineer';
    activities: BackendActivity[];
    deliverables: BackendDeliverable[];
  };
  databaseDevelopment: {
    chatmode: 'data-engineer';
    activities: DatabaseActivity[];
    deliverables: DatabaseDeliverable[];
  };
  integrationCoordination: {
    chatmode: 'software-architect';
    activities: IntegrationActivity[];
    deliverables: IntegrationDeliverable[];
  };
}

// React/TypeScript Frontend Implementation Coordination
const reactFeatureImplementation = {
  chatmode: 'frontend-engineer',
  phases: [
    {
      name: 'Component Architecture',
      activities: [
        'Design component hierarchy',
        'Define component interfaces',
        'Create reusable component library',
        'Implement state management strategy'
      ],
      implementation: `
// Feature Component Architecture
interface FeatureComponentProps {
  featureId: string;
  configuration: FeatureConfiguration;
  onFeatureUpdate: (update: FeatureUpdate) => void;
}

// Main feature container component
const FeatureContainer: React.FC<FeatureComponentProps> = ({
  featureId,
  configuration,
  onFeatureUpdate
}) => {
  const [featureState, setFeatureState] = useState<FeatureState>({
    loading: true,
    data: null,
    error: null
  });

  const { data, error, isLoading, refetch } = useFeatureData(featureId);
  const { mutate: updateFeature } = useFeatureUpdate();

  const handleFeatureChange = useCallback((changes: FeatureChanges) => {
    updateFeature(
      { featureId, changes },
      {
        onSuccess: (updatedFeature) => {
          onFeatureUpdate(updatedFeature);
          setFeatureState(prev => ({ ...prev, data: updatedFeature }));
        },
        onError: (error) => {
          setFeatureState(prev => ({ ...prev, error: error.message }));
        }
      }
    );
  }, [featureId, updateFeature, onFeatureUpdate]);

  if (isLoading) {
    return <FeatureLoadingSkeleton />;
  }

  if (error) {
    return (
      <FeatureErrorBoundary
        error={error}
        onRetry={() => refetch()}
        onReport={(errorReport) => reportError(errorReport)}
      />
    );
  }

  return (
    <div className="feature-container" data-testid="feature-container">
      <FeatureHeader
        title={data.title}
        configuration={configuration}
        onConfigurationChange={handleFeatureChange}
      />

      <FeatureContent
        data={data}
        isEditable={configuration.editable}
        onContentChange={handleFeatureChange}
      />

      <FeatureActions
        featureId={featureId}
        availableActions={data.availableActions}
        onActionExecute={handleFeatureChange}
      />
    </div>
  );
};

// Custom hooks for feature management
const useFeatureData = (featureId: string) => {
  return useQuery({
    queryKey: ['feature', featureId],
    queryFn: () => featureService.getFeature(featureId),
    staleTime: 5 * 60 * 1000,
    cacheTime: 10 * 60 * 1000,
    refetchOnWindowFocus: false
  });
};

const useFeatureUpdate = () => {
  const queryClient = useQueryClient();

  return useMutation({
    mutationFn: ({ featureId, changes }: { featureId: string; changes: FeatureChanges }) =>
      featureService.updateFeature(featureId, changes),
    onSuccess: (updatedFeature) => {
      queryClient.setQueryData(['feature', updatedFeature.id], updatedFeature);
      queryClient.invalidateQueries(['features']);
    }
  });
};

// Feature service for API communication
export const featureService = {
  async getFeature(featureId: string): Promise<Feature> {
    const response = await apiClient.get(\`/api/features/\${featureId}\`);
    return response.data;
  },

  async updateFeature(featureId: string, changes: FeatureChanges): Promise<Feature> {
    const response = await apiClient.put(\`/api/features/\${featureId}\`, changes);
    return response.data;
  },

  async createFeature(featureData: CreateFeatureRequest): Promise<Feature> {
    const response = await apiClient.post('/api/features', featureData);
    return response.data;
  }
};
      `
    }
  ],
  transition: 'Switch to `backend-engineer` chatmode for API implementation'
};

// Node.js/Express Backend Implementation Coordination
const nodeBackendFeatureImplementation = {
  chatmode: 'backend-engineer',
  phases: [
    {
      name: 'API Design & Implementation',
      activities: [
        'Design RESTful API endpoints',
        'Implement business logic services',
        'Add input validation and sanitization',
        'Implement error handling and logging'
      ],
      implementation: `
// Feature API Controller
import { Request, Response, NextFunction } from 'express';
import { FeatureService } from '../services/FeatureService';
import { validateFeatureRequest } from '../validators/featureValidator';
import { logger } from '../utils/logger';
import { ApiError } from '../utils/ApiError';

export class FeatureController {
  constructor(private featureService: FeatureService) {}

  async createFeature(req: Request, res: Response, next: NextFunction): Promise<void> {
    try {
      logger.info('Creating new feature', { requestId: req.id, body: req.body });

      const validatedData = validateFeatureRequest(req.body);
      const userId = req.user?.id;

      if (!userId) {
        throw new ApiError('Authentication required', 401);
      }

      const feature = await this.featureService.createFeature({
        ...validatedData,
        createdBy: userId
      });

      logger.info('Feature created successfully', {
        requestId: req.id,
        featureId: feature.id,
        userId
      });

      res.status(201).json({
        success: true,
        data: feature,
        message: 'Feature created successfully'
      });
    } catch (error) {
      logger.error('Error creating feature', {
        requestId: req.id,
        error: error.message,
        stack: error.stack
      });
      next(error);
    }
  }

  async getFeature(req: Request, res: Response, next: NextFunction): Promise<void> {
    try {
      const { id } = req.params;
      const userId = req.user?.id;

      logger.info('Fetching feature', { requestId: req.id, featureId: id, userId });

      const feature = await this.featureService.getFeature(id, userId);

      if (!feature) {
        throw new ApiError('Feature not found', 404);
      }

      res.json({
        success: true,
        data: feature
      });
    } catch (error) {
      logger.error('Error fetching feature', {
        requestId: req.id,
        featureId: req.params.id,
        error: error.message
      });
      next(error);
    }
  }

  async updateFeature(req: Request, res: Response, next: NextFunction): Promise<void> {
    try {
      const { id } = req.params;
      const userId = req.user?.id;
      const updates = validateFeatureUpdateRequest(req.body);

      logger.info('Updating feature', { requestId: req.id, featureId: id, updates, userId });

      const updatedFeature = await this.featureService.updateFeature(id, updates, userId);

      logger.info('Feature updated successfully', {
        requestId: req.id,
        featureId: id,
        userId
      });

      res.json({
        success: true,
        data: updatedFeature,
        message: 'Feature updated successfully'
      });
    } catch (error) {
      logger.error('Error updating feature', {
        requestId: req.id,
        featureId: req.params.id,
        error: error.message
      });
      next(error);
    }
  }
}

// Feature Service Implementation
export class FeatureService {
  constructor(
    private featureRepository: FeatureRepository,
    private permissionService: PermissionService,
    private notificationService: NotificationService,
    private cacheService: CacheService
  ) {}

  async createFeature(data: CreateFeatureRequest): Promise<Feature> {
    // Validate business rules
    await this.validateBusinessRules(data);

    // Create feature with transaction
    const feature = await this.featureRepository.transaction(async (trx) => {
      const newFeature = await this.featureRepository.create({
        ...data,
        status: FeatureStatus.DRAFT,
        createdAt: new Date(),
        updatedAt: new Date()
      }, trx);

      // Create associated metadata
      await this.createFeatureMetadata(newFeature.id, data.metadata, trx);

      // Set up permissions
      await this.permissionService.setupFeaturePermissions(newFeature.id, data.createdBy, trx);

      return newFeature;
    });

    // Send notifications
    await this.notificationService.notifyFeatureCreated(feature);

    // Clear related caches
    await this.cacheService.clearPattern(\`features:user:\${data.createdBy}:*\`);

    return feature;
  }

  async getFeature(featureId: string, userId: string): Promise<Feature | null> {
    // Check cache first
    const cacheKey = \`feature:\${featureId}:user:\${userId}\`;
    const cachedFeature = await this.cacheService.get(cacheKey);

    if (cachedFeature) {
      return JSON.parse(cachedFeature);
    }

    // Check permissions
    const hasPermission = await this.permissionService.canAccessFeature(featureId, userId);
    if (!hasPermission) {
      throw new ApiError('Access denied', 403);
    }

    // Fetch from database
    const feature = await this.featureRepository.findById(featureId);

    if (feature) {
      // Cache the result
      await this.cacheService.set(cacheKey, JSON.stringify(feature), 300); // 5 minutes
    }

    return feature;
  }

  private async validateBusinessRules(data: CreateFeatureRequest): Promise<void> {
    // Check feature name uniqueness
    const existingFeature = await this.featureRepository.findByName(data.name);
    if (existingFeature) {
      throw new ApiError('Feature with this name already exists', 400);
    }

    // Check user quota
    const userFeatureCount = await this.featureRepository.countByUser(data.createdBy);
    const userQuota = await this.getUserQuota(data.createdBy);

    if (userFeatureCount >= userQuota) {
      throw new ApiError('Feature quota exceeded', 400);
    }
  }
}
      `
    }
  ],
  transition: 'Switch to `data-engineer` chatmode for database implementation'
};

// Python/FastAPI Implementation Coordination
const pythonFastApiFeatureImplementation = {
  chatmode: 'backend-engineer',
  phases: [
    {
      name: 'FastAPI Feature Implementation',
      activities: [
        'Design Pydantic models and schemas',
        'Implement async API endpoints',
        'Add comprehensive validation',
        'Implement business logic services'
      ],
      implementation: `
# Feature API Implementation with FastAPI
from fastapi import APIRouter, Depends, HTTPException, BackgroundTasks
from sqlalchemy.ext.asyncio import AsyncSession
from typing import List, Optional
import logging
from datetime import datetime

from app.services.feature_service import FeatureService
from app.schemas.feature import FeatureCreate, FeatureUpdate, FeatureResponse
from app.core.dependencies import get_feature_service, get_current_user
from app.core.database import get_db_session
from app.models.user import User
from app.utils.logging import get_logger

logger = get_logger(__name__)
router = APIRouter(prefix="/api/features", tags=["features"])

@router.post("/", response_model=FeatureResponse)
async def create_feature(
    feature_data: FeatureCreate,
    background_tasks: BackgroundTasks,
    current_user: User = Depends(get_current_user),
    service: FeatureService = Depends(get_feature_service)
) -> FeatureResponse:
    """Create a new feature with comprehensive validation and business logic."""
    try:
        logger.info(
            "Creating new feature",
            extra={
                "user_id": current_user.id,
                "feature_name": feature_data.name,
                "feature_type": feature_data.feature_type
            }
        )

        # Create feature with user context
        feature = await service.create_feature(
            feature_data=feature_data,
            created_by=current_user.id
        )

        # Add background tasks
        background_tasks.add_task(
            service.send_feature_notifications,
            feature.id,
            current_user.id
        )

        background_tasks.add_task(
            service.update_analytics,
            "feature_created",
            {"feature_id": feature.id, "user_id": current_user.id}
        )

        logger.info(
            "Feature created successfully",
            extra={
                "feature_id": feature.id,
                "user_id": current_user.id
            }
        )

        return FeatureResponse(
            success=True,
            data=feature,
            message="Feature created successfully"
        )

    except ValueError as e:
        logger.warning(
            "Feature creation validation error",
            extra={"user_id": current_user.id, "error": str(e)}
        )
        raise HTTPException(status_code=400, detail=str(e))

    except Exception as e:
        logger.error(
            "Unexpected error creating feature",
            extra={
                "user_id": current_user.id,
                "error": str(e),
                "feature_data": feature_data.dict()
            },
            exc_info=True
        )
        raise HTTPException(status_code=500, detail="Internal server error")

@router.get("/{feature_id}", response_model=FeatureResponse)
async def get_feature(
    feature_id: str,
    current_user: User = Depends(get_current_user),
    service: FeatureService = Depends(get_feature_service)
) -> FeatureResponse:
    """Get feature by ID with permission checking."""
    try:
        feature = await service.get_feature(
            feature_id=feature_id,
            user_id=current_user.id
        )

        if not feature:
            raise HTTPException(status_code=404, detail="Feature not found")

        return FeatureResponse(success=True, data=feature)

    except HTTPException:
        raise
    except Exception as e:
        logger.error(
            "Error fetching feature",
            extra={
                "feature_id": feature_id,
                "user_id": current_user.id,
                "error": str(e)
            },
            exc_info=True
        )
        raise HTTPException(status_code=500, detail="Internal server error")

# Feature Service Implementation
from sqlalchemy import select, and_
from sqlalchemy.ext.asyncio import AsyncSession
from redis.asyncio import Redis
import json
from typing import Optional, List

class FeatureService:
    def __init__(
        self,
        db_session: AsyncSession,
        redis_client: Redis,
        permission_service: PermissionService,
        notification_service: NotificationService
    ):
        self.db = db_session
        self.redis = redis_client
        self.permission_service = permission_service
        self.notification_service = notification_service

    async def create_feature(
        self,
        feature_data: FeatureCreate,
        created_by: str
    ) -> Feature:
        """Create new feature with comprehensive business logic."""

        # Validate business rules
        await self._validate_business_rules(feature_data, created_by)

        try:
            # Begin database transaction
            async with self.db.begin():
                # Create feature entity
                feature = Feature(
                    name=feature_data.name,
                    description=feature_data.description,
                    feature_type=feature_data.feature_type,
                    configuration=feature_data.configuration,
                    status=FeatureStatus.DRAFT,
                    created_by=created_by,
                    created_at=datetime.utcnow(),
                    updated_at=datetime.utcnow()
                )

                self.db.add(feature)
                await self.db.flush()  # Get the feature.id

                # Create feature metadata
                await self._create_feature_metadata(
                    feature.id,
                    feature_data.metadata,
                    created_by
                )

                # Set up permissions
                await self.permission_service.setup_feature_permissions(
                    feature.id,
                    created_by,
                    feature_data.permissions or {}
                )

                # Commit transaction
                await self.db.commit()

            # Clear related caches
            await self._clear_user_feature_cache(created_by)

            return feature

        except Exception as e:
            await self.db.rollback()
            logger.error(f"Error creating feature: {e}", exc_info=True)
            raise

    async def get_feature(
        self,
        feature_id: str,
        user_id: str
    ) -> Optional[Feature]:
        """Get feature with caching and permission checking."""

        # Check cache first
        cache_key = f"feature:{feature_id}:user:{user_id}"
        cached_feature = await self.redis.get(cache_key)

        if cached_feature:
            return Feature.parse_raw(cached_feature)

        # Check permissions
        has_permission = await self.permission_service.can_access_feature(
            feature_id, user_id
        )
        if not has_permission:
            raise ValueError("Access denied")

        # Query database
        stmt = select(Feature).where(Feature.id == feature_id)
        result = await self.db.execute(stmt)
        feature = result.scalar_one_or_none()

        if feature:
            # Cache the result (5 minutes TTL)
            await self.redis.setex(
                cache_key,
                300,
                feature.json()
            )

        return feature

    async def _validate_business_rules(
        self,
        feature_data: FeatureCreate,
        created_by: str
    ) -> None:
        """Validate business rules before creating feature."""

        # Check name uniqueness
        stmt = select(Feature).where(Feature.name == feature_data.name)
        existing_feature = await self.db.execute(stmt)

        if existing_feature.scalar_one_or_none():
            raise ValueError("Feature with this name already exists")

        # Check user quota
        user_feature_count = await self._count_user_features(created_by)
        user_quota = await self._get_user_quota(created_by)

        if user_feature_count >= user_quota:
            raise ValueError("Feature quota exceeded")

        # Validate feature type constraints
        if not await self._validate_feature_type_constraints(feature_data):
            raise ValueError("Feature type constraints validation failed")

    async def send_feature_notifications(
        self,
        feature_id: str,
        user_id: str
    ) -> None:
        """Send notifications for feature creation (background task)."""
        try:
            await self.notification_service.notify_feature_created(
                feature_id, user_id
            )
        except Exception as e:
            logger.error(f"Error sending feature notifications: {e}")
      `
    }
  ],
  transition: 'Switch to `qa-engineer` chatmode for testing implementation'
};
```

### Stage 3: Quality Assurance & Testing Coordination

```typescript
interface QualityAssuranceCoordination {
  testingStrategy: {
    unitTesting: UnitTestingStrategy;
    integrationTesting: IntegrationTestingStrategy;
    e2eTesting: E2ETestingStrategy;
    performanceTesting: PerformanceTestingStrategy;
    securityTesting: SecurityTestingStrategy;
  };
  qualityGates: QualityGate[];
  testAutomation: TestAutomationConfiguration;
  chatmode: 'qa-engineer';
}

// Comprehensive testing implementation
const comprehensiveTestingStrategy = {
  chatmode: 'qa-engineer',
  phases: [
    {
      name: 'Test Planning & Strategy',
      activities: [
        'Define test coverage requirements',
        'Plan test data management',
        'Design test automation framework',
        'Set up test environments'
      ]
    },
    {
      name: 'Test Implementation',
      testing: {
        react: `
// React Component Testing with Testing Library
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import userEvent from '@testing-library/user-event';
import { rest } from 'msw';
import { setupServer } from 'msw/node';
import { FeatureContainer } from '../FeatureContainer';

// Mock server for API calls
const server = setupServer(
  rest.get('/api/features/:id', (req, res, ctx) => {
    return res(ctx.json({
      id: req.params.id,
      name: 'Test Feature',
      status: 'active',
      configuration: { editable: true },
      availableActions: ['edit', 'delete', 'share']
    }));
  }),

  rest.put('/api/features/:id', (req, res, ctx) => {
    return res(ctx.json({
      id: req.params.id,
      ...req.body,
      updatedAt: new Date().toISOString()
    }));
  })
);

beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());

describe('FeatureContainer Integration Tests', () => {
  let queryClient: QueryClient;
  const user = userEvent.setup();

  beforeEach(() => {
    queryClient = new QueryClient({
      defaultOptions: {
        queries: { retry: false },
        mutations: { retry: false }
      }
    });
  });

  const renderFeatureContainer = (props = {}) => {
    const defaultProps = {
      featureId: 'test-feature-123',
      configuration: { editable: true },
      onFeatureUpdate: jest.fn()
    };

    return render(
      <QueryClientProvider client={queryClient}>
        <FeatureContainer {...defaultProps} {...props} />
      </QueryClientProvider>
    );
  };

  test('should render feature container with loading state initially', () => {
    renderFeatureContainer();
    expect(screen.getByTestId('feature-loading-skeleton')).toBeInTheDocument();
  });

  test('should display feature content after successful data fetch', async () => {
    renderFeatureContainer();

    await waitFor(() => {
      expect(screen.getByTestId('feature-container')).toBeInTheDocument();
    });

    expect(screen.getByText('Test Feature')).toBeInTheDocument();
    expect(screen.getByTestId('feature-content')).toBeInTheDocument();
    expect(screen.getByTestId('feature-actions')).toBeInTheDocument();
  });

  test('should handle feature update successfully', async () => {
    const mockOnFeatureUpdate = jest.fn();
    renderFeatureContainer({ onFeatureUpdate: mockOnFeatureUpdate });

    await waitFor(() => {
      expect(screen.getByTestId('feature-container')).toBeInTheDocument();
    });

    const editButton = screen.getByRole('button', { name: /edit/i });
    await user.click(editButton);

    const nameInput = screen.getByLabelText(/feature name/i);
    await user.clear(nameInput);
    await user.type(nameInput, 'Updated Feature Name');

    const saveButton = screen.getByRole('button', { name: /save/i });
    await user.click(saveButton);

    await waitFor(() => {
      expect(mockOnFeatureUpdate).toHaveBeenCalledWith(
        expect.objectContaining({
          name: 'Updated Feature Name'
        })
      );
    });
  });

  test('should handle API errors gracefully', async () => {
    server.use(
      rest.get('/api/features/:id', (req, res, ctx) => {
        return res(ctx.status(500), ctx.json({ error: 'Server error' }));
      })
    );

    renderFeatureContainer();

    await waitFor(() => {
      expect(screen.getByTestId('feature-error-boundary')).toBeInTheDocument();
    });

    expect(screen.getByText(/something went wrong/i)).toBeInTheDocument();
    expect(screen.getByRole('button', { name: /retry/i })).toBeInTheDocument();
  });

  test('should retry failed requests when retry button is clicked', async () => {
    server.use(
      rest.get('/api/features/:id', (req, res, ctx) => {
        return res.once(ctx.status(500), ctx.json({ error: 'Server error' }));
      })
    );

    renderFeatureContainer();

    await waitFor(() => {
      expect(screen.getByTestId('feature-error-boundary')).toBeInTheDocument();
    });

    const retryButton = screen.getByRole('button', { name: /retry/i });
    await user.click(retryButton);

    await waitFor(() => {
      expect(screen.getByTestId('feature-container')).toBeInTheDocument();
    });
  });
});

// Performance Testing
describe('FeatureContainer Performance Tests', () => {
  test('should not re-render unnecessarily', async () => {
    const renderSpy = jest.fn();
    const TestWrapper = ({ children }) => {
      renderSpy();
      return children;
    };

    const { rerender } = render(
      <TestWrapper>
        <FeatureContainer featureId="test-123" configuration={{ editable: true }} onFeatureUpdate={() => {}} />
      </TestWrapper>
    );

    // Same props should not cause re-render
    rerender(
      <TestWrapper>
        <FeatureContainer featureId="test-123" configuration={{ editable: true }} onFeatureUpdate={() => {}} />
      </TestWrapper>
    );

    expect(renderSpy).toHaveBeenCalledTimes(1);
  });

  test('should handle large datasets efficiently', async () => {
    const startTime = performance.now();

    renderFeatureContainer({
      featureId: 'large-dataset-feature',
      configuration: { editable: true, itemCount: 10000 }
    });

    await waitFor(() => {
      expect(screen.getByTestId('feature-container')).toBeInTheDocument();
    });

    const endTime = performance.now();
    const renderTime = endTime - startTime;

    expect(renderTime).toBeLessThan(1000); // Should render in under 1 second
  });
});
        `,

        node: `
// Node.js API Integration Testing
import request from 'supertest';
import { app } from '../../../app';
import { setupTestDb, cleanupTestDb } from '../../utils/testDb';
import { createTestUser, createTestFeature } from '../../utils/testFactories';
import jwt from 'jsonwebtoken';

describe('Feature API Integration Tests', () => {
  let testUser: any;
  let authToken: string;

  beforeAll(async () => {
    await setupTestDb();
  });

  afterAll(async () => {
    await cleanupTestDb();
  });

  beforeEach(async () => {
    testUser = await createTestUser({
      email: 'test@example.com',
      role: 'user'
    });

    authToken = jwt.sign(
      { userId: testUser.id, email: testUser.email },
      process.env.JWT_SECRET!,
      { expiresIn: '1h' }
    );
  });

  describe('POST /api/features', () => {
    test('should create feature successfully with valid data', async () => {
      const featureData = {
        name: 'Test Feature',
        description: 'A test feature for integration testing',
        featureType: 'toggle',
        configuration: {
          enabled: true,
          rolloutPercentage: 50
        }
      };

      const response = await request(app)
        .post('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(featureData)
        .expect(201);

      expect(response.body).toEqual({
        success: true,
        data: expect.objectContaining({
          id: expect.any(String),
          name: featureData.name,
          description: featureData.description,
          status: 'draft',
          createdBy: testUser.id
        }),
        message: 'Feature created successfully'
      });
    });

    test('should return 400 for invalid feature data', async () => {
      const invalidData = {
        name: '', // Invalid: empty name
        description: 'Test description'
      };

      const response = await request(app)
        .post('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(invalidData)
        .expect(400);

      expect(response.body.success).toBe(false);
      expect(response.body.error).toContain('name');
    });

    test('should return 401 for unauthenticated requests', async () => {
      const featureData = {
        name: 'Test Feature',
        description: 'Test description'
      };

      await request(app)
        .post('/api/features')
        .send(featureData)
        .expect(401);
    });

    test('should enforce business rules (duplicate name)', async () => {
      const featureData = {
        name: 'Duplicate Feature',
        description: 'First feature'
      };

      // Create first feature
      await request(app)
        .post('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(featureData)
        .expect(201);

      // Try to create duplicate
      const response = await request(app)
        .post('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(featureData)
        .expect(400);

      expect(response.body.error).toContain('already exists');
    });
  });

  describe('GET /api/features/:id', () => {
    test('should return feature for authorized user', async () => {
      const feature = await createTestFeature({
        name: 'Test Feature',
        createdBy: testUser.id
      });

      const response = await request(app)
        .get(\`/api/features/\${feature.id}\`)
        .set('Authorization', \`Bearer \${authToken}\`)
        .expect(200);

      expect(response.body).toEqual({
        success: true,
        data: expect.objectContaining({
          id: feature.id,
          name: feature.name
        })
      });
    });

    test('should return 404 for non-existent feature', async () => {
      await request(app)
        .get('/api/features/non-existent-id')
        .set('Authorization', \`Bearer \${authToken}\`)
        .expect(404);
    });

    test('should return 403 for unauthorized access', async () => {
      const otherUser = await createTestUser({ email: 'other@example.com' });
      const feature = await createTestFeature({
        name: 'Private Feature',
        createdBy: otherUser.id
      });

      await request(app)
        .get(\`/api/features/\${feature.id}\`)
        .set('Authorization', \`Bearer \${authToken}\`)
        .expect(403);
    });
  });

  describe('PUT /api/features/:id', () => {
    test('should update feature successfully', async () => {
      const feature = await createTestFeature({
        name: 'Original Name',
        createdBy: testUser.id
      });

      const updateData = {
        name: 'Updated Name',
        description: 'Updated description'
      };

      const response = await request(app)
        .put(\`/api/features/\${feature.id}\`)
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(updateData)
        .expect(200);

      expect(response.body.data).toEqual(
        expect.objectContaining({
          id: feature.id,
          name: updateData.name,
          description: updateData.description
        })
      );
    });

    test('should validate update data', async () => {
      const feature = await createTestFeature({
        createdBy: testUser.id
      });

      const invalidUpdate = {
        name: '', // Invalid: empty name
        status: 'invalid-status' // Invalid status
      };

      const response = await request(app)
        .put(\`/api/features/\${feature.id}\`)
        .set('Authorization', \`Bearer \${authToken}\`)
        .send(invalidUpdate)
        .expect(400);

      expect(response.body.success).toBe(false);
    });
  });
});

// Performance Tests
describe('Feature API Performance Tests', () => {
  test('should handle concurrent requests efficiently', async () => {
    const concurrentRequests = 50;
    const requests = Array.from({ length: concurrentRequests }, (_, i) =>
      request(app)
        .post('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .send({
          name: \`Concurrent Feature \${i}\`,
          description: 'Performance test feature'
        })
    );

    const startTime = Date.now();
    const responses = await Promise.all(requests);
    const endTime = Date.now();

    const duration = endTime - startTime;
    const successfulRequests = responses.filter(r => r.status === 201).length;

    expect(successfulRequests).toBe(concurrentRequests);
    expect(duration).toBeLessThan(5000); // Should complete in under 5 seconds
  });

  test('should maintain response time under load', async () => {
    const iterations = 100;
    const responseTimes: number[] = [];

    for (let i = 0; i < iterations; i++) {
      const start = Date.now();

      await request(app)
        .get('/api/features')
        .set('Authorization', \`Bearer \${authToken}\`)
        .expect(200);

      const responseTime = Date.now() - start;
      responseTimes.push(responseTime);
    }

    const averageResponseTime = responseTimes.reduce((a, b) => a + b, 0) / iterations;
    const p95ResponseTime = responseTimes.sort((a, b) => a - b)[Math.floor(0.95 * iterations)];

    expect(averageResponseTime).toBeLessThan(100); // Average under 100ms
    expect(p95ResponseTime).toBeLessThan(200); // 95th percentile under 200ms
  });
});
        `,

        e2e: `
// E2E Testing with Playwright
import { test, expect, Page } from '@playwright/test';
import { LoginHelper } from '../helpers/LoginHelper';
import { FeatureHelper } from '../helpers/FeatureHelper';

test.describe('Feature Development Lifecycle E2E', () => {
  let page: Page;
  let loginHelper: LoginHelper;
  let featureHelper: FeatureHelper;

  test.beforeEach(async ({ page: p }) => {
    page = p;
    loginHelper = new LoginHelper(page);
    featureHelper = new FeatureHelper(page);

    // Login as test user
    await loginHelper.loginAs('testuser@example.com', 'password');
  });

  test('complete feature creation and management workflow', async () => {
    // Navigate to features page
    await page.goto('/features');
    await expect(page.locator('[data-testid="features-page"]')).toBeVisible();

    // Create new feature
    await page.click('[data-testid="create-feature-button"]');
    await expect(page.locator('[data-testid="create-feature-modal"]')).toBeVisible();

    await page.fill('[data-testid="feature-name-input"]', 'E2E Test Feature');
    await page.fill('[data-testid="feature-description-textarea"]', 'Feature created via E2E testing');
    await page.selectOption('[data-testid="feature-type-select"]', 'toggle');

    // Configure feature settings
    await page.click('[data-testid="feature-configuration-tab"]');
    await page.check('[data-testid="feature-enabled-checkbox"]');
    await page.fill('[data-testid="rollout-percentage-input"]', '25');

    // Save feature
    await page.click('[data-testid="save-feature-button"]');

    // Verify feature creation
    await expect(page.locator('[data-testid="success-notification"]')).toBeVisible();
    await expect(page.locator('[data-testid="success-notification"]')).toContainText('Feature created successfully');

    // Verify feature appears in list
    await page.goto('/features');
    await expect(page.locator('[data-testid="feature-card"]').first()).toContainText('E2E Test Feature');

    // Edit feature
    await page.click('[data-testid="feature-card"]:first-of-type [data-testid="edit-button"]');
    await page.fill('[data-testid="feature-name-input"]', 'Updated E2E Test Feature');
    await page.click('[data-testid="save-feature-button"]');

    // Verify update
    await expect(page.locator('[data-testid="success-notification"]')).toContainText('Feature updated successfully');
    await expect(page.locator('[data-testid="feature-card"]').first()).toContainText('Updated E2E Test Feature');

    // Test feature toggle
    await page.click('[data-testid="feature-card"]:first-of-type [data-testid="toggle-button"]');
    await expect(page.locator('[data-testid="feature-status"]').first()).toContainText('Active');

    // Delete feature
    await page.click('[data-testid="feature-card"]:first-of-type [data-testid="delete-button"]');
    await page.click('[data-testid="confirm-delete-button"]');

    // Verify deletion
    await expect(page.locator('[data-testid="success-notification"]')).toContainText('Feature deleted successfully');
    await expect(page.locator('[data-testid="feature-card"]').first()).not.toContainText('Updated E2E Test Feature');
  });

  test('feature permissions and access control', async () => {
    // Create feature as admin user
    await loginHelper.loginAs('admin@example.com', 'adminpass');

    const featureId = await featureHelper.createFeature({
      name: 'Admin Feature',
      description: 'Feature with restricted access'
    });

    // Set restricted permissions
    await featureHelper.setFeaturePermissions(featureId, {
      viewPermissions: ['admin', 'editor'],
      editPermissions: ['admin']
    });

    // Logout and login as regular user
    await loginHelper.logout();
    await loginHelper.loginAs('user@example.com', 'userpass');

    // Verify user cannot access restricted feature
    await page.goto(\`/features/\${featureId}\`);
    await expect(page.locator('[data-testid="access-denied-message"]')).toBeVisible();
    await expect(page.locator('[data-testid="access-denied-message"]')).toContainText('Access denied');

    // Login as editor
    await loginHelper.logout();
    await loginHelper.loginAs('editor@example.com', 'editorpass');

    // Verify editor can view but not edit
    await page.goto(\`/features/\${featureId}\`);
    await expect(page.locator('[data-testid="feature-details"]')).toBeVisible();
    await expect(page.locator('[data-testid="edit-button"]')).not.toBeVisible();
  });

  test('feature performance under normal usage', async () => {
    // Create multiple features for performance testing
    const features = await featureHelper.createMultipleFeatures(50);

    // Navigate to features list
    await page.goto('/features');

    // Measure page load time
    const startTime = Date.now();
    await expect(page.locator('[data-testid="features-page"]')).toBeVisible();
    const loadTime = Date.now() - startTime;

    expect(loadTime).toBeLessThan(2000); // Page should load in under 2 seconds

    // Test search performance
    const searchStartTime = Date.now();
    await page.fill('[data-testid="feature-search-input"]', 'Test Feature');
    await expect(page.locator('[data-testid="feature-card"]').first()).toBeVisible();
    const searchTime = Date.now() - searchStartTime;

    expect(searchTime).toBeLessThan(500); // Search should complete in under 500ms

    // Test pagination performance
    await page.click('[data-testid="next-page-button"]');
    await expect(page.locator('[data-testid="features-page"]')).toBeVisible();

    // Cleanup
    await featureHelper.deleteMultipleFeatures(features.map(f => f.id));
  });
});
        `
      }
    }
  ]
};
```

### Stage 4: Production Deployment & Monitoring

```typescript
interface ProductionDeploymentStage {
  deploymentStrategy: 'blue-green' | 'canary' | 'rolling';
  monitoringSetup: MonitoringConfiguration;
  rollbackPlan: RollbackPlan;
  postDeploymentValidation: ValidationPlan;
  chatmode: 'deployment-engineer';
}

const productionDeploymentCoordination = {
  chatmode: 'deployment-engineer',
  phases: [
    {
      name: 'Pre-deployment Validation',
      activities: [
        'Validate all quality gates passed',
        'Verify staging environment matches production',
        'Confirm rollback procedures are ready',
        'Validate monitoring and alerting setup'
      ]
    },
    {
      name: 'Deployment Execution',
      activities: [
        'Execute deployment strategy',
        'Monitor real-time metrics',
        'Validate health checks',
        'Confirm feature functionality'
      ]
    },
    {
      name: 'Post-deployment Monitoring',
      activities: [
        'Monitor business metrics impact',
        'Track user adoption and feedback',
        'Validate performance targets',
        'Document lessons learned'
      ]
    }
  ]
};
```

## Chatmode Transition Framework

### Feature Lifecycle Chatmode Coordination

```typescript
interface FeatureLifecycleTransitions {
  discovery: {
    primary: 'business-analyst';
    supporting: ['product-manager', 'ux-designer'];
    duration: '1-2 weeks';
    deliverables: ['Feature specification', 'User stories', 'Acceptance criteria'];
  };
  planning: {
    primary: 'software-architect';
    supporting: ['security-engineer', 'data-engineer'];
    duration: '3-5 days';
    deliverables: ['Technical design', 'Implementation plan', 'Risk assessment'];
  };
  implementation: {
    primary: 'frontend-engineer' | 'backend-engineer' | 'api-engineer';
    supporting: ['data-engineer', 'security-engineer'];
    duration: '2-4 weeks';
    deliverables: ['Feature implementation', 'Unit tests', 'Integration tests'];
  };
  testing: {
    primary: 'qa-engineer';
    supporting: ['security-engineer'];
    duration: '1-2 weeks';
    deliverables: ['Test results', 'Performance validation', 'Security audit'];
  };
  deployment: {
    primary: 'deployment-engineer';
    supporting: ['qa-engineer', 'security-engineer'];
    duration: '1-3 days';
    deliverables: ['Production deployment', 'Monitoring setup', 'Documentation'];
  };
}

class FeatureLifecycleOrchestrator {
  generateTransitionGuidance(
    currentStage: string,
    nextStage: string,
    featureContext: FeatureContext
  ): string {
    return `
## Feature Lifecycle Transition: ${currentStage} → ${nextStage}

### Feature Context
- **Feature Name**: ${featureContext.name}
- **Business Priority**: ${featureContext.priority}
- **Technical Complexity**: ${featureContext.complexity}
- **Timeline**: ${featureContext.timeline}

### Current Stage Summary
${this.generateStageSum

ary(currentStage, featureContext)}

### Next Stage Requirements
${this.generateNextStageRequirements(nextStage, featureContext)}

### Recommended Chatmode: ${this.getOptimalChatmode(nextStage, featureContext)}

### Context Handoff Information
${this.generateContextHandoff(currentStage, nextStage, featureContext)}

### Success Criteria for ${nextStage}
${this.generateSuccessCriteria(nextStage, featureContext)}
    `;
  }
}
```

## Quality Gates & Standards

### Feature Development Quality Framework

```typescript
interface FeatureQualityFramework {
  discoveryGates: QualityGate[];
  implementationGates: QualityGate[];
  testingGates: QualityGate[];
  deploymentGates: QualityGate[];
  postDeploymentGates: QualityGate[];
}

const featureQualityGates: FeatureQualityFramework = {
  discoveryGates: [
    {
      name: 'Requirements Completeness',
      criteria: [
        { metric: 'user-stories-defined', threshold: 100, unit: 'percentage' },
        { metric: 'acceptance-criteria-coverage', threshold: 100, unit: 'percentage' },
        { metric: 'business-value-defined', threshold: 1, unit: 'boolean' },
        { metric: 'success-metrics-defined', threshold: 3, unit: 'minimum-count' }
      ],
      automationLevel: 'manual',
      blockingLevel: 'critical'
    }
  ],

  implementationGates: [
    {
      name: 'Code Quality Gate',
      criteria: [
        { metric: 'test-coverage', threshold: 85, unit: 'percentage' },
        { metric: 'code-review-approval', threshold: 2, unit: 'count' },
        { metric: 'security-scan-passed', threshold: 1, unit: 'boolean' },
        { metric: 'performance-benchmarks-met', threshold: 1, unit: 'boolean' }
      ],
      automationLevel: 'fully-automated',
      blockingLevel: 'critical'
    }
  ],

  deploymentGates: [
    {
      name: 'Production Readiness Gate',
      criteria: [
        { metric: 'monitoring-setup', threshold: 1, unit: 'boolean' },
        { metric: 'rollback-plan-verified', threshold: 1, unit: 'boolean' },
        { metric: 'performance-baseline-established', threshold: 1, unit: 'boolean' },
        { metric: 'security-audit-passed', threshold: 1, unit: 'boolean' }
      ],
      automationLevel: 'semi-automated',
      blockingLevel: 'critical'
    }
  ]
};
```

## Examples & Use Cases

### Example 1: E-commerce Product Recommendation Feature

```bash
# Epic: "Implement AI-powered product recommendations"
# Business Value: Increase conversion rate by 15%
# Technical Complexity: High (ML integration, real-time processing)

# Stage 1: Discovery (business-analyst + product-manager)
# - User research on shopping behavior
# - Competitive analysis of recommendation engines
# - Business case development with ROI projections
# - Success metrics definition (click-through rate, conversion impact)

# Stage 2: Planning (software-architect + data-engineer)
# - ML model selection and training pipeline design
# - Real-time recommendation API architecture
# - Data privacy and GDPR compliance planning
# - Performance and scalability requirements

# Stage 3: Implementation (backend-engineer + data-engineer + frontend-engineer)
# - ML model training and validation
# - Recommendation service implementation
# - Frontend recommendation widgets
# - A/B testing framework integration

# Stage 4: Testing (qa-engineer + security-engineer)
# - ML model accuracy validation
# - Performance testing under peak load
# - Security audit of recommendation data
# - Privacy compliance verification

# Stage 5: Deployment (deployment-engineer)
# - Canary deployment with 5% traffic
# - Real-time monitoring of conversion metrics
# - Gradual rollout based on performance data
```

### Example 2: Mobile App Offline Mode Feature

```bash
# Epic: "Add offline functionality to mobile app"
# Business Value: Improve user retention in low-connectivity areas
# Technical Complexity: Medium (data synchronization, conflict resolution)

# Complete lifecycle with technology-specific implementations:
# - React Native frontend with offline-first architecture
# - Node.js sync service with conflict resolution
# - SQLite local storage with sync queues
# - Comprehensive testing including network interruption scenarios
```

### Example 3: Enterprise SSO Integration Feature

```bash
# Epic: "Integrate with enterprise SSO providers"
# Business Value: Enable enterprise customer acquisition
# Technical Complexity: High (security, multiple protocols, compliance)

# Security-focused lifecycle:
# - Extensive security review at each stage
# - Compliance validation (SOC2, SAML, OIDC)
# - Penetration testing and security audit
# - Zero-trust deployment with extensive monitoring
```

This comprehensive workflow orchestrates the complete feature development lifecycle from initial concept through production deployment, with intelligent coordination between specialized chatmodes and enterprise-grade quality assurance at every stage.