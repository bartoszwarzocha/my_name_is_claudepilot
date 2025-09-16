---
name: secure-code-review-and-sast
description: |
  **🤖 GitHub Copilot Chatmode: @security-engineer**

  Implement comprehensive secure code reviews and static application security testing programs with technology-adaptive vulnerability detection. Adapts SAST strategies to project technology stack and development workflow.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt SAST strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# Secure Code Review and Static Application Security Testing Framework

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@security-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All secure code review and SAST tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Conduct comprehensive secure code reviews and implement static application security testing (SAST) programs to identify, prioritize, and remediate security vulnerabilities in source code, ensuring secure development practices and reducing application security risks through automated scanning and manual review processes.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Configure SAST tools and security rules based on detected programming languages and frameworks
- Integrate security scanning with existing CI/CD pipelines and development workflows
- Scale security review processes based on project size, team structure, and security maturity level
- Align security rules and compliance requirements with industry standards and regulatory frameworks

## 🔄 HIGH-LEVEL ALGORITHMS

### Secure Code Review and SAST Implementation Methodology

1. **SAST Program Design and Tool Configuration**
   - Parse `.github/copilot.instructions.md` for technology stack, development workflow, and security requirements
   - Select appropriate SAST tools based on programming languages, frameworks, and enterprise requirements
   - Configure tool-specific security rules and vulnerability patterns for detected technologies
   - Design integration architecture with CI/CD pipelines, IDEs, and development workflow automation
   - Establish scanning workflows with incremental analysis, baseline management, and performance optimization

2. **Comprehensive Security Rule Development and Customization**
   - Implement technology-specific security rules for common vulnerability patterns and misconfigurations
   - Develop custom security rules for business logic vulnerabilities and organization-specific threats
   - Configure compliance-focused rules for regulatory requirements (SOC2, PCI-DSS, GDPR, HIPAA)
   - Establish rule prioritization with severity classification and false positive filtering mechanisms
   - Create security rule validation with test cases and effectiveness measurement procedures

3. **Development Workflow Integration and Automation**
   - Integrate SAST scanning with version control systems and pull request workflows
   - Configure automated security scanning triggers with commit hooks and pipeline automation
   - Implement security gate enforcement with build failure criteria and remediation requirements
   - Establish developer feedback mechanisms with in-IDE security alerts and remediation guidance
   - Create security metrics dashboards with vulnerability trends and remediation tracking

4. **Manual Code Review Process and Quality Assurance**
   - Establish secure code review procedures with security-focused review criteria and checklists
   - Implement peer review processes with security expert involvement and knowledge transfer
   - Create security review documentation with findings tracking and remediation validation
   - Develop security training programs with secure coding practices and vulnerability awareness
   - Establish continuous improvement processes with review effectiveness measurement and process optimization

## ✓ VALIDATION CRITERIA

### SAST Program Quality Standards

**Tool Configuration and Coverage Effectiveness (REQUIRED):**
- SAST tools properly configured for all detected programming languages and frameworks
- Security rules comprehensively cover OWASP Top 10 vulnerabilities and technology-specific threats
- Custom security rules developed for business logic vulnerabilities and organization-specific risks
- False positive rate maintained below acceptable threshold with proper rule tuning and validation
- Scanning performance optimized for development workflow integration without disrupting productivity

**Development Workflow Integration Success (REQUIRED):**
- SAST scanning seamlessly integrated with CI/CD pipelines and version control workflows
- Security gates properly configured with appropriate failure criteria and remediation requirements
- Developer feedback mechanisms functional with actionable remediation guidance and educational content
- Automated security scanning triggers operational with commit hooks and pull request validation
- Security metrics and reporting accessible through dashboards and management interfaces

**Security Review Process Maturity (REQUIRED):**
- Manual code review procedures established with security-focused criteria and expert involvement
- Peer review processes operational with knowledge transfer and security awareness development
- Security training programs implemented with secure coding practices and vulnerability education
- Review documentation comprehensive with findings tracking and remediation validation procedures
- Continuous improvement processes functional with effectiveness measurement and process optimization

**Compliance and Governance Alignment (REQUIRED):**
- Security rules aligned with applicable regulatory requirements and industry compliance standards
- Audit trail maintenance comprehensive with security review history and remediation evidence
- Governance processes established with security policy enforcement and exception management
- Compliance reporting automated with regulatory requirement mapping and evidence collection
- Risk management integration functional with vulnerability prioritization and business impact assessment

## 💡 USAGE EXAMPLES

### E-commerce Platform SAST Implementation
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, PostgreSQL database, AWS cloud infrastructure
SAST Focus: Payment security, customer data protection, PCI-DSS compliance, web application vulnerabilities

