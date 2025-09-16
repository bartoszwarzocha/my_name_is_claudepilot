---
description: Implement comprehensive integration between frontend and backend applications with seamless communication, robust authentication, proper error handling, and efficient data flow. Adapts to technology stack specified in copilot.instructions.md.
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

# Frontend-Backend Integration

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Cross-Layer Communication Architecture
- **API Integration Patterns**: Establish efficient communication protocols between frontend and backend layers
- **Data Flow Optimization**: Design optimal data transfer patterns with proper serialization and caching strategies
- **Real-time Communication**: Implement bidirectional communication using WebSockets, Server-Sent Events, or similar technologies
- **Error Boundary Management**: Create comprehensive error handling across the entire application stack

### Authentication and Security Integration
- **Unified Authentication**: Implement seamless authentication flow between frontend and backend systems
- **Session Management**: Design secure session handling with proper token management and refresh mechanisms
- **Authorization Enforcement**: Ensure consistent permission enforcement across frontend UI and backend APIs
- **Security Headers**: Configure appropriate security headers and CORS policies for cross-origin communication

### State Synchronization and Management
- **Client-Server State Sync**: Maintain consistent application state between frontend and backend systems
- **Optimistic Updates**: Implement optimistic UI updates with proper rollback mechanisms for failed operations
- **Offline Capabilities**: Design offline-first patterns with data synchronization when connectivity is restored
- **Cache Coherence**: Ensure data consistency between frontend caches and backend data sources

### Developer Experience and Tooling
- **Type Safety**: Establish end-to-end type safety from backend APIs to frontend components
- **Development Workflow**: Create efficient development workflows with hot reloading and live API integration
- **Error Debugging**: Implement comprehensive error tracking and debugging across the full stack
- **Documentation Integration**: Generate and maintain up-to-date integration documentation and API contracts

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Technology Stack Analysis and Adaptation
```
1. Read copilot.instructions.md to extract:
   - Frontend framework and technology preferences
   - Backend framework and API architecture
   - Authentication and security requirements
   - Performance and real-time communication needs

2. Analyze existing project structure:
   - Identify current integration patterns and communication layers
   - Understand existing authentication and authorization setup
   - Assess current error handling and state management approaches
   - Review existing development and testing workflows
```

### 2. Integration Architecture Design
```
1. Communication Layer Design:
   - Define API contracts and data transfer objects
   - Plan request/response patterns and error handling
   - Design authentication token flow and refresh mechanisms
   - Plan real-time communication architecture if needed

2. State Management Strategy:
   - Design client-side state management patterns
   - Plan server state synchronization mechanisms
   - Create optimistic update and rollback strategies
   - Design offline capability and sync patterns
```

### 3. Security and Authentication Implementation
```
1. Authentication Flow Design:
   - Implement unified login/logout processes
   - Create secure token storage and management
   - Design session refresh and expiration handling
   - Plan role-based access control integration

2. Security Enforcement:
   - Configure CORS policies and security headers
   - Implement request/response validation
   - Create comprehensive audit logging
   - Plan security testing and vulnerability assessment
```

### 4. Performance and Reliability Optimization
```
1. Performance Optimization:
   - Implement efficient data fetching patterns
   - Design caching strategies at multiple layers
   - Create request batching and deduplication
   - Plan lazy loading and pagination strategies

2. Error Handling and Resilience:
   - Implement comprehensive error boundary patterns
   - Create retry mechanisms with exponential backoff
   - Design graceful degradation for service failures
   - Plan monitoring and alerting for integration issues
```

### 5. Development and Testing Integration
```
1. Development Workflow:
   - Configure development environment integration
   - Implement hot reloading and live API integration
   - Create comprehensive type generation and validation
   - Plan API mocking and testing strategies

2. Quality Assurance:
   - Implement end-to-end testing across full stack
   - Create integration testing for API contracts
   - Plan performance testing for data flow
   - Design security testing for authentication flows
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Communication Excellence
- **API Integration**: Seamless communication between frontend and backend with proper error handling
- **Data Consistency**: Consistent data flow and state synchronization across application layers
- **Performance Standards**: Efficient data transfer with response times meeting application requirements
- **Real-time Capabilities**: Real-time communication working correctly where required

### ✅ Security Implementation
- **Authentication Flow**: Secure and user-friendly authentication with proper token management
- **Authorization Enforcement**: Consistent permission checking across frontend and backend
- **Data Protection**: Sensitive data properly protected in transit and at rest
- **Security Headers**: Appropriate CORS and security header configuration

### ✅ Developer Experience
- **Type Safety**: End-to-end type safety from backend APIs to frontend components
- **Development Efficiency**: Smooth development workflow with hot reloading and live integration
- **Error Debugging**: Comprehensive error tracking and debugging capabilities
- **Documentation Quality**: Clear integration documentation and API contracts

### ✅ Reliability and Performance
- **Error Handling**: Robust error handling across the entire application stack
- **Offline Support**: Graceful handling of network issues and offline scenarios
- **Caching Efficiency**: Effective caching strategies reducing unnecessary API calls
- **Monitoring Coverage**: Comprehensive monitoring of integration points and performance

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless coordination between api-engineer and frontend-engineer chatmodes
- **GitHub Actions**: Automated testing for frontend-backend integration
- **Configuration Adaptation**: Proper adaptation to project technology stack
- **Workflow Automation**: CI/CD pipeline integration for full-stack deployment

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: React + Node.js E-commerce Integration
```yaml
Context: E-commerce platform with React frontend and Node.js/Express backend
Technology Stack: Detected from copilot.instructions.md (React, TypeScript, Node.js, PostgreSQL)
Business Domain: E-commerce with product browsing, cart management, and checkout

