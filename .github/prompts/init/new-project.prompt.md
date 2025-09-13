---
name: new-project-initialization
description: Initialize new projects with GitHub Copilot framework, intelligent setup, and technology-adaptive configuration
tools: [github-copilot, project-scaffolding, configuration-generation, github-integration]
model: github-copilot
context_adaptation: true
---

# GitHub Copilot Framework - New Project Initialization

## Context Analysis Framework

This prompt automatically analyzes your development context and creates optimal project setup:

```markdown
## Intelligent Project Analysis
1. Read `copilot.instructions.md` for framework specifications
2. Detect existing project artifacts (package.json, requirements.txt, etc.)
3. Analyze current directory structure and development environment
4. Identify preferred technology patterns and conventions
5. Map requirements to optimal Copilot chatmode ecosystem
```

## Technology Detection & Adaptation

### Smart Technology Stack Detection

```typescript
// Automatic language and framework detection
interface TechnologyPreferences {
  primaryLanguage: string;
  framework: string;
  database: string;
  deployment: string;
  testing: string;
}

class ProjectTechnologyDetector {
  detectFromEnvironment(): TechnologyPreferences {
    const nodeVersion = process.env.NODE_VERSION;
    const pythonVersion = process.env.PYTHON_VERSION;
    const javaHome = process.env.JAVA_HOME;
    const dotnetVersion = process.env.DOTNET_VERSION;

    return {
      primaryLanguage: this.detectPrimaryLanguage(),
      framework: this.detectPreferredFramework(),
      database: this.detectDatabasePreference(),
      deployment: this.detectDeploymentPreference(),
      testing: this.detectTestingFramework()
    };
  }

  private detectPrimaryLanguage(): string {
    if (fs.existsSync('package.json')) return 'typescript';
    if (fs.existsSync('requirements.txt') || fs.existsSync('pyproject.toml')) return 'python';
    if (fs.existsSync('pom.xml') || fs.existsSync('build.gradle')) return 'java';
    if (fs.existsSync('*.csproj') || fs.existsSync('*.sln')) return 'csharp';
    if (fs.existsSync('go.mod')) return 'go';
    if (fs.existsSync('Cargo.toml')) return 'rust';
    return 'typescript'; // default
  }
}
```

### Multi-Language Project Templates

#### TypeScript/React Enterprise Template
```typescript
// Modern React + TypeScript project structure
const reactEnterpriseTemplate = {
  structure: {
    'src/': {
      'components/': 'Reusable UI components',
      'pages/': 'Route-based page components',
      'hooks/': 'Custom React hooks',
      'services/': 'API services and business logic',
      'types/': 'TypeScript type definitions',
      'utils/': 'Utility functions and helpers',
      '__tests__/': 'Component and integration tests'
    },
    'public/': 'Static assets',
    '.github/': 'GitHub workflows and templates',
    'docs/': 'Project documentation'
  },
  dependencies: {
    react: '^18.2.0',
    '@typescript-eslint/parser': '^6.0.0',
    tailwindcss: '^3.3.0',
    '@tanstack/react-query': '^4.32.0',
    zustand: '^4.4.1'
  },
  copilotConfig: {
    chatmodes: ['frontend-engineer', 'ux-designer', 'qa-engineer'],
    tools: ['react-devtools', 'typescript-language-server'],
    integrations: ['github-actions', 'vercel', 'storybook']
  }
};
```

#### Python/FastAPI Microservice Template
```python
# FastAPI + Python project structure
fastapi_template = {
    "structure": {
        "app/": {
            "api/": "API routes and endpoints",
            "core/": "Core application configuration",
            "db/": "Database models and connections",
            "services/": "Business logic services",
            "schemas/": "Pydantic models for API",
            "utils/": "Utility functions",
            "tests/": "Unit and integration tests"
        },
        "migrations/": "Database migrations",
        "scripts/": "Development and deployment scripts",
        ".github/": "GitHub workflows",
        "docs/": "API documentation"
    },
    "dependencies": {
        "fastapi": "^0.104.0",
        "uvicorn": "^0.24.0",
        "sqlalchemy": "^2.0.0",
        "alembic": "^1.12.0",
        "pytest": "^7.4.0",
        "pytest-asyncio": "^0.21.0"
    },
    "copilot_config": {
        "chatmodes": ["backend-engineer", "api-engineer", "data-engineer"],
        "tools": ["python-language-server", "sqlalchemy-devtools"],
        "integrations": ["github-actions", "docker", "postgresql"]
    }
}
```

