# My Name Is ClaudePilot - Prompts Documentation

## Overview

This directory contains comprehensive prompt engineering templates for GitHub Copilot, designed to provide expert-level assistance across the entire software development lifecycle. The prompts are organized into specialized categories and work in conjunction with the chatmodes defined in `.github/chatmodes/`.

## Architecture

```
.github/prompts/
├── agents/           # Specialized domain prompts (48 files)
│   ├── api/         # API development and integration (6 prompts)
│   ├── architecture/# System architecture and design (2 prompts)
│   ├── business/    # Business analysis and requirements (3 prompts)
│   ├── data/        # Data engineering and database design (4 prompts)
│   ├── deployment/  # DevOps and deployment automation (2 prompts)
│   ├── design/      # UX/UI design and user research (1 prompt)
│   ├── frontend/    # Frontend development and testing (12 prompts)
│   ├── product/     # Product management and planning (3 prompts)
│   ├── qa/          # Quality assurance and performance (1 prompt)
│   ├── quality/     # Test automation and quality processes (1 prompt)
│   ├── review/      # Code review and security assessment (2 prompts)
│   └── security/    # Security engineering and compliance (7 prompts)
├── init/            # Project initialization prompts (2 files)
├── workflows/       # End-to-end workflow orchestration (7 files)
├── README.md        # This documentation
└── TESTING.md       # Prompt validation and testing guide
```

## Prompt Categories

### 1. Agent Prompts (48 files)

Specialized prompts that provide domain-specific expertise for focused development tasks.

#### API Development (6 prompts)
- **frontend-backend-integration**: Full-stack integration patterns
- **graphql-api-development**: GraphQL schema design and implementation
- **microservices-architecture-patterns**: Distributed system patterns
- **rest-api-design-and-implementation**: RESTful API best practices
- **swagger-documentation-generation**: API documentation automation
- **swagger-to-endpoints-generation**: Code generation from OpenAPI specs

#### Architecture & Design (3 prompts)
- **system-architecture-design**: Enterprise architecture patterns
- **desktop-application-architecture**: Desktop application frameworks
- **user-research-and-persona-development**: UX research methodologies

#### Business Analysis (3 prompts)
- **business-case-development**: Business justification and ROI analysis
- **current-state-process-analysis**: Process mapping and optimization
- **stakeholder-requirements-gathering**: Requirements elicitation techniques

#### Data Engineering (4 prompts)
- **database-backend-integration**: Database connectivity patterns
- **database-design-and-etl-implementation**: Data architecture and ETL
- **database-to-entityframework-generation**: ORM code generation
- **desktop-database-integration**: Desktop data access patterns

#### DevOps & Deployment (2 prompts)
- **ci-cd-pipeline-and-infrastructure-setup**: Automated deployment pipelines
- **desktop-deployment-and-packaging**: Desktop application distribution

#### Frontend Development (12 prompts)
- **angular-component-development**: Angular best practices
- **build-tools-and-bundler-optimization**: Build system optimization
- **frontend-testing-and-quality-assurance**: Frontend testing strategies
- **modern-javascript-and-typescript-development**: ES6+ and TypeScript
- **progressive-web-app-development**: PWA implementation
- **react-component-development**: React patterns and hooks
- **react-component-development-and-testing**: React testing strategies
- **responsive-design-and-css-architecture**: CSS architecture patterns
- **state-management-and-data-flow**: State management solutions
- **swagger-to-angular-generation**: Angular service generation
- **web-accessibility-and-inclusive-design**: WCAG compliance
- **wxwidgets-desktop-development**: Cross-platform desktop development

#### Product Management (3 prompts)
- **feature-implementation-from-specification**: Spec-driven development
- **mvp-scoping-and-roadmap-planning**: Product strategy and planning
- **user-story-creation-and-prioritization**: Agile story management

#### Quality Assurance (3 prompts)
- **application-performance-optimization**: Performance tuning
- **test-automation-and-quality-assurance**: Test strategy and automation
- **security-vulnerability-assessment**: Security testing
- **sonarqube-code-quality-analysis**: Code quality metrics

#### Security Engineering (7 prompts)
- **compliance-audit-and-governance**: Regulatory compliance
- **identity-and-access-management**: Authentication and authorization
- **incident-response-and-forensics**: Security incident handling
- **penetration-testing-and-security-audit**: Security assessment
- **secure-code-review-and-sast**: Static security analysis
- **security-architecture-and-threat-modeling**: Security design
- **security-controls-implementation**: Security control implementation