Integration Focus:
- Product catalog with search and filtering
- Shopping cart state synchronization
- Secure checkout process with payment integration
- Real-time inventory updates and notifications

GitHub Copilot Workflow:
1. api-engineer chatmode → Design REST API contracts and authentication
2. frontend-engineer chatmode → Implement React components with API integration
3. security-engineer chatmode → Secure payment flow and data protection
4. qa-engineer chatmode → End-to-end testing for purchase workflows

Expected Deliverables:
- Type-safe API integration with generated TypeScript interfaces
- Secure authentication flow with JWT token management
- Optimistic shopping cart updates with server synchronization
- Real-time inventory updates using WebSocket integration
```

### Scenario 2: Angular + .NET Enterprise Application
```yaml
Context: Enterprise business application with Angular frontend and .NET Core backend
Technology Stack: Enterprise setup (Angular, TypeScript, .NET Core, SQL Server)
Business Domain: Business management with complex data relationships and reporting

Integration Focus:
- Complex business entity management
- Advanced search and filtering with server-side processing
- Role-based access control with fine-grained permissions
- Real-time collaboration and notifications

GitHub Copilot Workflow:
1. api-engineer chatmode → Design .NET Core Web API with Entity Framework
2. frontend-engineer chatmode → Angular services and reactive forms integration
3. security-engineer chatmode → Enterprise security and compliance implementation
4. data-engineer chatmode → Optimize complex queries and reporting

Expected Deliverables:
- Comprehensive Angular services with RxJS reactive patterns
- .NET Core API with advanced authentication and authorization
- Entity relationship management with optimistic concurrency
- Real-time collaboration features using SignalR
```

### Scenario 3: Vue.js + Python Healthcare Platform
```yaml
Context: HIPAA-compliant healthcare platform with Vue.js frontend and Python backend
Technology Stack: Healthcare setup (Vue.js, Python/FastAPI, PostgreSQL)
Business Domain: Healthcare with patient data management and compliance requirements

Integration Focus:
- Patient data management with privacy controls
- Appointment scheduling with real-time availability
- Medical records integration with audit trails
- Secure communication between providers and patients

GitHub Copilot Workflow:
1. api-engineer chatmode → Design HIPAA-compliant FastAPI with comprehensive audit logging
2. frontend-engineer chatmode → Vue.js components with healthcare data visualization
3. security-engineer chatmode → Healthcare security compliance and data protection
4. qa-engineer chatmode → Compliance testing and security validation

Expected Deliverables:
- HIPAA-compliant API integration with comprehensive audit trails
- Secure patient data visualization with role-based access
- Real-time appointment scheduling with conflict resolution
- Healthcare data interoperability with HL7 FHIR standards
```

### Scenario 4: Mobile-First PWA with Microservices
```yaml
Context: Progressive Web App with microservices backend architecture
Technology Stack: Modern setup (React/Vue.js, Service Workers, Microservices, API Gateway)
Business Domain: Mobile-first application with offline capabilities

Integration Focus:
- Offline-first architecture with service worker integration
- API gateway integration with multiple microservices
- Push notifications and background synchronization
- Progressive enhancement and performance optimization

GitHub Copilot Workflow:
1. api-engineer chatmode → Design API gateway and microservices integration
2. frontend-engineer chatmode → PWA implementation with offline capabilities
3. deployment-engineer chatmode → Microservices deployment and service mesh
4. qa-engineer chatmode → Performance testing and offline scenario validation

Expected Deliverables:
- Comprehensive offline-first architecture with service workers
- API gateway integration with intelligent request routing
- Background synchronization with conflict resolution
- Progressive enhancement for various device capabilities
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Frontend-Backend Integration → api-engineer chatmode (lead)
├─ Frontend Implementation → frontend-engineer chatmode
├─ Security Integration → security-engineer chatmode
├─ Data Optimization → data-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Deployment Pipeline → deployment-engineer chatmode
```

### Context Handoff Information
- **To frontend-engineer**: API contracts, authentication patterns, data structures, real-time endpoints
- **To security-engineer**: Authentication flows, authorization requirements, security headers, compliance needs
- **To data-engineer**: Data access patterns, query optimization, caching requirements
- **To qa-engineer**: Integration test scenarios, performance benchmarks, security test cases
- **To deployment-engineer**: Infrastructure requirements, environment configuration, monitoring setup

### GitHub Actions Integration
- **Integration Testing**: Automated testing for frontend-backend communication and data flow
- **Security Scanning**: Full-stack security analysis including authentication and data protection
- **Performance Testing**: End-to-end performance testing for user workflows
- **Type Safety Validation**: Automated validation of API contracts and type generation

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Technology Stack**: Automatically detects frontend and backend frameworks and applies appropriate integration patterns
- **Business Domain**: Adapts integration patterns to industry-specific requirements and compliance needs
- **Security Requirements**: Configures authentication and security patterns based on project specifications
- **Performance Needs**: Optimizes integration for real-time requirements and scalability expectations
- **Development Workflow**: Adapts to existing project structure and development practices

**The api-engineer chatmode will automatically coordinate with frontend-engineer chatmode to ensure seamless full-stack integration while maintaining the functional requirements specified above.**