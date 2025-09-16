---
description: Design scalable, maintainable system architecture aligned with business requirements and technology stack, implementing appropriate architectural patterns and ensuring high quality standards.
tools:
  - codebase
  - search
  - editFiles
  - runCommands
model: claude-4-sonnet
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `software-architect` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# System Architecture Design

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Architecture Strategy
- **System Design**: Create scalable, maintainable architecture that aligns with business goals and technical requirements
- **Technology Integration**: Design technology stack integration patterns that support current and future business needs
- **Quality Attributes**: Ensure architecture supports performance, security, reliability, and maintainability requirements
- **Evolution Planning**: Design architecture evolution strategy from MVP through enterprise scale

### Business-Technology Alignment
- **Domain Architecture**: Translate business domain requirements into appropriate architectural patterns and structures
- **Stakeholder Requirements**: Balance technical excellence with business constraints, timelines, and resource limitations
- **Risk Management**: Identify and mitigate architectural risks while maintaining business value delivery
- **Compliance Integration**: Incorporate industry-specific compliance and regulatory requirements into architectural design

### Scalability and Performance Design
- **Growth Planning**: Design architecture that scales efficiently with user growth and data volume increases
- **Performance Optimization**: Create performance-focused architecture with appropriate caching, load balancing, and optimization strategies
- **Resource Efficiency**: Optimize architecture for cost-effective resource utilization across development and production environments
- **Monitoring Integration**: Design comprehensive observability and monitoring capabilities into core architecture

### Technology Stack Optimization
- **Framework Selection**: Choose and integrate appropriate frameworks, libraries, and tools based on project requirements
- **Integration Patterns**: Design efficient integration patterns between different system components and external services
- **Development Efficiency**: Create architecture that enhances developer productivity and maintains code quality
- **Deployment Strategy**: Design deployment and infrastructure patterns that support reliable, scalable operations

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Comprehensive Requirements Analysis
```
1. Read copilot.instructions.md to extract:
   - Business domain and functional requirements
   - Technology stack preferences and constraints
   - Performance and scalability expectations
   - Security and compliance requirements

2. Stakeholder Requirements Assessment:
   - Identify key stakeholders and their architectural concerns
   - Analyze quality attribute requirements (performance, security, usability)
   - Understand business constraints and growth projections
   - Review existing systems and integration requirements
```

### 2. Architectural Pattern Selection and Design
```
1. Pattern Analysis and Selection:
   - Evaluate architectural patterns based on requirements analysis
   - Select appropriate patterns (layered, microservices, event-driven, etc.)
   - Design pattern combinations that address specific business needs
   - Plan pattern evolution and migration strategies

2. System Decomposition:
   - Design system boundaries and component responsibilities
   - Create module and service decomposition strategies
   - Plan data flow and communication patterns
   - Design integration and interface specifications
```

### 3. Technology Stack Integration and Optimization
```
1. Technology Architecture:
   - Design technology stack integration patterns
   - Select frameworks and tools based on architectural requirements
   - Plan database architecture and data management strategies
   - Design security architecture and authentication patterns

2. Infrastructure Design:
   - Plan deployment architecture and infrastructure requirements
   - Design scalability and load balancing strategies
   - Create disaster recovery and backup strategies
   - Plan monitoring and observability architecture
```

### 4. Quality Attributes and Non-Functional Requirements
```
1. Performance Architecture:
   - Design performance optimization strategies
   - Plan caching and data access optimization
   - Create load testing and performance monitoring strategies
   - Design capacity planning and resource scaling

2. Security and Compliance Architecture:
   - Design security architecture with defense in depth
   - Plan authentication and authorization strategies
   - Create compliance monitoring and audit capabilities
   - Design data protection and privacy strategies
```

