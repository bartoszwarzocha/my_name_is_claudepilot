---
description: Design and implement scalable microservices architecture with proper service decomposition, inter-service communication, and resilience patterns. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
  - vscodeAPI
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `api-engineer` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Microservices Architecture Patterns

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Service Architecture Design
- **Service Decomposition**: Design domain-driven service boundaries with clear business capabilities and data ownership
- **Service Communication**: Establish efficient inter-service communication patterns with proper protocols and data formats
- **Data Management**: Implement distributed data management strategies with consistency and transaction patterns
- **Service Discovery**: Create dynamic service discovery and registration mechanisms for scalable service ecosystems

### Resilience and Reliability
- **Fault Tolerance**: Implement circuit breaker, retry, and timeout patterns to handle service failures gracefully
- **Load Balancing**: Design intelligent load distribution strategies across service instances and availability zones
- **Health Monitoring**: Establish comprehensive health checks and observability across the entire service ecosystem
- **Graceful Degradation**: Implement fallback mechanisms and partial functionality during service outages

### Distributed System Patterns
- **API Gateway**: Design centralized API gateway for routing, authentication, and cross-cutting concerns
- **Event-Driven Architecture**: Implement asynchronous messaging patterns for loose coupling and scalability
- **Distributed Transactions**: Handle data consistency across services using saga patterns and compensating transactions
- **Configuration Management**: Centralized configuration management with environment-specific settings

### Security and Governance
- **Service Security**: Implement secure inter-service communication with authentication and authorization
- **Access Control**: Design distributed authorization patterns with proper permission propagation
- **Audit and Compliance**: Establish comprehensive logging and audit trails across distributed services
- **Version Management**: Plan service versioning strategies for backward compatibility and evolution

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Domain Analysis and Service Boundaries
```
1. Read copilot.instructions.md to extract:
   - Business domain and functional requirements
   - Technology stack and deployment preferences
   - Security and compliance requirements
   - Performance and scalability expectations

2. Domain-Driven Design Analysis:
   - Identify bounded contexts and business capabilities
   - Map domain entities and aggregates
   - Define service boundaries based on business logic cohesion
   - Plan data ownership and responsibility distribution
```

### 2. Service Architecture Planning
```
1. Service Design Patterns:
   - Define service interfaces and contracts
   - Plan service communication protocols (REST, GraphQL, gRPC, messaging)
   - Design data models and database-per-service patterns
   - Plan service deployment and scaling strategies

2. Integration Architecture:
   - Design API gateway for external client access
   - Plan service mesh for internal communication
   - Define event streaming and messaging patterns
   - Create service registry and discovery mechanisms
```

### 3. Resilience Implementation
```
1. Fault Tolerance Patterns:
   - Implement circuit breaker patterns for service protection
   - Design retry mechanisms with exponential backoff
   - Create timeout and bulkhead patterns for resource isolation
   - Plan graceful degradation and fallback strategies

2. Monitoring and Observability:
   - Implement distributed tracing across service calls
   - Create centralized logging with correlation IDs
   - Design metrics collection and alerting systems
   - Plan health check endpoints and monitoring dashboards
```

### 4. Data and Transaction Management
```
1. Data Architecture:
   - Design database-per-service patterns
   - Plan data synchronization and eventual consistency
   - Implement event sourcing where appropriate
   - Create data access patterns and API design

2. Distributed Transaction Handling:
   - Implement saga patterns for long-running transactions
   - Design compensating transaction mechanisms
   - Plan event-driven consistency models
   - Create transaction monitoring and rollback capabilities
```

### 5. Deployment and Operations
```
1. Infrastructure Automation:
   - Design containerization strategy for services
   - Plan orchestration with Kubernetes or container platforms
   - Create CI/CD pipelines for independent service deployment
   - Implement infrastructure as code for consistent environments

2. Service Management:
   - Design service versioning and backward compatibility
   - Plan rolling deployment and blue-green strategies
   - Create service configuration management
   - Implement security scanning and compliance validation
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Architecture Quality
- **Service Boundaries**: Clear domain boundaries with minimal coupling and high cohesion
- **Interface Design**: Well-defined service contracts with proper versioning and backward compatibility
- **Data Ownership**: Each service owns its data with clear responsibility boundaries
- **Scalability**: Services can scale independently based on load and performance requirements

### ✅ Resilience Standards
- **Fault Tolerance**: Circuit breakers, retries, and timeouts properly implemented
- **Service Health**: Comprehensive health checks and self-healing capabilities
- **Graceful Degradation**: System maintains partial functionality during service failures
- **Recovery Mechanisms**: Automatic recovery and manual intervention procedures defined

### ✅ Communication Excellence
- **Protocol Efficiency**: Appropriate communication protocols chosen for different interaction patterns
- **Message Reliability**: Guaranteed message delivery and duplicate handling where required
- **Service Discovery**: Dynamic service registration and discovery working correctly
- **Load Distribution**: Intelligent load balancing across service instances

### ✅ Security Implementation
- **Inter-Service Security**: Secure communication with proper authentication and encryption
- **Authorization**: Distributed authorization with proper permission propagation
- **Data Protection**: Sensitive data properly protected in transit and at rest
- **Audit Capabilities**: Comprehensive audit logging across all service interactions

### ✅ Operational Excellence
- **Monitoring Coverage**: Complete observability across all services and interactions
- **Deployment Automation**: Automated CI/CD pipelines for independent service deployment
- **Configuration Management**: Centralized configuration with environment-specific settings
- **Documentation**: Comprehensive service documentation and integration guides

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Microservices Platform
```yaml
Context: Large-scale e-commerce platform with independent business capabilities
Technology Stack: Detected from copilot.instructions.md (Java/Spring Boot, .NET Core, Node.js)
Business Domain: E-commerce with catalog, orders, payments, and user management

