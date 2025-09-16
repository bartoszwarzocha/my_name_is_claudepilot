---
name: swagger-to-angular-generation
description: |
  **🤖 GitHub Copilot Chatmode: @frontend-engineer**

  Expert Angular services and models generation from Swagger/OpenAPI with TypeScript integration and best practices for type-safe API integration.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt Angular generation patterns to project requirements.
---

# Angular Services and Models Generation from Swagger Documentation

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@frontend-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All Angular code generation tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Generate type-safe Angular services and models from Swagger/OpenAPI specifications that integrate seamlessly with Angular applications. Create production-ready code with comprehensive error handling, authentication integration, and maintainable architecture patterns.

**Angular Generation Requirements:**
- Parse Swagger/OpenAPI specifications and generate comprehensive TypeScript interfaces
- Create Angular services with proper HTTP client integration and error handling
- Implement authentication and authorization patterns for secure API communication
- Generate comprehensive validation and transformation utilities for API data
- Configure testing infrastructure for generated services and models
- Establish maintenance patterns for API specification updates and regeneration

## 🔄 HIGH-LEVEL ALGORITHMS

**Phase 1: API Specification Analysis**
1. Read .github/copilot.instructions.md to understand Angular version, architecture patterns, and project conventions
2. Parse Swagger/OpenAPI specification to identify endpoints, models, and authentication patterns
3. Analyze existing Angular service patterns and HTTP client configuration
4. Plan code generation strategy based on project structure and naming conventions
5. Identify custom transformations and validation requirements for business logic

**Phase 2: Model and Interface Generation**
1. Generate TypeScript interfaces for all API models with comprehensive type definitions
2. Create enum types for API constants and status codes
3. Implement validation schemas and transformation utilities for data mapping
4. Generate request and response type definitions for all endpoints
5. Create utility types for pagination, filtering, and common API patterns

**Phase 3: Service Implementation**
1. Generate Angular services with HTTP client integration and dependency injection
2. Implement authentication patterns including token management and refresh logic
3. Create error handling strategies with user-friendly error messages
4. Configure request and response interceptors for common functionality
5. Implement caching strategies and offline functionality where appropriate

**Phase 4: Testing and Documentation**
1. Generate comprehensive unit tests for all services and data transformations
2. Create integration tests for API communication and error scenarios
3. Implement mock services for development and testing environments
4. Generate documentation for service usage and API integration patterns
5. Create maintenance scripts for API specification updates and code regeneration

## ✓ VALIDATION CRITERIA

**Code Generation Quality:**
- Generated TypeScript interfaces provide complete type safety with zero 'any' types
- Angular services follow established patterns with proper dependency injection
- Error handling covers all API scenarios with actionable user feedback
- Authentication integration works seamlessly with existing security patterns

**Architecture Integration:**
- Generated code follows project naming conventions and architectural patterns
- Services integrate properly with existing HTTP client configuration
- Code generation process is repeatable and maintains consistency across updates
- Generated tests provide comprehensive coverage for API interactions

**Production Readiness:**
- Generated services handle network failures and timeout scenarios gracefully
- Performance optimization includes proper HTTP caching and request debouncing
- Security patterns protect against common API vulnerabilities
- Monitoring and logging provide adequate visibility for production debugging

**Maintenance and Updates:**
- API specification changes can be incorporated with minimal manual intervention
- Generated code remains compatible with Angular framework updates
- Documentation enables team understanding and consistent usage patterns
- Version control integration tracks generated code changes appropriately

## 💡 USAGE EXAMPLES

**E-commerce API Integration:**
```
API Focus: Product management, cart operations, order processing, payment integration
- Models: Product, CartItem, Order, Payment, Customer, Inventory
- Services: ProductService, CartService, OrderService, PaymentService
- Authentication: JWT tokens, customer sessions, administrative access
- Validation: Price calculations, inventory checks, payment verification
- Testing: Mock payment processing, inventory simulation, order workflow validation
```

**Enterprise Resource Planning API:**
```
API Focus: User management, resource allocation, reporting, workflow automation
- Models: Employee, Project, Resource, Report, Workflow, Permission
- Services: UserService, ProjectService, ResourceService, ReportService
- Authentication: Role-based access, SSO integration, permission validation
- Validation: Resource availability, workflow state transitions, report data integrity
- Testing: Permission scenarios, workflow state management, report generation
```

**Healthcare Management API:**
```
API Focus: Patient records, appointment scheduling, medical data, compliance
- Models: Patient, Appointment, MedicalRecord, Provider, Insurance, Compliance
- Services: PatientService, AppointmentService, MedicalService, ComplianceService
- Authentication: HIPAA-compliant access, multi-factor authentication, audit trails
- Validation: Medical data integrity, appointment constraints, compliance requirements
- Testing: Privacy scenarios, appointment conflicts, medical record validation
```

**Financial Services API:**
```
API Focus: Account management, transaction processing, reporting, regulatory compliance
- Models: Account, Transaction, Portfolio, Report, Compliance, AuditTrail
- Services: AccountService, TransactionService, PortfolioService, ComplianceService
- Authentication: Multi-level security, transaction authorization, regulatory access
- Validation: Financial calculations, regulatory compliance, audit trail integrity
- Testing: Transaction scenarios, compliance validation, security verification
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@frontend-engineer** leads Angular service generation and TypeScript integration
- **@backend-engineer** coordination for API specification validation and endpoint testing
- **@security-engineer** consultation for authentication patterns and secure communication
- **@qa-engineer** collaboration for testing strategy and validation scenarios

**Integration with GitHub Copilot IDE:**
- Intelligent code generation based on Swagger specification analysis
- Automated TypeScript interface creation with comprehensive type definitions
- Context-aware Angular service patterns with error handling and authentication
- Real-time validation and testing suggestions during API integration development

---
*This prompt enables expert Angular services and models generation from Swagger/OpenAPI specifications with type-safe integration and production-ready patterns for all business domains and project scales.*