### 5. Implementation and Evolution Planning
```
1. Implementation Strategy:
   - Create phased implementation plan with clear milestones
   - Design development team structure and responsibilities
   - Plan technical debt management and code quality strategies
   - Create architecture documentation and governance processes

2. Evolution and Maintenance:
   - Design architecture evolution and migration strategies
   - Plan technology refresh and modernization approaches
   - Create architecture review and validation processes
   - Design change management and impact assessment procedures
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Business Alignment and Value
- **Requirements Fulfillment**: Architecture addresses all identified business and technical requirements
- **Stakeholder Satisfaction**: Architecture meets stakeholder expectations and constraints
- **Business Value**: Architecture enables efficient business value delivery and growth
- **Cost Effectiveness**: Architecture optimizes total cost of ownership and resource utilization

### ✅ Technical Excellence and Quality
- **Scalability**: Architecture scales efficiently with growth in users, data, and functionality
- **Performance**: Architecture meets performance requirements with appropriate optimization strategies
- **Reliability**: Architecture provides high availability and fault tolerance capabilities
- **Security**: Architecture implements comprehensive security controls and compliance measures

### ✅ Development and Operational Efficiency
- **Developer Productivity**: Architecture enhances development efficiency and code quality
- **Maintainability**: Architecture supports easy maintenance, updates, and troubleshooting
- **Deployment Efficiency**: Architecture enables reliable, automated deployment and operations
- **Monitoring Capability**: Architecture provides comprehensive observability and monitoring

### ✅ Evolution and Future-Proofing
- **Adaptability**: Architecture accommodates changing business requirements and technology evolution
- **Technology Migration**: Architecture supports technology stack updates and migrations
- **Growth Support**: Architecture scales with business growth without major restructuring
- **Innovation Enablement**: Architecture enables rapid innovation and feature development

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with other development chatmodes
- **Documentation Quality**: Comprehensive architectural documentation and decision records
- **Configuration Adaptation**: Proper adaptation to project technology stack and requirements
- **Implementation Support**: Architecture design supports GitHub Copilot development workflows

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Platform Architecture
```yaml
Context: Scalable e-commerce platform with complex product catalog and order management
Technology Stack: Detected from copilot.instructions.md (React, Node.js, PostgreSQL, Redis)
Business Domain: E-commerce with high transaction volume and global user base

Architecture Focus:
- Microservices architecture for independent scaling of catalog, orders, and payments
- Event-driven architecture for order processing and inventory management
- CQRS pattern for read/write optimization in product catalog
- API gateway for unified client access and rate limiting

GitHub Copilot Workflow:
1. software-architect chatmode → Design comprehensive system architecture
2. api-engineer chatmode → Implement microservices and API gateway patterns
3. data-engineer chatmode → Design database architecture and data flow
4. deployment-engineer chatmode → Implement scalable infrastructure and deployment

Expected Deliverables:
- Comprehensive architecture documentation with system diagrams
- Microservices decomposition with clear service boundaries
- Event-driven communication patterns for business processes
- Scalability and performance optimization strategies
```

### Scenario 2: Healthcare Management System Architecture
```yaml
Context: HIPAA-compliant healthcare platform with complex data privacy requirements
Technology Stack: Enterprise setup (.NET Core, Angular, SQL Server, Azure)
Business Domain: Healthcare with patient data, provider networks, and regulatory compliance

Architecture Focus:
- Layered architecture with strict data access controls
- Domain-driven design for healthcare business logic
- Comprehensive audit logging and compliance monitoring
- Zero-trust security architecture with fine-grained permissions

GitHub Copilot Workflow:
1. software-architect chatmode → Design HIPAA-compliant system architecture
2. security-engineer chatmode → Implement comprehensive security and compliance controls
3. data-engineer chatmode → Design healthcare data architecture with privacy controls
4. qa-engineer chatmode → Create compliance testing and validation strategies