#### Java/Spring Boot Enterprise Template
```java
// Spring Boot enterprise project structure
@Component
public class SpringBootEnterpriseTemplate {

    private final ProjectStructure structure = ProjectStructure.builder()
        .sourceDirectory("src/main/java/com/company/project")
        .testDirectory("src/test/java/com/company/project")
        .resourcesDirectory("src/main/resources")
        .addPackage("controller", "REST API controllers")
        .addPackage("service", "Business logic services")
        .addPackage("repository", "Data access layer")
        .addPackage("model", "Entity models")
        .addPackage("config", "Configuration classes")
        .addPackage("dto", "Data transfer objects")
        .build();

    private final CopilotConfiguration copilotConfig = CopilotConfiguration.builder()
        .addChatmode("backend-engineer")
        .addChatmode("api-engineer")
        .addChatmode("security-engineer")
        .addTool("spring-boot-devtools")
        .addTool("java-language-server")
        .addIntegration("github-actions")
        .addIntegration("maven")
        .addIntegration("docker")
        .build();
}
```

#### .NET Core Web API Template
```csharp
// .NET Core Web API project structure
public class DotNetCoreWebApiTemplate
{
    public ProjectStructure Structure { get; } = new()
    {
        SourceDirectory = "src/",
        TestDirectory = "tests/",
        Directories = new Dictionary<string, string>
        {
            ["Controllers/"] = "API controllers",
            ["Services/"] = "Business logic services",
            ["Models/"] = "Data models and entities",
            ["DTOs/"] = "Data transfer objects",
            ["Repositories/"] = "Data access layer",
            ["Configuration/"] = "App configuration",
            ["Middleware/"] = "Custom middleware"
        }
    };

    public CopilotConfiguration CopilotConfig { get; } = new()
    {
        Chatmodes = ["backend-engineer", "api-engineer", "security-engineer"],
        Tools = ["omnisharp", "dotnet-cli", "entity-framework-tools"],
        Integrations = ["github-actions", "nuget", "azure-devops"]
    };
}
```

## Core Implementation Patterns

### 1. Intelligent Project Initialization Engine

```typescript
interface ProjectInitializationRequest {
  projectName: string;
  primaryLanguage: string;
  businessDomain: string;
  projectScale: 'startup' | 'sme' | 'enterprise';
  specialRequirements?: string[];
  githubIntegration: boolean;
  deploymentTarget?: string;
}

class GitHubCopilotProjectInitializer {
  async initializeProject(request: ProjectInitializationRequest): Promise<ProjectSetup> {
    // Step 1: Analyze context and preferences
    const context = await this.analyzeContext();

    // Step 2: Generate technology-specific template
    const template = await this.generateProjectTemplate(request, context);

    // Step 3: Create copilot.instructions.md
    const instructions = await this.generateCopilotInstructions(request, template);

    // Step 4: Set up GitHub integration
    const githubSetup = await this.setupGitHubIntegration(request);

    // Step 5: Initialize development environment
    const devEnvironment = await this.setupDevelopmentEnvironment(template);

    return {
      template,
      instructions,
      githubSetup,
      devEnvironment,
      readyForDevelopment: true
    };
  }

  private async generateProjectTemplate(
    request: ProjectInitializationRequest,
    context: ProjectContext
  ): Promise<ProjectTemplate> {
    const templateGenerator = this.getTemplateGenerator(request.primaryLanguage);
    return templateGenerator.generate(request, context);
  }
}
```

### 2. GitHub Integration Setup Engine

```typescript
class GitHubIntegrationSetup {
  async setupGitHubIntegration(project: ProjectInitializationRequest): Promise<GitHubSetup> {
    return {
      workflows: await this.generateWorkflows(project),
      issueTemplates: await this.generateIssueTemplates(project),
      prTemplates: await this.generatePRTemplates(project),
      codeowners: await this.generateCodeowners(project),
      dependabot: await this.setupDependabot(project),
      copilotConfiguration: await this.setupCopilotConfiguration(project)
    };
  }

  private async generateWorkflows(project: ProjectInitializationRequest): Promise<GitHubWorkflow[]> {
    const workflows = [
      this.generateCIWorkflow(project),
      this.generateCDWorkflow(project),
      this.generateCodeQualityWorkflow(project),
      this.generateSecurityWorkflow(project)
    ];

    return workflows.filter(Boolean);
  }

  private generateCIWorkflow(project: ProjectInitializationRequest): GitHubWorkflow {
    const languageConfig = this.getLanguageConfig(project.primaryLanguage);

    return {
      name: 'CI Pipeline',
      on: ['push', 'pull_request'],
      jobs: {
        test: {
          'runs-on': 'ubuntu-latest',
          steps: [
            { uses: 'actions/checkout@v4' },
            languageConfig.setupAction,
            { run: languageConfig.installCommand },
            { run: languageConfig.testCommand },
            { run: languageConfig.lintCommand }
          ]
        }
      }
    };
  }
}
```

