---
name: existing-project-integration
description: Safely integrate GitHub Copilot framework into existing projects with intelligent analysis and non-disruptive setup
tools: [github-copilot, file-analysis, project-detection, configuration-generation]
model: github-copilot
context_adaptation: true
---

# GitHub Copilot Framework Integration for Existing Projects

## Context Analysis Framework

This prompt automatically reads and adapts to your project context by analyzing:

```markdown
## Project Context Detection
1. Read `copilot.instructions.md` for framework specifications
2. Analyze existing project structure and technology stack
3. Detect current development workflows and tooling
4. Identify business domain and development stage
5. Map existing patterns to Copilot chatmode ecosystem
```

## Technology Detection & Adaptation

### Automatic Technology Stack Discovery

```typescript
// Frontend Framework Detection
const detectFrontend = () => {
  if (packageJson.dependencies?.react) return 'React + TypeScript';
  if (packageJson.dependencies?.['@angular/core']) return 'Angular + TypeScript';
  if (packageJson.dependencies?.vue) return 'Vue.js + TypeScript';
  return 'Vanilla JavaScript/TypeScript';
};

// Backend Framework Detection
const detectBackend = () => {
  if (packageJson.dependencies?.express) return 'Node.js + Express';
  if (files.includes('requirements.txt') && files.includes('main.py')) return 'Python + FastAPI';
  if (files.includes('pom.xml')) return 'Java + Spring Boot';
  if (files.includes('*.csproj')) return '.NET Core';
  if (files.includes('go.mod')) return 'Go';
  if (files.includes('Cargo.toml')) return 'Rust';
  return 'Custom Backend';
};
```

### Multi-Language Integration Patterns

#### React/TypeScript Projects
```typescript
// Copilot integration for React projects
interface CopilotConfig {
  framework: 'react';
  typescript: true;
  stateManagement: 'redux' | 'zustand' | 'context';
  testing: 'jest' | 'vitest';
  styling: 'tailwind' | 'styled-components' | 'css-modules';
}

const generateReactCopilotConfig = (project: ProjectAnalysis): CopilotConfig => ({
  framework: 'react',
  typescript: project.hasTypeScript,
  stateManagement: detectStateManagement(project),
  testing: detectTestFramework(project),
  styling: detectStylingApproach(project)
});
```

#### Python/FastAPI Projects
```python
# Copilot configuration for Python projects
from typing import Dict, Any, Optional
from pydantic import BaseModel

class CopilotPythonConfig(BaseModel):
    framework: str = "fastapi"
    async_support: bool = True
    database_orm: Optional[str] = None
    testing_framework: str = "pytest"
    code_formatter: str = "black"
    type_checking: str = "mypy"

    @classmethod
    def from_project_analysis(cls, project_path: str) -> "CopilotPythonConfig":
        """Generate Copilot config from existing Python project analysis"""
        return cls(
            database_orm=detect_orm(project_path),
            testing_framework=detect_test_framework(project_path),
            code_formatter=detect_formatter(project_path)
        )
```

#### Java/Spring Boot Projects
```java
// Copilot configuration for Java projects
@Configuration
@EnableCopilotIntegration
public class CopilotProjectConfig {

    @Bean
    public CopilotConfiguration copilotConfig() {
        return CopilotConfiguration.builder()
            .framework("spring-boot")
            .javaVersion(detectJavaVersion())
            .buildTool(detectBuildTool()) // maven/gradle
            .testFramework("junit5")
            .persistenceLayer(detectJpaProvider())
            .securityFramework("spring-security")
            .build();
    }

    private String detectBuildTool() {
        return Files.exists(Paths.get("pom.xml")) ? "maven" : "gradle";
    }
}
```

#### .NET Core Projects
```csharp
// Copilot integration for .NET projects
public class CopilotDotNetConfig
{
    public string Framework { get; set; } = "dotnet-core";
    public string TargetFramework { get; set; }
    public string DatabaseProvider { get; set; }
    public string TestingFramework { get; set; } = "xunit";
    public bool UseMinimalApis { get; set; }

    public static CopilotDotNetConfig FromProjectAnalysis(string projectPath)
    {
        var csprojContent = File.ReadAllText(Directory.GetFiles(projectPath, "*.csproj").First());

        return new CopilotDotNetConfig
        {
            TargetFramework = ExtractTargetFramework(csprojContent),
            DatabaseProvider = DetectEntityFrameworkProvider(csprojContent),
            UseMinimalApis = DetectMinimalApis(projectPath)
        };
    }
}
```

