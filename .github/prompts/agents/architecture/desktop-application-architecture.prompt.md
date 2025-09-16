---
description: Design comprehensive desktop application architecture that adapts to the technology stack, implementing appropriate architectural patterns, separation of concerns, and maintainable code structure for desktop applications.
tools:
  - codebase
  - search
  - editFiles
  - runCommands
model: claude-4-sonnet
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `software-architect` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Desktop Application Architecture Design

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Desktop-Specific Architecture Design
- **Application Structure**: Create scalable desktop application architecture with proper separation of concerns and maintainable code organization
- **UI/UX Architecture**: Design responsive, accessible desktop user interfaces that provide excellent user experience across different screen sizes
- **Performance Optimization**: Implement efficient resource management, memory optimization, and responsive user interactions
- **Platform Integration**: Design native platform integrations while maintaining cross-platform compatibility where required

### Technology Stack Integration
- **Framework Selection**: Choose and integrate appropriate desktop frameworks based on technology stack and platform requirements
- **Native Features**: Design integration with native desktop features like file system access, notifications, and system tray
- **Data Management**: Create efficient data storage, synchronization, and backup strategies for desktop applications
- **Security Implementation**: Implement desktop-specific security measures including data encryption and secure storage

### Scalability and Maintainability
- **Modular Design**: Create modular architecture that supports feature additions and independent component development
- **Code Organization**: Design clear code structure with proper layering and dependency management
- **Testing Architecture**: Plan comprehensive testing strategies including unit, integration, and UI automation testing
- **Deployment Strategy**: Design efficient deployment and update mechanisms for desktop applications

### User Experience and Accessibility
- **Responsive Design**: Create adaptive layouts that work across different screen resolutions and window sizes
- **Accessibility Standards**: Implement comprehensive accessibility features following platform-specific guidelines
- **Performance UX**: Design architecture that maintains responsive user interactions under various load conditions
- **Offline Capabilities**: Plan offline-first architecture with data synchronization when connectivity is available

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Technology Stack Analysis and Platform Requirements
```
1. Read copilot.instructions.md to extract:
   - Desktop technology stack and framework preferences
   - Target platforms and cross-platform requirements
   - Performance and user experience expectations
   - Integration requirements with external systems

2. Platform and Framework Assessment:
   - Analyze target platform requirements (Windows, macOS, Linux)
   - Evaluate framework capabilities and limitations
   - Assess development team expertise and project constraints
   - Review existing codebase and migration requirements
```

### 2. Architecture Pattern Selection and Design
```
1. Desktop Architecture Patterns:
   - Select appropriate patterns (MVC, MVP, MVVM, Clean Architecture)
   - Design component separation and responsibility boundaries
   - Plan data flow and state management strategies
   - Create event handling and communication patterns

2. Application Structure Design:
   - Design main application structure and entry points
   - Plan module organization and dependency management
   - Create service layer and business logic architecture
   - Design data access and persistence patterns
```

### 3. User Interface and Experience Architecture
```
1. UI Architecture Design:
   - Design responsive layout systems and component hierarchy
   - Plan theme and styling architecture for maintainability
   - Create reusable component libraries and design systems
   - Design navigation and user flow patterns

2. Interaction and State Management:
   - Plan application state management strategies
   - Design user interaction patterns and event handling
   - Create data binding and synchronization mechanisms
   - Plan error handling and user feedback systems
```

### 4. Performance and Resource Optimization
```
1. Performance Architecture:
   - Design efficient memory management and resource utilization
   - Plan background processing and threading strategies
   - Create caching and data optimization patterns
   - Design startup and loading optimization strategies

2. System Integration:
   - Plan native platform feature integration
   - Design file system and external resource access
   - Create inter-process communication if needed
   - Plan update and deployment mechanisms
```

### 5. Security and Data Protection
```
1. Desktop Security Architecture:
   - Design data encryption and secure storage mechanisms
   - Plan user authentication and authorization patterns
   - Create secure communication with external services
   - Design audit logging and security monitoring

2. Data Management and Backup:
   - Plan local data storage and database integration
   - Design data synchronization and backup strategies
   - Create import/export functionality and data portability
   - Plan disaster recovery and data protection measures
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Architecture Quality and Design
- **Separation of Concerns**: Clear separation between UI, business logic, and data layers
- **Modularity**: Well-defined modules with clear interfaces and minimal coupling
- **Scalability**: Architecture supports feature additions and application growth
- **Maintainability**: Code organization enables easy maintenance and debugging

### ✅ User Experience and Performance
- **Responsiveness**: Application maintains responsive UI under various load conditions
- **Performance Standards**: Fast startup times and efficient resource utilization
- **Accessibility**: Comprehensive accessibility features following platform guidelines
- **Cross-Platform Compatibility**: Consistent behavior across target platforms

### ✅ Technical Implementation Excellence
- **Framework Integration**: Proper use of chosen framework capabilities and conventions
- **Error Handling**: Comprehensive error handling with user-friendly feedback
- **Security Implementation**: Robust security measures appropriate for desktop applications
- **Testing Support**: Architecture enables comprehensive automated testing

### ✅ Platform Integration and Features
- **Native Integration**: Proper integration with platform-specific features and conventions
- **File System Access**: Secure and efficient file system operations
- **System Integration**: Integration with system notifications, clipboard, and other OS features
- **Update Mechanisms**: Reliable application update and maintenance capabilities

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with frontend-engineer and other relevant chatmodes
- **Documentation Quality**: Comprehensive architectural documentation and design decisions
- **Configuration Adaptation**: Proper adaptation to detected desktop technology stack
- **Development Workflow**: Architecture supports efficient GitHub Copilot development patterns

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Electron Business Application
```yaml
Context: Cross-platform business application with complex data management
Technology Stack: Detected from copilot.instructions.md (Electron, React, TypeScript, SQLite)
Business Domain: Business productivity tool with offline capabilities and cloud sync

