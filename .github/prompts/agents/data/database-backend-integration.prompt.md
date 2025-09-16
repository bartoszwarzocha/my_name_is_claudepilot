---
description: Design and implement comprehensive database-backend integration with advanced ORM configuration, data access patterns, transaction management, and API layer architecture. Adapts to project specifications defined in copilot.instructions.md.
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

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `data-engineer` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Database-Backend Integration

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Database Integration Architecture
- **ORM Configuration and Setup**: Establish robust object-relational mapping with connection pooling, transaction management, and performance optimization
- **Data Access Layer Design**: Implement repository patterns, service layers, and data validation with proper separation of concerns
- **Database Schema Management**: Design scalable database schemas with proper indexing, relationships, and migration strategies
- **Transaction Management**: Implement ACID-compliant transactions with proper isolation levels and rollback mechanisms

### API Data Layer Integration
- **RESTful Data Endpoints**: Create standardized API endpoints for data operations with proper HTTP methods and status codes
- **Data Transfer Objects**: Design efficient DTOs with validation, serialization, and transformation capabilities
- **Error Handling and Logging**: Implement comprehensive error handling with detailed logging and monitoring integration
- **Performance Optimization**: Optimize database queries, implement caching strategies, and prevent N+1 query problems

### Security and Data Protection
- **Access Control Integration**: Implement role-based data access with proper authentication and authorization
- **Data Validation and Sanitization**: Ensure input validation, SQL injection prevention, and data integrity enforcement
- **Audit Trail Implementation**: Create comprehensive audit logging for data changes and access patterns
- **Compliance and Governance**: Implement data protection measures meeting industry-specific compliance requirements

### Technology Stack Adaptation
- **Framework-Specific Implementation**: Adapt integration patterns to detected backend technology stack and ORM preferences
- **Database System Optimization**: Optimize for specific database systems with vendor-specific features and best practices
- **Scalability and Performance**: Design for horizontal and vertical scaling with load balancing and connection management
- **Development and Testing Support**: Create development-friendly patterns with testing support and debugging capabilities

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Technology Stack Analysis and Configuration
```
1. Read copilot.instructions.md to extract:
   - Backend technology stack and framework preferences
   - Database system and ORM technology selection
   - Business domain data modeling requirements
   - Performance and scalability expectations

2. Database Technology Assessment:
   - Analyze current database schema and migration requirements
   - Evaluate ORM capabilities and configuration needs
   - Assess connection pooling and transaction management requirements
   - Review performance optimization and caching strategies
```

### 2. Database Schema Design and Migration
```
1. Schema Analysis and Design:
   - Analyze business domain requirements for data modeling
   - Design normalized database schema with proper relationships
   - Implement indexing strategy for query performance optimization
   - Plan migration and versioning strategy for schema evolution

2. ORM Configuration and Setup:
   - Configure ORM framework with connection pooling and transaction management
   - Set up entity mapping with validation and constraint enforcement
   - Implement audit trails and soft delete patterns where required
   - Configure caching layers and performance optimization settings
```

### 3. Data Access Layer Implementation
```
1. Repository Pattern Implementation:
   - Design repository interfaces with clear separation of concerns
   - Implement concrete repository classes with error handling
   - Create service layer for business logic and transaction management
   - Set up dependency injection and configuration management

2. Query Optimization and Performance:
   - Implement efficient query patterns with proper joins and filtering
   - Set up pagination and sorting capabilities for large datasets
   - Create bulk operations for high-performance data processing
   - Implement caching strategies for frequently accessed data
```

### 4. API Integration and Data Transfer
```
1. RESTful Endpoint Design:
   - Create standardized CRUD endpoints with proper HTTP methods
   - Implement request/response DTOs with validation and transformation
   - Set up proper status codes and error response formatting
   - Configure CORS, security headers, and API versioning

2. Data Validation and Security:
   - Implement input validation with business rule enforcement
   - Set up SQL injection prevention and data sanitization
   - Create role-based access control for data operations
   - Implement audit logging and data access monitoring
```