## Core Implementation Patterns

### 1. Safe Project Analysis Engine

```typescript
interface ProjectAnalysis {
  structure: ProjectStructure;
  technology: TechnologyStack;
  businessContext: BusinessContext;
  existingTooling: ExistingTooling;
  integrationStrategy: IntegrationStrategy;
}

class ExistingProjectAnalyzer {
  async analyzeProject(projectPath: string): Promise<ProjectAnalysis> {
    const structure = await this.analyzeStructure(projectPath);
    const technology = await this.detectTechnologyStack(projectPath);
    const businessContext = await this.extractBusinessContext(projectPath);
    const existingTooling = await this.assessExistingTooling(projectPath);

    return {
      structure,
      technology,
      businessContext,
      existingTooling,
      integrationStrategy: this.generateIntegrationStrategy({
        structure, technology, businessContext, existingTooling
      })
    };
  }

  private async analyzeStructure(projectPath: string): Promise<ProjectStructure> {
    return {
      rootDirectories: await this.discoverDirectories(projectPath),
      entryPoints: await this.findEntryPoints(projectPath),
      configFiles: await this.findConfigurationFiles(projectPath),
      buildSystem: await this.detectBuildSystem(projectPath)
    };
  }
}
```

### 2. Non-Disruptive Integration System

```typescript
class CopilotIntegrationManager {
  async integrateFramework(analysis: ProjectAnalysis): Promise<IntegrationResult> {
    // Step 1: Validate integration safety
    const safetyCheck = await this.performSafetyCheck(analysis);
    if (!safetyCheck.isSafe) {
      throw new Error(`Integration blocked: ${safetyCheck.risks.join(', ')}`);
    }

    // Step 2: Generate copilot.instructions.md
    const instructions = await this.generateCopilotInstructions(analysis);

    // Step 3: Set up chatmode configurations
    const chatmodeConfig = await this.setupChatmodeConfigurations(analysis);

    // Step 4: Create GitHub integrations
    const githubIntegrations = await this.setupGitHubIntegrations(analysis);

    return {
      instructions,
      chatmodeConfig,
      githubIntegrations,
      adoptionRoadmap: this.generateAdoptionRoadmap(analysis)
    };
  }

  private async performSafetyCheck(analysis: ProjectAnalysis): Promise<SafetyCheck> {
    return {
      isSafe: true,
      risks: [],
      recommendations: [
        'Integration will only add configuration files',
        'No existing code will be modified',
        'All existing workflows will be preserved'
      ]
    };
  }
}
```

## GitHub Integration Points

### 1. GitHub Actions Workflow Integration

```yaml
# .github/workflows/copilot-integration.yml
name: GitHub Copilot Framework Integration

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  copilot-analysis:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run Copilot Project Analysis
        run: |
          # Analyze project structure and generate insights
          npx @github/copilot-cli analyze-project

      - name: Generate Copilot Suggestions
        run: |
          # Generate context-aware code suggestions
          npx @github/copilot-cli generate-suggestions

  integration-validation:
    runs-on: ubuntu-latest
    needs: copilot-analysis
    steps:
      - name: Validate Copilot Configuration
        run: |
          # Ensure copilot.instructions.md is valid
          npx @github/copilot-cli validate-config
```

### 2. GitHub Issues & Projects Integration

```typescript
// GitHub integration for project management
interface GitHubCopilotIntegration {
  issues: {
    autoLabeling: boolean;
    chatmodeAssignment: boolean;
    codeGenerationTriggers: boolean;
  };
  pullRequests: {
    copilotReviews: boolean;
    codeQualityChecks: boolean;
    suggestionGeneration: boolean;
  };
  projects: {
    automaticTaskCreation: boolean;
    progressTracking: boolean;
    chatmodeWorkflows: boolean;
  };
}

const setupGitHubIntegration = (projectAnalysis: ProjectAnalysis): GitHubCopilotIntegration => ({
  issues: {
    autoLabeling: true,
    chatmodeAssignment: true,
    codeGenerationTriggers: projectAnalysis.technology.supportsAutomation
  },
  pullRequests: {
    copilotReviews: true,
    codeQualityChecks: true,
    suggestionGeneration: true
  },
  projects: {
    automaticTaskCreation: projectAnalysis.businessContext.hasProjectManagement,
    progressTracking: true,
    chatmodeWorkflows: true
  }
});
```

