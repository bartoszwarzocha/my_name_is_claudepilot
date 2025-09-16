---
description: Generate complete, production-ready API endpoints from Swagger/OpenAPI specifications with proper validation, error handling, and security implementation. Adapts to technology stack defined in copilot.instructions.md.
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

# API Endpoint Generation from Swagger/OpenAPI Specifications

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Design-First API Implementation
- **Specification Analysis**: Parse and analyze existing Swagger/OpenAPI specifications to understand API contracts and requirements
- **Endpoint Generation**: Generate complete API endpoint implementations that match specification requirements exactly
- **Model Implementation**: Create data models, DTOs, and validation logic based on OpenAPI schema definitions
- **Contract Validation**: Ensure generated code maintains strict adherence to API specification contracts

### Production-Ready Code Generation
- **Framework Integration**: Generate code using appropriate backend framework patterns and conventions
- **Security Implementation**: Implement authentication, authorization, and security measures defined in API specifications
- **Error Handling**: Create comprehensive error handling with proper HTTP status codes and error responses
- **Input Validation**: Implement robust input validation based on OpenAPI schema constraints and business rules

### Business Logic Integration
- **Service Layer Design**: Create proper service layer architecture for business logic implementation
- **Data Access Patterns**: Generate appropriate data access layer integration with ORM and database patterns
- **Transaction Management**: Implement proper transaction handling and data consistency patterns
- **Integration Points**: Create hooks for external service integration and business rule enforcement

### Quality and Maintainability
- **Code Quality**: Generate clean, maintainable code following framework conventions and best practices
- **Testing Support**: Create test templates and mock implementations for comprehensive API testing
- **Documentation Sync**: Maintain synchronization between generated code and OpenAPI documentation
- **Version Compatibility**: Handle API versioning and backward compatibility requirements

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. OpenAPI Specification Analysis
```
1. Read copilot.instructions.md to extract:
   - Backend framework and technology preferences
   - Business domain and validation requirements
   - Security and authentication mechanisms
   - Database technology and ORM patterns

2. Parse OpenAPI specification:
   - Extract all endpoint definitions and operations
   - Analyze data models and schema definitions
   - Identify security schemes and authentication requirements
   - Review error response patterns and status codes
```

### 2. Framework-Specific Code Generation Strategy
```
1. Technology Stack Adaptation:
   - Select appropriate code generation templates for detected framework
   - Map OpenAPI types to framework-specific data types
   - Apply framework conventions for routing and controller patterns
   - Configure framework-specific validation and security mechanisms

2. Architecture Pattern Selection:
   - Design controller-service-repository patterns where appropriate
   - Plan dependency injection and configuration patterns
   - Create middleware and interceptor implementations
   - Design error handling and response formatting patterns
```

### 3. Model and Validation Implementation
```
1. Data Model Generation:
   - Generate entity classes from OpenAPI schemas
   - Implement validation annotations and constraints
   - Create DTO classes for request/response handling
   - Design model mapping and transformation logic

2. Business Logic Framework:
   - Create service interfaces from API operations
   - Generate service implementation templates
   - Implement business rule validation placeholders
   - Design transaction and error handling patterns
```

### 4. Security and Integration Implementation
```
1. Security Implementation:
   - Generate authentication and authorization code
   - Implement security schemes defined in OpenAPI specification
   - Create security middleware and filters
   - Design role-based access control patterns

2. Integration Layer:
   - Generate database integration code with ORM patterns
   - Create external service integration templates
   - Implement logging and monitoring integration
   - Design performance optimization patterns
```

### 5. Testing and Documentation Maintenance
```
1. Test Generation:
   - Create unit test templates for generated endpoints
   - Generate integration test scenarios from OpenAPI examples
   - Create mock implementations for external dependencies
   - Design contract testing validation

2. Documentation Synchronization:
   - Ensure generated code matches OpenAPI specification
   - Create code comments linking to specification requirements
   - Generate developer documentation for implementation
   - Plan specification update and regeneration workflows
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Specification Compliance
- **Contract Adherence**: Generated endpoints exactly match OpenAPI specification requirements
- **Data Model Accuracy**: All generated models conform to OpenAPI schema definitions
- **Security Implementation**: Authentication and authorization match specification security schemes
- **Response Format Compliance**: All responses match specified status codes and response schemas

### ✅ Production Quality
- **Code Quality**: Generated code follows framework best practices and conventions
- **Error Handling**: Comprehensive error handling with proper HTTP status codes and messages
- **Validation Implementation**: Robust input validation preventing malformed requests and data corruption
- **Performance Standards**: Generated code meets performance requirements for expected load

### ✅ Framework Integration
- **Technology Alignment**: Generated code uses appropriate framework patterns and conventions
- **Database Integration**: Proper ORM integration with efficient query patterns
- **Security Framework**: Integration with framework security mechanisms and authentication systems
- **Testing Support**: Generated test templates enable comprehensive API validation

### ✅ Maintainability and Evolution
- **Code Readability**: Generated code is clean, well-documented, and maintainable
- **Specification Sync**: Clear mapping between generated code and OpenAPI specification
- **Version Management**: Support for API versioning and backward compatibility
- **Regeneration Support**: Safe regeneration without losing custom business logic

### ✅ GitHub Copilot Integration
- **Automated Generation**: Code generation integrated with GitHub Actions workflows
- **Chatmode Coordination**: Seamless integration with other chatmodes for complete solution
- **Configuration Adaptation**: Proper adaptation to project technology stack and requirements
- **Quality Validation**: Automated validation of generated code against specifications

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Spring Boot E-commerce API Implementation
```yaml
Context: E-commerce platform with comprehensive OpenAPI specification for product and order management
Technology Stack: Detected from copilot.instructions.md (Java, Spring Boot, Spring Security, JPA)
Business Domain: E-commerce with complex product catalog and order processing