### 5. Testing, Monitoring, and Maintenance
```
1. Testing Strategy Implementation:
   - Create unit tests for repository and service layers
   - Implement integration tests for database operations
   - Set up performance testing for query optimization validation
   - Create test data management and cleanup strategies

2. Monitoring and Maintenance:
   - Implement comprehensive logging for database operations
   - Set up performance monitoring and alerting
   - Create backup and recovery procedures
   - Plan maintenance and optimization workflows
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Database Integration Excellence
- **ORM Configuration**: Properly configured ORM with connection pooling, transaction management, and performance optimization
- **Schema Design**: Well-designed database schema with proper normalization, indexing, and relationship management
- **Migration Strategy**: Robust migration system with versioning and rollback capabilities
- **Performance Optimization**: Optimized queries with appropriate indexing and caching strategies

### ✅ Data Access Layer Quality
- **Repository Pattern**: Clean repository pattern implementation with proper separation of concerns
- **Service Layer**: Well-designed service layer with business logic encapsulation and transaction management
- **Error Handling**: Comprehensive error handling with proper exception management and logging
- **Data Validation**: Robust input validation with business rule enforcement and constraint checking

### ✅ API Integration Standards
- **RESTful Design**: Standardized REST API endpoints with proper HTTP methods and status codes
- **DTO Implementation**: Efficient data transfer objects with validation and transformation capabilities
- **Security Implementation**: Proper authentication, authorization, and data protection measures
- **Documentation Quality**: Comprehensive API documentation with examples and usage guidelines

### ✅ Performance and Scalability
- **Query Performance**: Optimized database queries with proper indexing and join strategies
- **Connection Management**: Efficient connection pooling and resource management
- **Caching Strategy**: Effective caching implementation for improved performance
- **Scalability Design**: Architecture supports horizontal and vertical scaling requirements

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with api-engineer for endpoint development and security-engineer for data protection
- **Documentation Quality**: Comprehensive database and API documentation supporting development workflows
- **Configuration Adaptation**: Proper adaptation to project technology stack and business domain requirements
- **Testing Support**: Complete testing framework for database operations and API integration validation

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Database Integration
```yaml
Context: E-commerce platform with complex product catalog, inventory, and order management
Technology Stack: Detected from copilot.instructions.md (Java Spring Boot, PostgreSQL, Redis)
Business Domain: E-commerce with high-volume transactions and complex product relationships

Database Integration Focus:
- Product catalog with categories, variants, and pricing tiers
- Inventory management with real-time stock tracking
- Order processing with payment and fulfillment workflows
- Customer data with purchase history and preferences

GitHub Copilot Workflow:
1. data-engineer chatmode → Design e-commerce database schema with Spring Boot JPA integration
2. api-engineer chatmode → Implement RESTful endpoints for product catalog and order management
3. security-engineer chatmode → Implement payment data protection and audit trails
4. qa-engineer chatmode → Create comprehensive testing for transactional integrity

Expected Deliverables:
- E-commerce database schema with proper normalization and indexing
- Spring Boot JPA entities with validation and audit trails
- Repository and service layers with transaction management
- RESTful API endpoints with comprehensive error handling and documentation
```

### Scenario 2: Healthcare Data Integration
```yaml
Context: Healthcare management system with patient data, clinical workflows, and regulatory compliance
Technology Stack: Healthcare-compliant setup (.NET Core, SQL Server, Entity Framework)
Business Domain: Healthcare with HIPAA compliance and clinical data management

Database Integration Focus:
- Patient medical records with clinical data relationships
- Appointment scheduling with provider and resource management
- Billing and insurance processing with regulatory reporting
- Clinical decision support with data analytics integration

GitHub Copilot Workflow:
1. data-engineer chatmode → Design HIPAA-compliant database with Entity Framework integration
2. security-engineer chatmode → Implement healthcare data protection and access controls
3. api-engineer chatmode → Create clinical workflow APIs with audit trail requirements
4. qa-engineer chatmode → Establish patient safety and data integrity validation

