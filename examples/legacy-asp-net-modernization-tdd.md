# Example 3: Legacy ASP.NET to Modern Web Application - TDD Migration with Playwright Testing

**Execution Date:** 2025-09-13
**Source Framework Commit:** ed83359 (my_name_is_claude)
**Framework Version:** My Name Is ClaudePilot v1.0 - GitHub Copilot Enterprise Framework

## Brief Application Description

Complete migration of a legacy ASP.NET application with C++ backend components to a modern Angular web application with .NET Core API. The legacy system lacks any documentation, requiring reverse engineering and comprehensive analysis. The project follows Test-Driven Development (TDD) methodology with Playwright for end-to-end testing, ensuring full functional parity and improved architecture.

## Key Technology Assumptions

- **Legacy System:**
  - Frontend: ASP.NET WebForms (.aspx pages)
  - Backend: Mixed C++/C# codebase with COM interop
  - Database: SQL Server with stored procedures
  - Architecture: Monolithic, tightly coupled

- **Target System:**
  - Frontend: Angular 17+ with TypeScript, Angular Material
  - Backend: .NET 8 Web API with Clean Architecture
  - Database: Entity Framework Core with SQL Server
  - Architecture: Clean Architecture, microservices-ready
  - Testing: TDD approach with Playwright E2E testing

## Sample copilot.instructions.md Content

```markdown
# My Name Is ClaudePilot - Legacy ASP.NET Modernization Project

## 0. Project Metadata
- **project_name**: legacy-modernization-tdd
- **project_description**: Complete migration from legacy ASP.NET/C++ to modern Angular/.NET Core with TDD approach
- **primary_language**: typescript
- **business_domain**: enterprise
- **project_scale**: enterprise
- **development_stage**: development

## 1. Project Description
Comprehensive modernization of legacy ASP.NET application to modern web architecture using Test-Driven Development methodology. Includes reverse engineering, functional analysis, and complete system rewrite with full test coverage.

## 2. Domains and Goals
- Business domains: enterprise application modernization, legacy system migration
- Main project goals: complete system modernization, zero functional regression, improved maintainability, comprehensive test coverage

## 3. Technologies
- **Frontend – technologies and tools**: Angular 17+, TypeScript, Angular Material, RxJS, NgRx, Playwright
- **Backend – technologies and tools**: .NET 8, Entity Framework Core, MediatR, AutoMapper, xUnit
- **Database**: SQL Server, Entity Framework migrations, repository pattern
- **Testing**: TDD methodology, Playwright E2E testing, xUnit, Jasmine/Karma

## 4. Chatmodes and Specializations
[Uses all 12 chatmodes with emphasis on legacy analysis, TDD methodology, and comprehensive testing]

## 5. Integrations and Dependencies
- Legacy system analysis: Code reverse engineering tools
- Testing frameworks: Playwright, xUnit, Angular Testing Library
- Migration tools: Database schema comparison, data migration utilities
- CI/CD: GitHub Actions with comprehensive testing pipeline

## 6. Non-functional Requirements
- Performance: Match or exceed legacy system performance
- Reliability: Zero functional regression, 99.9% uptime
- Security: Modern security practices, vulnerability elimination
- Maintainability: Clean code, comprehensive documentation, test coverage >95%
```

## Project Initialization and Legacy Analysis

### Step 1: Legacy System Analysis Setup
```bash
# Create migration project workspace
mkdir legacy-modernization-tdd
cd legacy-modernization-tdd

# Setup analysis directories
mkdir legacy-analysis
mkdir modern-implementation
mkdir test-specifications

# Copy copilot.instructions.md
cp /path/to/copilot.instructions.md ./

# Initialize Git repository
git init
git add copilot.instructions.md
git commit -m "Initial TDD migration project setup"
```

### Step 2: GitHub Copilot Chat Setup for TDD
```
# Start GitHub Copilot Chat with TDD focus
# Ensure copilot.instructions.md is loaded for project context
```

