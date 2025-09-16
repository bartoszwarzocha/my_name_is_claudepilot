---
description: Conduct comprehensive stakeholder interviews and requirements workshops to understand business needs, processes, and success criteria through systematic analysis and structured documentation. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - search
  - editFiles
  - runCommands
  - githubRepo
  - vscodeAPI
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `business-analyst` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Stakeholder Requirements Gathering

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Stakeholder Engagement and Analysis
- **Stakeholder Identification and Mapping**: Identify all relevant stakeholders with analysis of influence, interest levels, and decision-making authority
- **Structured Requirements Discovery**: Conduct systematic interviews and workshops to understand business needs, processes, and success criteria
- **Business Context Understanding**: Analyze current state challenges, pain points, and strategic objectives driving project requirements
- **Multi-Perspective Requirements Capture**: Gather functional, non-functional, and business requirements from diverse stakeholder perspectives

### Requirements Documentation and Validation
- **Business Requirements Documentation**: Create comprehensive Business Requirements Document with clear traceability and stakeholder approval
- **Process Mapping and Analysis**: Document current state processes and define future state vision with stakeholder validation
- **Success Criteria Definition**: Establish measurable success criteria and key performance indicators with stakeholder agreement
- **Requirements Traceability**: Maintain clear linkage between business needs and technical requirements for solution validation

### Stakeholder Communication and Consensus Building
- **Multi-Audience Communication**: Adapt communication style and content to different stakeholder roles and organizational levels
- **Conflict Resolution**: Identify and resolve conflicting requirements through stakeholder negotiation and prioritization
- **Requirements Prioritization**: Facilitate stakeholder collaboration to prioritize requirements based on business value and implementation feasibility
- **Formal Approval Process**: Secure stakeholder sign-off and establish requirements baseline for project execution

### Business Domain Expertise and Adaptation
- **Industry-Specific Requirements**: Understand and capture domain-specific regulatory, compliance, and operational requirements
- **Technology Integration Needs**: Identify system integration requirements and technical constraints within business context
- **Organizational Change Impact**: Assess change management requirements and stakeholder adoption considerations
- **Strategic Alignment Validation**: Ensure requirements align with business strategy and competitive positioning objectives

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Stakeholder Analysis and Engagement Planning
```
1. Read copilot.instructions.md to extract:
   - Business domain and industry-specific stakeholder landscape
   - Project scale and organizational context
   - Technology stack and system integration requirements
   - Stakeholder structure and decision-making processes

2. Stakeholder Mapping and Analysis:
   - Identify primary and secondary stakeholders across business functions
   - Map stakeholder influence, interest, and decision-making authority
   - Plan engagement approach based on stakeholder roles and preferences
   - Define interview and workshop objectives for each stakeholder group
```

### 2. Requirements Discovery and Analysis
```
1. Structured Interview Process:
   - Conduct role-specific stakeholder interviews with targeted questioning
   - Explore current state processes and pain points systematically
   - Identify functional and non-functional requirements through guided discovery
   - Document stakeholder priorities and success criteria definitions

2. Workshop Facilitation:
   - Design collaborative workshops for cross-functional requirements gathering
   - Facilitate process mapping and future state visioning sessions
   - Enable stakeholder collaboration for requirements prioritization
   - Build consensus on requirements scope and acceptance criteria
```

### 3. Requirements Documentation and Traceability
```
1. Business Requirements Documentation:
   - Create comprehensive Business Requirements Document with clear structure
   - Document functional requirements with detailed user scenarios and acceptance criteria
   - Capture non-functional requirements including performance, security, and compliance needs
   - Establish requirements traceability matrix linking business needs to technical solutions

2. Process and Success Criteria Documentation:
   - Document current state process maps with stakeholder validation
   - Define future state process vision aligned with business objectives
   - Establish measurable success criteria and key performance indicators
   - Create stakeholder matrix with roles, responsibilities, and approval authority
```

### 4. Requirements Validation and Consensus Building
```
1. Stakeholder Review and Validation:
   - Conduct formal requirements review sessions with stakeholder groups
   - Facilitate conflict resolution for competing or contradictory requirements
   - Validate requirements completeness and accuracy through stakeholder feedback
   - Ensure requirements align with business strategy and technical feasibility

2. Requirements Baseline and Approval:
   - Prioritize requirements based on business value and implementation complexity
   - Secure formal stakeholder approval and requirements sign-off
   - Establish requirements change control process and governance
   - Plan handoff to product management and technical teams
```

