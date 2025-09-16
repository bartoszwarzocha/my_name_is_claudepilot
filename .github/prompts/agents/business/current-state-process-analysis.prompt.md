---
description: Analyze existing business processes to identify improvement opportunities, inefficiencies, pain points, and automation possibilities with comprehensive workflow mapping and stakeholder analysis. Adapts to project specifications defined in copilot.instructions.md.
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

# Current State Process Analysis

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Process Discovery and Documentation
- **End-to-End Process Mapping**: Document complete business workflows from initiation to completion with all decision points and handoffs
- **Stakeholder Role Analysis**: Identify and document all roles, responsibilities, and decision-making authorities within processes
- **System Integration Assessment**: Map current technology ecosystem and data flows between systems and manual touchpoints
- **Performance Baseline Establishment**: Quantify current process performance including time, cost, quality, and user satisfaction metrics

### Gap Analysis and Improvement Identification
- **Inefficiency Detection**: Identify bottlenecks, redundancies, manual effort that could be automated, and process delays
- **Pain Point Analysis**: Document user frustrations, error-prone activities, and process complexity issues
- **Compliance Gap Assessment**: Evaluate adherence to regulatory requirements and industry standards
- **Technology Gap Evaluation**: Assess system capabilities versus business needs and integration requirements

### Opportunity Assessment and Prioritization
- **Automation Potential Analysis**: Evaluate opportunities for process automation with ROI and feasibility assessment
- **Process Optimization Opportunities**: Identify simplification, consolidation, and workflow improvement possibilities
- **Technology Enhancement Needs**: Assess requirements for system upgrades, integrations, and new technology adoption
- **Strategic Alignment Evaluation**: Analyze how current processes support or hinder business objectives and competitive positioning

### Data-Driven Analysis and Validation
- **Quantitative Process Metrics**: Measure process cycle times, error rates, resource utilization, and cost analysis
- **Qualitative Stakeholder Feedback**: Gather user experience insights and process satisfaction assessment
- **Comparative Analysis**: Benchmark against industry best practices and competitive process standards
- **Impact Assessment**: Evaluate business impact of identified inefficiencies and improvement opportunities

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Process Discovery and Context Analysis
```
1. Read copilot.instructions.md to extract:
   - Business domain and industry-specific process requirements
   - Project scale and organizational context
   - Current technology stack and system landscape
   - Stakeholder structure and decision-making hierarchy

2. Process Identification and Scoping:
   - Identify key business processes within project scope
   - Define process boundaries and interaction points
   - Map stakeholder involvement and process ownership
   - Establish analysis scope and success criteria
```

### 2. Current State Documentation and Mapping
```
1. Workflow Documentation:
   - Map end-to-end process flows with decision points
   - Document inputs, outputs, triggers, and completion criteria
   - Identify all stakeholder touchpoints and handoffs
   - Catalog current systems and tools used in each process step

2. Performance Data Collection:
   - Gather quantitative metrics (time, cost, volume, quality)
   - Collect qualitative feedback through stakeholder interviews
   - Observe actual process execution and variations
   - Document current reporting and monitoring capabilities
```

### 3. Analysis and Gap Identification
```
1. Inefficiency Analysis:
   - Identify process bottlenecks and delay points
   - Analyze manual effort and automation opportunities
   - Evaluate data quality issues and inconsistencies
   - Assess compliance gaps and risk areas

2. Technology Assessment:
   - Map system integration points and data flows
   - Evaluate current tool effectiveness and user satisfaction
   - Identify manual data entry and duplicate effort
   - Assess system scalability and performance limitations
```

### 4. Improvement Opportunity Assessment
```
1. Opportunity Identification:
   - Evaluate automation potential with cost-benefit analysis
   - Identify process simplification and consolidation opportunities
   - Assess technology upgrade and integration needs
   - Evaluate training and change management requirements

2. Impact and Feasibility Analysis:
   - Prioritize improvements based on business impact and implementation effort
   - Assess resource requirements and timeline implications
   - Evaluate technical feasibility with current technology stack
   - Consider change management and stakeholder adoption challenges
```