## Detailed Step-by-Step TDD Migration Workflow

### Phase 1: Legacy System Reverse Engineering

#### Step 1.1: Switch to business-analyst chatmode
```
Switch to business-analyst chatmode
```

#### Step 1.2: Apply current state process analysis
```
@github .github/prompts/agents/business/current-state-process-analysis.prompt.md

Context: Legacy ASP.NET system without documentation
- System scope: Complete functional analysis from code and database
- Business processes: Reverse engineer from user interfaces and workflows
- Data flow analysis: Database relationships and stored procedure logic
- User roles and permissions: Extract from code-based authorization
```

**Expected Results:**
- Complete functional specification derived from code analysis
- Business process mapping from legacy system behavior
- Data model documentation from database analysis
- User role and permission matrix

#### Step 1.3: Switch to software-architect chatmode
```
Switch to software-architect chatmode
```

#### Step 1.4: Apply architecture evolution guidance
```
@github .github/prompts/workflows/architecture-evolution-guidance.prompt.md

Context: Complete legacy system modernization strategy
- Current state: Monolithic ASP.NET with C++ backend components
- Target state: Angular SPA with .NET Core API, Clean Architecture
- Migration approach: Big Bang with comprehensive TDD coverage
- Risk mitigation: Parallel system operation during transition
```

**Expected Results:**
- Comprehensive migration architecture plan
- Risk assessment and mitigation strategies
- Test-first development approach specification
- System cutover and rollback procedures

### Phase 2: Test Specification Development (TDD Foundation)

#### Step 2.1: Switch to qa-engineer chatmode
```
Switch to qa-engineer chatmode
```

#### Step 2.2: Apply test automation and quality assurance
```
@github .github/prompts/agents/quality/test-automation-and-quality-assurance.prompt.md

Context: TDD approach for legacy system migration
- Test pyramid: Comprehensive unit, integration, and E2E testing
- Playwright E2E: Complete user workflow automation
- Legacy behavior validation: Ensure zero functional regression
- Test data management: Production-like test scenarios
```

**Expected Results:**
- Complete test specification based on legacy system analysis
- Playwright E2E test suite covering all user workflows
- Test data generation and management strategy
- TDD development guidelines and standards

#### Step 2.3: Develop comprehensive Playwright test specifications
```
Apply Playwright test development for legacy system parity
- User workflow mapping: Extract all user journeys from legacy system
- Data scenarios: Cover all business data combinations
- Error handling: Test all legacy error conditions and edge cases
- Performance baselines: Establish performance benchmarks from legacy system
```

**Expected Results:**
- Complete Playwright test suite specification
- Test scenarios covering 100% of legacy functionality
- Performance benchmark definitions
- Error condition and edge case coverage

### Phase 3: API Development with TDD

#### Step 3.1: Switch to api-engineer chatmode
```
Switch to api-engineer chatmode
```

#### Step 3.2: Apply REST API design and implementation
```
@github .github/prompts/agents/api/rest-api-design-and-implementation.prompt.md

Context: .NET Core API development with TDD for legacy migration
- API design: RESTful endpoints matching legacy functionality
- TDD approach: Write tests first, then implement API endpoints
- Data contracts: Ensure compatibility with legacy data structures
- Error handling: Implement consistent error responses
```

**Expected Results:**
- Complete API specification with OpenAPI documentation
- TDD test suite for all API endpoints
- Data mapping from legacy database to modern entities
- Comprehensive error handling and validation

#### Step 3.3: Apply TDD API development workflow
```
For each legacy function identified:
1. Write failing API test based on legacy behavior
2. Implement minimal API endpoint to pass test
3. Refactor for clean code while maintaining test success
4. Validate against Playwright E2E tests
```

**Expected Results:**
- API endpoints developed with 100% test coverage
- Functional parity with legacy system validated
- Clean Architecture implementation with proper separation
- Comprehensive API documentation and examples

### Phase 4: Database Migration and Data Engineering

#### Step 4.1: Switch to data-engineer chatmode
```
Switch to data-engineer chatmode
```

