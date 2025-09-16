---
description: Design and implement efficient GraphQL APIs with advanced features like subscriptions, caching, and federation. Build scalable GraphQL APIs that provide flexible data fetching capabilities. Adapts to project specifications defined in copilot.instructions.md.
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

# GraphQL API Development

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Core GraphQL Architecture
- **Schema Design**: Create type-safe GraphQL schemas that accurately represent business domain relationships
- **Resolver Implementation**: Develop efficient resolvers with proper data fetching and transformation logic
- **Query Optimization**: Implement efficient query execution with batching, caching, and N+1 problem prevention
- **Type System**: Establish comprehensive type definitions with proper validation and error handling

### Advanced GraphQL Features
- **Real-time Subscriptions**: Implement GraphQL subscriptions for real-time data updates and live notifications
- **Schema Federation**: Design federated GraphQL architecture for microservices and distributed systems
- **Caching Strategy**: Implement intelligent caching at multiple levels (query, field, and data source)
- **Query Complexity Analysis**: Establish query depth and complexity limits to prevent abuse and performance issues

### Security and Performance
- **Authentication Integration**: Implement secure authentication mechanisms compatible with GraphQL execution model
- **Authorization Controls**: Enforce field-level and operation-level authorization with context-aware permissions
- **Rate Limiting**: Implement sophisticated rate limiting based on query complexity and resource consumption
- **Input Validation**: Comprehensive validation of all GraphQL inputs with custom scalar types and business rules

### Developer Experience
- **Schema Documentation**: Generate comprehensive GraphQL schema documentation with examples and usage guides
- **GraphQL Playground**: Configure interactive GraphQL IDE for development and testing
- **Introspection Management**: Control schema introspection for development and production environments
- **Error Handling**: Implement structured error responses with proper error codes and debugging information

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Project Configuration Analysis
```
1. Read copilot.instructions.md to extract:
   - GraphQL framework preferences (Apollo Server, GraphQL Yoga, Mercurius, etc.)
   - Backend technology and runtime environment
   - Database and data source configuration
   - Authentication and authorization requirements

2. Analyze existing project structure:
   - Identify current API patterns and data models
   - Understand authentication and session management
   - Assess existing data access layers and ORM usage
   - Review current testing and documentation approaches
```

### 2. Schema-First Design Process
```
1. Domain Modeling:
   - Map business entities to GraphQL types
   - Define relationships between types (one-to-one, one-to-many, many-to-many)
   - Identify queries, mutations, and subscription requirements
   - Plan schema evolution and versioning strategy

2. Type System Design:
   - Create scalars, enums, interfaces, and unions as needed
   - Design input types for mutations with proper validation
   - Plan error types and error handling strategies
   - Define pagination patterns (offset, cursor-based, relay-style)
```

### 3. Resolver Architecture Implementation
```
1. Data Layer Integration:
   - Design efficient data fetching patterns
   - Implement DataLoader for batching and caching
   - Create repository patterns for data access
   - Plan database query optimization strategies

2. Business Logic Integration:
   - Implement domain-specific business rules in resolvers
   - Create middleware for cross-cutting concerns
   - Design context propagation for authentication and authorization
   - Plan error propagation and handling strategies
```

### 4. Performance and Security Optimization
```
1. Query Optimization:
   - Implement query complexity analysis and limits
   - Configure query depth limiting and timeouts
   - Design caching strategies (in-memory, Redis, CDN)
   - Implement query whitelisting for production

2. Security Implementation:
   - Configure authentication integration with GraphQL context
   - Implement field-level authorization with directives
   - Add input sanitization and validation layers
   - Configure CORS and security headers appropriately
```

### 5. Real-time and Advanced Features
```
1. Subscription Implementation:
   - Design real-time subscription architecture
   - Implement WebSocket or Server-Sent Events integration
   - Create subscription filters and authorization
   - Plan subscription performance and scalability

2. Federation and Composition:
   - Design schema federation for microservices
   - Implement gateway composition and routing
   - Create cross-service type extensions
   - Plan schema registry and governance
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Schema Design Excellence
- **Type Safety**: Complete type definitions with proper nullability and validation
- **Schema Consistency**: Consistent naming conventions and relationship modeling
- **Documentation**: Comprehensive schema documentation with field descriptions and examples
- **Evolution Strategy**: Clear versioning and deprecation strategy for schema changes

### ✅ Performance Standards
- **Query Efficiency**: Resolvers implement proper batching and avoid N+1 problems
- **Response Times**: GraphQL operations complete within acceptable limits (< 200ms for simple queries)
- **Complexity Controls**: Query complexity analysis prevents resource exhaustion
- **Caching Effectiveness**: Appropriate caching strategies implemented at multiple levels

### ✅ Security Implementation
- **Authentication**: Robust authentication mechanism integrated with GraphQL execution
- **Authorization**: Field-level and operation-level authorization properly enforced
- **Input Validation**: Comprehensive validation preventing injection and malformed requests
- **Rate Limiting**: Sophisticated rate limiting based on query complexity and user context

### ✅ Developer Experience
- **Interactive Documentation**: GraphQL Playground or similar tool configured for development
- **Schema Introspection**: Proper introspection controls for different environments
- **Error Messages**: Clear, actionable error messages with proper error codes
- **Testing Support**: Comprehensive testing utilities and mock data support

### ✅ Advanced Features Implementation
- **Real-time Capabilities**: Subscriptions working correctly with proper authorization
- **Federation Support**: Schema federation implemented for distributed architecture (if required)
- **Monitoring Integration**: Performance monitoring and observability implemented
- **Production Readiness**: Query whitelisting, security hardening, and performance optimization

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Social Media Platform
```yaml
Context: Real-time social platform with posts, comments, and live interactions
Technology Stack: Detected from copilot.instructions.md (Node.js + Apollo Server, Python + Strawberry)
Business Domain: Social media with real-time interactions and content management

