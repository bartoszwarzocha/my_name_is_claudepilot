---
description: Generate comprehensive Swagger/OpenAPI documentation from existing backend code with complete endpoint coverage, model definitions, and interactive examples. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - search
  - editFiles
  - runCommands
  - githubRepo
  - vscodeAPI
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `api-engineer` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Swagger/OpenAPI Documentation Generation

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive API Documentation
- **Endpoint Discovery**: Analyze existing backend code to identify all API endpoints with complete parameter and response definitions
- **Model Documentation**: Extract and document all data models, DTOs, and entity relationships from codebase
- **Interactive Documentation**: Generate interactive Swagger UI with working examples and API testing capabilities
- **Business Logic Documentation**: Capture business rules, validation constraints, and domain-specific logic in API documentation

### Code-First Documentation Generation
- **Framework Integration**: Integrate with existing backend frameworks to extract API metadata and annotations
- **Automatic Updates**: Establish automated documentation generation workflows that stay synchronized with code changes
- **Annotation Enhancement**: Add or enhance existing code annotations to improve documentation quality
- **Version Management**: Generate versioned documentation with backward compatibility and change tracking

### Production-Ready Documentation Standards
- **Security Documentation**: Document authentication, authorization, and security requirements for each endpoint
- **Error Handling**: Comprehensive documentation of error responses, status codes, and troubleshooting guides
- **Usage Examples**: Provide realistic usage examples, code samples, and integration patterns
- **Performance Guidelines**: Document performance expectations, rate limits, and optimization recommendations

### Integration and Distribution
- **Client SDK Generation**: Enable automatic client SDK generation from OpenAPI specifications
- **API Portal Integration**: Prepare documentation for API portals and developer documentation sites
- **Testing Integration**: Generate test cases and validation scenarios from API specifications
- **Monitoring Setup**: Configure API monitoring and observability based on documented specifications

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Backend Framework Analysis and Configuration
```
1. Read copilot.instructions.md to extract:
   - Backend framework and technology stack
   - Existing API documentation approach and tools
   - Business domain and documentation requirements
   - Integration and client generation needs

2. Analyze existing codebase structure:
   - Identify API controllers, routes, and endpoint definitions
   - Discover data models, DTOs, and validation annotations
   - Understand authentication and authorization patterns
   - Review existing documentation and annotation coverage
```

### 2. API Metadata Extraction and Enhancement
```
1. Framework-Specific Extraction:
   - Extract endpoint definitions using framework-appropriate tools
   - Parse existing annotations and documentation comments
   - Identify request/response models and validation rules
   - Discover authentication and security requirements

2. Documentation Enhancement:
   - Add missing OpenAPI annotations where needed
   - Enhance existing documentation with business context
   - Create comprehensive model documentation
   - Document error scenarios and edge cases
```

### 3. OpenAPI Specification Generation
```
1. Specification Assembly:
   - Generate comprehensive OpenAPI 3.0+ specification
   - Include all discovered endpoints with complete metadata
   - Document security schemes and authentication flows
   - Create detailed model schemas with validation rules

2. Documentation Enrichment:
   - Add business context and usage examples
   - Include performance and rate limiting information
   - Document API versioning and deprecation policies
   - Create comprehensive error response documentation
```

### 4. Interactive Documentation and Testing
```
1. Swagger UI Configuration:
   - Configure interactive Swagger UI with project branding
   - Set up authentication testing capabilities
   - Create realistic example data and test scenarios
   - Enable API testing directly from documentation

2. Advanced Features:
   - Configure code generation for multiple languages
   - Set up automated testing from OpenAPI specifications
   - Create mock servers for development and testing
   - Generate Postman collections and other integration tools
```

### 5. Automation and Maintenance
```
1. CI/CD Integration:
   - Set up automated documentation generation in GitHub Actions
   - Configure documentation deployment to GitHub Pages or API portals
   - Implement documentation validation and quality checks
   - Create alerts for documentation drift or missing coverage

2. Maintenance Workflows:
   - Establish documentation review processes
   - Create templates for new API development
   - Set up monitoring for documentation completeness
   - Plan periodic documentation audits and improvements
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Documentation Completeness
- **Endpoint Coverage**: All API endpoints documented with complete request/response specifications
- **Model Documentation**: All data models and DTOs properly documented with field descriptions
- **Security Requirements**: Authentication and authorization clearly documented for all endpoints
- **Error Responses**: Comprehensive error response documentation with status codes and examples

### ✅ Technical Accuracy
- **Code Synchronization**: Documentation accurately reflects current codebase and API behavior
- **Validation Rules**: All input validation and business rules properly documented
- **Data Types**: Accurate data type definitions with proper constraints and formats
- **API Versioning**: Version information and compatibility requirements clearly specified

### ✅ Usability and Quality
- **Interactive Testing**: Swagger UI allows successful API testing with authentication
- **Example Quality**: Realistic examples that demonstrate proper API usage patterns
- **Error Guidance**: Clear troubleshooting information and common error scenarios
- **Integration Support**: Documentation supports client SDK generation and integration

### ✅ Production Standards
- **Performance Information**: Response time expectations and rate limiting documented
- **Security Guidelines**: Security best practices and compliance requirements included
- **Monitoring Integration**: Documentation supports observability and monitoring setup
- **Change Management**: Version control and change tracking properly implemented

### ✅ GitHub Copilot Integration
- **Automated Generation**: Documentation automatically generated and updated via GitHub Actions
- **Chatmode Coordination**: Seamless integration with frontend-engineer for client integration
- **Configuration Adaptation**: Proper adaptation to project technology stack and requirements
- **Quality Validation**: Automated validation of documentation completeness and accuracy

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Spring Boot E-commerce API Documentation
```yaml
Context: Large-scale e-commerce platform with Spring Boot REST APIs
Technology Stack: Detected from copilot.instructions.md (Java, Spring Boot, Spring Security, JPA)
Business Domain: E-commerce with product catalog, orders, and payment processing