#### Step 4.2: Apply database design and ETL implementation
```
@github .github/prompts/agents/data/database-design-and-etl-implementation.prompt.md

Context: Legacy SQL Server database modernization with Entity Framework
- Schema migration: Convert legacy tables to Entity Framework models
- Data migration: ETL process from legacy to modern schema
- Stored procedure conversion: Convert to LINQ queries or repository methods
- Performance optimization: Index strategy and query optimization
```

**Expected Results:**
- Entity Framework models matching legacy data structures
- Data migration scripts with validation
- Performance-optimized repository implementations
- Comprehensive database testing strategy

#### Step 4.3: Implement TDD database testing
```
Apply TDD approach to database layer:
1. Write integration tests for data operations
2. Implement repository pattern with Entity Framework
3. Validate data integrity and business rules
4. Performance testing for query optimization
```

**Expected Results:**
- Repository implementations with 100% test coverage
- Data integrity validation through automated tests
- Performance benchmarks meeting legacy system standards
- Comprehensive database integration test suite

### Phase 5: Frontend Development with Angular and TDD

#### Step 5.1: Switch to frontend-engineer chatmode
```
Switch to frontend-engineer chatmode
```

#### Step 5.2: Apply Angular component development
```
@github .github/prompts/agents/frontend/angular-component-development.prompt.md

Context: Angular SPA development with TDD for legacy migration
- Component architecture: Modern Angular patterns replacing legacy WebForms
- State management: NgRx for complex state, services for simple state
- Form handling: Reactive forms replacing legacy server controls
- UI/UX: Modern Angular Material design system
```

**Expected Results:**
- Angular component architecture matching legacy functionality
- Reactive form implementations for all legacy forms
- State management strategy for complex application state
- Modern UI components with accessibility compliance

#### Step 5.3: Apply frontend testing and quality assurance
```
@github .github/prompts/agents/frontend/frontend-testing-and-quality-assurance.prompt.md

Context: Angular application testing with TDD methodology
- Component testing: Test-first component development
- Service testing: HTTP interceptors and business logic testing
- Integration testing: Component and service integration
- E2E validation: Playwright tests validating Angular implementation
```

**Expected Results:**
- Angular components developed with test-first methodology
- Comprehensive unit and integration test suite
- Service layer testing with HTTP mocking
- E2E test validation of complete user workflows

### Phase 6: Security and Compliance Implementation

#### Step 6.1: Switch to security-engineer chatmode
```
Switch to security-engineer chatmode
```

#### Step 6.2: Apply security architecture and threat modeling
```
@github .github/prompts/agents/security/security-architecture-and-threat-modeling.prompt.md

Context: Security modernization from legacy ASP.NET to modern architecture
- Authentication: Modern JWT-based authentication replacing legacy session management
- Authorization: Role-based access control with proper separation of concerns
- Data protection: Encryption at rest and in transit
- Vulnerability elimination: Address legacy security issues
```

**Expected Results:**
- Modern authentication and authorization implementation
- Comprehensive security testing and validation
- Vulnerability assessment and remediation
- Security compliance validation and documentation

#### Step 6.3: Apply penetration testing and security audit
```
@github .github/prompts/agents/security/penetration-testing-and-security-audit.prompt.md

Context: Security validation for modernized application
- Automated security testing: Integration with CI/CD pipeline
- Manual penetration testing: Comprehensive security assessment
- Compliance validation: Industry standard compliance verification
- Security monitoring: Implement security event logging and monitoring
```

**Expected Results:**
- Comprehensive security test suite integrated with CI/CD
- Penetration testing results and remediation
- Security monitoring and alerting implementation
- Compliance documentation and audit trail

### Phase 7: Performance Optimization and TDD Validation

#### Step 7.1: Switch to qa-engineer chatmode
```
Switch to qa-engineer chatmode
```

