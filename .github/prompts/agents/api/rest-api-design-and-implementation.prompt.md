---
description: Design and implement scalable, secure REST APIs following best practices with comprehensive validation, error handling, and documentation. Adapts to project specifications defined in copilot.instructions.md.
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

# REST API Design and Implementation

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Core API Architecture
- **RESTful Resource Design**: Create resource-based API endpoints following REST principles with proper HTTP method mapping
- **URL Structure Design**: Implement consistent, hierarchical URL patterns that reflect business domain relationships
- **Request/Response Design**: Define clear data contracts with comprehensive input validation and standardized response formats
- **HTTP Status Code Implementation**: Use appropriate HTTP status codes for all response scenarios with meaningful error messages

### Security Implementation
- **Authentication Strategy**: Implement robust authentication mechanism appropriate to business domain requirements
- **Authorization Controls**: Enforce role-based or attribute-based access control at resource and operation levels
- **Input Validation**: Comprehensive validation and sanitization of all incoming data with business rule enforcement
- **Data Protection**: Secure handling of sensitive data including encryption, masking, and audit trails

### Integration Capabilities
- **Frontend API Integration**: Design APIs optimized for frontend consumption with efficient data structures
- **External System Integration**: Support for third-party API integration with proper error handling and retry logic
- **Real-time Communication**: Implement WebSocket or Server-Sent Events for real-time data updates where needed
- **API Versioning**: Establish versioning strategy to ensure backward compatibility and smooth evolution

### Documentation and Testing
- **API Documentation**: Generate comprehensive OpenAPI/Swagger documentation with interactive examples
- **Integration Guides**: Create clear integration documentation with code examples and best practices
- **Automated Testing**: Implement comprehensive test suites including unit, integration, and contract tests
- **Performance Monitoring**: Establish monitoring and observability for API performance and health

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Project Context Analysis
```
1. Read copilot.instructions.md to extract:
   - Backend framework and primary language
   - Business domain and security requirements
   - Database technology and ORM preferences
   - Performance and scalability expectations

2. Analyze existing project structure:
   - Identify current API patterns and conventions
   - Understand authentication and authorization setup
   - Assess integration points and dependencies
   - Review existing testing and documentation approaches
```

### 2. Resource Modeling and Design
```
1. Business Domain Analysis:
   - Map business entities to REST resources
   - Define resource relationships and hierarchies
   - Identify CRUD operations and business actions
   - Plan nested resources and collection endpoints

2. API Contract Definition:
   - Design URL structure following REST conventions
   - Map HTTP methods to business operations
   - Define request and response schemas
   - Plan pagination, filtering, and search patterns
```

### 3. Technology-Adaptive Implementation
```
1. Framework Pattern Selection:
   - Apply detected framework best practices (Spring Boot, .NET Core, NestJS, FastAPI, etc.)
   - Use framework-appropriate architectural patterns
   - Implement framework-specific security mechanisms
   - Leverage framework testing and documentation tools

2. Database Integration:
   - Design efficient data access patterns
   - Implement optimized queries with proper indexing
   - Use appropriate ORM/ODM patterns for detected technology
   - Plan transaction management and data consistency
```

### 4. Quality and Security Enforcement
```
1. Security Implementation:
   - Configure authentication based on project requirements
   - Implement authorization with proper role/permission mapping
   - Add input validation and sanitization layers
   - Establish audit logging and monitoring

2. Performance Optimization:
   - Implement caching strategies appropriate to data patterns
   - Add pagination for collection endpoints
   - Optimize database queries and data fetching
   - Configure rate limiting and throttling
```

### 5. GitHub Integration and Automation
```
1. CI/CD Pipeline Setup:
   - Configure automated API testing with GitHub Actions
   - Implement security scanning for vulnerabilities
   - Set up automated documentation deployment
   - Create performance testing and monitoring

2. Documentation and Examples:
   - Generate OpenAPI/Swagger specifications
   - Create integration examples for frontend teams
   - Document authentication and error handling
   - Provide troubleshooting guides and best practices
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ RESTful Design Compliance
- **HTTP Methods**: Correct usage of GET (safe, idempotent), POST (create), PUT (idempotent update), PATCH (partial update), DELETE (idempotent removal)
- **Resource URLs**: Consistent naming with nouns for resources, proper nesting for relationships
- **Status Codes**: Appropriate HTTP status codes (200, 201, 400, 401, 403, 404, 409, 422, 500, etc.)
- **Content Negotiation**: Proper handling of Accept and Content-Type headers

### ✅ Security Standards Met
- **Authentication**: Robust authentication mechanism appropriate to business domain (JWT, OAuth2, API Keys, etc.)
- **Authorization**: Proper access control implementation with principle of least privilege
- **Input Validation**: Comprehensive validation preventing injection attacks and data corruption
- **HTTPS Enforcement**: All API endpoints secured with TLS encryption
- **Rate Limiting**: Protection against abuse with configurable rate limits

### ✅ Documentation Excellence
- **OpenAPI Specification**: Complete API documentation with request/response examples
- **Interactive Documentation**: Working API explorer with authentication setup
- **Integration Examples**: Clear code examples for common integration patterns
- **Error Documentation**: Comprehensive error codes and troubleshooting guides
- **Change Log**: Versioning documentation with migration guides

### ✅ Performance and Reliability
- **Response Times**: API endpoints respond within acceptable limits (< 200ms for simple queries)
- **Pagination**: Efficient pagination implementation for collection endpoints
- **Caching**: Appropriate caching strategies implemented where beneficial
- **Error Handling**: Graceful error handling with meaningful error messages
- **Monitoring**: Health checks and observability implemented

### ✅ GitHub Copilot Integration
- **Chatmode Integration**: Seamless transitions to related chatmodes (frontend-engineer, security-engineer, etc.)
- **GitHub Actions**: Automated testing, security scanning, and documentation deployment
- **Configuration Adaptation**: Reads and adapts to copilot.instructions.md project specifications
- **Workflow Automation**: CI/CD pipeline integrated with GitHub ecosystem

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Platform API
```yaml
Context: Online store with product catalog, order management, and user accounts
Technology Stack: Detected from copilot.instructions.md (e.g., Node.js + Express, Java + Spring Boot)
Business Domain: E-commerce with inventory management and payment processing

