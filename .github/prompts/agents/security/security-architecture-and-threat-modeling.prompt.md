---
name: security-architecture-and-threat-modeling
description: |
  **🤖 GitHub Copilot Chatmode: @security-engineer**

  Design comprehensive security architecture and conduct thorough threat modeling with technology-adaptive security patterns and frameworks. Adapts security architecture to project technology stack and business domain requirements.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt security architecture strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# Security Architecture and Threat Modeling Framework

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@security-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All security architecture and threat modeling tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Design comprehensive security architecture and conduct thorough threat modeling to establish robust security controls and frameworks that protect applications, data, and infrastructure while enabling business operations and maintaining compliance requirements across all system components and business processes.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Configure security architecture based on detected technology stack, database systems, and infrastructure patterns
- Scale security controls based on application complexity, user base, and business criticality
- Align security framework with industry-specific requirements for fintech, healthcare, ecommerce domains
- Adapt threat modeling methodology to development stage from MVP to enterprise-grade implementations

## 🔄 HIGH-LEVEL ALGORITHMS

### Security Architecture and Threat Modeling Methodology

1. **Security Requirements Analysis and Asset Classification**
   - Parse `.github/copilot.instructions.md` for technology stack, business domain, and regulatory requirements
   - Conduct comprehensive asset inventory with data classification and business value assessment
   - Analyze regulatory compliance requirements (GDPR, HIPAA, PCI-DSS, SOX) for applicable frameworks
   - Assess business risk tolerance with threat landscape analysis and impact assessment
   - Define security objectives with confidentiality, integrity, and availability requirements

2. **Threat Modeling and Risk Assessment Framework**
   - Implement systematic threat modeling using STRIDE, PASTA, or OCTAVE methodology
   - Conduct attack surface analysis with entry point identification and threat vector mapping
   - Perform threat actor profiling with capability assessment and motivation analysis
   - Execute vulnerability assessment with technology-specific weakness identification
   - Generate risk matrix with likelihood and impact assessment for prioritized remediation

3. **Security Architecture Design and Control Implementation**
   - Design defense-in-depth security architecture with layered security controls and redundant protection
   - Implement zero trust architecture principles with verify-never-trust and least privilege access
   - Configure security control frameworks with preventive, detective, and corrective controls
   - Establish security monitoring and incident response capabilities with SIEM integration
   - Create security governance framework with policy enforcement and compliance validation

4. **Security Integration and Continuous Validation**
   - Integrate security controls with application architecture and infrastructure components
   - Implement security testing and validation procedures with automated security scanning
   - Establish security metrics and monitoring with key performance indicators and dashboards
   - Create security documentation with architecture diagrams, threat models, and control matrices
   - Design security maintenance and evolution processes with continuous improvement and adaptation

## ✓ VALIDATION CRITERIA

### Security Architecture Quality Standards

**Architecture Design Completeness (REQUIRED):**
- Security architecture comprehensively addresses all identified assets, threats, and business requirements
- Defense-in-depth strategy implemented with multiple security layers and redundant protection mechanisms
- Zero trust principles applied with identity verification, device trust, and network segmentation
- Security control frameworks aligned with applicable regulatory requirements and industry standards
- Risk-based approach implemented with appropriate controls for identified threat levels and business impact

**Threat Modeling Effectiveness (REQUIRED):**
- Threat modeling methodology systematically applied with comprehensive threat identification and analysis
- Attack surface analysis complete with entry point enumeration and threat vector documentation
- Threat actor profiling accurate with capability assessment and motivation analysis
- Vulnerability assessment comprehensive with technology-specific weakness identification and prioritization
- Risk assessment quantified with likelihood and impact evaluation for informed decision-making

**Control Implementation Adequacy (REQUIRED):**
- Security controls properly implemented with preventive, detective, and corrective capabilities
- Technology integration seamless with application architecture and infrastructure components
- Monitoring and alerting comprehensive with security event detection and incident response automation
- Compliance requirements addressed with control mapping and regulatory framework alignment
- Performance impact minimized with efficient security control implementation and optimization

**Documentation and Governance Quality (REQUIRED):**
- Security architecture documentation comprehensive with diagrams, threat models, and control specifications
- Governance framework established with policy enforcement, exception management, and compliance validation
- Security metrics defined with key performance indicators and continuous monitoring capabilities
- Maintenance procedures documented with security evolution and continuous improvement processes
- Stakeholder communication effective with executive reporting and technical implementation guidance

## 💡 USAGE EXAMPLES

