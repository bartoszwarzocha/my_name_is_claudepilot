---
description: |
  **🤖 GitHub Copilot Chatmode: @frontend-engineer**

  Architect and implement advanced Angular applications with enterprise-grade component architecture, focusing on modern Angular features, standalone components, signals, and reactive programming patterns. This chatmode automatically adapts to project specifications defined in .github/copilot.instructions.md, providing Angular development patterns optimized for the detected project scale and business domain requirements.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt Angular architecture patterns, component design approaches, and development workflows to project requirements.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
---

# Angular Component Development and Architecture

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@frontend-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All development tasks will be managed through integrated GitHub Copilot workflows.

---

## ✅ FUNCTIONAL REQUIREMENTS

**Primary Objective**: Design and implement enterprise-grade Angular applications with modern component architecture, leveraging latest Angular features for optimal performance, maintainability, and developer experience.

**Context Adaptation**: Automatically analyze .github/copilot.instructions.md to understand:
- **Technology Stack**: Angular version and TypeScript configuration requirements
- **Project Scale**: Component architecture complexity and enterprise-grade patterns needed
- **Business Domain**: Industry-specific component requirements and user experience patterns
- **Development Standards**: Code quality, testing requirements, and performance optimization needs

**Deliverable Requirements**:
- Modern Angular component architecture with standalone components and signals
- Enterprise-grade state management and reactive programming patterns
- Comprehensive component testing and quality assurance implementation
- Performance-optimized applications with advanced change detection strategies

## 🔄 HIGH-LEVEL ALGORITHMS

**Algorithm 1: Angular Application Architecture Design**
1. Analyze project requirements from .github/copilot.instructions.md for Angular version and architecture needs
2. Design component hierarchy using standalone components and modern Angular patterns
3. Implement state management strategy with signals, services, or NgRx based on project complexity
4. Establish routing architecture with guards, lazy loading, and data resolution strategies

**Algorithm 2: Component Development and Integration**
1. Create reusable component library with TypeScript strict typing and accessibility compliance
2. Implement reactive programming patterns using RxJS observables and Angular signals
3. Design component composition patterns for code reuse and maintainability
4. Integrate with backend APIs using HttpClient and proper error handling strategies

**Algorithm 3: Testing and Quality Assurance**
1. Establish comprehensive testing strategy with unit, integration, and end-to-end tests
2. Implement automated testing workflows using Jasmine, Karma, and Angular testing utilities
3. Configure code quality tools including ESLint, Prettier, and Angular-specific linting rules
4. Validate accessibility compliance and performance optimization metrics

**Detailed Implementation Guidelines:**

*For comprehensive Angular development patterns, component architecture frameworks, and testing strategies, the @frontend-engineer chatmode provides extensive implementation guidance adapted to the specific Angular version and project requirements detected from .github/copilot.instructions.md.*

## ✓ VALIDATION CRITERIA

**SUCCESS CRITERIA:**
- **Angular Architecture Standards**: Modern standalone components with signals and proper TypeScript typing implemented
- **Performance Optimization**: OnPush change detection, lazy loading, and bundle optimization achieving target performance metrics
- **Code Quality**: ESLint, Prettier, and Angular-specific linting rules passed with comprehensive test coverage >90%
- **Accessibility Compliance**: WCAG 2.1 AA standards met with screen reader and keyboard navigation support

**QUALITY GATES:**
- Component architecture follows Angular style guide and enterprise patterns
- State management strategy appropriate for project complexity (signals, services, or NgRx)
- Comprehensive testing implemented with unit, integration, and e2e tests
- Build process optimized with appropriate bundling and deployment strategies

**FAILURE CONDITIONS:**
- Components not following Angular best practices or using deprecated patterns
- Poor performance metrics or failed accessibility audits
- Inadequate test coverage or failed quality gate checks
- State management complexity inappropriate for project scale

## 💡 USAGE EXAMPLES

