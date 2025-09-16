---
name: penetration-testing-and-security-audit
description: |
  **🤖 GitHub Copilot Chatmode: @security-engineer**

  Conduct comprehensive penetration testing and security audits with technology-adaptive testing methodologies. Adapts testing strategies to project technology stack and compliance requirements.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt penetration testing strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# Penetration Testing and Security Audit Framework

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@security-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All penetration testing and security audit tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Execute systematic penetration testing and security audits to identify vulnerabilities, validate security controls, and ensure robust defense against real-world attacks through comprehensive assessment methodologies that align with industry frameworks and compliance requirements.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Configure testing methodologies based on detected technology stack and application architecture
- Scale testing scope based on project complexity, infrastructure size, and attack surface analysis
- Align with industry-specific threats and compliance requirements for tailored attack scenarios
- Adapt testing techniques to application types (web, mobile, API, cloud, desktop) and security maturity level

## 🔄 HIGH-LEVEL ALGORITHMS

### Penetration Testing and Security Audit Methodology

1. **Pre-Engagement Planning and Scope Definition**
   - Parse `.github/copilot.instructions.md` for technology stack, application architecture, and business domain
   - Define comprehensive testing scope with target systems, authorized users, and rules of engagement
   - Select appropriate testing methodology (OWASP WSTG, NIST SP 800-115, PTES) based on project requirements
   - Establish testing timeline with authorized testing windows and emergency contact procedures
   - Configure compliance requirements mapping with relevant frameworks (SOC2, PCI-DSS, GDPR, HIPAA)

2. **Reconnaissance and Information Gathering**
   - Execute passive reconnaissance with domain analysis, certificate transparency logs, and OSINT gathering
   - Conduct active network scanning with host discovery, port enumeration, and service identification
   - Perform technology stack fingerprinting with version detection and configuration analysis
   - Analyze attack surface with subdomain enumeration, directory discovery, and API endpoint identification
   - Gather intelligence on potential attack vectors and vulnerability patterns specific to detected technologies

3. **Vulnerability Assessment and Exploitation Testing**
   - Execute comprehensive web application testing with OWASP Top 10 vulnerability assessment
   - Perform network penetration testing with service exploitation and lateral movement simulation
   - Conduct authentication and session management testing with bypass techniques and privilege escalation
   - Test input validation with injection attacks, XSS, and data validation bypass techniques
   - Validate access controls with authorization bypass and privilege escalation testing

4. **Security Control Validation and Compliance Testing**
   - Assess security architecture implementation with defense-in-depth validation and control effectiveness
   - Test incident response capabilities with simulated attack scenarios and response validation
   - Validate compliance requirements with framework-specific control testing and gap analysis
   - Perform business logic testing with workflow manipulation and abuse case validation
   - Generate comprehensive findings with risk assessment, business impact analysis, and remediation guidance

## ✓ VALIDATION CRITERIA

### Penetration Testing Quality Standards

**Testing Coverage Completeness (REQUIRED):**
- All identified attack surface components tested with appropriate methodologies and techniques
- OWASP Top 10 vulnerabilities comprehensively assessed across all application components and APIs
- Network infrastructure tested with service exploitation and lateral movement validation
- Authentication and authorization mechanisms validated with bypass and privilege escalation testing
- Business logic and workflow testing completed with abuse case and edge condition validation

**Vulnerability Detection Effectiveness (REQUIRED):**
- All critical and high-severity vulnerabilities identified with successful proof-of-concept exploitation
- False positive rate maintained below 5% with thorough validation and verification procedures
- Risk assessment accuracy validated with business impact analysis and exploitability confirmation
- Vulnerability findings documented with detailed evidence, reproduction steps, and impact analysis
- Remediation guidance provided with specific technical recommendations and implementation priorities

**Compliance Framework Alignment (REQUIRED):**
- Industry-specific compliance requirements tested with framework-specific control validation
- Regulatory obligations assessed with gap analysis and remediation roadmap development
- Security control effectiveness validated through penetration testing and vulnerability assessment
- Audit readiness confirmed with comprehensive documentation and evidence collection
- Compliance reporting generated with executive summary and technical findings appropriate for regulatory review

**Professional Standards Adherence (REQUIRED):**
- Testing methodology compliance with chosen framework (OWASP, NIST, PTES) maintained throughout assessment
- Ethical hacking principles followed with respect for system integrity and business operations
- Documentation quality meets professional standards with executive summary and technical detail appropriate for stakeholders
- Chain of custody maintained for all testing artifacts and evidence collection procedures
- Remediation timeline recommendations aligned with business risk tolerance and operational constraints

## 💡 USAGE EXAMPLES