## Code Generation Templates

### 1. Copilot Instructions Generator

```typescript
interface CopilotInstructionsTemplate {
  projectMetadata: ProjectMetadata;
  technologyStack: TechnologyStackConfig;
  chatmodeConfiguration: ChatmodeConfig;
  integrationPoints: IntegrationConfig;
}

class CopilotInstructionsGenerator {
  generateInstructions(analysis: ProjectAnalysis): string {
    const template = `
# ${analysis.businessContext.projectName} - GitHub Copilot Instructions

## 0. Project Metadata
- **project_name**: ${analysis.businessContext.projectName}
- **project_description**: ${analysis.businessContext.description}
- **primary_language**: ${analysis.technology.primaryLanguage}
- **business_domain**: ${analysis.businessContext.domain}
- **project_scale**: ${analysis.businessContext.scale}
- **development_stage**: ${analysis.businessContext.stage}

## 1. Technology Stack Configuration
${this.generateTechnologyConfig(analysis.technology)}

## 2. Chatmode Ecosystem
${this.generateChatmodeConfig(analysis)}

## 3. GitHub Integration
${this.generateGitHubIntegration(analysis)}

## 4. Development Standards
${this.generateDevelopmentStandards(analysis)}
    `;

    return template.trim();
  }
}
```

### 2. Chatmode Configuration Templates

```typescript
// React project chatmode configuration
const reactChatmodeConfig = {
  'frontend-engineer': {
    context: {
      framework: 'React',
      typescript: true,
      stateManagement: 'Redux Toolkit',
      testing: 'Jest + React Testing Library',
      styling: 'Tailwind CSS'
    },
    tools: ['copilot-code-completion', 'react-devtools', 'typescript-language-server'],
    integrations: ['github-issues', 'github-actions', 'storybook']
  },

  'backend-engineer': {
    context: {
      framework: 'Node.js + Express',
      database: 'PostgreSQL',
      orm: 'Prisma',
      testing: 'Jest + Supertest',
      authentication: 'JWT'
    },
    tools: ['copilot-code-completion', 'nodejs-debugger', 'prisma-studio'],
    integrations: ['github-actions', 'database-migrations', 'api-documentation']
  }
};
```

## Quality Gates & Standards

### 1. Integration Safety Validation

```typescript
interface SafetyValidation {
  structuralIntegrity: boolean;
  configurationSafety: boolean;
  workflowPreservation: boolean;
  rollbackCapability: boolean;
}

class IntegrationSafetyValidator {
  async validateIntegration(projectPath: string): Promise<SafetyValidation> {
    return {
      structuralIntegrity: await this.checkStructuralIntegrity(projectPath),
      configurationSafety: await this.validateConfigurationSafety(projectPath),
      workflowPreservation: await this.ensureWorkflowPreservation(projectPath),
      rollbackCapability: await this.verifyRollbackCapability(projectPath)
    };
  }

  private async checkStructuralIntegrity(projectPath: string): Promise<boolean> {
    // Ensure no existing files are modified
    const existingFiles = await this.getExistingFiles(projectPath);
    const plannedChanges = await this.getPlannedChanges(projectPath);

    return !plannedChanges.some(change =>
      change.type === 'modify' && existingFiles.includes(change.path)
    );
  }
}
```

### 2. Code Quality Standards

```typescript
interface CopilotQualityStandards {
  codeGeneration: CodeGenerationStandards;
  documentation: DocumentationStandards;
  testing: TestingStandards;
  security: SecurityStandards;
}

const copilotQualityStandards: CopilotQualityStandards = {
  codeGeneration: {
    typeSafety: 'strict',
    errorHandling: 'comprehensive',
    performanceOptimized: true,
    productionReady: true
  },
  documentation: {
    inlineComments: 'contextual',
    apiDocumentation: 'automatic',
    typeDocumentation: 'complete',
    exampleUsage: 'included'
  },
  testing: {
    unitTestCoverage: 'minimum-80-percent',
    integrationTests: 'critical-paths',
    e2eTests: 'user-workflows',
    testDocumentation: 'comprehensive'
  },
  security: {
    inputValidation: 'strict',
    outputSanitization: 'automatic',
    authenticationPatterns: 'secure-defaults',
    encryptionStandards: 'industry-standard'
  }
};
```