### 5. Recommendations and Future State Preparation
```
1. Improvement Roadmap Development:
   - Create prioritized list of improvement opportunities
   - Define success metrics and measurement strategies
   - Plan implementation approach and resource requirements
   - Establish change management and communication strategies

2. Stakeholder Validation and Buy-in:
   - Present findings and recommendations to stakeholders
   - Validate process maps and improvement opportunities
   - Secure commitment for future state design and implementation
   - Establish governance and monitoring frameworks
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Process Documentation Completeness
- **Comprehensive Mapping**: All in-scope processes documented with complete end-to-end flows and decision points
- **Stakeholder Validation**: Process maps validated and approved by process owners and key stakeholders
- **System Integration Coverage**: Complete documentation of technology touchpoints and data flows
- **Performance Baseline**: Quantified current state performance metrics established for improvement measurement

### ✅ Analysis Quality and Accuracy
- **Data-Driven Insights**: Analysis supported by quantitative metrics and qualitative stakeholder feedback
- **Root Cause Identification**: Clear identification of underlying causes for inefficiencies and pain points
- **Comprehensive Gap Analysis**: Complete assessment of process, technology, and compliance gaps
- **Validated Findings**: Analysis findings confirmed through multiple data sources and stakeholder validation

### ✅ Improvement Opportunity Assessment
- **Prioritized Opportunities**: Improvement opportunities ranked by business impact and implementation feasibility
- **Quantified Benefits**: Clear articulation of potential benefits with ROI and business value estimation
- **Feasibility Assessment**: Realistic evaluation of implementation requirements and constraints
- **Strategic Alignment**: Improvement opportunities aligned with business objectives and competitive strategy

### ✅ Actionable Recommendations
- **Specific Improvements**: Clear, actionable recommendations with defined scope and success criteria
- **Implementation Roadmap**: Logical sequencing of improvements with resource and timeline considerations
- **Change Management**: Consideration of stakeholder adoption and organizational change requirements
- **Success Measurement**: Defined metrics and monitoring approaches for improvement validation

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with software-architect for technical analysis and ux-designer for user experience assessment
- **Documentation Quality**: Comprehensive process documentation supporting future chatmode activities
- **Configuration Adaptation**: Analysis adapted to project business domain and technology context
- **Implementation Support**: Analysis findings support GitHub Copilot development and automation workflows

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Order Processing Analysis
```yaml
Context: E-commerce platform analyzing order processing workflow for automation opportunities
Technology Stack: Detected from copilot.instructions.md (React, Node.js, PostgreSQL, payment gateways)
Business Domain: E-commerce with customer journey optimization and operational efficiency focus

Process Analysis Focus:
- Customer order placement through checkout completion
- Inventory management and fulfillment coordination
- Payment processing and fraud detection workflows
- Customer service and returns management processes

GitHub Copilot Workflow:
1. business-analyst chatmode → Complete current state process analysis with e-commerce focus
2. software-architect chatmode → Analyze technical system integration and automation capabilities
3. frontend-engineer chatmode → Assess user experience pain points in customer-facing processes
4. api-engineer chatmode → Evaluate backend system integration and automation opportunities

Expected Deliverables:
- Complete e-commerce process maps with customer journey analysis
- Bottleneck identification in order processing and fulfillment workflows
- Automation opportunity assessment with ROI analysis for inventory and payment processing
- User experience pain point analysis with conversion optimization recommendations
```

### Scenario 2: Healthcare Patient Care Workflow Analysis
```yaml
Context: Healthcare organization analyzing patient care workflows for compliance and efficiency improvements
Technology Stack: Healthcare-compliant setup (EHR systems, HIPAA compliance, HL7 integration)
Business Domain: Healthcare with patient safety, compliance, and care coordination focus

Process Analysis Focus:
- Patient registration and intake processes
- Clinical documentation and care coordination workflows
- Appointment scheduling and resource management
- Billing and insurance processing automation

GitHub Copilot Workflow:
1. business-analyst chatmode → Analyze healthcare workflows with compliance and patient safety focus
2. security-engineer chatmode → Assess HIPAA compliance gaps and data protection requirements
3. data-engineer chatmode → Evaluate clinical data integration and interoperability opportunities
4. qa-engineer chatmode → Analyze patient safety protocols and quality improvement opportunities