## GitHub Integration Points

### 1. Advanced GitHub Actions Integration

```yaml
# .github/workflows/copilot-enhanced-ci.yml
name: GitHub Copilot Enhanced CI/CD

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

      - name: Setup GitHub Copilot Environment
        run: |
          # Configure Copilot for CI environment
          gh copilot config set --context ci-environment

      - name: Generate Code Analysis
        run: |
          # Use Copilot to analyze code quality and suggest improvements
          gh copilot analyze --output-format json > copilot-analysis.json

      - name: Automated Code Suggestions
        run: |
          # Generate context-aware code suggestions
          gh copilot suggest improvements --based-on-analysis copilot-analysis.json

  technology-specific-tests:
    strategy:
      matrix:
        include:
          - language: typescript
            node-version: '18'
            test-command: 'npm test'
          - language: python
            python-version: '3.11'
            test-command: 'pytest'
          - language: java
            java-version: '17'
            test-command: 'mvn test'
          - language: csharp
            dotnet-version: '8.0'
            test-command: 'dotnet test'

    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Language Environment
        uses: ./.github/actions/setup-${{ matrix.language }}
        with:
          version: ${{ matrix.node-version || matrix.python-version || matrix.java-version || matrix.dotnet-version }}

      - name: Copilot-Enhanced Testing
        run: |
          # Run tests with Copilot code analysis
          ${{ matrix.test-command }} --copilot-enhanced
```

### 2. GitHub Issues & Projects Automation

```typescript
// GitHub Issues automation with Copilot integration
interface CopilotIssueAutomation {
  autoLabeling: {
    enabled: boolean;
    chatmodeMapping: Record<string, string[]>;
    complexityDetection: boolean;
  };
  codeGeneration: {
    enabled: boolean;
    triggerKeywords: string[];
    templateGeneration: boolean;
  };
  projectManagement: {
    automaticTaskCreation: boolean;
    progressTracking: boolean;
    chatmodeWorkflows: boolean;
  };
}

const setupIssueAutomation = (projectConfig: ProjectInitializationRequest): CopilotIssueAutomation => ({
  autoLabeling: {
    enabled: true,
    chatmodeMapping: {
      'frontend': ['frontend-engineer', 'ux-designer'],
      'backend': ['backend-engineer', 'api-engineer'],
      'security': ['security-engineer'],
      'performance': ['qa-engineer'],
      'architecture': ['software-architect']
    },
    complexityDetection: true
  },
  codeGeneration: {
    enabled: true,
    triggerKeywords: ['copilot:generate', 'copilot:implement', 'copilot:refactor'],
    templateGeneration: projectConfig.projectScale === 'enterprise'
  },
  projectManagement: {
    automaticTaskCreation: projectConfig.projectScale !== 'startup',
    progressTracking: true,
    chatmodeWorkflows: true
  }
});
```

### 3. Pull Request Enhancement

```yaml
# .github/workflows/copilot-pr-enhancement.yml
name: Copilot PR Enhancement

on:
  pull_request:
    types: [opened, synchronize, reopened]

jobs:
  copilot-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Copilot Code Review
        run: |
          # Generate AI-powered code review
          gh copilot review --pr-number ${{ github.event.number }} \
            --focus security,performance,maintainability

      - name: Generate Code Suggestions
        run: |
          # Provide specific improvement suggestions
          gh copilot suggest --context pr-review \
            --diff-base origin/${{ github.base_ref }}

      - name: Update PR Description
        run: |
          # Enhance PR description with AI insights
          gh copilot enhance-pr-description \
            --pr-number ${{ github.event.number }}
```

## Code Generation Templates

### 1. Technology-Specific Copilot Instructions

```typescript
interface CopilotInstructionsGenerator {
  generateForTechnology(language: string, framework: string): string;
}

class TechnologySpecificInstructionsGenerator implements CopilotInstructionsGenerator {
  generateForTechnology(language: string, framework: string): string {
    const baseTemplate = this.getBaseTemplate();
    const languageConfig = this.getLanguageConfig(language);
    const frameworkConfig = this.getFrameworkConfig(framework);

    return `
# ${this.projectName} - GitHub Copilot Instructions