GraphQL Design Focus:
- User profiles and social connections
- Posts, comments, and reactions with real-time updates
- Media uploads and content management
- Real-time notifications and messaging

GitHub Copilot Workflow:
1. api-engineer chatmode → Design GraphQL schema and real-time subscriptions
2. frontend-engineer chatmode → Integrate with React/Vue using GraphQL clients
3. security-engineer chatmode → Implement content moderation and user safety
4. qa-engineer chatmode → Performance testing for real-time features

Expected Deliverables:
- Comprehensive GraphQL schema with social media entities
- Real-time subscriptions for posts, comments, and notifications
- Efficient data fetching with DataLoader and caching
- Authentication and authorization for user-generated content
```

### Scenario 2: E-commerce Product Catalog
```yaml
Context: Large-scale e-commerce with complex product data and inventory management
Technology Stack: Adapted to project configuration (Java + GraphQL Java, .NET + Hot Chocolate)
Business Domain: E-commerce with complex product relationships and search

GraphQL Design Focus:
- Product catalog with variants, categories, and attributes
- Inventory management with real-time stock updates
- Search and filtering with faceted navigation
- Order management and customer data

GitHub Copilot Workflow:
1. api-engineer chatmode → Design federated schema for product and order services
2. data-engineer chatmode → Optimize database queries and search indices
3. frontend-engineer chatmode → Build product browse and search interfaces
4. deployment-engineer chatmode → Scale GraphQL federation infrastructure

Expected Deliverables:
- Federated GraphQL schema across multiple microservices
- Advanced search capabilities with GraphQL queries
- Real-time inventory updates via subscriptions
- Performance optimization for large product catalogs
```

### Scenario 3: Healthcare Data Platform
```yaml
Context: HIPAA-compliant healthcare platform with patient data and provider integration
Technology Stack: Enterprise-grade setup (.NET Core + Hot Chocolate, Java + GraphQL SPQR)
Business Domain: Healthcare with strict compliance and data privacy requirements

GraphQL Design Focus:
- Patient data with comprehensive privacy controls
- Provider networks and appointment scheduling
- Medical records with role-based access
- Integration with external healthcare systems

GitHub Copilot Workflow:
1. api-engineer chatmode → Design HIPAA-compliant GraphQL architecture
2. security-engineer chatmode → Implement field-level authorization and audit logging
3. data-engineer chatmode → Optimize healthcare data access patterns
4. qa-engineer chatmode → Compliance testing and security validation

Expected Deliverables:
- HIPAA-compliant GraphQL API with comprehensive audit trails
- Field-level authorization for sensitive patient data
- Integration patterns for healthcare data standards (HL7 FHIR)
- Advanced error handling for compliance requirements
```

### Scenario 4: Financial Trading Platform
```yaml
Context: Real-time financial data platform with trading and portfolio management
Technology Stack: High-performance setup (Go + gqlgen, Rust + async-graphql)
Business Domain: Financial services with real-time data and regulatory compliance

GraphQL Design Focus:
- Real-time market data and price feeds
- Portfolio management and trading operations
- Risk management and compliance reporting
- Integration with financial data providers

GitHub Copilot Workflow:
1. api-engineer chatmode → Design high-performance GraphQL for real-time data
2. security-engineer chatmode → Implement financial data security and compliance
3. qa-engineer chatmode → Performance testing for high-frequency data
4. deployment-engineer chatmode → Deploy high-availability trading infrastructure

Expected Deliverables:
- High-performance GraphQL API with real-time market data subscriptions
- Advanced caching and data federation for financial services
- Compliance controls for financial data access
- Monitoring and alerting for trading system reliability
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
GraphQL Schema Design → api-engineer chatmode
├─ Security & Authorization → security-engineer chatmode
├─ Database Optimization → data-engineer chatmode
├─ Frontend Integration → frontend-engineer chatmode
├─ Performance Testing → qa-engineer chatmode
└─ Production Deployment → deployment-engineer chatmode
```

### Context Handoff Information
- **To security-engineer**: Schema definition, field-level permissions, subscription authorization
- **To frontend-engineer**: GraphQL schema, query patterns, subscription endpoints
- **To data-engineer**: Data access patterns, resolver optimization, caching requirements
- **To qa-engineer**: GraphQL operations, performance benchmarks, security test scenarios
- **To deployment-engineer**: Infrastructure requirements, federation setup, monitoring needs

### GitHub Actions Integration
- **Schema Validation**: Automated schema linting and breaking change detection
- **Query Testing**: Comprehensive GraphQL operation testing with performance benchmarks
- **Security Scanning**: GraphQL-specific security analysis and vulnerability detection
- **Documentation**: Automatic schema documentation generation and deployment

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **GraphQL Framework**: Automatically detects and applies patterns for Apollo Server, GraphQL Yoga, Hot Chocolate, etc.
- **Business Domain**: Adapts GraphQL schema design to industry-specific requirements and compliance needs
- **Performance Requirements**: Optimizes for real-time requirements and query complexity based on project needs
- **Security Specifications**: Configures authentication and authorization based on project security requirements
- **Integration Patterns**: Adapts to existing project architecture and microservices setup

**The api-engineer chatmode will automatically analyze project configuration and apply GraphQL-appropriate implementation patterns while maintaining the functional requirements specified above.**