API Design Focus:
- Product catalog with categories, search, and filtering
- Shopping cart and order management with payment integration
- User authentication and profile management
- Inventory tracking with real-time updates

GitHub Copilot Workflow:
1. api-engineer chatmode → Design core API structure
2. security-engineer chatmode → Implement payment security and PCI compliance
3. frontend-engineer chatmode → Integrate with React/Angular frontend
4. qa-engineer chatmode → Comprehensive API testing strategy

Expected Deliverables:
- RESTful API with comprehensive product and order endpoints
- Secure payment processing integration
- Real-time inventory updates via WebSocket
- Complete OpenAPI documentation with frontend integration examples
```

### Scenario 2: Healthcare Management System
```yaml
Context: HIPAA-compliant patient data management with appointment scheduling
Technology Stack: Adapted to project configuration (.NET Core, Java + Spring Security)
Business Domain: Healthcare with strict privacy and compliance requirements

API Design Focus:
- Patient data management with HIPAA compliance
- Appointment scheduling and provider management
- Medical records with role-based access control
- Integration with Electronic Health Record (EHR) systems

GitHub Copilot Workflow:
1. api-engineer chatmode → Design HIPAA-compliant API structure
2. security-engineer chatmode → Implement advanced security and audit logging
3. data-engineer chatmode → Optimize for healthcare data patterns
4. deployment-engineer chatmode → HIPAA-compliant infrastructure deployment

Expected Deliverables:
- HIPAA-compliant API with comprehensive audit trails
- Role-based access control for different healthcare roles
- HL7 FHIR standard integration capabilities
- Security documentation and compliance validation
```

### Scenario 3: Financial Services API
```yaml
Context: Banking application with account management and transaction processing
Technology Stack: Enterprise-grade framework (Java + Spring Boot, .NET Core)
Business Domain: Financial services with PCI-DSS and regulatory compliance

API Design Focus:
- Account management with multi-factor authentication
- Secure transaction processing with fraud detection
- Regulatory reporting and audit trails
- Integration with external financial institutions

GitHub Copilot Workflow:
1. api-engineer chatmode → Design secure financial API architecture
2. security-engineer chatmode → Implement PCI-DSS compliance and threat protection
3. qa-engineer chatmode → Comprehensive security and performance testing
4. deployment-engineer chatmode → Secure, highly available deployment

Expected Deliverables:
- PCI-DSS compliant API with advanced security controls
- Fraud detection and prevention mechanisms
- Comprehensive audit logging and regulatory reporting
- High availability architecture with disaster recovery
```

### Scenario 4: Microservices Architecture
```yaml
Context: Distributed system with multiple API services and service mesh
Technology Stack: Containerized deployment (Docker, Kubernetes)
Business Domain: Large-scale application with service-oriented architecture

API Design Focus:
- Inter-service communication patterns
- API gateway integration and routing
- Service discovery and load balancing
- Distributed tracing and monitoring

GitHub Copilot Workflow:
1. api-engineer chatmode → Design service contracts and communication patterns
2. deployment-engineer chatmode → Container orchestration and service mesh
3. qa-engineer chatmode → Contract testing and end-to-end validation
4. Multiple chatmodes → Coordinate cross-service development

Expected Deliverables:
- Well-defined service contracts with API versioning
- Resilient inter-service communication with circuit breakers
- Comprehensive distributed tracing and monitoring
- Automated service deployment and scaling
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Initial API Design → api-engineer chatmode
├─ Security Requirements → security-engineer chatmode
├─ Database Integration → data-engineer chatmode
├─ Frontend Integration → frontend-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Deployment Pipeline → deployment-engineer chatmode
```

### Context Handoff Information
- **To security-engineer**: API endpoints, authentication requirements, data sensitivity levels
- **To frontend-engineer**: API contracts, data structures, integration patterns
- **To data-engineer**: Data access patterns, query optimization requirements
- **To qa-engineer**: API specifications, test scenarios, performance requirements
- **To deployment-engineer**: Infrastructure requirements, scaling needs, monitoring setup

### GitHub Actions Integration
- **API Testing Pipeline**: Automated endpoint testing with contract validation and performance benchmarks
- **Security Scanning**: Integrated SAST/DAST analysis with vulnerability assessment
- **Documentation Deployment**: Automatic OpenAPI documentation updates with version management
- **Contract Testing**: Consumer-driven contract testing with service integration validation

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Technology Stack**: Automatically detects backend framework and applies appropriate patterns
- **Business Domain**: Adapts API design to industry-specific requirements and compliance needs
- **Security Requirements**: Configures authentication and authorization based on project security specifications
- **Performance Needs**: Optimizes for scalability and performance requirements specified in project configuration
- **Integration Patterns**: Adapts to existing project architecture and integration requirements

**The api-engineer chatmode will automatically analyze project configuration and apply technology-appropriate implementation patterns while maintaining the functional requirements specified above.**