### 5. Knowledge Transfer and Implementation Support
```
1. Requirements Communication:
   - Create stakeholder-specific requirements summaries and presentations
   - Develop requirements artifacts for technical team handoff
   - Facilitate knowledge transfer sessions with implementation teams
   - Establish ongoing stakeholder communication and feedback mechanisms

2. Implementation Readiness:
   - Validate requirements against technical constraints and project timeline
   - Support solution design reviews and requirements traceability validation
   - Plan stakeholder involvement in testing and acceptance activities
   - Prepare change management and training requirements based on stakeholder analysis
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Stakeholder Engagement Excellence
- **Complete Stakeholder Coverage**: All relevant stakeholders identified and engaged with appropriate level of involvement
- **Stakeholder Satisfaction**: High stakeholder satisfaction with engagement process and requirements capture accuracy
- **Consensus Achievement**: Clear stakeholder consensus on requirements priorities and project scope
- **Formal Approval**: Documented stakeholder approval and sign-off on final requirements baseline

### ✅ Requirements Quality and Completeness
- **Comprehensive Coverage**: All functional, non-functional, and business requirements captured with appropriate detail
- **Clear Documentation**: Requirements documented with unambiguous language and testable acceptance criteria
- **Traceability Established**: Clear linkage between business needs and requirements with impact analysis capability
- **Validation Completed**: Requirements validated through stakeholder review and confirmed accuracy

### ✅ Business Alignment and Strategic Value
- **Strategic Alignment**: Requirements clearly aligned with business strategy and competitive positioning objectives
- **Business Value Articulation**: Clear articulation of business value and expected outcomes from requirements implementation
- **Success Metrics Definition**: Measurable success criteria and KPIs established with stakeholder agreement
- **Risk and Constraint Identification**: Business risks and constraints identified and addressed in requirements documentation

### ✅ Implementation Readiness
- **Technical Feasibility**: Requirements validated against technical constraints and system capabilities
- **Prioritization Completed**: Requirements prioritized based on business value and implementation complexity
- **Change Management Planning**: Stakeholder change impact assessed and change management requirements identified
- **Handoff Preparation**: Requirements documentation and artifacts prepared for seamless handoff to implementation teams

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with product-manager for strategy development and ux-designer for user experience design
- **Documentation Quality**: Comprehensive requirements documentation supporting GitHub Copilot development workflows
- **Configuration Adaptation**: Requirements gathering adapted to project business domain and technology context
- **Implementation Support**: Requirements artifacts support GitHub Copilot implementation and validation activities

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Platform Requirements Gathering
```yaml
Context: E-commerce company implementing new customer experience and operational efficiency platform
Technology Stack: Detected from copilot.instructions.md (React, Node.js, PostgreSQL, payment gateways)
Business Domain: E-commerce with customer experience optimization and operational scalability focus

Stakeholder Engagement Focus:
- Marketing and sales teams for customer experience requirements
- Operations and fulfillment teams for inventory and order processing needs
- Customer service teams for support workflow and CRM integration
- Finance teams for payment processing and reporting requirements

GitHub Copilot Workflow:
1. business-analyst chatmode → Comprehensive stakeholder requirements gathering with e-commerce focus
2. product-manager chatmode → Translate requirements into product strategy and feature prioritization
3. ux-designer chatmode → Design customer experience based on captured user journey requirements
4. frontend-engineer chatmode → Implement customer-facing features meeting stakeholder requirements

Expected Deliverables:
- E-commerce business requirements document with customer journey and operational workflows
- Stakeholder matrix with e-commerce specific roles and responsibilities
- Success criteria framework with conversion optimization and operational efficiency metrics
- Requirements traceability matrix linking business needs to technical implementation
```

### Scenario 2: Healthcare System Requirements Gathering
```yaml
Context: Healthcare organization implementing patient care and compliance management system
Technology Stack: Healthcare-compliant setup (EHR integration, HIPAA compliance, HL7 standards)
Business Domain: Healthcare with patient safety, regulatory compliance, and care coordination focus

Stakeholder Engagement Focus:
- Clinical staff for patient care workflows and clinical decision support requirements
- Compliance officers for HIPAA, FDA, and healthcare regulatory requirements
- IT security teams for patient data protection and system security needs
- Administrative staff for billing, scheduling, and operational efficiency requirements

GitHub Copilot Workflow:
1. business-analyst chatmode → Healthcare stakeholder requirements with compliance and patient safety focus
2. security-engineer chatmode → Validate security and compliance requirements against healthcare regulations
3. data-engineer chatmode → Analyze clinical data integration and interoperability requirements
4. qa-engineer chatmode → Establish patient safety and quality assurance validation criteria