Expected Deliverables:
- Healthcare process maps with compliance checkpoints and audit trails
- Clinical workflow efficiency analysis with care coordination improvement opportunities
- HIPAA compliance gap assessment with risk mitigation recommendations
- Patient safety protocol evaluation with quality improvement roadmap
```

### Scenario 3: Financial Services Risk Management Analysis
```yaml
Context: Financial institution analyzing risk management and compliance processes
Technology Stack: Enterprise financial setup (mainframe integration, real-time processing, regulatory reporting)
Business Domain: Financial services with regulatory compliance and risk management focus

Process Analysis Focus:
- Customer onboarding and KYC processes
- Transaction monitoring and fraud detection workflows
- Regulatory reporting and compliance management
- Risk assessment and credit decision processes

GitHub Copilot Workflow:
1. business-analyst chatmode → Analyze financial processes with regulatory compliance and risk focus
2. security-engineer chatmode → Evaluate fraud detection and security protocol effectiveness
3. data-engineer chatmode → Assess real-time data processing and reporting automation opportunities
4. api-engineer chatmode → Analyze system integration for regulatory reporting and compliance

Expected Deliverables:
- Financial services process maps with regulatory compliance checkpoints
- Risk management workflow analysis with automation and monitoring improvements
- Fraud detection process evaluation with real-time monitoring enhancement opportunities
- Regulatory reporting efficiency analysis with automation and accuracy improvement recommendations
```

### Scenario 4: Manufacturing Operations Analysis
```yaml
Context: Manufacturing company analyzing production and supply chain processes
Technology Stack: Industrial setup (ERP systems, IoT sensors, manufacturing execution systems)
Business Domain: Manufacturing with operational efficiency and quality management focus

Process Analysis Focus:
- Production planning and scheduling workflows
- Quality control and inspection processes
- Supply chain coordination and inventory management
- Maintenance and equipment management procedures

GitHub Copilot Workflow:
1. business-analyst chatmode → Analyze manufacturing processes with operational efficiency and quality focus
2. data-engineer chatmode → Evaluate IoT data integration and predictive analytics opportunities
3. qa-engineer chatmode → Assess quality control processes and automated testing possibilities
4. deployment-engineer chatmode → Analyze manufacturing system integration and automation infrastructure

Expected Deliverables:
- Manufacturing process maps with efficiency bottleneck identification
- Quality control workflow analysis with automated inspection and monitoring improvements
- Supply chain coordination process evaluation with real-time visibility and optimization opportunities
- Predictive maintenance process design with IoT integration and cost reduction analysis
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Current State Process Analysis → business-analyst chatmode (lead)
├─ Technical System Analysis → software-architect chatmode
├─ User Experience Assessment → ux-designer chatmode
├─ Security and Compliance Review → security-engineer chatmode
├─ Data Flow Analysis → data-engineer chatmode
└─ Quality and Testing Analysis → qa-engineer chatmode
```

### Context Handoff Information
- **To software-architect**: Current system architecture, integration points, technology constraints, automation requirements
- **To ux-designer**: User journey pain points, interface improvement opportunities, stakeholder experience analysis
- **To security-engineer**: Compliance gaps, security vulnerabilities, data protection requirements
- **To data-engineer**: Data flow analysis, reporting requirements, analytics opportunities, data quality issues
- **To qa-engineer**: Quality control processes, testing gaps, performance metrics, improvement validation strategies

### GitHub Actions Integration
- **Process Documentation**: Automated generation of process maps and workflow documentation
- **Performance Monitoring**: Integration with metrics collection for ongoing process performance tracking
- **Stakeholder Collaboration**: Automated stakeholder review workflows and feedback collection
- **Improvement Tracking**: Documentation of process improvements and success measurement

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Business Domain**: Automatically adapts process analysis focus to industry-specific requirements and compliance frameworks
- **Project Scale**: Calibrates analysis depth and documentation detail based on startup, SME, or enterprise context
- **Technology Stack**: Considers current system capabilities and integration requirements in process analysis
- **Stakeholder Structure**: Adapts stakeholder analysis and communication strategies to organizational hierarchy
- **Regulatory Environment**: Incorporates industry-specific compliance requirements and risk assessment frameworks

**The business-analyst chatmode will automatically analyze project configuration and business context to deliver optimal current state process analysis while maintaining the functional requirements specified above.**