Expected Deliverables:
- HIPAA-compliant architecture with comprehensive security controls
- Domain-driven design for healthcare business processes
- Data architecture with privacy and consent management
- Compliance monitoring and audit trail capabilities
```

### Scenario 3: Financial Trading Platform Architecture
```yaml
Context: High-frequency trading platform with real-time data processing requirements
Technology Stack: High-performance setup (Java, React, Apache Kafka, Redis, PostgreSQL)
Business Domain: Financial services with real-time trading and risk management

Architecture Focus:
- Event-sourcing architecture for audit trails and data consistency
- High-performance messaging with Apache Kafka for real-time data streams
- CQRS pattern for optimized read/write operations
- Circuit breaker and bulkhead patterns for system resilience

GitHub Copilot Workflow:
1. software-architect chatmode → Design high-performance trading system architecture
2. data-engineer chatmode → Implement real-time data processing and event sourcing
3. security-engineer chatmode → Design financial data security and compliance
4. qa-engineer chatmode → Create performance testing and system validation

Expected Deliverables:
- High-performance architecture with real-time data processing
- Event-sourcing implementation with comprehensive audit trails
- Risk management and compliance monitoring systems
- Performance optimization for high-frequency trading operations
```

### Scenario 4: IoT and Analytics Platform Architecture
```yaml
Context: IoT platform with massive data ingestion and real-time analytics
Technology Stack: Cloud-native setup (React, Python, Apache Kafka, InfluxDB, Kubernetes)
Business Domain: IoT with device management, data analytics, and machine learning

Architecture Focus:
- Lambda architecture for batch and real-time data processing
- Microservices architecture for device management and analytics
- Event-driven architecture for IoT data ingestion and processing
- Machine learning pipeline integration for predictive analytics

GitHub Copilot Workflow:
1. software-architect chatmode → Design scalable IoT data architecture
2. data-engineer chatmode → Implement data ingestion and analytics pipelines
3. deployment-engineer chatmode → Design cloud-native infrastructure and scaling
4. qa-engineer chatmode → Create performance testing for high-volume data processing

Expected Deliverables:
- Scalable IoT data architecture with real-time and batch processing
- Device management system with secure communication protocols
- Analytics pipeline with machine learning integration
- Cloud-native deployment with auto-scaling capabilities
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
System Architecture Design → software-architect chatmode (lead)
├─ API Design → api-engineer chatmode
├─ Data Architecture → data-engineer chatmode
├─ Security Architecture → security-engineer chatmode
├─ Frontend Architecture → frontend-engineer chatmode
├─ Quality Architecture → qa-engineer chatmode
└─ Infrastructure Architecture → deployment-engineer chatmode
```

### Context Handoff Information
- **To api-engineer**: Service boundaries, API contracts, integration patterns, communication protocols
- **To data-engineer**: Data architecture, storage patterns, data flow, consistency requirements
- **To security-engineer**: Security architecture, authentication patterns, compliance requirements
- **To frontend-engineer**: Frontend architecture, user experience patterns, performance requirements
- **To qa-engineer**: Quality attributes, testing strategies, performance requirements
- **To deployment-engineer**: Infrastructure requirements, scaling patterns, operational requirements

### GitHub Actions Integration
- **Architecture Validation**: Automated validation of architectural decisions and patterns
- **Documentation Generation**: Automated generation of architectural documentation and diagrams
- **Compliance Checking**: Automated validation of architectural compliance with standards
- **Performance Monitoring**: Automated monitoring of architectural quality attributes

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Business Domain**: Adapts architectural patterns to industry-specific requirements and compliance needs
- **Technology Stack**: Selects appropriate architectural patterns based on detected technology preferences
- **Project Scale**: Adjusts architectural complexity based on startup, SME, or enterprise requirements
- **Quality Attributes**: Prioritizes architectural quality attributes based on project specifications
- **Integration Requirements**: Adapts architecture to existing systems and integration constraints

**The software-architect chatmode will automatically analyze project configuration and business requirements to design optimal system architecture while maintaining the functional requirements specified above.**