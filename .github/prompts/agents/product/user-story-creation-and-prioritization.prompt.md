---
name: user-story-creation-and-prioritization
description: Transform business requirements into prioritized user stories with clear acceptance criteria and strategic backlog management
tools: [all]
model: claude-sonnet-4
---

# User Story Creation and Prioritization

**Purpose: Transform business requirements into prioritized user stories with clear acceptance criteria, ensuring maximum value delivery and development efficiency**

## Context Adaptation Framework

Read and understand project specifications from `copilot.instructions.md` file. Adapt all user story creation and prioritization approaches to match:

- **Project domain and business context**
- **User personas and target segments**
- **Technology stack and development constraints**
- **Business objectives and success metrics**
- **Development methodology and team structure**
- **Release cadence and delivery timeline**

All user stories and prioritization frameworks must align with project-specific context while maintaining clear value delivery focus.

---

## 🎯 Mission

Create well-structured user stories that translate business requirements into actionable development tasks, prioritized by business value, user impact, and strategic alignment with continuous backlog optimization.

## 📋 Comprehensive User Story Framework

### Step 1: Advanced User Story Structure

**Standard Format Enhancement:**
```typescript
interface UserStory {
  format: "As a [user persona], I want [specific functionality] so that [measurable business value]";

  components: {
    userPersona: {
      role: string;
      context: string;
      experience_level: string;
      primary_goals: string[];
    };

    functionality: {
      action: string;
      scope: string;
      integration_points: string[];
      technical_constraints: string[];
    };

    businessValue: {
      user_benefit: string;
      business_impact: string;
      success_metrics: Metric[];
      strategic_alignment: string;
    };
  };
}
```

**Extended Story Template:**
```markdown
## User Story: [Story Title]

**Story ID:** [PROJ-###]
**Epic:** [Parent Epic Name]
**Theme:** [Strategic Theme]
**Priority:** [High/Medium/Low]

### User Story
As a [detailed user persona with context]
I want [specific functionality with clear scope]
So that [measurable business value and user benefit]

### Business Context
- **Strategic Objective:** [How this supports business goals]
- **User Impact:** [Expected improvement in user experience]
- **Business Value:** [Revenue, efficiency, or competitive advantage]
- **Success Metrics:** [Specific KPIs to measure success]

### Acceptance Criteria
**Scenario 1: [Happy Path]**
- Given [specific context and preconditions]
- When [user performs specific action]
- Then [expected system behavior and outcome]
- And [additional verification points]

**Scenario 2: [Edge Case]**
- Given [different context or conditions]
- When [alternative user action]
- Then [appropriate system response]

**Scenario 3: [Error Handling]**
- Given [error conditions]
- When [user encounters error]
- Then [graceful error handling and recovery]

### Technical Considerations
- **Dependencies:** [Other stories or systems required]
- **Integration Points:** [APIs, services, external systems]
- **Performance Requirements:** [Response time, throughput]
- **Security Requirements:** [Authentication, authorization, data protection]

### Definition of Done
- [ ] Code implemented following coding standards
- [ ] Unit tests written with >90% coverage
- [ ] Integration tests passing
- [ ] Performance requirements validated
- [ ] Security review completed
- [ ] Accessibility standards met (WCAG 2.1 AA)
- [ ] User documentation updated
- [ ] Stakeholder acceptance obtained
```

### Step 2: Story Hierarchy and Classification

**Epic Level Stories (3-6 months):**
```typescript
interface Epic {
  name: string;
  description: string;
  business_objective: string;
  user_segments: UserSegment[];
  features: Feature[];
  success_criteria: SuccessCriteria[];
  dependencies: Epic[];
  estimated_effort: string;
  business_value_score: number;
}

// Example: User Account Management Epic
const userAccountEpic: Epic = {
  name: "Comprehensive User Account Management",
  description: "Enable users to create, manage, and customize their accounts with security and personalization features",
  business_objective: "Increase user retention by 25% through improved account experience",
  user_segments: ["new_users", "existing_users", "enterprise_users"],
  features: ["registration", "profile_management", "security_settings", "preferences"],
  success_criteria: [
    { metric: "user_retention_rate", target: "25% increase", timeframe: "3 months" },
    { metric: "account_completion_rate", target: "80%", timeframe: "1 month" }
  ]
};
```

