---
name: frontend-testing-quality-assurance
description: |
  **🤖 GitHub Copilot Chatmode: @frontend-engineer**

  Comprehensive frontend testing strategies and quality assurance frameworks with advanced automation, intelligent test generation, and seamless integration with GitHub Copilot workflows.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt testing strategies to project requirements.
---

# Frontend Testing and Quality Assurance

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@frontend-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All testing and quality assurance tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Establish comprehensive frontend testing and quality assurance that validates application reliability, performance, and accessibility across all supported browsers and devices. Create automated testing pipelines that integrate seamlessly with development workflows and provide actionable insights for continuous quality improvement.

**Testing Strategy Requirements:**
- Implement comprehensive testing pyramid (unit, integration, end-to-end)
- Establish automated quality gates for code quality, accessibility, and performance
- Configure cross-browser and cross-device testing automation
- Create visual regression testing for UI consistency validation
- Implement performance monitoring with Core Web Vitals tracking
- Establish accessibility compliance validation (WCAG standards)

## 🔄 HIGH-LEVEL ALGORITHMS

**Phase 1: Testing Strategy Assessment and Configuration**
1. Read .github/copilot.instructions.md to determine project technology stack and requirements
2. Analyze existing testing setup and identify gaps in coverage
3. Select appropriate testing frameworks based on project context (Jest/Vitest, Cypress/Playwright)
4. Configure testing environments and browser automation setup
5. Establish baseline metrics for performance and accessibility standards

**Phase 2: Test Suite Implementation**
1. Implement unit testing framework with comprehensive component coverage
2. Create integration testing patterns for user workflows and API interactions
3. Develop end-to-end testing suite covering critical user journeys
4. Configure visual regression testing for UI consistency validation
5. Implement accessibility testing automation with axe-core integration

**Phase 3: Quality Assurance Automation**
1. Configure pre-commit hooks with linting, type checking, and unit tests
2. Implement CI/CD quality gates for integration and deployment validation
3. Create performance testing automation with Web Vitals monitoring
4. Establish cross-browser testing automation for supported platforms
5. Configure test reporting and failure notification systems

**Phase 4: Monitoring and Continuous Improvement**
1. Implement production monitoring with synthetic testing
2. Create performance budgets and automated alerts for regressions
3. Establish quality metrics dashboard and reporting
4. Configure automated test maintenance and coverage tracking
5. Create documentation and training for team testing practices

## ✓ VALIDATION CRITERIA

**Testing Coverage Excellence:**
- Unit tests achieve minimum 85% line coverage and 90% branch coverage
- Integration tests cover all critical user workflows and API interactions
- End-to-end tests validate all business-critical functionality and user journeys
- Visual regression tests prevent UI inconsistencies across browsers and devices

**Quality Assurance Automation:**
- All tests execute successfully in CI/CD pipeline with zero flaky test tolerance
- Cross-browser testing validates functionality on Chrome, Firefox, Safari, and Edge
- Accessibility tests achieve WCAG 2.1 AA compliance with zero critical violations
- Performance tests meet Core Web Vitals thresholds (LCP <2.5s, FID <100ms, CLS <0.1)

**Development Workflow Integration:**
- Pre-commit hooks prevent low-quality code commits with automated validation
- Pull request quality gates ensure all tests pass before code review
- Deployment pipeline blocks releases that fail quality standards
- Test execution completes within 15 minutes for full test suite

**Production Quality Monitoring:**
- Synthetic monitoring detects production issues within 5 minutes
- Performance monitoring alerts on Core Web Vitals degradation
- Error tracking captures and categorizes frontend errors with actionable insights
- Test maintenance automation keeps test suite healthy and up-to-date

## 💡 USAGE EXAMPLES

**E-commerce Application Testing:**
```
Testing Strategy: Focus on cart functionality, checkout workflows, product search
- Unit Tests: Product catalog components, cart logic, price calculations
- Integration Tests: Add-to-cart workflows, payment form validation, search filters
- E2E Tests: Complete purchase journey, user authentication, order management
- Performance Tests: Product page loading, search response times, checkout speed
- Accessibility Tests: Screen reader navigation, keyboard-only shopping experience
```

**Enterprise Dashboard Testing:**
```
Testing Strategy: Emphasize data visualization, user permissions, complex workflows
- Unit Tests: Chart components, data transformation utilities, permission helpers
- Integration Tests: Dashboard data loading, user role-based content, API integrations
- E2E Tests: Report generation, data export, multi-user collaboration features
- Performance Tests: Large dataset rendering, real-time data updates, memory usage
- Accessibility Tests: Chart accessibility, keyboard navigation, screen reader compatibility
```

**Healthcare Platform Testing:**
```
Testing Strategy: Prioritize privacy, accessibility, audit trails, regulatory compliance
- Unit Tests: Patient data components, medical calculations, validation logic
- Integration Tests: Electronic health records, appointment scheduling, secure messaging
- E2E Tests: Patient portal workflows, provider dashboards, compliance reporting
- Performance Tests: Medical record loading, search performance, real-time monitoring
- Accessibility Tests: WCAG AAA compliance, assistive technology support, medical device integration
```

**Financial Application Testing:**
```
Testing Strategy: Focus on security, precision, regulatory compliance, audit trails
- Unit Tests: Financial calculations, transaction processing, validation rules
- Integration Tests: Account management, transaction workflows, reporting systems
- E2E Tests: Banking operations, investment portfolios, regulatory reporting
- Performance Tests: Transaction processing speed, real-time market data, concurrent users
- Accessibility Tests: Financial data accessibility, calculator interfaces, assistive technology
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@frontend-engineer** leads testing strategy and implementation
- **@security-engineer** consultation for security testing patterns
- **@qa-engineer** coordination for advanced testing methodologies
- **@deployment-engineer** integration for CI/CD pipeline testing automation

**Integration with GitHub Copilot IDE:**
- Intelligent test generation based on component analysis and user behavior patterns
- Automated test case suggestions during code review and pull request workflows
- Real-time testing feedback integrated with IDE error highlighting and suggestions
- Context-aware testing recommendations based on project structure and technology stack

---
*This prompt enables comprehensive frontend testing and quality assurance with automated validation across accessibility, performance, and cross-browser compatibility for all business domains and project scales.*