Expected Deliverables:
- HIPAA-compliant database schema with comprehensive audit trails
- Entity Framework models with healthcare data validation
- Clinical workflow APIs with regulatory compliance features
- Data protection and access control implementation
```

### Scenario 3: Financial Services Data Architecture
```yaml
Context: Financial institution with transaction processing, risk management, and regulatory reporting
Technology Stack: Enterprise financial setup (Java, Oracle, Spring Data JPA)
Business Domain: Financial services with real-time transaction processing and compliance

Database Integration Focus:
- Account management with complex financial product relationships
- Transaction processing with real-time fraud detection
- Risk assessment with regulatory reporting requirements
- Customer onboarding with KYC and compliance workflows

GitHub Copilot Workflow:
1. data-engineer chatmode → Design financial database with Spring Data JPA and Oracle optimization
2. security-engineer chatmode → Implement financial security controls and fraud detection
3. api-engineer chatmode → Create real-time transaction processing APIs
4. deployment-engineer chatmode → Set up high-availability database infrastructure

Expected Deliverables:
- Financial services database with transaction integrity and audit requirements
- Spring Data JPA integration with Oracle-specific optimizations
- Real-time transaction processing with fraud detection capabilities
- Regulatory reporting and compliance data management
```

### Scenario 4: IoT and Analytics Data Platform
```yaml
Context: IoT platform with massive data ingestion, real-time analytics, and machine learning integration
Technology Stack: Cloud-native setup (Python FastAPI, PostgreSQL, InfluxDB, Redis)
Business Domain: IoT with time-series data, device management, and predictive analytics

Database Integration Focus:
- Time-series data storage with efficient compression and querying
- Device management with metadata and configuration tracking
- Real-time analytics with streaming data processing
- Machine learning model integration with feature store management

GitHub Copilot Workflow:
1. data-engineer chatmode → Design IoT data architecture with FastAPI and multi-database integration
2. api-engineer chatmode → Implement high-throughput data ingestion and analytics APIs
3. deployment-engineer chatmode → Set up scalable data infrastructure with auto-scaling
4. qa-engineer chatmode → Create performance testing for high-volume data processing

Expected Deliverables:
- IoT data architecture with time-series and relational database integration
- FastAPI implementation with SQLAlchemy and InfluxDB integration
- High-performance data ingestion with real-time processing capabilities
- Analytics APIs with machine learning model integration
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Database-Backend Integration → data-engineer chatmode (lead)
├─ API Endpoint Implementation → api-engineer chatmode
├─ Data Security Implementation → security-engineer chatmode
├─ Frontend Data Integration → frontend-engineer chatmode
├─ Performance Testing → qa-engineer chatmode
└─ Infrastructure Setup → deployment-engineer chatmode
```

### Context Handoff Information
- **To api-engineer**: Database schema design, repository patterns, DTO specifications, API endpoint requirements
- **To security-engineer**: Data access control requirements, audit trail specifications, compliance validation needs
- **To frontend-engineer**: API endpoint documentation, data models, integration patterns, error handling
- **To qa-engineer**: Testing strategies, performance benchmarks, data validation scenarios
- **To deployment-engineer**: Database configuration, connection pooling, backup and recovery requirements

### GitHub Actions Integration
- **Database Migration**: Automated database schema migration and versioning
- **Integration Testing**: Automated testing for database operations and API endpoints
- **Performance Monitoring**: Continuous monitoring of database performance and query optimization
- **Security Scanning**: Automated security scanning for SQL injection and data protection vulnerabilities

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Backend Technology**: Automatically detects and configures integration patterns for Spring Boot, .NET Core, FastAPI, Express.js, or other frameworks
- **Database System**: Optimizes for PostgreSQL, MySQL, SQL Server, Oracle, or NoSQL databases based on project configuration
- **Business Domain**: Adapts data modeling and validation patterns to e-commerce, healthcare, financial, or other industry requirements
- **Performance Requirements**: Configures caching, connection pooling, and optimization strategies based on scale and performance needs
- **Security Standards**: Implements appropriate security measures and compliance requirements based on industry and regulatory context

**The data-engineer chatmode will automatically analyze project configuration and technology stack to deliver optimal database-backend integration while maintaining the functional requirements specified above.**