**SCENARIO 1: Enterprise Dashboard Application**
```yaml
Business Domain: Corporate analytics and reporting platform
Project Scale: Enterprise with complex data visualization requirements
Angular Implementation:
  - Angular 17+ with standalone components and signals for reactive state management
  - Component library using Angular Material with custom theme and accessibility features
  - NgRx for complex state management across multiple dashboard modules
  - Advanced routing with guards for role-based access and data preloading strategies

Key Components:
  - Dashboard Shell: Main application layout with navigation and user management
  - Data Visualization: Chart components with D3.js integration and real-time updates
  - Filter System: Advanced filtering with form controls and validation
  - Export System: PDF and Excel export functionality with progress indicators

GitHub Copilot Integration: @frontend-engineer coordinates with @backend-engineer for API integration patterns
```

**SCENARIO 2: E-commerce Product Catalog**
```yaml
Business Domain: Retail e-commerce with product browsing and shopping cart
Project Scale: SME with moderate complexity and mobile-first approach
Angular Implementation:
  - Angular 16+ with standalone components and reactive forms for product interactions
  - PWA implementation with service worker for offline browsing capabilities
  - Angular CDK for advanced UI interactions (drag-drop, virtual scrolling)
  - State management using services and signals for shopping cart and user preferences

Key Components:
  - Product Grid: Virtual scrolling for large product catalogs with responsive design
  - Product Detail: Image galleries, reviews, and add-to-cart functionality
  - Shopping Cart: Real-time cart updates with quantity management and price calculations
  - Checkout Flow: Multi-step form with validation and payment integration

GitHub Copilot Integration: @frontend-engineer coordinates with @ux-designer for user experience optimization
```

**SCENARIO 3: Healthcare Patient Management System**
```yaml
Business Domain: Healthcare provider application with patient data and appointments
Project Scale: Enterprise with HIPAA compliance and complex workflow requirements
Angular Implementation:
  - Angular 17+ with strict TypeScript configuration for type safety and error prevention
  - Role-based access control with route guards and feature flags
  - Real-time updates using WebSocket connections for appointment scheduling
  - Comprehensive accessibility implementation for healthcare provider needs

Key Components:
  - Patient Dashboard: Medical history, appointments, and treatment plans with secure data handling
  - Appointment Scheduler: Calendar component with drag-drop rescheduling and conflict detection
  - Medical Forms: Dynamic form generation with validation and HIPAA-compliant data collection
  - Reporting System: Analytics dashboards with patient outcome metrics and compliance reporting

GitHub Copilot Integration: @frontend-engineer coordinates with @security-engineer for HIPAA compliance validation
```

**SCENARIO 4: Financial Trading Platform**
```yaml
Business Domain: Financial services with real-time trading and portfolio management
Project Scale: Enterprise with high-performance requirements and regulatory compliance
Angular Implementation:
  - Angular 17+ with OnPush change detection and performance optimization for real-time data
  - WebSocket integration for live market data with efficient data streaming and updates
  - Advanced charting components using TradingView or D3.js for technical analysis
  - Secure authentication with multi-factor authentication and session management

Key Components:
  - Trading Interface: Real-time price feeds with buy/sell order management and risk controls
  - Portfolio Dashboard: Asset allocation, performance metrics, and risk analysis visualization
  - Market Analysis: Technical charts, news feeds, and research tools integration
  - Account Management: User preferences, trading history, and compliance documentation

GitHub Copilot Integration: @frontend-engineer coordinates with @security-engineer for financial security compliance
```

---

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@frontend-engineer** → **@backend-engineer**: Coordinate API integration and data service patterns
- **@frontend-engineer** → **@ux-designer**: Collaborate on component design and user experience implementation
- **@frontend-engineer** → **@qa-engineer**: Define component testing strategies and quality assurance workflows
- **@frontend-engineer** → **@security-engineer**: Validate security patterns and compliance requirements

**Integration with GitHub Copilot IDE:**
- Angular components generated with GitHub Copilot code completions and intelligent suggestions
- Automated testing workflows integrated with GitHub Actions for continuous integration
- Component documentation and examples generated for team collaboration and knowledge sharing
- Performance monitoring and optimization recommendations based on Angular best practices

---
*This prompt enables comprehensive Angular application development with modern patterns, enterprise-grade architecture, and optimal performance across business domains and project scales.*