#### Step 7.2: Apply application performance optimization
```
@github .github/prompts/agents/qa/application-performance-optimization.prompt.md

Context: Performance optimization with TDD validation
- Performance baselines: Match or exceed legacy system performance
- Load testing: Comprehensive performance testing with realistic scenarios
- Optimization: Database, API, and frontend performance tuning
- Monitoring: Application performance monitoring implementation
```

**Expected Results:**
- Performance optimization meeting or exceeding legacy benchmarks
- Comprehensive load testing results and validation
- Performance monitoring and alerting implementation
- Performance regression testing in CI/CD pipeline

### Phase 8: Deployment and CI/CD with TDD Integration

#### Step 8.1: Switch to deployment-engineer chatmode
```
Switch to deployment-engineer chatmode
```

#### Step 8.2: Apply CI/CD pipeline and infrastructure setup
```
@github .github/prompts/agents/deployment/ci-cd-pipeline-and-infrastructure-setup.prompt.md

Context: CI/CD pipeline with comprehensive TDD validation
- Pipeline stages: Build, test, security scan, performance validation, deploy
- Test integration: All test types (unit, integration, E2E) in pipeline
- Quality gates: Zero tolerance for test failures or security issues
- Deployment strategy: Blue-green deployment with automated rollback
```

**Expected Results:**
- Complete CI/CD pipeline with comprehensive testing
- Quality gates ensuring test coverage and performance standards
- Automated deployment with rollback capabilities
- Infrastructure as code with environment consistency

### Phase 9: End-to-End Migration Validation

#### Step 9.1: Apply feature development lifecycle
```
@github .github/prompts/workflows/feature-development-lifecycle.prompt.md

Context: Complete system validation and user acceptance testing
- System validation: End-to-end functional parity verification
- Performance validation: System performance under production load
- User acceptance: Stakeholder validation of modernized system
- Production readiness: Final validation before system cutover
```

**Expected Results:**
- Complete system validation with zero functional regression
- Performance validation meeting or exceeding legacy system
- User acceptance sign-off and training completion
- Production cutover plan with rollback procedures

#### Step 9.2: Apply enterprise development governance
```
@github .github/prompts/workflows/enterprise-development-governance.prompt.md

Context: Enterprise governance for legacy system replacement
- Change management: Controlled system cutover with approval processes
- Risk management: Comprehensive risk assessment and mitigation
- Audit compliance: Complete audit trail and documentation
- Business continuity: Zero-downtime migration with failback capabilities
```

**Expected Results:**
- Enterprise governance framework compliance
- Risk management and mitigation implementation
- Complete audit trail and documentation
- Business continuity assurance with tested failback procedures

## Advanced TDD and Playwright Integration

### Playwright Test Development Strategy

```typescript
// Example: Legacy form migration with Playwright validation
test.describe('Invoice Creation Workflow', () => {
  test('should create invoice matching legacy system behavior', async ({ page }) => {
    // Test based on legacy system analysis
    await page.goto('/invoices/create');

    // Fill form with legacy-equivalent data
    await page.fill('[data-testid="customer-select"]', 'CUST001');
    await page.fill('[data-testid="invoice-amount"]', '1500.00');

    // Validate calculations match legacy system
    const calculatedTotal = await page.textContent('[data-testid="total-amount"]');
    expect(calculatedTotal).toBe('$1,650.00'); // Including legacy tax calculation

    // Submit and validate database state
    await page.click('[data-testid="save-invoice"]');

    // Verify invoice creation matches legacy database structure
    const invoiceId = await page.textContent('[data-testid="invoice-id"]');
    expect(invoiceId).toMatch(/^INV-\d{6}$/); // Legacy invoice ID format
  });
});
```

### TDD API Development Pattern

