---
name: identity-and-access-management
description: |
  **🤖 GitHub Copilot Chatmode: @security-engineer**

  Design and implement enterprise-grade identity and access management with technology-adaptive authentication and authorization solutions. Adapts IAM strategies to project technology stack and security requirements.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt IAM strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# Identity and Access Management Framework

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@security-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All identity and access management tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Design and implement enterprise-grade identity and access management (IAM) infrastructure that provides secure, scalable, and user-friendly authentication and authorization while enabling zero trust architecture and comprehensive governance across all user populations and business domains.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Configure IAM architecture based on detected technology stack and application frameworks
- Scale identity solutions based on user populations (employees, customers, partners, services)
- Align with industry-specific compliance requirements and identity governance frameworks
- Adapt to infrastructure model (cloud, on-premise, hybrid) for appropriate federation strategies

## 🔄 HIGH-LEVEL ALGORITHMS

### Identity and Access Management Implementation Methodology

1. **Enterprise Identity Architecture Design and Configuration**
   - Parse `.github/copilot.instructions.md` for technology stack, user populations, and security requirements
   - Design identity domain structure for different user types (employee, customer, partner, service)
   - Configure authentication services with multi-factor authentication and single sign-on capabilities
   - Establish authorization engines with role-based and attribute-based access control frameworks
   - Create identity provider integration strategy for internal and external authentication sources

2. **Zero Trust Authentication and Authorization Implementation**
   - Implement continuous identity verification with risk-based authentication policies
   - Deploy multi-factor authentication framework with hardware tokens, software tokens, and biometric authentication
   - Configure adaptive authentication engine with user risk scoring and contextual risk assessment
   - Establish privileged access management with session monitoring and just-in-time access workflows
   - Create comprehensive authorization framework with policy decision engines and attribute management

3. **Identity Lifecycle and Governance Automation**
   - Implement automated joiner/mover/leaver processes with role-based provisioning and deprovisioning
   - Deploy access governance workflows with self-service portals and approval workflows
   - Configure periodic access certification with automated compliance monitoring and policy violation detection
   - Establish identity analytics platform with behavioral monitoring and anomaly detection capabilities
   - Create comprehensive audit and reporting system with compliance dashboards and regulatory reporting

4. **Technology Integration and Security Controls Implementation**
   - Integrate with detected technology stack using appropriate authentication protocols and frameworks
   - Implement single sign-on federation capabilities with SAML, OAuth, and OpenID Connect support
   - Deploy directory service integration with synchronization and attribute mapping capabilities
   - Configure security monitoring integration with SIEM systems and threat intelligence platforms
   - Establish comprehensive governance controls with policy enforcement and exception management

## ✓ VALIDATION CRITERIA

### IAM Architecture Quality Standards

**Authentication Security Effectiveness (REQUIRED):**
- Multi-factor authentication implemented with phishing-resistant methods and adaptive policies
- Single sign-on deployed with secure federation protocols and comprehensive application integration
- Risk-based authentication functioning with behavioral analytics and contextual assessment
- Privileged access management operational with session monitoring and just-in-time elevation
- Authentication success rate maintains >99% availability with security policy compliance

**Authorization Framework Completeness (REQUIRED):**
- Attribute-based access control implemented with centralized policy decision points
- Role-based access control configured with hierarchical role inheritance and segregation of duties
- Fine-grained permissions system operational with resource-level access control
- Dynamic authorization policies functional with real-time risk assessment and policy adaptation
- Access control policies aligned with business requirements and regulatory compliance frameworks

**Identity Governance Process Maturity (REQUIRED):**
- Automated lifecycle management operational for joiner/mover/leaver processes with role-based provisioning
- Access certification processes functional with periodic reviews and automated compliance monitoring
- Identity analytics platform operational with behavioral monitoring and insider threat detection
- Governance workflows implemented with approval processes and policy violation remediation
- Audit capabilities comprehensive with compliance reporting and regulatory examination support

**Technology Integration and Scalability Success (REQUIRED):**
- Technology stack integration seamless with native authentication protocols and security controls
- Directory service synchronization operational with accurate attribute mapping and real-time updates
- Application integration complete with SSO federation and legacy system support
- Performance scalable across user populations without degrading authentication response times
- Monitoring and alerting comprehensive with identity-related security event detection and response

## 💡 USAGE EXAMPLES