Expected Deliverables:
- Healthcare business requirements with patient safety and regulatory compliance focus
- Clinical workflow documentation with HIPAA compliance checkpoints
- Stakeholder analysis including clinical, administrative, and regulatory perspectives
- Success criteria with patient outcomes, compliance, and operational efficiency metrics
```

### Scenario 3: Financial Services Requirements Gathering
```yaml
Context: Financial institution implementing risk management and regulatory compliance platform
Technology Stack: Enterprise financial setup (mainframe integration, real-time processing, regulatory reporting)
Business Domain: Financial services with regulatory compliance, risk management, and customer service focus

Stakeholder Engagement Focus:
- Risk management teams for fraud detection and credit risk assessment requirements
- Compliance officers for regulatory reporting and audit trail needs
- Customer service teams for account management and support workflow requirements
- Operations teams for transaction processing and reconciliation needs

GitHub Copilot Workflow:
1. business-analyst chatmode → Financial services stakeholder requirements with compliance and risk focus
2. security-engineer chatmode → Analyze financial security and fraud detection requirements
3. api-engineer chatmode → Design system integration for regulatory reporting and compliance
4. data-engineer chatmode → Implement real-time risk monitoring and regulatory reporting requirements

Expected Deliverables:
- Financial services business requirements with regulatory compliance and risk management focus
- Stakeholder analysis including risk, compliance, operations, and customer service perspectives
- Requirements documentation with audit trail and regulatory reporting specifications
- Success criteria with risk reduction, compliance efficiency, and customer satisfaction metrics
```

### Scenario 4: Manufacturing Operations Requirements Gathering
```yaml
Context: Manufacturing company implementing production optimization and quality management system
Technology Stack: Industrial setup (ERP integration, IoT sensors, manufacturing execution systems)
Business Domain: Manufacturing with operational efficiency, quality management, and supply chain optimization focus

Stakeholder Engagement Focus:
- Production managers for manufacturing workflow and efficiency requirements
- Quality assurance teams for inspection processes and compliance standards
- Supply chain managers for inventory management and supplier coordination needs
- Maintenance teams for equipment management and predictive maintenance requirements

GitHub Copilot Workflow:
1. business-analyst chatmode → Manufacturing stakeholder requirements with operational efficiency and quality focus
2. data-engineer chatmode → Analyze IoT data integration and predictive analytics requirements
3. qa-engineer chatmode → Establish quality control and automated testing requirements
4. deployment-engineer chatmode → Design manufacturing system integration and automation infrastructure

Expected Deliverables:
- Manufacturing business requirements with operational efficiency and quality management focus
- Production workflow documentation with quality control checkpoints and efficiency metrics
- Stakeholder analysis including production, quality, supply chain, and maintenance perspectives
- Success criteria with operational efficiency, quality improvement, and cost reduction metrics
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Stakeholder Requirements Gathering → business-analyst chatmode (lead)
├─ Product Strategy Development → product-manager chatmode
├─ User Experience Design → ux-designer chatmode
├─ Technical Architecture → software-architect chatmode
├─ Security and Compliance → security-engineer chatmode
└─ Quality Assurance → qa-engineer chatmode
```

### Context Handoff Information
- **To product-manager**: Business requirements, stakeholder priorities, success criteria, market and competitive analysis
- **To ux-designer**: User journey requirements, stakeholder experience needs, interface and interaction specifications
- **To software-architect**: Technical requirements, system integration needs, performance and scalability expectations
- **To security-engineer**: Security requirements, compliance specifications, data protection and audit needs
- **To qa-engineer**: Quality criteria, testing requirements, acceptance criteria and validation specifications

### GitHub Actions Integration
- **Requirements Documentation**: Automated generation of requirements documentation and stakeholder artifacts
- **Stakeholder Collaboration**: Automated stakeholder review workflows and feedback collection systems
- **Requirements Traceability**: Integration with development workflows for requirements tracking and validation
- **Change Management**: Documentation of requirements changes and stakeholder approval workflows

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Business Domain**: Automatically adapts stakeholder identification and requirements focus to industry-specific needs and regulatory frameworks
- **Project Scale**: Calibrates stakeholder engagement approach and documentation detail based on startup, SME, or enterprise context
- **Organizational Structure**: Adapts stakeholder mapping and communication strategies to organizational hierarchy and decision-making processes
- **Technology Context**: Frames technical requirements and system integration needs based on existing technology stack
- **Regulatory Environment**: Incorporates industry-specific compliance requirements and regulatory stakeholder engagement

**The business-analyst chatmode will automatically analyze project configuration and business context to deliver optimal stakeholder requirements gathering while maintaining the functional requirements specified above.**