**Feature Level Stories (1-3 sprints):**
```typescript
interface FeatureStory {
  epic_id: string;
  feature_name: string;
  user_personas: string[];
  business_value: BusinessValue;
  technical_complexity: TechnicalComplexity;
  dependencies: Dependency[];
  acceptance_criteria: AcceptanceCriteria[];
}

// Example: User Profile Management Feature
const profileManagementFeature: FeatureStory = {
  epic_id: "EPIC-001",
  feature_name: "User Profile Management",
  user_personas: ["registered_user", "premium_user"],
  business_value: {
    user_satisfaction_impact: "high",
    revenue_impact: "medium",
    strategic_importance: "high"
  },
  technical_complexity: {
    backend_effort: "medium",
    frontend_effort: "medium",
    integration_effort: "low"
  }
};
```

**Task Level Stories (1 sprint or less):**
```typescript
interface TaskStory {
  feature_id: string;
  task_name: string;
  implementation_details: string;
  technical_requirements: TechnicalRequirement[];
  effort_estimate: number; // story points
  developer_type: string; // frontend, backend, fullstack
}
```

### Step 3: Advanced Acceptance Criteria Development

**Behavior-Driven Development (BDD) Format:**
```gherkin
Feature: User Profile Management
  As a registered user
  I want to update my profile information
  So that my account reflects accurate personal data

  Background:
    Given I am a logged-in user
    And I have a complete user profile

  Scenario: Successfully update profile information
    Given I am on the profile management page
    When I update my first name to "John"
    And I update my last name to "Doe"
    And I click the "Save Changes" button
    Then I should see a "Profile updated successfully" message
    And my profile should display "John Doe" as the full name
    And the changes should be persisted in the database

  Scenario: Validation error handling
    Given I am on the profile management page
    When I clear the required "Email" field
    And I click the "Save Changes" button
    Then I should see "Email is required" error message
    And the form should not be submitted
    And I should remain on the profile management page

  Scenario: Profile update with image upload
    Given I am on the profile management page
    When I upload a profile image that is 2MB in size
    And the image is in JPG format
    And I click the "Save Changes" button
    Then the image should be uploaded successfully
    And I should see the new image in my profile
    And the image should be optimized for web display
```

**Non-Functional Requirements Integration:**
```typescript
interface NonFunctionalCriteria {
  performance: {
    response_time: "< 2 seconds for profile updates";
    concurrent_users: "Support 1000 simultaneous profile updates";
    data_load_time: "< 1 second for profile data retrieval";
  };

  security: {
    authentication: "Must verify user identity before updates";
    authorization: "Users can only update their own profiles";
    data_validation: "Server-side validation for all input fields";
    audit_trail: "Log all profile changes with timestamp and user ID";
  };

  usability: {
    accessibility: "WCAG 2.1 AA compliance for all form elements";
    responsive_design: "Functional on mobile, tablet, and desktop";
    error_messages: "Clear, actionable error messages";
    progressive_enhancement: "Basic functionality without JavaScript";
  };

  compatibility: {
    browsers: "Chrome 90+, Firefox 88+, Safari 14+, Edge 90+";
    mobile_os: "iOS 14+, Android 10+";
    api_versions: "Backward compatible with API v2.0";
  };
}
```

## 🏆 Advanced Prioritization Framework

### Multi-Criteria Decision Analysis (MCDA)

