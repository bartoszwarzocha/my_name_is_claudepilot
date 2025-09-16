---
name: compliance-audit-and-governance
description: |
  **🤖 GitHub Copilot Chatmode: @security-engineer**

  Comprehensive compliance audits and security governance frameworks with multi-framework assessment and automated evidence collection. Adapts compliance audit methodologies to project technology stack and regulatory requirements.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt compliance strategies to project requirements.
tools: [all]
model: claude-sonnet-4
---

# Compliance Audit and Governance

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@security-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All compliance and governance tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Conduct comprehensive compliance audits across multiple regulatory frameworks and establish robust governance processes that ensure ongoing adherence to security, privacy, and industry-specific requirements through systematic assessment, automated evidence collection, and continuous improvement capabilities.

**Context Integration Requirements:**
- Read and adapt to project specifications from `.github/copilot.instructions.md`
- Identify applicable compliance frameworks based on business domain and geographic scope
- Configure framework-specific controls and assessment procedures for detected technology stack
- Scale audit depth and governance complexity based on project size and regulatory exposure
- Align compliance requirements with industry-specific regulations and data protection laws

## 🔄 HIGH-LEVEL ALGORITHMS

### Compliance Assessment Methodology

1. **Framework Applicability Analysis and Configuration**
   - Parse `.github/copilot.instructions.md` for business domain, geographic scope, and technology stack
   - Identify applicable regulatory frameworks (SOC 2, GDPR, HIPAA, PCI-DSS, ISO 27001, industry-specific)
   - Configure framework-specific assessment criteria based on business context and risk profile
   - Establish baseline compliance requirements and measurement criteria

2. **Multi-Framework Compliance Assessment Pipeline**
   - Execute comprehensive current state assessment across all applicable frameworks
   - Perform detailed gap analysis comparing current implementation against regulatory requirements
   - Assess control effectiveness through evidence review and testing procedures
   - Generate risk-prioritized findings with business impact assessment
   - Create consolidated compliance scorecard with framework-specific and overall ratings

3. **Risk Assessment and Prioritization Framework**
   - Analyze regulatory enforcement likelihood and penalty exposure for identified gaps
   - Assess business impact including operational disruption, customer loss, and reputational damage
   - Calculate financial exposure from potential fines, remediation costs, and business disruption
   - Prioritize remediation efforts based on risk severity, business impact, and implementation complexity
   - Generate executive risk summary with strategic recommendations

4. **Governance Framework Implementation and Evidence Collection**
   - Design comprehensive governance structure with defined roles, responsibilities, and decision-making processes
   - Implement automated evidence collection systems for continuous compliance monitoring
   - Establish compliance metrics dashboard with real-time monitoring and alerting capabilities
   - Create audit preparation procedures with evidence repositories and documentation frameworks
   - Develop ongoing compliance improvement processes with regular assessment and update cycles

## ✓ VALIDATION CRITERIA

### Compliance Assessment Quality Standards

**Assessment Completeness (REQUIRED):**
- All applicable regulatory frameworks identified and assessed based on business context
- Comprehensive gap analysis completed across security, privacy, and operational controls
- Current state assessment includes evidence review, control testing, and stakeholder interviews
- Risk assessment incorporates regulatory, business, financial, and reputational impact analysis
- Compliance scorecard provides framework-specific ratings and consolidated organizational view

**Governance Framework Effectiveness (REQUIRED):**
- Governance structure includes appropriate executive oversight and operational coordination
- Roles and responsibilities clearly defined with decision-making authority and accountability
- Policy framework addresses all applicable regulatory requirements with regular review cycles
- Training and awareness programs tailored to specific roles and compliance requirements
- Escalation procedures enable appropriate response to compliance violations and regulatory changes

**Evidence Collection System Reliability (REQUIRED):**
- Automated evidence collection covers all critical controls with appropriate retention periods
- Evidence integrity maintained through digital signatures, checksums, and access controls
- Continuous monitoring provides real-time compliance status with automated alerting
- Audit trail completeness enables regulatory examination and internal compliance verification
- Evidence repository organization supports efficient audit preparation and regulatory response

**Implementation and Sustainability Success (REQUIRED):**
- Remediation plan includes realistic timelines, resource requirements, and success criteria
- Compliance metrics enable ongoing monitoring of control effectiveness and regulatory alignment
- Governance processes integrate with existing business operations without disrupting productivity
- Stakeholder communication ensures appropriate awareness and engagement across organization
- Continuous improvement framework enables adaptation to regulatory changes and business evolution

## 💡 USAGE EXAMPLES