### E-commerce Platform IAM
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, PostgreSQL database, AWS cloud infrastructure
User Populations: Employees (internal), Customers (external), Partners (B2B), Services (APIs)

IAM Architecture Focus:
- Customer identity platform with social login integration and privacy-compliant consent management
- Employee authentication with corporate directory integration and privileged access management
- Partner federation with B2B identity trust relationships and certificate-based authentication
- Service-to-service authentication with mutual TLS and OAuth client credentials flow

Key Deliverables:
- Multi-tenant customer identity platform with self-service registration and profile management
- Corporate employee SSO with Active Directory integration and MFA enforcement
- B2B partner federation framework with SAML-based trust relationships and automated provisioning
- API security framework with OAuth 2.0/JWT tokens and comprehensive service identity management
- Identity governance dashboard with customer privacy controls and employee access certification
```

### Healthcare Technology IAM
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core API, SQL Server database, React frontend, Azure cloud services
User Populations: Healthcare providers, Patients, Administrative staff, System integrations

IAM Architecture Focus:
- HIPAA-compliant identity architecture with strong authentication and audit trail requirements
- Healthcare provider credentialing with professional license validation and role-based access
- Patient portal authentication with privacy-first design and consent management capabilities
- Administrative staff access controls with segregation of duties and privileged access management

Key Deliverables:
- Healthcare provider identity verification with professional credentialing integration
- Patient identity platform with privacy controls and HIPAA-compliant consent management
- Administrative access controls with role-based permissions and audit trail generation
- HIPAA compliance framework with access logging, breach detection, and regulatory reporting
- Clinical workflow integration with secure authentication and authorization for patient data access
```

### Financial Services IAM
```yaml
Business Domain: Financial Services Platform
Technology Stack: Java/Spring Boot backend, PostgreSQL database, Angular frontend, multi-cloud deployment
User Populations: Employees, Customers, Regulators, Third-party integrations

IAM Architecture Focus:
- Financial services compliance with SOX, PCI-DSS, and regional financial regulations
- High-security authentication with hardware tokens and biometric authentication for privileged users
- Customer financial data protection with strong authentication and fraud detection integration
- Regulatory examination support with comprehensive audit trails and compliance reporting

Key Deliverables:
- Financial services compliance framework with SOX IT general controls and PCI-DSS requirements
- High-security employee authentication with smart cards, biometrics, and privileged session management
- Customer identity platform with fraud detection integration and financial privacy protection
- Regulatory compliance system with comprehensive audit trails and examination readiness
- Third-party integration security with certificate-based authentication and API security controls
```

### Enterprise SaaS IAM
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Python/Django backend, Redis caching, PostgreSQL database, Kubernetes orchestration
User Populations: Enterprise customers, Customer employees, SaaS administrators, System services

IAM Architecture Focus:
- Multi-tenant enterprise identity platform with customer isolation and white-label capabilities
- Enterprise customer federation with SAML/OIDC integration and customer directory synchronization
- SaaS administrative controls with super-admin capabilities and customer tenant management
- Scalable service identity management with Kubernetes service mesh integration

Key Deliverables:
- Multi-tenant identity architecture with customer isolation and enterprise federation capabilities
- Enterprise customer SSO integration with major identity providers and directory synchronization
- SaaS platform administration with tenant management and customer support access controls
- Kubernetes-native service identity with SPIFFE/SPIRE integration and mutual TLS authentication
- Enterprise customer compliance support with SOC 2 attestation and customer security questionnaire responses
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@security-engineer** → **@backend-engineer**: Implement authentication APIs and authorization middleware integration
- **@security-engineer** → **@frontend-engineer**: Integrate identity context and role-based access control components
- **@security-engineer** → **@deployment-engineer**: Configure identity infrastructure and directory service integration
- **@security-engineer** → **@qa-engineer**: Define identity security testing procedures and compliance validation

**Integration with GitHub Copilot IDE:**
- Identity management workflows integrated with GitHub Actions for automated provisioning and compliance monitoring
- Authentication security testing integrated with CI/CD pipelines for continuous security validation
- Identity governance documentation integrated with GitHub Wiki and security policy repositories
- Access control implementation integrated with code review workflows and security requirement validation

---
*This prompt enables comprehensive identity and access management with enterprise-grade authentication, authorization, and governance capabilities adapted to specific technology stacks and business requirements.*