Architecture Focus:
- Main/renderer process architecture with IPC communication
- React-based UI with responsive design and component libraries
- SQLite local database with cloud synchronization
- File system integration for document management

GitHub Copilot Workflow:
1. software-architect chatmode → Design Electron application architecture
2. frontend-engineer chatmode → Implement React UI components and state management
3. data-engineer chatmode → Design local database and sync patterns
4. security-engineer chatmode → Implement data protection and secure communication

Expected Deliverables:
- Electron application architecture with proper process separation
- React UI architecture with responsive design system
- Local data storage with cloud synchronization
- Cross-platform deployment and auto-update system
```

### Scenario 2: WPF Enterprise Application
```yaml
Context: Windows enterprise application with complex business workflows
Technology Stack: Enterprise setup (C#, WPF, Entity Framework, SQL Server)
Business Domain: Enterprise resource planning with role-based access and reporting

Architecture Focus:
- MVVM architecture with proper view model design
- Entity Framework integration with complex business entities
- Role-based security and audit logging
- Advanced reporting and data visualization

GitHub Copilot Workflow:
1. software-architect chatmode → Design WPF MVVM architecture
2. data-engineer chatmode → Implement Entity Framework models and repositories
3. security-engineer chatmode → Design enterprise security and audit systems
4. qa-engineer chatmode → Create comprehensive testing strategies

Expected Deliverables:
- WPF application with clean MVVM architecture
- Entity Framework integration with business logic layer
- Enterprise security with role-based access control
- Comprehensive reporting and data visualization components
```

### Scenario 3: PyQt Scientific Application
```yaml
Context: Scientific data analysis application with complex visualizations
Technology Stack: Scientific setup (Python, PyQt6, NumPy, Matplotlib, PostgreSQL)
Business Domain: Scientific research with data analysis and visualization

Architecture Focus:
- Model-View-Presenter architecture for scientific workflows
- Advanced data visualization and interactive plotting
- Plugin architecture for extensible analysis modules
- High-performance data processing and computation

GitHub Copilot Workflow:
1. software-architect chatmode → Design PyQt scientific application architecture
2. data-engineer chatmode → Implement data processing and database integration
3. frontend-engineer chatmode → Create advanced visualization components
4. qa-engineer chatmode → Design scientific validation and testing procedures

Expected Deliverables:
- PyQt application with scientific workflow architecture
- Advanced data visualization and interactive plotting components
- Plugin system for extensible analysis capabilities
- High-performance data processing with scientific libraries
```

### Scenario 4: JavaFX Cross-Platform Application
```yaml
Context: Cross-platform desktop application with modern UI requirements
Technology Stack: Modern setup (Java, JavaFX, Spring Boot, H2/PostgreSQL)
Business Domain: Creative tools with real-time collaboration and cloud integration

Architecture Focus:
- JavaFX with FXML and CSS for modern UI design
- Spring Boot integration for dependency injection and services
- Real-time collaboration with WebSocket communication
- Plugin architecture for extensible creative tools

GitHub Copilot Workflow:
1. software-architect chatmode → Design JavaFX application architecture
2. api-engineer chatmode → Implement real-time communication and cloud integration
3. frontend-engineer chatmode → Create modern JavaFX UI with CSS styling
4. deployment-engineer chatmode → Design cross-platform deployment and distribution

Expected Deliverables:
- JavaFX application with modern UI architecture
- Spring Boot integration with dependency injection
- Real-time collaboration with WebSocket integration
- Cross-platform deployment with native installers
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Desktop Architecture Design → software-architect chatmode (lead)
├─ UI Implementation → frontend-engineer chatmode
├─ Data Architecture → data-engineer chatmode
├─ Security Implementation → security-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Deployment Pipeline → deployment-engineer chatmode
```

### Context Handoff Information
- **To frontend-engineer**: UI architecture, component design, user interaction patterns, styling requirements
- **To data-engineer**: Data storage patterns, synchronization requirements, performance optimization
- **To security-engineer**: Security architecture, data protection, user authentication patterns
- **To qa-engineer**: Testing strategies, automation requirements, performance benchmarks
- **To deployment-engineer**: Deployment requirements, platform-specific packaging, update mechanisms

### GitHub Actions Integration
- **Architecture Validation**: Automated validation of architectural patterns and design decisions
- **Performance Testing**: Automated performance testing for desktop application responsiveness
- **Cross-Platform Testing**: Automated testing across different operating systems
- **Package Generation**: Automated generation of platform-specific installation packages

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Desktop Framework**: Automatically detects and applies framework-specific architectural patterns (Electron, WPF, PyQt, JavaFX, etc.)
- **Platform Requirements**: Adapts architecture based on target platforms and cross-platform requirements
- **Business Domain**: Customizes architecture patterns for specific use cases (business, scientific, creative, etc.)
- **Performance Needs**: Optimizes architecture for desktop application performance and resource requirements
- **Integration Requirements**: Adapts to existing systems and external service integration needs

**The software-architect chatmode will automatically analyze project configuration and desktop requirements to design optimal desktop application architecture while maintaining the functional requirements specified above.**