**Weighted Scoring Model:**
```typescript
interface PrioritizationCriteria {
  businessValue: {
    weight: 0.30;
    factors: {
      revenue_impact: number; // 1-10 scale
      user_satisfaction: number; // 1-10 scale
      strategic_alignment: number; // 1-10 scale
      competitive_advantage: number; // 1-10 scale
    };
  };

  technicalFeasibility: {
    weight: 0.25;
    factors: {
      implementation_complexity: number; // 1-10 scale (10 = simple)
      technical_risk: number; // 1-10 scale (10 = low risk)
      resource_availability: number; // 1-10 scale
      technology_maturity: number; // 1-10 scale
    };
  };

  userImpact: {
    weight: 0.25;
    factors: {
      user_base_size: number; // 1-10 scale
      frequency_of_use: number; // 1-10 scale
      pain_point_severity: number; // 1-10 scale
      user_delight_potential: number; // 1-10 scale
    };
  };

  riskAndDependencies: {
    weight: 0.20;
    factors: {
      market_timing: number; // 1-10 scale
      regulatory_compliance: number; // 1-10 scale
      dependency_complexity: number; // 1-10 scale (10 = independent)
      rollback_difficulty: number; // 1-10 scale (10 = easy rollback)
    };
  };
}

// Prioritization calculation
function calculatePriority(story: UserStory, criteria: PrioritizationCriteria): number {
  const businessScore = calculateWeightedScore(criteria.businessValue);
  const technicalScore = calculateWeightedScore(criteria.technicalFeasibility);
  const userScore = calculateWeightedScore(criteria.userImpact);
  const riskScore = calculateWeightedScore(criteria.riskAndDependencies);

  return (businessScore * 0.30) + (technicalScore * 0.25) +
         (userScore * 0.25) + (riskScore * 0.20);
}
```

### Value vs Effort Matrix with Risk Assessment

**Advanced 3D Prioritization:**
```typescript
interface StoryPrioritization {
  id: string;
  title: string;
  businessValue: number; // 1-100
  implementationEffort: number; // story points
  riskLevel: RiskLevel; // low, medium, high
  dependencies: string[];

  priority: Priority; // calculated based on multiple factors
  quadrant: Quadrant; // "quick_wins" | "major_projects" | "fill_ins" | "avoid"

  recommendedAction: {
    timeline: string;
    rationale: string;
    prerequisites: string[];
    success_criteria: string[];
  };
}

enum Priority {
  P0_CRITICAL = "P0 - Critical",
  P1_HIGH = "P1 - High",
  P2_MEDIUM = "P2 - Medium",
  P3_LOW = "P3 - Low",
  P4_BACKLOG = "P4 - Backlog"
}

// Prioritization examples
const prioritizedStories: StoryPrioritization[] = [
  {
    id: "PROJ-001",
    title: "User Authentication System",
    businessValue: 95,
    implementationEffort: 13,
    riskLevel: "medium",
    priority: Priority.P0_CRITICAL,
    quadrant: "major_projects",
    recommendedAction: {
      timeline: "Sprint 1-3",
      rationale: "Foundation for all user-centric features",
      prerequisites: ["Security audit", "Architecture review"],
      success_criteria: ["99.9% uptime", "2FA support", "OAuth integration"]
    }
  },
  {
    id: "PROJ-002",
    title: "Enhanced Error Messages",
    businessValue: 70,
    implementationEffort: 3,
    riskLevel: "low",
    priority: Priority.P1_HIGH,
    quadrant: "quick_wins",
    recommendedAction: {
      timeline: "Sprint 1",
      rationale: "High user satisfaction impact with minimal effort",
      prerequisites: ["UX review", "Content guidelines"],
      success_criteria: ["Reduced support tickets by 30%"]
    }
  }
];
```

### MoSCoW Method with Timeline Integration

**Release Planning Integration:**
```typescript
interface MoSCoWPrioritization {
  mustHave: {
    stories: UserStory[];
    business_justification: string;
    release_blocker: boolean;
    estimated_effort: number;
    dependencies: string[];
  };

  shouldHave: {
    stories: UserStory[];
    value_proposition: string;
    fallback_plan: string;
    effort_threshold: number;
  };

  couldHave: {
    stories: UserStory[];
    opportunity_cost: string;
    time_permitting: boolean;
    future_release_candidate: boolean;
  };

  wontHave: {
    stories: UserStory[];
    exclusion_rationale: string;
    future_consideration: boolean;
    stakeholder_communication: string;
  };
}
```