## Transition Guidance

### From Analysis to Implementation
```markdown
After completing project analysis, transition to appropriate chatmode:

**For Architecture Changes**: Switch to `software-architect` chatmode
**For Security Review**: Switch to `security-engineer` chatmode
**For Code Quality**: Switch to `qa-engineer` chatmode
**For Documentation**: Switch to `business-analyst` chatmode
**For Deployment Setup**: Switch to `deployment-engineer` chatmode
```

### Chatmode Integration Workflow
```typescript
const integrationWorkflow = {
  phase1: {
    chatmode: 'business-analyst',
    focus: 'Requirements analysis and documentation',
    deliverables: ['Project analysis report', 'Integration strategy']
  },
  phase2: {
    chatmode: 'software-architect',
    focus: 'Architecture validation and optimization',
    deliverables: ['Architecture review', 'Integration architecture']
  },
  phase3: {
    chatmode: 'security-engineer',
    focus: 'Security assessment and compliance',
    deliverables: ['Security audit', 'Compliance validation']
  },
  phase4: {
    chatmode: 'deployment-engineer',
    focus: 'CI/CD and GitHub Actions integration',
    deliverables: ['GitHub workflows', 'Deployment automation']
  }
};
```

## Examples & Use Cases

### Example 1: Large React Enterprise Application

```bash
# Project Structure
/enterprise-react-app
├── src/
│   ├── components/
│   ├── pages/
│   ├── services/
│   └── utils/
├── __tests__/
├── .github/workflows/
├── package.json
└── tsconfig.json

# Generated Copilot Configuration
# Focus: Enterprise patterns, performance, accessibility
# Chatmodes: frontend-engineer, security-engineer, qa-engineer
# Integration: GitHub Actions, Issue tracking, Code review
```

### Example 2: Python FastAPI Microservice

```bash
# Project Structure
/python-microservice
├── app/
│   ├── api/
│   ├── core/
│   ├── db/
│   └── models/
├── tests/
├── requirements.txt
├── docker-compose.yml
└── Dockerfile

# Generated Copilot Configuration
# Focus: API design, async patterns, container deployment
# Chatmodes: backend-engineer, api-engineer, deployment-engineer
# Integration: Docker builds, API testing, Documentation
```

### Example 3: Full-Stack Java Spring Boot + Angular

```bash
# Project Structure
/fullstack-java-app
├── backend/
│   ├── src/main/java/
│   ├── src/test/java/
│   └── pom.xml
├── frontend/
│   ├── src/app/
│   ├── src/assets/
│   └── package.json
└── docker/

# Generated Copilot Configuration
# Focus: Enterprise Java patterns, Angular best practices
# Chatmodes: backend-engineer, frontend-engineer, data-engineer
# Integration: Maven builds, Angular CLI, E2E testing
```

## Integration Execution Process

### Step 1: Initial Analysis
```typescript
// Run comprehensive project analysis
const analysis = await analyzeExistingProject('./');
console.log('Project Analysis Complete:', {
  technology: analysis.technology.stack,
  complexity: analysis.metrics.complexity,
  readiness: analysis.integration.readiness
});
```

### Step 2: Safety Validation
```typescript
// Validate integration safety
const safety = await validateIntegrationSafety(analysis);
if (!safety.isSafe) {
  throw new Error(`Integration blocked: ${safety.risks.join(', ')}`);
}
```

### Step 3: Configuration Generation
```typescript
// Generate copilot.instructions.md
const instructions = await generateCopilotInstructions(analysis);
await writeFile('./copilot.instructions.md', instructions);

// Set up GitHub integration
await setupGitHubIntegration(analysis);
```

### Step 4: Adoption Roadmap
```markdown
## Immediate Actions (Week 1)
- [ ] Review generated copilot.instructions.md
- [ ] Test basic chatmode functionality
- [ ] Validate GitHub integrations

## Short-term Goals (Month 1)
- [ ] Integrate with existing development workflow
- [ ] Train team on chatmode usage patterns
- [ ] Establish code generation standards

## Long-term Integration (Quarter 1)
- [ ] Full chatmode ecosystem adoption
- [ ] Advanced GitHub Copilot features
- [ ] Team productivity optimization
```

This prompt provides comprehensive, safe integration of the GitHub Copilot framework into existing projects while preserving all existing functionality and workflows.