Microservices Design:
- Product Catalog Service (product data, search, recommendations)
- Order Management Service (order processing, workflow, status tracking)
- Payment Service (payment processing, fraud detection, billing)
- User Service (authentication, profile management, preferences)
- Inventory Service (stock management, reservation, allocation)
- Notification Service (email, SMS, push notifications)

GitHub Copilot Workflow:
1. api-engineer chatmode → Design service boundaries and communication patterns
2. data-engineer chatmode → Plan distributed data architecture and consistency
3. security-engineer chatmode → Implement inter-service security and compliance
4. deployment-engineer chatmode → Container orchestration and service mesh

Expected Deliverables:
- Domain-driven service decomposition with clear boundaries
- Event-driven architecture for order processing workflows
- Resilient payment processing with circuit breakers and retries
- Comprehensive monitoring and distributed tracing
```

### Scenario 2: Financial Services Microservices
```yaml
Context: Banking platform with strict regulatory compliance and high availability
Technology Stack: Enterprise-grade (.NET Core, Java/Spring Security, Service Mesh)
Business Domain: Financial services with account management, transactions, and compliance

Microservices Design:
- Account Service (account management, balance tracking)
- Transaction Service (payment processing, transaction history)
- Risk Management Service (fraud detection, compliance monitoring)
- Customer Service (KYC, customer data, relationship management)
- Reporting Service (regulatory reporting, analytics)
- Audit Service (transaction logging, compliance tracking)

GitHub Copilot Workflow:
1. api-engineer chatmode → Design secure financial service architecture
2. security-engineer chatmode → Implement PCI-DSS and banking compliance
3. qa-engineer chatmode → Comprehensive testing for financial regulations
4. deployment-engineer chatmode → High-availability infrastructure deployment

Expected Deliverables:
- PCI-DSS compliant microservices architecture
- Advanced security patterns for financial data protection
- Comprehensive audit logging and regulatory reporting
- High-availability deployment with disaster recovery
```

### Scenario 3: Healthcare Microservices Ecosystem
```yaml
Context: HIPAA-compliant healthcare platform with patient data and provider integration
Technology Stack: Secure enterprise setup (Java/Spring Security, .NET Core, API Gateway)
Business Domain: Healthcare with patient records, appointments, and provider networks

Microservices Design:
- Patient Service (patient data, medical history, HIPAA compliance)
- Provider Service (healthcare provider information, networks)
- Appointment Service (scheduling, availability, notifications)
- Medical Records Service (EMR integration, document management)
- Billing Service (insurance processing, claims management)
- Integration Service (HL7 FHIR, external healthcare systems)

GitHub Copilot Workflow:
1. api-engineer chatmode → Design HIPAA-compliant service architecture
2. security-engineer chatmode → Implement healthcare data security and privacy
3. data-engineer chatmode → Healthcare data integration and interoperability
4. qa-engineer chatmode → Compliance testing and security validation

Expected Deliverables:
- HIPAA-compliant microservices with comprehensive audit trails
- HL7 FHIR integration for healthcare data interoperability
- Advanced security patterns for patient data protection
- Comprehensive compliance monitoring and reporting
```

### Scenario 4: IoT and Real-time Data Platform
```yaml
Context: IoT platform with real-time data processing and device management
Technology Stack: Event-driven architecture (Apache Kafka, Redis, MongoDB)
Business Domain: IoT with device management, data processing, and analytics

Microservices Design:
- Device Management Service (device registration, configuration)
- Data Ingestion Service (real-time data collection, validation)
- Stream Processing Service (real-time analytics, event processing)
- Alert Service (threshold monitoring, notification management)
- Analytics Service (historical data analysis, reporting)
- Gateway Service (device communication, protocol translation)

GitHub Copilot Workflow:
1. api-engineer chatmode → Design event-driven microservices architecture
2. data-engineer chatmode → Real-time data processing and stream analytics
3. qa-engineer chatmode → Performance testing for high-throughput systems
4. deployment-engineer chatmode → Scalable container orchestration

Expected Deliverables:
- Event-driven microservices for real-time data processing
- Scalable stream processing with Apache Kafka integration
- Device management with secure communication protocols
- Comprehensive monitoring for IoT device networks
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Microservices Architecture → api-engineer chatmode
├─ Domain Analysis → business-analyst chatmode
├─ Data Architecture → data-engineer chatmode
├─ Security Design → security-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Infrastructure → deployment-engineer chatmode
```

### Context Handoff Information
- **To data-engineer**: Service data boundaries, consistency requirements, integration patterns
- **To security-engineer**: Service communication security, authorization patterns, compliance needs
- **To qa-engineer**: Service contracts, integration testing, performance requirements
- **To deployment-engineer**: Container requirements, orchestration needs, monitoring setup
- **To business-analyst**: Service boundaries validation, business capability mapping

### GitHub Actions Integration
- **Service Testing**: Automated testing for service contracts and integration points
- **Security Scanning**: Microservices-specific security analysis and vulnerability detection
- **Deployment Automation**: Independent service deployment with rolling updates
- **Infrastructure Validation**: Service mesh and infrastructure compliance testing

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Technology Stack**: Automatically detects microservices frameworks and applies appropriate patterns
- **Business Domain**: Adapts service decomposition to industry-specific requirements and compliance
- **Infrastructure Preferences**: Configures deployment and orchestration based on project infrastructure
- **Security Requirements**: Implements security patterns based on project compliance and regulatory needs
- **Performance Expectations**: Optimizes service architecture for scalability and performance requirements

**The api-engineer chatmode will automatically analyze project configuration and apply microservices-appropriate architectural patterns while maintaining the functional requirements specified above.**