```csharp
// Example: TDD API endpoint development
[Fact]
public async Task CreateInvoice_ShouldMatchLegacyBehavior()
{
    // Arrange - Based on legacy system analysis
    var invoiceRequest = new CreateInvoiceRequest
    {
        CustomerId = "CUST001",
        Amount = 1500.00m,
        TaxRate = 0.10m // Legacy tax calculation
    };

    // Act
    var response = await _client.PostAsJsonAsync("/api/invoices", invoiceRequest);

    // Assert - Validate against legacy system behavior
    response.StatusCode.Should().Be(HttpStatusCode.Created);

    var invoice = await response.Content.ReadFromJsonAsync<InvoiceResponse>();
    invoice.Total.Should().Be(1650.00m); // Legacy calculation validation
    invoice.InvoiceNumber.Should().MatchRegex(@"^INV-\d{6}$"); // Legacy format
}
```

## Key GitHub Copilot Features for TDD Migration

### 1. Legacy Code Analysis
- **Code understanding**: Deep analysis of legacy ASP.NET and C++ codebase
- **Business logic extraction**: Automated identification of business rules
- **Database reverse engineering**: Schema and relationship analysis

### 2. TDD Methodology Integration
- **Test-first development**: Guided TDD workflow for each component
- **Behavior preservation**: Ensuring zero functional regression
- **Comprehensive coverage**: Unit, integration, and E2E test development

### 3. Playwright E2E Testing
- **User workflow automation**: Complete user journey testing
- **Legacy behavior validation**: Ensuring new system matches legacy functionality
- **Cross-browser testing**: Comprehensive browser compatibility validation

### 4. Migration Risk Mitigation
- **Parallel system validation**: Running both systems for comparison
- **Rollback procedures**: Comprehensive failback strategies
- **Performance benchmarking**: Ensuring performance parity or improvement

## Expected Project Outcomes

### Technical Deliverables
- ✅ Complete Angular SPA replacing legacy WebForms
- ✅ Modern .NET Core API with Clean Architecture
- ✅ Entity Framework Core replacing legacy data access
- ✅ Comprehensive test suite with >95% coverage
- ✅ Playwright E2E tests covering all user workflows
- ✅ Modern security implementation with vulnerability elimination
- ✅ Performance optimization meeting or exceeding legacy benchmarks
- ✅ Complete CI/CD pipeline with quality gates

### Business Outcomes
- ✅ Zero functional regression from legacy system
- ✅ Improved system maintainability and extensibility
- ✅ Enhanced security and compliance posture
- ✅ Reduced operational costs and technical debt
- ✅ Modern user experience and accessibility compliance

### Quality Metrics
- **Test Coverage**: >95% code coverage across all layers
- **Functional Parity**: 100% legacy functionality preserved
- **Performance**: Match or exceed legacy system performance
- **Security**: Zero high-severity vulnerabilities
- **Reliability**: >99.9% uptime with automated failover

## Lessons Learned

### TDD Migration Advantages
1. **Risk mitigation**: Comprehensive testing prevents functional regression
2. **Documentation**: Tests serve as living documentation of system behavior
3. **Confidence**: High confidence in migration success through validation
4. **Quality**: Superior code quality through test-driven development

### GitHub Copilot for Legacy Migration
1. **Code analysis**: Excellent at understanding complex legacy systems
2. **Test generation**: Automated test case generation from legacy behavior
3. **Pattern recognition**: Identifying common migration patterns and solutions
4. **Risk assessment**: Built-in migration risk identification and mitigation

### Best Practices for TDD Migration
1. **Comprehensive analysis**: Thorough legacy system understanding before starting
2. **Test-first approach**: Always write tests before implementing new functionality
3. **Behavior preservation**: Focus on maintaining exact legacy behavior initially
4. **Incremental improvement**: Optimize and improve after functional parity is achieved

### Recommendations for Similar Projects
1. **Use TDD methodology**: Essential for complex legacy migrations
2. **Playwright integration**: Critical for end-to-end validation
3. **Parallel system operation**: Run both systems during transition period
4. **Comprehensive monitoring**: Monitor both systems for comparison and validation

---

*This example demonstrates a complete TDD-driven legacy system migration using My Name Is ClaudePilot framework, showcasing how to safely modernize complex legacy applications while ensuring zero functional regression.*