## 📝 Story Writing Excellence Framework

### INVEST+ Criteria (Enhanced)

**INVEST Criteria with Modern Extensions:**
```typescript
interface StoryQuality {
  independent: {
    criteria: "Can be developed and deployed separately";
    validation: "No blocking dependencies on other stories";
    score: number; // 1-10
  };

  negotiable: {
    criteria: "Details can be discussed and refined";
    validation: "Acceptance criteria allow for implementation flexibility";
    score: number;
  };

  valuable: {
    criteria: "Delivers clear user or business value";
    validation: "Measurable impact on user experience or business metrics";
    score: number;
  };

  estimable: {
    criteria: "Development effort can be reasonably estimated";
    validation: "Team has enough information for planning poker";
    score: number;
  };

  small: {
    criteria: "Fits within a sprint timeframe";
    validation: "Can be completed by one developer in 1-2 weeks";
    score: number;
  };

  testable: {
    criteria: "Clear acceptance criteria for validation";
    validation: "Automated and manual testing strategies defined";
    score: number;
  };

  // Modern extensions
  accessible: {
    criteria: "Considers accessibility requirements";
    validation: "WCAG compliance and inclusive design";
    score: number;
  };

  secure: {
    criteria: "Security implications assessed";
    validation: "Authentication, authorization, data protection considered";
    score: number;
  };

  performant: {
    criteria: "Performance requirements specified";
    validation: "Response time, throughput, scalability defined";
    score: number;
  };
}
```

### Comprehensive Story Templates

**API Development Story:**
```markdown
## User Story: RESTful User Profile API

### Story Details
**As a** frontend developer
**I want** a RESTful API for user profile management
**So that** I can build responsive user interfaces with reliable data access

### API Specification
**Endpoints:**
- GET /api/v1/users/{id}/profile - Retrieve user profile
- PUT /api/v1/users/{id}/profile - Update user profile
- PATCH /api/v1/users/{id}/profile - Partial profile updates
- DELETE /api/v1/users/{id}/profile - Deactivate profile

### Acceptance Criteria

**Scenario: Successful profile retrieval**
```json
Given a user with ID "12345" exists
When I send GET request to "/api/v1/users/12345/profile"
Then I receive HTTP 200 response
And the response body contains:
{
  "id": "12345",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "profileImage": "https://cdn.example.com/profiles/12345.jpg",
  "lastUpdated": "2025-09-13T10:30:00Z"
}
```

**Scenario: Profile update validation**
```json
Given I am authenticated as user "12345"
When I send PUT request to "/api/v1/users/12345/profile"
With invalid email format in request body
Then I receive HTTP 400 response
And the response contains validation errors
```

### Technical Requirements
- **Authentication:** JWT token required for all operations
- **Authorization:** Users can only access their own profiles
- **Rate Limiting:** 100 requests per minute per user
- **Caching:** Profile data cached for 5 minutes
- **Monitoring:** API response time metrics tracked
```

**Frontend Component Story:**
```markdown
## User Story: Responsive User Profile Component

### Story Details
**As a** end user
**I want** a responsive profile editing interface
**So that** I can manage my account information on any device

### Component Specifications
**Framework:** React with TypeScript
**Styling:** Styled-components with responsive breakpoints
**Validation:** React Hook Form with Zod schema validation
**State Management:** React Query for server state

### Acceptance Criteria

**Scenario: Mobile responsive design**
```typescript
Given I access the profile component on a mobile device (320px width)
When the component renders
Then all form fields are properly stacked vertically
And touch targets are at least 44px in height
And text is readable without horizontal scrolling
```

**Scenario: Real-time validation**
```typescript
Given I am editing my email address
When I enter an invalid email format
Then I see an inline error message immediately
And the save button remains disabled
And the error message is accessible to screen readers
```

### Implementation Details
```typescript
interface ProfileComponentProps {
  userId: string;
  initialData?: UserProfile;
  onSave: (data: UserProfile) => Promise<void>;
  onCancel: () => void;
}