## 0. Project Metadata
- **project_name**: ${this.projectName}
- **primary_language**: ${language}
- **framework**: ${framework}
- **business_domain**: ${this.businessDomain}
- **project_scale**: ${this.projectScale}
- **development_stage**: mvp

## 1. Technology Stack
${this.generateTechnologySection(languageConfig, frameworkConfig)}

## 2. Chatmode Ecosystem
${this.generateChatmodeSection(language, framework)}

## 3. Development Patterns
${this.generatePatternsSection(languageConfig, frameworkConfig)}

## 4. GitHub Integration
${this.generateGitHubIntegrationSection()}
    `;
  }

  private generateTechnologySection(languageConfig: any, frameworkConfig: any): string {
    return `
- **Primary Language**: ${languageConfig.name} ${languageConfig.version}
- **Framework**: ${frameworkConfig.name} ${frameworkConfig.version}
- **Package Manager**: ${languageConfig.packageManager}
- **Testing**: ${frameworkConfig.testingFramework}
- **Build Tool**: ${frameworkConfig.buildTool}
- **Database**: ${this.databaseChoice || 'PostgreSQL'}
- **Deployment**: ${this.deploymentTarget || 'Docker + GitHub Actions'}
    `;
  }
}
```

### 2. Automated Project Scaffolding

```typescript
class ProjectScaffolder {
  async scaffoldProject(config: ProjectInitializationRequest): Promise<void> {
    // Create directory structure
    await this.createDirectoryStructure(config);

    // Generate configuration files
    await this.generateConfigurationFiles(config);

    // Set up GitHub integration
    await this.setupGitHubIntegration(config);

    // Initialize development environment
    await this.initializeDevelopmentEnvironment(config);

    // Create initial code templates
    await this.generateInitialCode(config);
  }

  private async createDirectoryStructure(config: ProjectInitializationRequest): Promise<void> {
    const template = this.getProjectTemplate(config.primaryLanguage);

    for (const [path, description] of Object.entries(template.structure)) {
      await fs.mkdir(path, { recursive: true });
      await fs.writeFile(
        `${path}/.gitkeep`,
        `# ${description}\n# This directory is part of the ${config.projectName} project structure.`
      );
    }
  }

  private async generateConfigurationFiles(config: ProjectInitializationRequest): Promise<void> {
    const generators = {
      typescript: () => this.generateTypeScriptConfig(config),
      python: () => this.generatePythonConfig(config),
      java: () => this.generateJavaConfig(config),
      csharp: () => this.generateDotNetConfig(config)
    };

    const generator = generators[config.primaryLanguage];
    if (generator) {
      await generator();
    }
  }
}
```

## Quality Gates & Standards

### 1. Code Quality Enforcement

```typescript
interface CopilotQualityGates {
  codeGeneration: CodeGenerationStandards;
  documentation: DocumentationRequirements;
  testing: TestingStandards;
  security: SecurityStandards;
}

const establishQualityGates = (projectScale: string): CopilotQualityGates => ({
  codeGeneration: {
    typeSafety: projectScale === 'enterprise' ? 'strict' : 'standard',
    errorHandling: 'comprehensive',
    performanceOptimized: true,
    productionReady: projectScale !== 'startup',
    codeComments: projectScale === 'enterprise' ? 'extensive' : 'contextual'
  },
  documentation: {
    apiDocumentation: 'automatic',
    inlineComments: 'contextual',
    readmeGeneration: 'comprehensive',
    architectureDocumentation: projectScale === 'enterprise'
  },
  testing: {
    unitTestCoverage: projectScale === 'enterprise' ? 90 : 70,
    integrationTests: 'critical-paths',
    e2eTests: projectScale !== 'startup',
    performanceTests: projectScale === 'enterprise'
  },
  security: {
    inputValidation: 'strict',
    outputSanitization: 'automatic',
    dependencyScanning: true,
    secretsDetection: true,
    complianceFramework: projectScale === 'enterprise' ? 'comprehensive' : 'basic'
  }
});
```

### 2. Development Environment Validation

```typescript
class DevelopmentEnvironmentValidator {
  async validateSetup(projectPath: string): Promise<ValidationResult> {
    const checks = await Promise.all([
      this.validateProjectStructure(projectPath),
      this.validateConfigurationFiles(projectPath),
      this.validateGitHubIntegration(projectPath),
      this.validateCopilotConfiguration(projectPath),
      this.validateDevelopmentTools(projectPath)
    ]);

    return {
      isValid: checks.every(check => check.passed),
      checks,
      recommendations: this.generateRecommendations(checks)
    };
  }

