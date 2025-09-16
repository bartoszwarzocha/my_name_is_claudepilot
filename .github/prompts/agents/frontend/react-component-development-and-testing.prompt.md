---
name: react-component-development-and-testing
description: |
  **🤖 GitHub Copilot Chatmode: @frontend-engineer**

  Expert React component development with TypeScript integration, comprehensive testing strategies, and modern patterns for scalable, maintainable applications.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt React development patterns to project requirements.
---

# React Component Development and Testing

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@frontend-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All React component development and testing tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Develop robust, scalable React components with comprehensive TypeScript integration, modern architectural patterns, and thorough testing strategies. Create reusable, accessible components that follow best practices for performance, maintainability, and user experience while integrating seamlessly with modern React ecosystem tools.

**React Development Requirements:**
- Implement modern React patterns including hooks, context, and compound components
- Establish comprehensive TypeScript integration with strict type safety
- Create thorough testing strategies covering unit, integration, and accessibility testing
- Configure performance optimization with memoization and lazy loading
- Implement accessibility best practices with ARIA and semantic HTML
- Establish component documentation and design system integration

## 🔄 HIGH-LEVEL ALGORITHMS

**Phase 1: Component Architecture and Design Patterns**
1. Read .github/copilot.instructions.md to determine React version, TypeScript config, and architectural preferences
2. Analyze project structure and existing component patterns for consistency
3. Design component architecture using appropriate patterns (compound, render props, custom hooks)
4. Implement TypeScript interfaces and types for component props and state
5. Configure component composition and reusability patterns

**Phase 2: Component Implementation and Optimization**
1. Develop components using modern React features and performance optimizations
2. Implement proper state management with hooks or external libraries
3. Configure memoization strategies for performance optimization
4. Establish error boundaries and error handling patterns
5. Implement accessibility features with ARIA attributes and semantic markup

**Phase 3: Testing Strategy Implementation**
1. Create comprehensive unit tests with React Testing Library
2. Implement integration tests for component interactions and workflows
3. Configure accessibility testing with axe-core and manual testing strategies
4. Develop performance testing for render times and memory usage
5. Establish visual regression testing for UI consistency

**Phase 4: Documentation and Maintenance**
1. Create component documentation with Storybook or similar tools
2. Implement design system integration and component variations
3. Configure automated testing pipelines and quality gates
4. Establish component maintenance patterns and refactoring strategies
5. Create component usage guidelines and best practices documentation

## ✓ VALIDATION CRITERIA

**Component Quality Standards:**
- All components implement proper TypeScript typing with zero 'any' types
- Component props include comprehensive validation and default values
- Error handling covers all edge cases with graceful degradation
- Performance optimization maintains 60fps rendering under normal load

**Testing Coverage Excellence:**
- Unit test coverage exceeds 90% for component logic and user interactions
- Integration tests validate component composition and data flow
- Accessibility tests ensure WCAG 2.1 AA compliance for all components
- Visual regression tests prevent unintended UI changes

**Architecture and Maintainability:**
- Components follow single responsibility principle with clear separation of concerns
- Custom hooks extract reusable logic with proper dependency management
- Component composition enables flexible layouts and content structures
- Documentation provides clear usage examples and API reference

**Performance and User Experience:**
- Components implement proper memoization to prevent unnecessary re-renders
- Lazy loading strategies optimize initial bundle size and load times
- Accessibility features support keyboard navigation and screen readers
- Error boundaries prevent component failures from crashing the application

## 💡 USAGE EXAMPLES

**E-commerce Product Component Development:**
```
Component Architecture: Focus on product display, cart integration, variation selection
- Components: ProductCard, ProductGallery, VariationSelector, AddToCart
- Testing: Price calculation, inventory validation, cart state management
- Accessibility: Product information for screen readers, keyboard navigation
- Performance: Image lazy loading, variation data memoization
- TypeScript: Product interfaces, cart types, API response types
```

**Enterprise Dashboard Component Suite:**
```
Component Architecture: Emphasize data visualization, user permissions, complex layouts
- Components: DataTable, ChartWidget, FilterPanel, UserRoleProvider
- Testing: Data transformation, permission validation, chart rendering
- Accessibility: Data table navigation, chart descriptions, filter announcements
- Performance: Virtual scrolling, chart data memoization, permission caching
- TypeScript: Chart data types, permission interfaces, dashboard configuration
```

**Healthcare Form Components:**
```
Component Architecture: Prioritize validation, data security, compliance requirements
- Components: MedicalForm, PatientSelector, ComplianceWrapper, AuditTrail
- Testing: Form validation, data sanitization, compliance requirements
- Accessibility: Form labels, error announcements, medical term definitions
- Performance: Form state optimization, validation debouncing, data persistence
- TypeScript: Medical data types, validation schemas, compliance interfaces
```

**Social Media Content Components:**
```
Component Architecture: Focus on content creation, real-time updates, user interactions
- Components: PostComposer, ContentFeed, InteractionButton, UserAvatar
- Testing: Content validation, real-time updates, interaction handling
- Accessibility: Content descriptions, interaction feedback, user context
- Performance: Content virtualization, image optimization, interaction debouncing
- TypeScript: Content types, user interfaces, interaction event types
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@frontend-engineer** leads React component architecture and implementation
- **@ux-designer** collaboration for component design and user experience patterns
- **@qa-engineer** coordination for testing strategies and accessibility validation
- **@performance-engineer** consultation for optimization and rendering performance

**Integration with GitHub Copilot IDE:**
- Intelligent component scaffolding based on project patterns and conventions
- Automated TypeScript interface generation from component props and usage
- Context-aware testing code generation with proper mocking and assertions
- Real-time accessibility and performance optimization suggestions during development

---
*This prompt enables expert React component development with TypeScript integration, comprehensive testing, and modern architectural patterns for all business domains and project scales.*