interface UserProfile {
  firstName: string;
  lastName: string;
  email: string;
  phoneNumber?: string;
  profileImage?: File;
  preferences: UserPreferences;
}
```
```

## 🎯 Advanced Backlog Management

### Dynamic Backlog Organization

**Backlog Structure with Automation:**
```typescript
interface ProductBacklog {
  epics: Epic[];
  features: Feature[];
  stories: UserStory[];
  technical_debt: TechnicalDebtItem[];
  bugs: BugReport[];

  organization: {
    by_priority: Story[];
    by_epic: Record<string, Story[]>;
    by_sprint_readiness: Record<ReadinessLevel, Story[]>;
    by_team: Record<string, Story[]>;
  };

  automation_rules: {
    priority_refresh: "Daily based on business metrics";
    dependency_tracking: "Automatic validation of story dependencies";
    effort_estimation: "Planning poker integration";
    progress_tracking: "Real-time story status updates";
  };
}

enum ReadinessLevel {
  READY = "Ready for development",
  NEEDS_REFINEMENT = "Requires additional details",
  BLOCKED = "Dependencies not met",
  IN_REVIEW = "Stakeholder review pending"
}
```

### Story Lifecycle with Metrics

**Comprehensive Story Tracking:**
```typescript
interface StoryLifecycle {
  stages: {
    ideation: {
      timestamp: Date;
      source: "stakeholder" | "user_feedback" | "technical_debt" | "competitive_analysis";
      initial_value_estimate: number;
    };

    definition: {
      timestamp: Date;
      author: string;
      acceptance_criteria_count: number;
      stakeholder_reviews: Review[];
    };

    estimation: {
      timestamp: Date;
      story_points: number;
      estimation_method: "planning_poker" | "t_shirt_sizing" | "expert_judgment";
      confidence_level: number; // 1-10
    };

    development: {
      start_date: Date;
      developer_assigned: string;
      progress_updates: ProgressUpdate[];
      blockers_encountered: Blocker[];
    };

    testing: {
      test_cases_created: number;
      automated_tests_coverage: number;
      manual_testing_completed: boolean;
      defects_found: DefectReport[];
    };

    delivery: {
      completion_date: Date;
      actual_effort: number;
      user_acceptance: boolean;
      business_value_realized: number;
    };
  };

  metrics: {
    cycle_time: number; // days from ready to done
    effort_variance: number; // actual vs estimated
    defect_density: number; // defects per story point
    user_satisfaction: number; // post-delivery feedback
  };
}
```

## 🤝 Cross-Functional Collaboration Framework

### Stakeholder Integration Workflows

**Business Analyst Collaboration:**
```typescript
interface BACollaboration {
  requirements_validation: {
    process: "Joint story review sessions";
    frequency: "Weekly during sprint planning";
    deliverables: ["Requirements traceability matrix", "Business rules documentation"];
  };

  acceptance_criteria_refinement: {
    process: "Collaborative AC writing workshops";
    participants: ["Product Manager", "Business Analyst", "UX Designer", "Tech Lead"];
    output: "Refined and validated acceptance criteria";
  };

  business_process_alignment: {
    validation_method: "Story walkthrough against current state processes";
    documentation: "Process impact assessment for each story";
    approval_required: boolean;
  };
}
```

**UX Designer Integration:**
```typescript
interface UXCollaboration {
  design_system_alignment: {
    component_mapping: "Map stories to design system components";
    new_component_identification: "Flag stories requiring new design patterns";
    accessibility_review: "WCAG compliance assessment for each story";
  };

  user_journey_validation: {
    journey_mapping: "Align stories with user journey touchpoints";
    usability_requirements: "Define usability acceptance criteria";
    prototype_validation: "User testing requirements for complex stories";
  };

  design_handoff_process: {
    design_assets: "Required design deliverables per story";
    developer_collaboration: "Design-development review checkpoints";
    implementation_validation: "Design QA process for delivered stories";
  };
}
```