Security Analysis Areas:
- JavaScript/TypeScript security with XSS prevention, injection attacks, and client-side vulnerability detection
- Node.js backend security with authentication bypass, authorization flaws, and server-side vulnerability scanning
- Payment processing security with PCI-DSS compliance rules and sensitive data exposure detection
- API security analysis with REST endpoint security, authentication bypass, and data validation flaws

Key Deliverables:
- JavaScript/Node.js SAST configuration with e-commerce security rules and PCI-DSS compliance validation
- Payment security rule development with credit card data detection and encryption validation
- E-commerce business logic security analysis with cart manipulation and checkout process vulnerability detection
- Developer security training with payment security best practices and secure coding guidelines
- PCI-DSS compliance reporting with automated scanning and security control validation
```

### Healthcare Technology SAST Program
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core API, SQL Server database, React frontend, Azure cloud services
SAST Focus: HIPAA compliance, PHI protection, healthcare data security, medical device software security

Security Analysis Areas:
- .NET Core security with authentication vulnerabilities, authorization flaws, and healthcare-specific threats
- Healthcare data protection with PHI detection, encryption validation, and HIPAA technical safeguards
- Medical device software security with FDA cybersecurity framework compliance and patient safety validation
- Healthcare API security with medical data access controls and patient privacy protection

Key Deliverables:
- .NET Core SAST configuration with healthcare security rules and HIPAA compliance validation
- PHI detection and protection rules with healthcare data classification and encryption enforcement
- Medical device software security analysis with FDA cybersecurity framework alignment
- Healthcare developer training with HIPAA technical safeguards and secure medical software development
- Healthcare compliance reporting with HIPAA security rule validation and audit trail generation
```

### Financial Services SAST Implementation
```yaml
Business Domain: Financial Services Platform
Technology Stack: Java/Spring Boot backend, PostgreSQL database, Angular frontend, multi-cloud deployment
SAST Focus: SOX compliance, financial data protection, trading system security, regulatory requirements

Security Analysis Areas:
- Java/Spring Boot security with financial application vulnerabilities and enterprise security patterns
- Financial data protection with sensitive information detection and regulatory compliance validation
- Trading system security with transaction integrity, market manipulation prevention, and audit trail validation
- Financial API security with payment processing, account management, and regulatory reporting security

Key Deliverables:
- Java/Spring Boot SAST configuration with financial services security rules and SOX compliance validation
- Financial data security analysis with sensitive information detection and encryption enforcement
- Trading system security validation with transaction integrity and market risk management
- Financial services developer training with banking security standards and regulatory compliance requirements
- SOX compliance reporting with IT general controls validation and financial system security assessment
```

### Enterprise SaaS SAST Program
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Python/Django backend, Redis caching, PostgreSQL database, Kubernetes orchestration
SAST Focus: Multi-tenancy security, enterprise customer data protection, SOC 2 compliance, container security

Security Analysis Areas:
- Python/Django security with web framework vulnerabilities and enterprise application security patterns
- Multi-tenant security with customer data isolation, cross-tenant access prevention, and data segregation validation
- Container security analysis with Kubernetes configuration security and orchestration vulnerability detection
- Enterprise API security with customer data access controls and federated authentication security

Key Deliverables:
- Python/Django SAST configuration with multi-tenant security rules and enterprise application validation
- Multi-tenancy security analysis with customer data isolation and cross-contamination prevention
- Container and Kubernetes security scanning with orchestration configuration and deployment security
- Enterprise customer security training with multi-tenant development practices and data isolation requirements
- SOC 2 compliance reporting with trust service criteria validation and enterprise security controls assessment
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@security-engineer** → **@backend-engineer** / **@frontend-engineer**: Provide secure coding guidance and vulnerability remediation support
- **@security-engineer** → **@qa-engineer**: Coordinate security testing integration with quality assurance workflows
- **@security-engineer** → **@deployment-engineer**: Configure SAST tool integration with CI/CD pipelines and infrastructure
- **@security-engineer** → **@business-analyst**: Communicate security requirements and compliance obligations to development teams

**Integration with GitHub Copilot IDE:**
- SAST scanning integrated with GitHub Actions for automated security validation and CI/CD workflow integration
- Security findings integrated with GitHub Issues for vulnerability tracking and remediation management
- Code review security checklists integrated with GitHub Pull Requests for secure development workflow
- Security training and documentation integrated with GitHub Wiki for developer education and best practices

---
*This prompt enables comprehensive secure code review and SAST implementation with technology-adaptive vulnerability detection, development workflow integration, and continuous security improvement.*