---
name: github-issue-to-implementation
description: Complete workflow from GitHub Issue analysis to production-ready implementation with intelligent chatmode coordination
tools: [github-copilot, github-integration, issue-analysis, code-generation, workflow-automation]
model: github-copilot
context_adaptation: true
workflow_type: true
---

# GitHub Issue to Implementation Workflow

## Context Analysis Framework

This workflow automatically analyzes your development context and guides you through the complete implementation process:

```markdown
## Intelligent Context Detection
1. Read `copilot.instructions.md` for project specifications and standards
2. Analyze GitHub Issue details (labels, assignees, project, milestone)
3. Detect related Issues, PRs, and project context
4. Understand current codebase state and architecture
5. Map requirements to optimal implementation approach and chatmode sequence
```

## GitHub Integration Points

### 1. Issue Analysis & Understanding

```typescript
// Automatic GitHub Issue analysis
interface IssueAnalysis {
  issueDetails: {
    title: string;
    description: string;
    labels: string[];
    assignees: string[];
    milestone?: string;
    project?: string;
  };
  complexity: 'simple' | 'moderate' | 'complex' | 'epic';
  category: 'feature' | 'bug' | 'enhancement' | 'refactor' | 'documentation';
  estimatedEffort: 'small' | 'medium' | 'large' | 'xl';
  technicalDomains: string[];
  dependencies: {
    relatedIssues: number[];
    blockedBy: number[];
    blocks: number[];
  };
}

class GitHubIssueAnalyzer {
  async analyzeIssue(issueNumber: number): Promise<IssueAnalysis> {
    const issue = await this.fetchIssueDetails(issueNumber);

    return {
      issueDetails: this.extractIssueDetails(issue),
      complexity: this.assessComplexity(issue),
      category: this.categorizeIssue(issue),
      estimatedEffort: this.estimateEffort(issue),
      technicalDomains: this.identifyTechnicalDomains(issue),
      dependencies: await this.analyzeDependencies(issue)
    };
  }

  private assessComplexity(issue: GitHubIssue): 'simple' | 'moderate' | 'complex' | 'epic' {
    const indicators = {
      simple: issue.body.length < 500 && issue.labels.includes('good first issue'),
      moderate: issue.body.length < 1500 && !issue.labels.includes('epic'),
      complex: issue.body.length > 1500 || issue.labels.some(l => ['architecture', 'breaking-change'].includes(l)),
      epic: issue.labels.includes('epic') || issue.body.includes('## Subtasks')
    };

    return Object.entries(indicators).find(([_, matches]) => matches)?.[0] as any || 'moderate';
  }
}
```

### 2. Technology Detection & Implementation Strategy

```typescript
// Technology-specific implementation strategies
interface ImplementationStrategy {
  primaryChatmode: string;
  supportingChatmodes: string[];
  implementationPhases: ImplementationPhase[];
  qualityGates: QualityGate[];
  deploymentStrategy: DeploymentStrategy;
}

class ImplementationStrategyGenerator {
  generateStrategy(analysis: IssueAnalysis, projectContext: ProjectContext): ImplementationStrategy {
    const strategy = this.getBaseStrategy(analysis.category, analysis.complexity);

    return {
      primaryChatmode: this.selectPrimaryChatmode(analysis, projectContext),
      supportingChatmodes: this.selectSupportingChatmodes(analysis, projectContext),
      implementationPhases: this.planImplementationPhases(analysis, projectContext),
      qualityGates: this.defineQualityGates(analysis, projectContext),
      deploymentStrategy: this.planDeployment(analysis, projectContext)
    };
  }

  private selectPrimaryChatmode(analysis: IssueAnalysis, context: ProjectContext): string {
    const chatmodeMapping = {
      'frontend': 'frontend-engineer',
      'backend': 'backend-engineer',
      'api': 'api-engineer',
      'database': 'data-engineer',
      'security': 'security-engineer',
      'performance': 'qa-engineer',
      'architecture': 'software-architect',
      'ux/ui': 'ux-designer',
      'deployment': 'deployment-engineer'
    };

    const primaryDomain = analysis.technicalDomains[0];
    return chatmodeMapping[primaryDomain] || 'software-architect';
  }
}
```

## Workflow Stages

### Stage 1: Issue Analysis & Planning