### 2. Initialization Prompts (2 files)

Project setup and configuration prompts for different project types:

- **existing-project**: Onboarding to existing codebases
- **new-project**: Greenfield project initialization

### 3. Workflow Prompts (7 files)

End-to-end orchestration prompts that coordinate multiple phases and teams:

- **github-issue-to-implementation**: Complete issue-to-production workflow
- **pr-review-to-deployment**: Review-to-deployment automation
- **feature-development-lifecycle**: Feature development coordination
- **bug-fix-coordination**: Incident response and bug resolution
- **architecture-evolution-guidance**: System modernization and migration
- **cross-chatmode-context-handoff**: Context preservation between chatmodes
- **enterprise-development-governance**: Compliance and governance automation

## Key Features

### Technology Adaptivity
All prompts are designed to adapt to different technology stacks:
- **Frontend**: React, Angular, Vue.js, vanilla JavaScript
- **Backend**: Node.js, Python/FastAPI, Java/Spring Boot, .NET Core
- **Database**: SQL and NoSQL databases with appropriate ORM/ODM
- **Cloud**: AWS, Azure, GCP with infrastructure as code

### Enterprise Integration
- **GitHub Actions**: Automated CI/CD workflow generation
- **Security**: OWASP compliance and security best practices
- **Monitoring**: Observability and alerting integration
- **Documentation**: Automated documentation generation

### Quality Assurance
- **Testing**: Unit, integration, and E2E testing strategies
- **Code Quality**: Linting, formatting, and static analysis
- **Performance**: Performance monitoring and optimization
- **Accessibility**: WCAG compliance and inclusive design

### Compliance & Governance
- **Standards**: SOC2, GDPR, HIPAA, PCI-DSS, ISO27001
- **Audit**: Automated compliance reporting
- **Risk Management**: Risk assessment and mitigation
- **Change Management**: Controlled deployment processes

## Usage Patterns

### 1. Direct Prompt Usage
Reference prompts directly in GitHub Copilot Chat:
```
@github /prompts/agents/api/rest-api-design-and-implementation.prompt.md
```

### 2. Chatmode Integration
Prompts work seamlessly with chatmodes:
```
Switch to api-engineer chatmode for REST API development
```

### 3. Workflow Orchestration
Use workflow prompts for complex multi-phase projects:
```
@github /prompts/workflows/feature-development-lifecycle.prompt.md
```

## Best Practices

### Prompt Selection
1. **Start with initialization** prompts for new projects
2. **Use agent prompts** for focused, domain-specific tasks
3. **Apply workflow prompts** for complex, multi-phase coordination
4. **Combine prompts** for comprehensive coverage

### Context Management
- Always read `copilot.instructions.md` for project-specific configuration
- Maintain technology stack consistency across related prompts
- Use cross-chatmode handoff for complex transitions

### Quality Gates
- Validate generated code against project standards
- Run automated tests and quality checks
- Follow security and compliance requirements
- Document architectural decisions and changes

## Customization

### Project-Specific Adaptation
Prompts automatically adapt to:
- Technology stack defined in `copilot.instructions.md`
- Project structure and conventions
- Security and compliance requirements
- Team processes and workflows

### Extension Points
- Add custom prompts following the established patterns
- Extend existing prompts with project-specific requirements
- Integrate with external tools and services
- Customize workflow orchestration logic

## Integration with Chatmodes

Prompts are designed to work with the 12 specialized chatmodes:

1. **business-analyst** - Business requirements and process analysis
2. **software-architect** - System architecture and technical design
3. **ux-designer** - User experience and interface design
4. **api-engineer** - API development and integration
5. **frontend-engineer** - User interface development
6. **backend-engineer** - Server-side development
7. **data-engineer** - Data architecture and analytics
8. **security-engineer** - Security architecture and compliance
9. **deployment-engineer** - DevOps and deployment automation
10. **qa-engineer** - Quality assurance and testing
11. **product-manager** - Product strategy and planning
12. **reviewer** - Code review and quality validation

## Support and Contribution

### Validation
All prompts are validated using the testing framework described in `TESTING.md`.

### Updates
Prompts are continuously updated to reflect:
- Latest technology trends and best practices
- New GitHub Copilot capabilities
- Evolving compliance and security requirements
- Community feedback and contributions

### Migration
For projects migrating from other frameworks, see the migration documentation in the `work/` directory.

---

*This documentation is part of the My Name Is ClaudePilot framework - a comprehensive GitHub Copilot solution for enterprise software development.*