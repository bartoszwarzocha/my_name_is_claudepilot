---
name: sonarqube-code-quality-analysis
description: |
  **🤖 GitHub Copilot Chatmode: @reviewer**

  Comprehensive code quality analysis using SonarQube with automated quality gates, metrics tracking, and continuous improvement. Adapts quality management approaches to project technology stack and development methodology.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt code quality strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# SonarQube Code Quality Analysis

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@reviewer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All review and assessment tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Establish comprehensive code quality analysis using SonarQube to systematically evaluate maintainability, reliability, and security standards across the entire codebase. Configure automated quality gates with technology-specific rules and thresholds. Generate detailed quality metrics, trend analysis, and actionable improvement recommendations. Integrate quality assessment seamlessly into development workflows with CI/CD pipeline automation.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Configure language-specific quality profiles and rules based on detected technology stack
- Scale quality standards and thresholds appropriate for project size and team maturity
- Align quality gates with business risk tolerance and development methodology
- Integrate quality analysis with existing development tools and workflows

## 🔄 HIGH-LEVEL ALGORITHMS

### Code Quality Analysis Methodology

1. **SonarQube Configuration and Setup**
   - Parse `.github/copilot.instructions.md` for technology stack, quality standards, and team maturity level
   - Detect programming languages and frameworks to configure appropriate quality profiles
   - Set up language-specific analysis rules, coverage requirements, and quality gate thresholds
   - Configure project-specific exclusions, test patterns, and source code organization

2. **Comprehensive Quality Scanning and Analysis**
   - Execute static code analysis using technology-appropriate SonarQube analyzers
   - Collect test coverage data from project-specific testing frameworks and tools
   - Analyze code complexity, duplication, maintainability, and security vulnerability patterns
   - Generate quality metrics across reliability, maintainability, security, and coverage dimensions
   - Process historical quality data for trend analysis and improvement tracking

3. **Quality Gate Evaluation and Validation**
   - Apply configured quality gates with business-appropriate thresholds and criteria
   - Evaluate new code quality against established baseline and improvement targets
   - Assess pull request quality impact and provide development team feedback
   - Generate quality gate status reports with detailed failure analysis and remediation guidance
   - Coordinate quality validation with CI/CD pipeline integration and deployment decisions

4. **Quality Improvement Planning and Recommendations**
   - Analyze quality trends and identify systematic improvement opportunities
   - Prioritize technical debt reduction based on business impact and remediation effort
   - Generate targeted recommendations for code quality, testing, and architecture improvements
   - Create quality coaching materials and best practice guidance for development teams
   - Establish continuous quality monitoring with automated alerting and reporting capabilities

## ✓ VALIDATION CRITERIA

### Code Quality Analysis Standards

**Quality Assessment Completeness (REQUIRED):**
- All source code analyzed using appropriate language-specific SonarQube analyzers
- Test coverage data collected and integrated from project testing frameworks
- Quality metrics calculated across maintainability, reliability, security, and coverage dimensions
- Historical trend analysis completed with baseline comparison and improvement tracking
- Technical debt quantified with business impact assessment and remediation priority guidance

**Quality Gate Configuration Accuracy (REQUIRED):**
- Quality thresholds configured appropriately for project scale and team maturity level
- Language-specific rules activated and customized based on technology stack requirements
- New code quality standards established with appropriate improvement targets and criteria
- Quality gate failures provide clear guidance for remediation and improvement actions
- Integration with CI/CD pipelines prevents quality regression and enforces improvement standards

**Quality Improvement Effectiveness (REQUIRED):**
- Quality trends demonstrate measurable improvement over time with systematic debt reduction
- Recommendations address root causes of quality issues rather than symptoms
- Technical debt prioritization considers business impact, remediation effort, and team capacity
- Quality coaching materials enable team skill development and best practice adoption
- Continuous quality monitoring provides early warning of quality degradation and improvement opportunities

**Integration and Automation Success (REQUIRED):**
- SonarQube analysis integrated seamlessly into development workflows without disrupting productivity
- Quality metrics accessible through project dashboards and reporting systems
- Automated quality feedback provided to developers through pull request comments and IDE integration
- Quality data exported to project management tools for planning and resource allocation decisions
- Documentation and training enable team adoption of quality improvement practices and tools

## 💡 USAGE EXAMPLES