```typescript
interface WorkflowStage1 {
  tasks: [
    'Analyze GitHub Issue requirements',
    'Understand acceptance criteria',
    'Identify technical domains and complexity',
    'Review related Issues and PRs',
    'Select optimal chatmode sequence',
    'Plan implementation approach'
  ];
  chatmode: 'business-analyst' | 'software-architect';
  deliverables: [
    'Detailed requirements analysis',
    'Technical implementation plan',
    'Chatmode transition roadmap',
    'Quality gates definition'
  ];
}

// Stage 1 Implementation Guide
const stage1Guide = {
  businessAnalyst: {
    focus: 'Requirements clarification and stakeholder alignment',
    activities: [
      'Parse Issue description and acceptance criteria',
      'Identify missing requirements or ambiguities',
      'Analyze business impact and user value',
      'Review related Issues for context',
      'Validate understanding with stakeholders if needed'
    ],
    transition: 'Switch to `software-architect` chatmode for technical planning'
  },

  softwareArchitect: {
    focus: 'Technical approach and architecture decisions',
    activities: [
      'Analyze current codebase architecture',
      'Design implementation approach',
      'Identify affected components and systems',
      'Plan database schema changes if needed',
      'Define integration points and APIs',
      'Select appropriate design patterns'
    ],
    transition: 'Switch to primary implementation chatmode (frontend/backend/api-engineer)'
  }
};
```

### Stage 2: Implementation Development

```typescript
interface WorkflowStage2 {
  implementationPhases: {
    preparation: 'Environment setup and branch creation';
    development: 'Core feature implementation';
    testing: 'Unit and integration tests';
    documentation: 'Code documentation and API specs';
    review: 'Self-review and quality checks';
  };
  chatmodeSequence: string[];
  qualityStandards: QualityStandards;
}

// Technology-Adaptive Implementation Patterns

// React/TypeScript Frontend Implementation
const reactImplementationPattern = {
  chatmode: 'frontend-engineer',
  structure: {
    'src/components/': 'Feature-specific components',
    'src/hooks/': 'Custom React hooks',
    'src/services/': 'API service integration',
    'src/types/': 'TypeScript type definitions',
    '__tests__/': 'Component tests'
  },
  implementation: `
// Feature Component Implementation
interface FeatureProps {
  issueId: number;
  requirements: Requirements;
}

const FeatureComponent: React.FC<FeatureProps> = ({ issueId, requirements }) => {
  const [state, setState] = useState<FeatureState>({
    loading: false,
    data: null,
    error: null
  });

  const { data, error, isLoading } = useFeatureData(issueId);

  return (
    <div className="feature-container">
      {isLoading && <LoadingSpinner />}
      {error && <ErrorMessage error={error} />}
      {data && <FeatureContent data={data} requirements={requirements} />}
    </div>
  );
};

// Custom Hook for Feature Logic
const useFeatureData = (issueId: number) => {
  return useQuery({
    queryKey: ['feature', issueId],
    queryFn: () => fetchFeatureData(issueId),
    staleTime: 5 * 60 * 1000
  });
};