Implementation Focus:
- Product catalog endpoints with search and filtering capabilities
- Order management with multi-step checkout and payment processing
- User authentication and role-based access control
- Inventory management with real-time stock updates

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate Spring Boot controllers and services from OpenAPI spec
2. data-engineer chatmode → Implement JPA entities and repository patterns
3. security-engineer chatmode → Implement Spring Security integration
4. qa-engineer chatmode → Generate comprehensive test suites for all endpoints

Expected Deliverables:
- Complete Spring Boot REST controllers with proper annotations
- JPA entities with validation and relationship mapping
- Spring Security configuration with JWT authentication
- Comprehensive test suite with MockMvc integration testing
```

### Scenario 2: .NET Core Healthcare API Implementation
```yaml
Context: HIPAA-compliant healthcare platform with detailed OpenAPI specification
Technology Stack: Enterprise setup (.NET Core, Entity Framework, Azure AD)
Business Domain: Healthcare with patient data management and regulatory compliance

Implementation Focus:
- Patient data management with comprehensive privacy controls
- Provider network integration with credential verification
- Appointment scheduling with complex availability rules
- Medical records with audit trail and compliance requirements

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate .NET Core Web API controllers from OpenAPI specification
2. security-engineer chatmode → Implement HIPAA-compliant security and audit logging
3. data-engineer chatmode → Create Entity Framework models with healthcare data patterns
4. qa-engineer chatmode → Generate compliance testing and validation scenarios

Expected Deliverables:
- .NET Core API controllers with comprehensive attribute-based routing
- Entity Framework models with healthcare data validation
- Azure AD integration with role-based authorization
- HIPAA compliance testing and audit trail validation
```

### Scenario 3: Node.js Financial Services API Implementation
```yaml
Context: Banking platform with strict OpenAPI specification for financial transactions
Technology Stack: Financial setup (Node.js, Express, TypeScript, PostgreSQL)
Business Domain: Financial services with transaction processing and regulatory requirements

Implementation Focus:
- Account management with KYC and compliance validation
- Transaction processing with fraud detection integration
- Regulatory reporting with comprehensive audit requirements
- Risk management with real-time monitoring and alerting

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate Express.js routes and TypeScript interfaces from OpenAPI
2. security-engineer chatmode → Implement PCI-DSS compliance and fraud detection
3. data-engineer chatmode → Create PostgreSQL integration with transaction safety
4. deployment-engineer chatmode → Set up secure deployment with monitoring

Expected Deliverables:
- Express.js routes with comprehensive TypeScript type safety
- Financial transaction models with validation and audit logging
- PCI-DSS compliant security implementation
- Real-time monitoring and fraud detection integration
```

### Scenario 4: Python FastAPI Microservices Implementation
```yaml
Context: Microservices architecture with detailed OpenAPI specifications for each service
Technology Stack: Modern setup (Python, FastAPI, Pydantic, PostgreSQL, Docker)
Business Domain: Distributed system with multiple business capabilities

Implementation Focus:
- Service-specific endpoint implementation with inter-service communication
- Pydantic models with comprehensive validation and serialization
- Authentication and authorization across service boundaries
- API gateway integration and service discovery

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate FastAPI endpoints with automatic OpenAPI integration
2. deployment-engineer chatmode → Implement service discovery and gateway integration
3. qa-engineer chatmode → Create contract testing between microservices
4. security-engineer chatmode → Implement distributed security and authorization

Expected Deliverables:
- FastAPI endpoints with automatic request/response validation
- Pydantic models with comprehensive business rule validation
- Inter-service communication with proper error handling
- Microservices testing with contract validation
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
OpenAPI Code Generation → api-engineer chatmode (lead)
├─ Data Model Implementation → data-engineer chatmode
├─ Security Implementation → security-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Deployment Pipeline → deployment-engineer chatmode
```

### Context Handoff Information
- **To data-engineer**: Data models, database schemas, ORM patterns, transaction requirements
- **To security-engineer**: Security schemes, authentication flows, authorization requirements
- **To qa-engineer**: API specifications for testing, validation scenarios, contract testing
- **To deployment-engineer**: Service deployment requirements, monitoring setup, infrastructure needs

### GitHub Actions Integration
- **Code Generation**: Automated endpoint generation from OpenAPI specification updates
- **Specification Validation**: Automated validation of generated code against OpenAPI contracts
- **Quality Assurance**: Automated testing of generated endpoints with specification compliance
- **Documentation Sync**: Automated synchronization between code and OpenAPI documentation

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Backend Framework**: Automatically detects and applies framework-specific code generation patterns
- **Business Domain**: Adapts generated code to industry-specific requirements and validation rules
- **Security Requirements**: Implements security patterns based on project specifications and compliance needs
- **Database Technology**: Configures appropriate ORM patterns and data access strategies
- **Performance Expectations**: Optimizes generated code for scalability and performance requirements

**The api-engineer chatmode will automatically analyze project configuration and OpenAPI specifications to generate production-ready endpoint implementations while maintaining the functional requirements specified above.**