### E-commerce Platform Security Architecture
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, PostgreSQL database, AWS cloud infrastructure
Security Focus: Payment security, customer data protection, PCI-DSS compliance, scalable e-commerce security

Security Architecture Components:
- Payment security architecture with PCI-DSS compliance, tokenization, and secure payment processing
- Customer data protection with encryption, access controls, and privacy-by-design implementation
- E-commerce threat modeling with cart manipulation, price tampering, and fraud prevention
- Cloud security architecture with AWS security services and infrastructure hardening

Key Deliverables:
- E-commerce security architecture with payment processing security and customer data protection
- PCI-DSS compliance framework with cardholder data environment segmentation and controls
- Threat model with e-commerce attack scenarios and payment fraud prevention strategies
- AWS cloud security implementation with infrastructure security and monitoring integration
- Security governance with e-commerce security policies and incident response procedures
```

### Healthcare Technology Security Architecture
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core API, SQL Server database, React frontend, Azure cloud services
Security Focus: HIPAA compliance, PHI protection, medical device security, healthcare interoperability

Security Architecture Components:
- HIPAA-compliant security architecture with administrative, physical, and technical safeguards
- Protected Health Information protection with encryption, access controls, and audit trails
- Medical device security with FDA cybersecurity framework and patient safety considerations
- Healthcare interoperability security with HL7 FHIR and secure data exchange protocols

Key Deliverables:
- Healthcare security architecture with HIPAA compliance and PHI protection framework
- Medical device security design with FDA cybersecurity framework alignment and patient safety validation
- Healthcare threat modeling with clinical workflow analysis and patient data protection scenarios
- Azure healthcare cloud security with compliance validation and regulatory audit support
- Healthcare governance framework with HIPAA policy enforcement and breach response procedures
```

### Financial Services Security Architecture
```yaml
Business Domain: Financial Services Platform
Technology Stack: Java/Spring Boot backend, PostgreSQL database, Angular frontend, multi-cloud deployment
Security Focus: SOX compliance, financial data protection, trading system security, regulatory requirements

Security Architecture Components:
- Financial services security architecture with SOX compliance and regulatory requirement alignment
- Trading system security with market data protection, transaction integrity, and audit trails
- Financial data protection with encryption, access controls, and regulatory compliance validation
- Multi-cloud security with cross-cloud identity federation and data sovereignty requirements

Key Deliverables:
- Financial services security architecture with SOX compliance and regulatory framework alignment
- Trading system security design with market manipulation prevention and transaction integrity validation
- Financial threat modeling with insider threat analysis and market risk assessment scenarios
- Multi-cloud security framework with identity federation and regulatory compliance across jurisdictions
- Financial governance with regulatory reporting and audit trail generation for compliance examination
```

### Enterprise SaaS Security Architecture
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Python/Django backend, Redis caching, PostgreSQL database, Kubernetes orchestration
Security Focus: Multi-tenancy security, enterprise customer data protection, SOC 2 compliance, container security

Security Architecture Components:
- Multi-tenant security architecture with customer data isolation and cross-tenant breach prevention
- Container security architecture with Kubernetes hardening and orchestration security controls
- Enterprise identity and access management with federated authentication and customer SSO integration
- SaaS security monitoring with customer-specific security dashboards and compliance reporting

Key Deliverables:
- Multi-tenant security architecture with customer data isolation and enterprise-grade security controls
- Container and Kubernetes security framework with orchestration hardening and runtime protection
- Enterprise SaaS threat modeling with multi-tenancy attack scenarios and customer data protection analysis
- SOC 2 security architecture with trust service criteria implementation and compliance validation
- Enterprise customer security framework with security questionnaire responses and assurance documentation
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@security-engineer** → **@software-architect**: Coordinate security architecture integration with overall system design
- **@security-engineer** → **@backend-engineer** / **@frontend-engineer**: Implement security controls and threat mitigation measures
- **@security-engineer** → **@deployment-engineer**: Configure infrastructure security and monitoring implementation
- **@security-engineer** → **@business-analyst**: Communicate security requirements and compliance obligations to stakeholders

**Integration with GitHub Copilot IDE:**
- Security architecture documentation integrated with GitHub Wiki for design documentation and threat model maintenance
- Threat modeling workflows integrated with GitHub Issues for security requirement tracking and risk management
- Security control implementation integrated with GitHub Pull Requests for security review and validation
- Compliance framework integration with GitHub Actions for automated security validation and audit preparation

---
*This prompt enables comprehensive security architecture design and threat modeling with technology-adaptive security patterns, regulatory compliance alignment, and continuous security validation.*