Documentation Focus:
- Product catalog APIs with complex search and filtering
- Order management with multi-step checkout process
- Payment integration with security and compliance requirements
- User management with role-based access control

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate comprehensive OpenAPI documentation from Spring Boot annotations
2. security-engineer chatmode → Document security requirements and compliance measures
3. frontend-engineer chatmode → Generate TypeScript client SDK for React integration
4. qa-engineer chatmode → Create automated testing from OpenAPI specifications

Expected Deliverables:
- Complete OpenAPI 3.0 specification with Spring Boot integration
- Interactive Swagger UI with authentication testing capability
- Generated TypeScript client SDK with type safety
- Automated documentation deployment via GitHub Actions
```

### Scenario 2: .NET Core Healthcare API Documentation
```yaml
Context: HIPAA-compliant healthcare platform with .NET Core Web API
Technology Stack: Enterprise setup (.NET Core, Entity Framework, Azure AD)
Business Domain: Healthcare with patient data management and compliance requirements

Documentation Focus:
- Patient data APIs with privacy and consent management
- Provider network APIs with credential verification
- Appointment scheduling with availability optimization
- Medical records with audit trail requirements

GitHub Copilot Workflow:
1. api-engineer chatmode → Extract documentation from .NET Core attributes and XML comments
2. security-engineer chatmode → Document HIPAA compliance and data protection measures
3. data-engineer chatmode → Document data relationships and integrity constraints
4. qa-engineer chatmode → Generate compliance test scenarios from specifications

Expected Deliverables:
- HIPAA-compliant API documentation with comprehensive audit requirements
- Generated C# client SDK with healthcare data models
- Compliance validation testing integrated with CI/CD
- Secure documentation portal with access controls
```

### Scenario 3: Node.js Financial Services API Documentation
```yaml
Context: Banking platform with Node.js/Express APIs and strict regulatory requirements
Technology Stack: Financial setup (Node.js, Express, TypeScript, MongoDB)
Business Domain: Financial services with transaction processing and regulatory compliance

Documentation Focus:
- Account management APIs with KYC and compliance checks
- Transaction processing with fraud detection integration
- Regulatory reporting APIs with audit trail requirements
- Risk management APIs with real-time monitoring

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate OpenAPI documentation from Express routes and TypeScript types
2. security-engineer chatmode → Document PCI-DSS compliance and security measures
3. qa-engineer chatmode → Create performance and security testing scenarios
4. deployment-engineer chatmode → Set up secure documentation deployment

Expected Deliverables:
- PCI-DSS compliant API documentation with security controls
- Generated JavaScript/TypeScript client libraries
- Automated security testing from API specifications
- Integration with banking compliance and audit systems
```

### Scenario 4: Python FastAPI Microservices Documentation
```yaml
Context: Microservices architecture with Python FastAPI services
Technology Stack: Modern setup (Python, FastAPI, Pydantic, Docker, Kubernetes)
Business Domain: Distributed system with multiple business capabilities

Documentation Focus:
- Service-specific API documentation with inter-service communication
- Data models with Pydantic validation and serialization
- Authentication and authorization across service boundaries
- Service discovery and API gateway integration

GitHub Copilot Workflow:
1. api-engineer chatmode → Generate comprehensive OpenAPI docs from FastAPI automatic generation
2. deployment-engineer chatmode → Document service deployment and discovery patterns
3. qa-engineer chatmode → Create contract testing between services
4. frontend-engineer chatmode → Generate client libraries for multiple services

Expected Deliverables:
- Comprehensive microservices API documentation with service relationships
- Generated Python client libraries for inter-service communication
- Contract testing automation with service API specifications
- API gateway integration with unified documentation portal
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
API Documentation Generation → api-engineer chatmode (lead)
├─ Security Documentation → security-engineer chatmode
├─ Client SDK Generation → frontend-engineer chatmode
├─ Testing Integration → qa-engineer chatmode
└─ Documentation Deployment → deployment-engineer chatmode
```

### Context Handoff Information
- **To security-engineer**: Security requirements, authentication flows, compliance documentation needs
- **To frontend-engineer**: OpenAPI specifications, client SDK requirements, integration patterns
- **To qa-engineer**: API specifications for testing, performance requirements, validation scenarios
- **To deployment-engineer**: Documentation deployment requirements, portal integration, monitoring setup

### GitHub Actions Integration
- **Documentation Generation**: Automated OpenAPI specification generation from code changes
- **Quality Validation**: Automated validation of documentation completeness and accuracy
- **SDK Generation**: Automatic client SDK generation and publishing
- **Portal Deployment**: Automated deployment to documentation portals and GitHub Pages

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Backend Framework**: Automatically detects and applies framework-specific documentation extraction (Spring Boot, .NET Core, FastAPI, Express)
- **Business Domain**: Adapts documentation standards to industry-specific requirements and compliance needs
- **Integration Requirements**: Configures client SDK generation and API portal integration based on project needs
- **Security Specifications**: Documents security requirements and compliance measures based on project specifications
- **Documentation Standards**: Adapts to existing documentation practices and quality requirements

**The api-engineer chatmode will automatically analyze project configuration and apply appropriate documentation generation patterns while maintaining the functional requirements specified above.**