  private async validateCopilotConfiguration(projectPath: string): Promise<ValidationCheck> {
    const instructionsPath = path.join(projectPath, 'copilot.instructions.md');
    const exists = await fs.pathExists(instructionsPath);

    if (!exists) {
      return {
        name: 'Copilot Configuration',
        passed: false,
        message: 'copilot.instructions.md not found'
      };
    }

    const content = await fs.readFile(instructionsPath, 'utf-8');
    const hasRequiredSections = [
      'Project Metadata',
      'Technology Stack',
      'Chatmode Ecosystem',
      'GitHub Integration'
    ].every(section => content.includes(section));

    return {
      name: 'Copilot Configuration',
      passed: hasRequiredSections,
      message: hasRequiredSections ? 'Valid configuration' : 'Missing required sections'
    };
  }
}
```

## Transition Guidance

### Project Initialization Workflow
```markdown
After completing project initialization, follow this development workflow:

**Phase 1 - Foundation Setup**: Continue with `software-architect` chatmode for architecture review
**Phase 2 - Implementation**: Switch to appropriate implementation chatmode (`frontend-engineer`, `backend-engineer`)
**Phase 3 - Quality Assurance**: Use `qa-engineer` chatmode for testing and performance optimization
**Phase 4 - Security Review**: Switch to `security-engineer` chatmode for security audit
**Phase 5 - Deployment**: Use `deployment-engineer` chatmode for CI/CD and deployment setup
```

### Development Lifecycle Integration
```typescript
const developmentLifecycle = {
  initialization: {
    chatmode: 'new-project-initialization',
    deliverables: ['Project structure', 'Configuration files', 'GitHub integration']
  },
  architecture: {
    chatmode: 'software-architect',
    deliverables: ['Architecture documentation', 'Technology decisions', 'Scalability plan']
  },
  development: {
    chatmodes: ['frontend-engineer', 'backend-engineer', 'api-engineer'],
    deliverables: ['Feature implementation', 'API development', 'UI components']
  },
  testing: {
    chatmode: 'qa-engineer',
    deliverables: ['Test automation', 'Performance optimization', 'Quality metrics']
  },
  deployment: {
    chatmode: 'deployment-engineer',
    deliverables: ['CI/CD pipelines', 'Infrastructure setup', 'Monitoring']
  }
};
```

## Examples & Use Cases

### Example 1: Modern Web Application (React + TypeScript)

```bash
# Project Initialization Request
{
  "projectName": "modern-web-app",
  "primaryLanguage": "typescript",
  "businessDomain": "saas",
  "projectScale": "startup",
  "githubIntegration": true,
  "deploymentTarget": "vercel"
}

# Generated Structure
/modern-web-app
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   └── services/
├── .github/
│   ├── workflows/
│   └── issue-templates/
├── copilot.instructions.md
├── package.json
├── tsconfig.json
└── README.md

# Copilot Configuration Focus
# - React development patterns
# - TypeScript best practices
# - Component-driven development
# - Performance optimization
```

### Example 2: Enterprise API (Java Spring Boot)

```bash
# Project Initialization Request
{
  "projectName": "enterprise-api",
  "primaryLanguage": "java",
  "businessDomain": "enterprise",
  "projectScale": "enterprise",
  "githubIntegration": true,
  "deploymentTarget": "kubernetes"
}

# Generated Structure
/enterprise-api
├── src/
│   └── main/java/com/company/api/
│       ├── controller/
│       ├── service/
│       ├── repository/
│       └── model/
├── .github/
│   ├── workflows/
│   └── dependabot.yml
├── copilot.instructions.md
├── pom.xml
└── Dockerfile

# Copilot Configuration Focus
# - Enterprise Java patterns
# - Spring Boot best practices
# - Security and compliance
# - Microservices architecture
```

### Example 3: ML/AI Application (Python FastAPI)

```bash
# Project Initialization Request
{
  "projectName": "ml-api-service",
  "primaryLanguage": "python",
  "businessDomain": "ai",
  "projectScale": "sme",
  "specialRequirements": ["machine-learning", "async-processing"],
  "deploymentTarget": "docker"
}

# Generated Structure
/ml-api-service
├── app/
│   ├── api/
│   ├── ml/
│   ├── core/
│   └── services/
├── notebooks/
├── models/
├── .github/workflows/
├── copilot.instructions.md
├── requirements.txt
└── docker-compose.yml

# Copilot Configuration Focus
# - FastAPI async patterns
# - ML model integration
# - Data processing pipelines
# - Performance optimization
```

This comprehensive prompt creates production-ready projects with full GitHub Copilot integration, technology-specific optimizations, and enterprise-grade development workflows.