### E-commerce Platform Security Testing
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, PostgreSQL database, AWS cloud infrastructure
Testing Focus: Payment processing security, customer data protection, PCI-DSS compliance

Security Testing Areas:
- Payment card data protection with PCI-DSS requirement validation and cardholder data encryption testing
- Customer account security with authentication bypass testing and session management validation
- E-commerce business logic with cart manipulation, price modification, and checkout process abuse testing
- API security testing with REST endpoint enumeration, authorization bypass, and data exposure validation

Key Deliverables:
- PCI-DSS compliance testing report with cardholder data environment assessment and gap analysis
- Web application security assessment with OWASP Top 10 vulnerability testing and exploitation validation
- API penetration testing results with authentication bypass and authorization flaw documentation
- E-commerce business logic testing with transaction manipulation and fraud prevention validation
- Executive summary with payment security risks and customer data protection recommendations
```

### Healthcare Technology Security Audit
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core API, SQL Server database, React frontend, Azure cloud services
Testing Focus: HIPAA compliance, PHI protection, medical device security, clinical workflow validation

Security Testing Areas:
- Protected Health Information security with HIPAA technical safeguards testing and data encryption validation
- Healthcare API security with medical data access controls and patient privacy protection testing
- Azure cloud security with infrastructure configuration validation and access control testing
- Clinical workflow security with healthcare provider authentication and patient data access validation

Key Deliverables:
- HIPAA security compliance audit with technical safeguards assessment and PHI protection validation
- Healthcare API penetration testing with medical data exposure analysis and access control validation
- Azure cloud security assessment with infrastructure hardening and identity management testing
- Clinical workflow security testing with healthcare provider access controls and audit trail validation
- Healthcare industry compliance report with medical device security and patient safety recommendations
```

### Financial Services Security Assessment
```yaml
Business Domain: Financial Services Platform
Technology Stack: Java/Spring Boot backend, PostgreSQL database, Angular frontend, multi-cloud deployment
Testing Focus: SOX compliance, financial data protection, trading system security, regulatory requirements

Security Testing Areas:
- Financial system security with SOX IT general controls testing and financial reporting integrity validation
- Trading platform security with market data protection and transaction integrity testing
- Multi-cloud security with infrastructure configuration testing and cross-cloud attack simulation
- Financial API security with transaction manipulation testing and authorization bypass validation

Key Deliverables:
- SOX compliance security assessment with IT general controls validation and financial system integrity testing
- Trading platform penetration testing with market manipulation testing and transaction security validation
- Multi-cloud security audit with infrastructure hardening and identity federation testing
- Financial API security assessment with payment processing validation and regulatory compliance testing
- Financial industry regulatory report with banking compliance and market risk management recommendations
```

### Enterprise SaaS Security Testing
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Python/Django backend, Redis caching, PostgreSQL database, Kubernetes orchestration
Testing Focus: Multi-tenancy security, enterprise customer data protection, SOC 2 compliance, container security

Security Testing Areas:
- Multi-tenant isolation testing with customer data segregation validation and cross-tenant breach prevention
- Container security assessment with Kubernetes configuration testing and orchestration security validation
- Enterprise authentication testing with SSO integration validation and federated identity security assessment
- SaaS API security with multi-tenant authorization testing and customer data access validation

Key Deliverables:
- Multi-tenant security assessment with customer data isolation testing and cross-contamination prevention validation
- Container security audit with Kubernetes hardening and orchestration security configuration testing
- Enterprise SSO integration testing with federated authentication and authorization validation
- SOC 2 security control testing with trust service criteria validation and enterprise compliance assessment
- Enterprise SaaS security report with customer assurance documentation and security questionnaire responses
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@security-engineer** → **@qa-engineer**: Coordinate security testing integration with quality assurance procedures
- **@security-engineer** → **@backend-engineer** / **@frontend-engineer**: Provide vulnerability remediation guidance and secure development recommendations
- **@security-engineer** → **@deployment-engineer**: Validate infrastructure security configuration and deployment hardening
- **@security-engineer** → **@business-analyst**: Communicate security risks and compliance requirements to stakeholders

**Integration with GitHub Copilot IDE:**
- Penetration testing workflows integrated with GitHub Actions for automated security validation and CI/CD integration
- Vulnerability findings integrated with GitHub Issues for remediation tracking and security improvement management
- Security testing documentation integrated with GitHub Wiki for security assessment history and compliance evidence
- Remediation guidance integrated with GitHub Pull Requests for secure code development and vulnerability fixes

---
*This prompt enables comprehensive penetration testing and security auditing with technology-adaptive assessment methodologies, compliance framework validation, and continuous security improvement.*