### E-commerce Platform Quality Analysis
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, MongoDB database, microservices architecture
Team Maturity: Mixed experience levels, need quality coaching and best practice guidance

Quality Focus:
- Frontend code quality with React component patterns and TypeScript usage
- Backend API quality with Express middleware and database integration patterns
- Test coverage for critical business logic and user interaction flows
- Code duplication reduction across microservices and shared utility functions
- Security analysis for payment processing and customer data handling

Key Deliverables:
- JavaScript/TypeScript quality profiles with e-commerce specific rules and thresholds
- Test coverage analysis with focus on checkout, payment, and inventory management
- Technical debt assessment with business impact analysis for performance-critical areas
- Quality coaching materials for React best practices and API design standards
- Automated quality gates integrated with deployment pipeline for production releases
```

### Enterprise Governance Platform
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Java/Spring Boot, PostgreSQL, Angular frontend, Docker containerization
Team Maturity: Senior developers, high quality standards, compliance requirements

Quality Focus:
- Enterprise Java development standards with Spring framework best practices
- Angular frontend quality with TypeScript strict mode and component architecture
- Database integration quality with JPA/Hibernate optimization and query performance
- Code security analysis with enterprise authentication and authorization patterns
- Compliance-ready documentation and code maintainability for audit requirements

Key Deliverables:
- Enterprise Java quality profiles with compliance-specific rules and security analysis
- Angular code quality assessment with component architecture and performance guidelines
- Database code quality evaluation with query optimization and data access pattern analysis
- Comprehensive quality dashboard with compliance metrics and audit trail documentation
- Quality improvement roadmap with technical debt reduction and maintainability enhancement
```

### Healthcare Technology Compliance
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core, SQL Server, React frontend, Azure cloud services
Team Maturity: Healthcare domain experts, strict regulatory compliance requirements

Quality Focus:
- HIPAA compliance code analysis with data protection and privacy pattern validation
- Medical device software quality with FDA regulatory requirement alignment
- Healthcare data handling quality with encryption and access control validation
- Clinical workflow code quality with patient safety and data integrity requirements
- Regulatory audit readiness with comprehensive documentation and traceability

Key Deliverables:
- Healthcare-specific .NET quality profiles with HIPAA compliance rules and validation
- Medical device software quality assessment with FDA cybersecurity framework alignment
- Healthcare data flow quality analysis with PHI protection and audit trail requirements
- Regulatory compliance dashboard with quality metrics and documentation for audit purposes
- Quality improvement plan with healthcare-specific best practices and regulatory guidance
```

### Financial Services Audit
```yaml
Business Domain: Financial Services Platform
Technology Stack: Python/Django, PostgreSQL, React frontend, multi-cloud deployment
Team Maturity: Financial domain expertise, SOX compliance and audit requirements

Quality Focus:
- Financial services code quality with SOX compliance and audit trail requirements
- Trading system code quality with performance, accuracy, and regulatory compliance
- Customer financial data protection with security analysis and privacy compliance
- Risk management code quality with business continuity and disaster recovery validation
- Regulatory reporting code quality with accuracy, timeliness, and audit trail requirements

Key Deliverables:
- Financial services Python quality profiles with SOX compliance and regulatory rules
- Trading system quality assessment with performance optimization and accuracy validation
- Financial data security analysis with customer protection and regulatory compliance
- Risk management code quality evaluation with business continuity and compliance requirements
- Regulatory quality dashboard with audit-ready metrics and compliance documentation
```



## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@reviewer** → **@security-engineer**: Coordinate security validation and compliance verification
- **@reviewer** → **@qa-engineer**: Define quality standards and testing requirement validation
- **@reviewer** → **@frontend-engineer** / **@backend-engineer**: Provide code review guidance and improvement recommendations
- **@reviewer** → **@deployment-engineer**: Validate deployment security and operational readiness

**Integration with GitHub Copilot IDE:**
- Review workflows integrated with GitHub Pull Requests and automated quality gates
- Security scanning integrated with development workflows and vulnerability management
- Code quality metrics dashboard integrated with team performance tracking
- Automated compliance reporting integrated with GitHub Issues and audit requirements

---
*This prompt enables comprehensive code quality analysis with automated SonarQube workflows, quality gate validation, and continuous improvement across business domains and technology stacks.*