// API Service Integration
const featureService = {
  async fetchFeatureData(issueId: number): Promise<FeatureData> {
    const response = await apiClient.get(\`/api/features/\${issueId}\`);
    return response.data;
  },

  async updateFeature(issueId: number, data: UpdateData): Promise<void> {
    await apiClient.put(\`/api/features/\${issueId}\`, data);
  }
};
  `,
  transition: 'Switch to `backend-engineer` chatmode for API implementation'
};

// Node.js/Express Backend Implementation
const nodeBackendImplementationPattern = {
  chatmode: 'backend-engineer',
  structure: {
    'src/controllers/': 'API route controllers',
    'src/services/': 'Business logic services',
    'src/models/': 'Data models and validation',
    'src/middleware/': 'Custom middleware',
    'tests/': 'Integration and unit tests'
  },
  implementation: `
// Feature Controller Implementation
import { Request, Response } from 'express';
import { FeatureService } from '../services/FeatureService';
import { validateFeatureRequest } from '../validators/featureValidator';

export class FeatureController {
  constructor(private featureService: FeatureService) {}

  async createFeature(req: Request, res: Response): Promise<void> {
    try {
      const validatedData = validateFeatureRequest(req.body);
      const feature = await this.featureService.createFeature(validatedData);

      res.status(201).json({
        success: true,
        data: feature,
        message: 'Feature created successfully'
      });
    } catch (error) {
      res.status(400).json({
        success: false,
        error: error.message
      });
    }
  }

  async getFeature(req: Request, res: Response): Promise<void> {
    try {
      const { id } = req.params;
      const feature = await this.featureService.getFeature(parseInt(id));

      if (!feature) {
        res.status(404).json({
          success: false,
          error: 'Feature not found'
        });
        return;
      }

      res.json({
        success: true,
        data: feature
      });
    } catch (error) {
      res.status(500).json({
        success: false,
        error: error.message
      });
    }
  }
}

// Feature Service Implementation
export class FeatureService {
  async createFeature(data: CreateFeatureRequest): Promise<Feature> {
    // Validate business rules
    await this.validateBusinessRules(data);

    // Create feature in database
    const feature = await this.featureRepository.create({
      ...data,
      createdAt: new Date(),
      status: 'active'
    });

    // Send notification
    await this.notificationService.notifyFeatureCreated(feature);

    return feature;
  }

  private async validateBusinessRules(data: CreateFeatureRequest): Promise<void> {
    // Implement business validation logic
    if (await this.featureRepository.existsByName(data.name)) {
      throw new Error('Feature with this name already exists');
    }
  }
}
  `,
  transition: 'Switch to `data-engineer` chatmode for database implementation'
};

// Python/FastAPI Implementation
const pythonFastApiImplementationPattern = {
  chatmode: 'backend-engineer',
  structure: {
    'app/api/': 'API routes and endpoints',
    'app/services/': 'Business logic services',
    'app/models/': 'Pydantic models',
    'app/db/': 'Database models and connections',
    'tests/': 'Pytest tests'
  },
  implementation: `
# Feature API Implementation
from fastapi import APIRouter, HTTPException, Depends
from typing import List
from app.services.feature_service import FeatureService
from app.schemas.feature import FeatureCreate, FeatureResponse
from app.core.dependencies import get_feature_service

router = APIRouter(prefix="/api/features", tags=["features"])

@router.post("/", response_model=FeatureResponse)
async def create_feature(
    feature_data: FeatureCreate,
    service: FeatureService = Depends(get_feature_service)
) -> FeatureResponse:
    """Create a new feature based on GitHub Issue requirements."""
    try:
        feature = await service.create_feature(feature_data)
        return FeatureResponse(
            success=True,
            data=feature,
            message="Feature created successfully"
        )
    except ValueError as e:
        raise HTTPException(status_code=400, detail=str(e))
    except Exception as e:
        raise HTTPException(status_code=500, detail="Internal server error")

@router.get("/{feature_id}", response_model=FeatureResponse)
async def get_feature(
    feature_id: int,
    service: FeatureService = Depends(get_feature_service)
) -> FeatureResponse:
    """Get feature by ID."""
    feature = await service.get_feature(feature_id)
    if not feature:
        raise HTTPException(status_code=404, detail="Feature not found")

    return FeatureResponse(success=True, data=feature)

# Feature Service Implementation
class FeatureService:
    def __init__(self, feature_repository: FeatureRepository):
        self.feature_repository = feature_repository

    async def create_feature(self, data: FeatureCreate) -> Feature:
        # Validate business rules
        await self._validate_business_rules(data)

        # Create feature
        feature = await self.feature_repository.create(
            Feature(
                **data.dict(),
                created_at=datetime.utcnow(),
                status=FeatureStatus.ACTIVE
            )
        )

        # Send notification
        await self._notify_feature_created(feature)

        return feature

    async def _validate_business_rules(self, data: FeatureCreate) -> None:
        if await self.feature_repository.exists_by_name(data.name):
            raise ValueError("Feature with this name already exists")
  `,
  transition: 'Switch to `qa-engineer` chatmode for testing implementation'
};

// Java/Spring Boot Implementation
const javaSpringBootImplementationPattern = {
  chatmode: 'backend-engineer',
  structure: {
    'src/main/java/controller/': 'REST controllers',
    'src/main/java/service/': 'Business logic services',
    'src/main/java/model/': 'Entity models',
    'src/main/java/repository/': 'Data access layer',
    'src/test/java/': 'JUnit tests'
  },
  implementation: `
// Feature Controller Implementation
@RestController
@RequestMapping("/api/features")
@Validated
@Slf4j
public class FeatureController {

    private final FeatureService featureService;

    public FeatureController(FeatureService featureService) {
        this.featureService = featureService;
    }

    @PostMapping
    public ResponseEntity<ApiResponse<Feature>> createFeature(
            @Valid @RequestBody CreateFeatureRequest request) {
        try {
            Feature feature = featureService.createFeature(request);
            return ResponseEntity.status(HttpStatus.CREATED)
                    .body(ApiResponse.success(feature, "Feature created successfully"));
        } catch (IllegalArgumentException e) {
            return ResponseEntity.badRequest()
                    .body(ApiResponse.error(e.getMessage()));
        }
    }

    @GetMapping("/{id}")
    public ResponseEntity<ApiResponse<Feature>> getFeature(@PathVariable Long id) {
        return featureService.findById(id)
                .map(feature -> ResponseEntity.ok(ApiResponse.success(feature)))
                .orElse(ResponseEntity.notFound().build());
    }
}

// Feature Service Implementation
@Service
@Transactional
public class FeatureService {

    private final FeatureRepository featureRepository;
    private final NotificationService notificationService;

    public FeatureService(FeatureRepository featureRepository,
                         NotificationService notificationService) {
        this.featureRepository = featureRepository;
        this.notificationService = notificationService;
    }

    public Feature createFeature(CreateFeatureRequest request) {
        // Validate business rules
        validateBusinessRules(request);

        // Create feature entity
        Feature feature = Feature.builder()
                .name(request.getName())
                .description(request.getDescription())
                .status(FeatureStatus.ACTIVE)
                .createdAt(LocalDateTime.now())
                .build();

        // Save to database
        feature = featureRepository.save(feature);

        // Send notification
        notificationService.notifyFeatureCreated(feature);

        return feature;
    }

    private void validateBusinessRules(CreateFeatureRequest request) {
        if (featureRepository.existsByName(request.getName())) {
            throw new IllegalArgumentException("Feature with this name already exists");
        }
    }
}
  `,
  transition: 'Switch to `security-engineer` chatmode for security review'
};
```

### Stage 3: Quality Assurance & Testing

```typescript
interface WorkflowStage3 {
  testingStrategy: {
    unitTests: 'Comprehensive unit test coverage';
    integrationTests: 'API and component integration tests';
    e2eTests: 'End-to-end user workflow tests';
    performanceTests: 'Performance and load testing';
  };
  chatmode: 'qa-engineer';
  qualityGates: QualityGate[];
}

// Quality Assurance Implementation Patterns
const qaImplementationPatterns = {
  react: `
// React Testing Library + Jest Implementation
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { FeatureComponent } from '../FeatureComponent';

describe('FeatureComponent', () => {
  let queryClient: QueryClient;

  beforeEach(() => {
    queryClient = new QueryClient({
      defaultOptions: { queries: { retry: false } }
    });
  });

  const renderComponent = (props = {}) => {
    return render(
      <QueryClientProvider client={queryClient}>
        <FeatureComponent issueId={123} {...props} />
      </QueryClientProvider>
    );
  };

  test('should render loading state initially', () => {
    renderComponent();
    expect(screen.getByTestId('loading-spinner')).toBeInTheDocument();
  });

  test('should display feature content after data loads', async () => {
    // Mock API response
    const mockFeatureData = { id: 123, name: 'Test Feature', status: 'active' };
    jest.spyOn(featureService, 'fetchFeatureData').mockResolvedValue(mockFeatureData);

    renderComponent();

    await waitFor(() => {
      expect(screen.getByText('Test Feature')).toBeInTheDocument();
    });
  });

  test('should handle user interactions correctly', async () => {
    const mockUpdateFeature = jest.spyOn(featureService, 'updateFeature');
    renderComponent();

    const updateButton = await screen.findByRole('button', { name: /update/i });
    fireEvent.click(updateButton);

    await waitFor(() => {
      expect(mockUpdateFeature).toHaveBeenCalledWith(123, expect.any(Object));
    });
  });
});
  `,

  node: `
// Express + Jest + Supertest Implementation
import request from 'supertest';
import { app } from '../app';
import { FeatureService } from '../services/FeatureService';

describe('Feature API', () => {
  let featureService: jest.Mocked<FeatureService>;

  beforeEach(() => {
    featureService = {
      createFeature: jest.fn(),
      getFeature: jest.fn(),
      updateFeature: jest.fn(),
      deleteFeature: jest.fn()
    } as any;
  });

  describe('POST /api/features', () => {
    test('should create feature successfully', async () => {
      const mockFeature = { id: 1, name: 'Test Feature', status: 'active' };
      featureService.createFeature.mockResolvedValue(mockFeature);

      const response = await request(app)
        .post('/api/features')
        .send({ name: 'Test Feature', description: 'Test Description' })
        .expect(201);

      expect(response.body).toEqual({
        success: true,
        data: mockFeature,
        message: 'Feature created successfully'
      });
    });

    test('should handle validation errors', async () => {
      const response = await request(app)
        .post('/api/features')
        .send({ description: 'Missing name field' })
        .expect(400);

      expect(response.body.success).toBe(false);
      expect(response.body.error).toContain('name');
    });
  });

  describe('GET /api/features/:id', () => {
    test('should return feature when found', async () => {
      const mockFeature = { id: 1, name: 'Test Feature' };
      featureService.getFeature.mockResolvedValue(mockFeature);

      const response = await request(app)
        .get('/api/features/1')
        .expect(200);

      expect(response.body.data).toEqual(mockFeature);
    });

    test('should return 404 when feature not found', async () => {
      featureService.getFeature.mockResolvedValue(null);

      await request(app)
        .get('/api/features/999')
        .expect(404);
    });
  });
});
  `,

  python: `
# FastAPI + Pytest Implementation
import pytest
from httpx import AsyncClient
from app.main import app
from app.services.feature_service import FeatureService
from app.schemas.feature import FeatureCreate

@pytest.fixture
async def client():
    async with AsyncClient(app=app, base_url="http://test") as ac:
        yield ac

@pytest.fixture
def mock_feature_service(mocker):
    return mocker.patch('app.core.dependencies.get_feature_service')

class TestFeatureAPI:
    async def test_create_feature_success(self, client: AsyncClient, mock_feature_service):
        # Arrange
        mock_feature = {"id": 1, "name": "Test Feature", "status": "active"}
        mock_feature_service.return_value.create_feature.return_value = mock_feature

        # Act
        response = await client.post(
            "/api/features/",
            json={"name": "Test Feature", "description": "Test Description"}
        )

        # Assert
        assert response.status_code == 200
        assert response.json()["success"] is True
        assert response.json()["data"]["name"] == "Test Feature"

    async def test_create_feature_validation_error(self, client: AsyncClient):
        # Act
        response = await client.post("/api/features/", json={"description": "Missing name"})

        # Assert
        assert response.status_code == 422
        assert "name" in response.json()["detail"][0]["loc"]

    async def test_get_feature_success(self, client: AsyncClient, mock_feature_service):
        # Arrange
        mock_feature = {"id": 1, "name": "Test Feature"}
        mock_feature_service.return_value.get_feature.return_value = mock_feature

        # Act
        response = await client.get("/api/features/1")

        # Assert
        assert response.status_code == 200
        assert response.json()["data"]["id"] == 1

    async def test_get_feature_not_found(self, client: AsyncClient, mock_feature_service):
        # Arrange
        mock_feature_service.return_value.get_feature.return_value = None

        # Act
        response = await client.get("/api/features/999")

        # Assert
        assert response.status_code == 404
  `,

  java: `
// Spring Boot + JUnit 5 + TestContainers Implementation
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
@Testcontainers
class FeatureControllerIntegrationTest {

    @Autowired
    private TestRestTemplate restTemplate;

    @Autowired
    private FeatureRepository featureRepository;

    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:14")
            .withDatabaseName("testdb")
            .withUsername("test")
            .withPassword("test");

    @DynamicPropertySource
    static void configureProperties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgres::getJdbcUrl);
        registry.add("spring.datasource.username", postgres::getUsername);
        registry.add("spring.datasource.password", postgres::getPassword);
    }

    @BeforeEach
    void setUp() {
        featureRepository.deleteAll();
    }

    @Test
    void createFeature_ShouldReturnCreatedFeature() {
        // Given
        CreateFeatureRequest request = CreateFeatureRequest.builder()
                .name("Test Feature")
                .description("Test Description")
                .build();

        // When
        ResponseEntity<ApiResponse> response = restTemplate.postForEntity(
                "/api/features", request, ApiResponse.class);

        // Then
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.CREATED);
        assertThat(response.getBody().isSuccess()).isTrue();
        assertThat(featureRepository.count()).isEqualTo(1);
    }

    @Test
    void getFeature_ShouldReturnFeatureWhenExists() {
        // Given
        Feature feature = Feature.builder()
                .name("Test Feature")
                .description("Test Description")
                .status(FeatureStatus.ACTIVE)
                .build();
        feature = featureRepository.save(feature);

        // When
        ResponseEntity<ApiResponse> response = restTemplate.getForEntity(
                "/api/features/" + feature.getId(), ApiResponse.class);

        // Then
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);
        assertThat(response.getBody().isSuccess()).isTrue();
    }

    @Test
    void getFeature_ShouldReturn404WhenNotExists() {
        // When
        ResponseEntity<ApiResponse> response = restTemplate.getForEntity(
                "/api/features/999", ApiResponse.class);

        // Then
        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.NOT_FOUND);
    }
}
  `
};
```

### Stage 4: Review & Deployment Preparation

```typescript
interface WorkflowStage4 {
  reviewProcess: {
    selfReview: 'Code self-review checklist';
    peerReview: 'Pull request preparation';
    securityReview: 'Security vulnerability check';
    performanceReview: 'Performance impact assessment';
  };
  chatmode: 'reviewer' | 'security-engineer';
  deploymentPreparation: DeploymentPreparation;
}

const stage4Guide = {
  selfReviewChecklist: [
    'Code follows project style guidelines',
    'All tests pass and provide adequate coverage',
    'Documentation is updated and accurate',
    'No sensitive data or secrets in code',
    'Error handling is comprehensive',
    'Performance considerations are addressed',
    'Accessibility requirements are met (frontend)',
    'API documentation is updated (backend)',
    'Database migrations are safe and reversible',
    'Configuration changes are documented'
  ],

  pullRequestPreparation: {
    title: 'Clear, descriptive PR title following conventions',
    description: `
## Summary
Brief description of changes and how they address the GitHub Issue.

## GitHub Issue
Closes #[issue-number]

## Changes Made
- [ ] Feature implementation
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] Database changes (if any)

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed
- [ ] Edge cases considered

## Security & Performance
- [ ] Security review completed
- [ ] No performance regressions
- [ ] Resource usage optimized

## Deployment Notes
Any special deployment considerations or steps.
    `,
    reviewers: 'Automatic assignment based on code ownership and expertise'
  }
};
```

## Chatmode Transition Framework

### Intelligent Chatmode Routing

```typescript
interface ChatmodeTransition {
  fromStage: string;
  toStage: string;
  chatmode: string;
  contextHandoff: ContextHandoff;
  transitionCriteria: string[];
}

class ChatmodeTransitionManager {
  getOptimalTransition(
    currentStage: WorkflowStage,
    issueAnalysis: IssueAnalysis,
    projectContext: ProjectContext
  ): ChatmodeTransition {

    const transitionMap: Record<string, ChatmodeTransition[]> = {
      'analysis': [
        {
          fromStage: 'analysis',
          toStage: 'implementation',
          chatmode: this.selectImplementationChatmode(issueAnalysis),
          contextHandoff: this.prepareImplementationContext(issueAnalysis),
          transitionCriteria: [
            'Requirements are clearly understood',
            'Technical approach is defined',
            'Implementation plan is approved'
          ]
        }
      ],
      'implementation': [
        {
          fromStage: 'implementation',
          toStage: 'testing',
          chatmode: 'qa-engineer',
          contextHandoff: this.prepareTestingContext(issueAnalysis),
          transitionCriteria: [
            'Core implementation is complete',
            'Basic functionality works',
            'Ready for comprehensive testing'
          ]
        }
      ],
      'testing': [
        {
          fromStage: 'testing',
          toStage: 'review',
          chatmode: 'reviewer',
          contextHandoff: this.prepareReviewContext(issueAnalysis),
          transitionCriteria: [
            'All tests are passing',
            'Code coverage meets standards',
            'Performance is acceptable'
          ]
        }
      ]
    };

    return transitionMap[currentStage]?.[0] || this.getDefaultTransition();
  }

  private selectImplementationChatmode(analysis: IssueAnalysis): string {
    const primaryDomain = analysis.technicalDomains[0];

    const chatmodeMapping = {
      'frontend': 'frontend-engineer',
      'backend': 'backend-engineer',
      'api': 'api-engineer',
      'database': 'data-engineer',
      'security': 'security-engineer',
      'infrastructure': 'deployment-engineer',
      'ux/ui': 'ux-designer'
    };

    return chatmodeMapping[primaryDomain] || 'software-architect';
  }
}
```

### Context Preservation Patterns

```typescript
interface WorkflowContext {
  issueDetails: IssueAnalysis;
  implementationDecisions: ImplementationDecision[];
  codeChanges: CodeChange[];
  testResults: TestResult[];
  qualityMetrics: QualityMetric[];
  deploymentPlan: DeploymentPlan;
}

class WorkflowContextManager {
  preserveContext(fromChatmode: string, toChatmode: string, context: WorkflowContext): string {
    return `
## Context Handoff from ${fromChatmode} to ${toChatmode}

### GitHub Issue Context
- **Issue #**: ${context.issueDetails.issueDetails.title}
- **Complexity**: ${context.issueDetails.complexity}
- **Category**: ${context.issueDetails.category}
- **Technical Domains**: ${context.issueDetails.technicalDomains.join(', ')}

### Implementation Decisions Made
${context.implementationDecisions.map(decision =>
  `- **${decision.area}**: ${decision.decision} (Rationale: ${decision.rationale})`
).join('\n')}

### Code Changes Summary
${context.codeChanges.map(change =>
  `- ${change.type}: ${change.file} - ${change.description}`
).join('\n')}

### Current Status
- **Completion**: ${this.calculateCompletionPercentage(context)}%
- **Next Steps**: ${this.generateNextSteps(toChatmode, context)}
- **Blockers**: ${context.blockers || 'None'}

### Quality Gates Status
${context.qualityMetrics.map(metric =>
  `- ${metric.name}: ${metric.status} (${metric.value})`
).join('\n')}

### Transition Instructions
${this.generateTransitionInstructions(toChatmode, context)}
    `;
  }
}
```

## Quality Gates & Standards

### Enterprise-Grade Quality Framework

```typescript
interface QualityGate {
  name: string;
  criteria: QualityCriteria[];
  automationLevel: 'manual' | 'semi-automated' | 'fully-automated';
  blockingLevel: 'warning' | 'error' | 'critical';
  chatmodeResponsible: string;
}

const enterpriseQualityGates: QualityGate[] = [
  {
    name: 'Code Quality Gate',
    criteria: [
      { metric: 'code-coverage', threshold: 80, unit: 'percentage' },
      { metric: 'complexity-score', threshold: 10, unit: 'cyclomatic' },
      { metric: 'duplication', threshold: 3, unit: 'percentage' },
      { metric: 'maintainability-index', threshold: 20, unit: 'score' }
    ],
    automationLevel: 'fully-automated',
    blockingLevel: 'error',
    chatmodeResponsible: 'qa-engineer'
  },

  {
    name: 'Security Gate',
    criteria: [
      { metric: 'vulnerability-scan', threshold: 0, unit: 'high-severity' },
      { metric: 'dependency-check', threshold: 0, unit: 'known-vulnerabilities' },
      { metric: 'secrets-detection', threshold: 0, unit: 'exposed-secrets' },
      { metric: 'security-headers', threshold: 100, unit: 'percentage' }
    ],
    automationLevel: 'fully-automated',
    blockingLevel: 'critical',
    chatmodeResponsible: 'security-engineer'
  },

  {
    name: 'Performance Gate',
    criteria: [
      { metric: 'response-time', threshold: 200, unit: 'milliseconds' },
      { metric: 'memory-usage', threshold: 512, unit: 'megabytes' },
      { metric: 'cpu-utilization', threshold: 70, unit: 'percentage' },
      { metric: 'database-queries', threshold: 50, unit: 'per-request' }
    ],
    automationLevel: 'semi-automated',
    blockingLevel: 'warning',
    chatmodeResponsible: 'qa-engineer'
  },

  {
    name: 'Documentation Gate',
    criteria: [
      { metric: 'api-documentation-coverage', threshold: 100, unit: 'percentage' },
      { metric: 'code-comments', threshold: 70, unit: 'percentage' },
      { metric: 'readme-completeness', threshold: 90, unit: 'percentage' },
      { metric: 'changelog-updated', threshold: 100, unit: 'boolean' }
    ],
    automationLevel: 'manual',
    blockingLevel: 'warning',
    chatmodeResponsible: 'business-analyst'
  }
];
```

### Automated Quality Validation

```yaml
# GitHub Actions workflow for quality gates
name: Quality Gates Validation

on:
  pull_request:
    branches: [ main, develop ]

jobs:
  code-quality:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Code Quality Analysis
        run: |
          # SonarQube analysis
          sonar-scanner \
            -Dsonar.projectKey=${{ github.repository }} \
            -Dsonar.sources=src \
            -Dsonar.tests=tests \
            -Dsonar.coverage.exclusions="**/*.test.*,**/tests/**"

      - name: Validate Coverage Threshold
        run: |
          coverage report --fail-under=80

  security-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Security Scan
        uses: securecodewarrior/github-action-add-sarif@v1
        with:
          sarif-file: security-scan-results.sarif

      - name: Dependency Vulnerability Check
        run: |
          npm audit --audit-level high
          # or: pip-audit for Python, etc.

  performance-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Performance Tests
        run: |
          # Load testing with artillery or similar
          npx artillery quick \
            --count 100 \
            --num 10 \
            http://localhost:3000/api/features

      - name: Validate Performance Metrics
        run: |
          # Validate response times and resource usage
          node scripts/validate-performance.js
```

## Examples & Use Cases

### Example 1: Frontend Feature Implementation (React)

```bash
# GitHub Issue: "Add user dashboard with real-time notifications"
# Labels: ["frontend", "feature", "high-priority"]
# Complexity: moderate
# Estimated effort: medium

# Workflow Execution:
# 1. Analysis Stage (business-analyst chatmode)
#    - Parse requirements: User dashboard with real-time notifications
#    - Identify acceptance criteria: Display user data, show live notifications
#    - Technical domains: frontend, real-time, api-integration

# 2. Architecture Stage (software-architect chatmode)
#    - Design component architecture
#    - Plan WebSocket integration for real-time features
#    - Define API requirements

# 3. Implementation Stage (frontend-engineer chatmode)
#    - Create dashboard components
#    - Implement WebSocket connection
#    - Add notification system
#    - Style with design system

# 4. Testing Stage (qa-engineer chatmode)
#    - Unit tests for components
#    - Integration tests for WebSocket
#    - E2E tests for user workflows

# 5. Review Stage (reviewer chatmode)
#    - Code review checklist
#    - Performance validation
#    - Accessibility audit
```

### Example 2: API Endpoint Implementation (Node.js)

```bash
# GitHub Issue: "Create REST API for feature management"
# Labels: ["backend", "api", "database"]
# Complexity: moderate
# Estimated effort: large

# Workflow Execution:
# 1. Analysis Stage (business-analyst chatmode)
#    - Define API requirements and endpoints
#    - Document request/response schemas
#    - Identify data validation rules

# 2. Architecture Stage (software-architect chatmode)
#    - Design API architecture
#    - Plan database schema changes
#    - Define error handling strategy

# 3. Implementation Stage (api-engineer chatmode)
#    - Create Express routes and controllers
#    - Implement business logic services
#    - Add input validation and sanitization
#    - Create OpenAPI documentation

# 4. Database Stage (data-engineer chatmode)
#    - Design database schema
#    - Create migration scripts
#    - Optimize queries and indexes

# 5. Security Stage (security-engineer chatmode)
#    - Implement authentication/authorization
#    - Add rate limiting and request validation
#    - Security audit and penetration testing

# 6. Testing Stage (qa-engineer chatmode)
#    - API integration tests
#    - Load and performance testing
#    - Security vulnerability testing
```

### Example 3: Bug Fix Implementation (Full-Stack)

```bash
# GitHub Issue: "User authentication fails intermittently"
# Labels: ["bug", "critical", "authentication", "backend"]
# Complexity: complex
# Estimated effort: large

# Workflow Execution:
# 1. Analysis Stage (business-analyst chatmode)
#    - Analyze bug reports and reproduction steps
#    - Identify affected user workflows
#    - Prioritize impact and urgency

# 2. Investigation Stage (software-architect chatmode)
#    - Review authentication architecture
#    - Analyze logs and monitoring data
#    - Identify potential root causes

# 3. Fix Implementation (backend-engineer chatmode)
#    - Debug authentication service
#    - Implement fix for identified issues
#    - Add enhanced logging and monitoring

# 4. Security Review (security-engineer chatmode)
#    - Validate security implications of fix
#    - Ensure no new vulnerabilities introduced
#    - Review authentication flow end-to-end

# 5. Testing Stage (qa-engineer chatmode)
#    - Reproduce original bug scenarios
#    - Test fix under various conditions
#    - Regression testing for related features
#    - Load testing for authentication service

# 6. Deployment Stage (deployment-engineer chatmode)
#    - Plan deployment strategy
#    - Prepare rollback procedures
#    - Monitor deployment and system health
```

This comprehensive workflow provides intelligent guidance from GitHub Issue analysis through production deployment, with seamless transitions between specialized chatmodes and enterprise-grade quality standards.