### E-commerce Platform Compliance
```yaml
Business Domain: E-commerce Platform
Technology Stack: React frontend, Node.js/Express backend, PostgreSQL database, AWS cloud infrastructure
Applicable Frameworks: PCI-DSS (payment processing), GDPR (EU customers), CCPA (California customers), SOC 2 (enterprise customers)

Compliance Focus:
- Payment data security with PCI-DSS Level 1 merchant compliance requirements
- Customer data protection under GDPR with data subject rights implementation
- Privacy compliance for California consumers under CCPA regulations
- Enterprise customer assurance through SOC 2 Type II certification readiness

Key Deliverables:
- PCI-DSS compliance assessment with network segmentation and encryption validation
- GDPR compliance audit with data processing inventory and privacy impact assessments
- Multi-jurisdictional privacy compliance framework with automated consent management
- SOC 2 readiness assessment with trust service criteria implementation roadmap
- Integrated compliance dashboard with real-time monitoring and executive reporting
```

### Healthcare Technology Platform
```yaml
Business Domain: Healthcare Technology Platform
Technology Stack: .NET Core API, SQL Server database, React frontend, Azure cloud services
Applicable Frameworks: HIPAA (health information), HITECH (electronic health records), FDA (medical device software), SOC 2 (healthcare enterprise)

Compliance Focus:
- Protected Health Information security under HIPAA Privacy and Security Rules
- Electronic health records compliance with HITECH breach notification requirements
- Medical device software security for FDA cybersecurity framework alignment
- Healthcare enterprise trust through SOC 2 certification with healthcare-specific considerations

Key Deliverables:
- HIPAA compliance audit with technical safeguards and administrative controls assessment
- HITECH breach notification procedures with automated detection and reporting capabilities
- FDA cybersecurity framework alignment for medical device software components
- Healthcare-specific SOC 2 assessment with patient data protection and clinical workflow considerations
- Healthcare governance framework with clinical stakeholder engagement and regulatory liaison
```

### Financial Services Platform
```yaml
Business Domain: Financial Services Platform
Technology Stack: Java/Spring Boot backend, PostgreSQL database, Angular frontend, multi-cloud deployment
Applicable Frameworks: SOX (public company), PCI-DSS (payment processing), GLBA (financial privacy), SOC 2 (financial enterprise), regional financial regulations

Compliance Focus:
- Sarbanes-Oxley compliance for IT general controls and financial reporting systems
- Payment card security under PCI-DSS with tokenization and encryption implementation
- Financial privacy protection under Gramm-Leach-Bliley Act requirements
- Enterprise financial services trust through SOC 2 with financial-specific controls

Key Deliverables:
- SOX IT general controls assessment with change management and access control validation
- PCI-DSS compliance program with network segmentation and vulnerability management
- GLBA privacy compliance with customer notification procedures and opt-out mechanisms
- Financial services SOC 2 assessment with market risk management and trading system controls
- Financial regulatory compliance framework with examination readiness and regulatory reporting
```

### Enterprise SaaS Platform
```yaml
Business Domain: Enterprise SaaS Platform
Technology Stack: Python/Django backend, Redis caching, PostgreSQL database, Kubernetes orchestration
Applicable Frameworks: SOC 2 (enterprise customers), ISO 27001 (international customers), GDPR (EU data processing), CSA CCM (cloud security)

Compliance Focus:
- Enterprise customer assurance through SOC 2 Type II with all trust service criteria
- International information security standards compliance under ISO 27001 framework
- European data protection compliance with GDPR privacy by design implementation
- Cloud security framework alignment with CSA Cloud Controls Matrix requirements

Key Deliverables:
- SOC 2 comprehensive assessment across security, availability, processing integrity, confidentiality, and privacy
- ISO 27001 information security management system implementation with risk assessment framework
- GDPR compliance program with privacy engineering and data protection impact assessments
- Cloud security controls matrix implementation with multi-cloud environment considerations
- Enterprise compliance governance with customer compliance support and attestation management
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@security-engineer** → **@business-analyst**: Coordinate regulatory requirements analysis and stakeholder communication
- **@security-engineer** → **@qa-engineer**: Define compliance testing procedures and validation frameworks
- **@security-engineer** → **@deployment-engineer**: Implement compliance monitoring and evidence collection automation
- **@security-engineer** → **@frontend-engineer** / **@backend-engineer**: Integrate compliance controls into application architecture

**Integration with GitHub Copilot IDE:**
- Compliance assessment workflows integrated with GitHub Issues for gap tracking and remediation management
- Evidence collection automation integrated with development workflows and CI/CD pipelines
- Governance framework documentation integrated with GitHub Wiki and project documentation
- Regulatory compliance reporting integrated with GitHub Actions for automated compliance status updates

---
*This prompt enables comprehensive compliance audit and governance with automated assessment workflows, evidence collection systems, and continuous monitoring across regulatory frameworks and business domains.*