### Development Team Integration

**Technical Feasibility Assessment:**
```typescript
interface TechnicalFeasibility {
  architecture_impact: {
    system_changes: "Required modifications to existing architecture";
    new_dependencies: "Additional libraries or services needed";
    performance_implications: "Expected impact on system performance";
    security_considerations: "Security review requirements";
  };

  implementation_approach: {
    technical_strategy: "High-level implementation approach";
    alternative_solutions: "Other possible implementation methods";
    proof_of_concept_needed: boolean;
    spike_story_required: boolean;
  };

  testing_strategy: {
    unit_testing_approach: "Unit test requirements and coverage targets";
    integration_testing: "Integration test scenarios";
    end_to_end_testing: "E2E test automation requirements";
    performance_testing: "Load and performance test needs";
  };
}
```

## 📊 Success Metrics and KPI Framework

### Story-Level Metrics

**Individual Story Performance:**
```typescript
interface StoryMetrics {
  delivery_metrics: {
    cycle_time: number; // hours from start to done
    effort_accuracy: number; // actual vs estimated effort ratio
    first_time_quality: number; // stories delivered without defects
    acceptance_rate: number; // stakeholder acceptance percentage
  };

  business_impact: {
    user_adoption: number; // feature usage after delivery
    business_value_realization: number; // actual vs predicted value
    user_satisfaction_score: number; // post-delivery user feedback
    support_ticket_impact: number; // change in support volume
  };

  technical_quality: {
    code_coverage: number; // automated test coverage percentage
    technical_debt_introduced: number; // code quality metrics
    performance_impact: number; // system performance changes
    security_issues: number; // security vulnerabilities introduced
  };
}
```

**Portfolio-Level Analytics:**
```typescript
interface BacklogAnalytics {
  velocity_trends: {
    story_points_per_sprint: number[];
    story_completion_rate: number[];
    epic_progression_rate: number;
    release_predictability: number;
  };

  value_delivery: {
    business_value_per_sprint: number[];
    user_satisfaction_trends: number[];
    feature_adoption_rates: Record<string, number>;
    revenue_impact_attribution: Record<string, number>;
  };

  process_efficiency: {
    story_refinement_effectiveness: number;
    estimation_accuracy_trends: number[];
    defect_prevention_rate: number;
    stakeholder_engagement_score: number;
  };
}
```

## 📤 Comprehensive Deliverables

**Product Backlog Documentation:**
- **Prioritized User Stories** with detailed acceptance criteria
- **Epic Roadmap** with business value alignment
- **Sprint Planning Materials** with ready-to-develop stories
- **Stakeholder Communication Plan** with regular update schedules
- **Success Metrics Dashboard** with real-time progress tracking

**Story Development Artifacts:**
- **User Story Templates** adapted to project context
- **Acceptance Criteria Standards** with BDD format examples
- **Definition of Done Checklists** for quality assurance
- **Prioritization Framework** with weighted scoring models
- **Collaboration Workflows** with cross-functional team integration

**Process Documentation:**
- **Backlog Management Procedures** with automation guidelines
- **Story Lifecycle Tracking** with metrics collection
- **Stakeholder Engagement Protocols** with feedback integration
- **Quality Assurance Standards** with testing requirements
- **Continuous Improvement Framework** with retrospective insights

---

## Transition to Development

**Next Steps:**
Based on the prioritized user stories and defined acceptance criteria, consider switching to specialized chatmodes for implementation:

- Switch to **software-architect** chatmode to design technical solutions supporting the highest priority stories
- Switch to **ux-designer** chatmode to create user experience designs for user-facing stories
- Switch to **backend-engineer** chatmode to implement API and data layer stories
- Switch to **frontend-engineer** chatmode to develop user interface components and interactions

*Strategic user story creation and prioritization ensure development teams deliver maximum value through clear requirements, measurable outcomes, and continuous stakeholder alignment.*