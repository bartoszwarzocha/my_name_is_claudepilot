---
name: pr-review-to-deployment
description: |
  **🤖 PR Review to Deployment Workflow**

  Complete pull request review and deployment orchestration with automated quality gates and intelligent deployment coordination. Adapts review and deployment strategy to project requirements and risk assessment.

  **📋 Context Integration**: Automatically reads copilot.instructions.md and adapts workflow execution to project deployment standards and quality requirements.
tools: [all]
model: claude-sonnet-4
workflow_type: end-to-end
---

# PR Review to Deployment - Complete Review and Release Workflow

**🤖 DEPLOYMENT WORKFLOW ACTIVATION**: This prompt orchestrates complete pull request review through production deployment with automated quality validation.
**📋 CONTEXT ADAPTATION**: The workflow reads copilot.instructions.md and adapts execution to project deployment standards and risk tolerance.
**🔄 INTELLIGENT QUALITY GATES**: Automated quality validation with deployment risk assessment and rollback preparation.

## ✅ FUNCTIONAL REQUIREMENTS

Orchestrate comprehensive pull request review and deployment workflow from code review initiation through production deployment validation, including automated quality assessment, security validation, deployment coordination, monitoring setup, and rollback preparation while maintaining deployment safety and business continuity standards.

**Context Integration Requirements:**
- Read and analyze copilot.instructions.md for deployment standards, quality gates, and risk tolerance configuration
- Analyze pull request changes including code modifications, test coverage, and integration impact assessment
- Execute comprehensive review process with automated quality checks and manual validation coordination
- Coordinate deployment process with appropriate staging, production rollout, and monitoring integration
- Maintain deployment audit trail and rollback capability throughout complete deployment lifecycle

## 🔄 HIGH-LEVEL ALGORITHMS

### PR Review to Deployment Orchestration

1. **Comprehensive Pull Request Analysis and Quality Assessment**
   - Analyze pull request changes including code modifications, test additions, and documentation updates
   - Read copilot.instructions.md to understand deployment standards, quality requirements, and risk tolerance
   - Execute automated quality checks including code analysis, security scanning, and performance validation
   - Assess deployment risk based on change scope, affected systems, and business impact considerations
   - Coordinate manual review process with appropriate reviewers and domain experts

2. **Quality Gate Validation and Approval Coordination**
   - Execute comprehensive testing including unit tests, integration tests, and acceptance criteria validation
   - Perform security validation including vulnerability scanning, dependency analysis, and compliance verification
   - Validate performance requirements including load testing, resource utilization, and scalability assessment
   - Coordinate approval process with appropriate stakeholders and technical reviewers
   - Generate deployment readiness assessment with risk analysis and rollback preparation

3. **Deployment Coordination and Production Rollout**
   - Plan deployment strategy based on risk assessment including staging, canary, or blue-green deployment
   - Execute deployment process with appropriate infrastructure preparation and monitoring setup
   - Coordinate production rollout with gradual traffic increase and performance monitoring
   - Validate deployment success through health checks, performance metrics, and error monitoring
   - Establish rollback procedures with automated triggers and manual intervention capabilities

4. **Post-Deployment Validation and Monitoring Setup**
   - Validate production deployment success through comprehensive health checking and performance validation
   - Monitor application performance with metrics tracking, error detection, and alerting configuration
   - Execute user acceptance validation and stakeholder feedback collection
   - Update deployment documentation with release notes, operational procedures, and troubleshooting guides
   - Establish continuous monitoring with performance tracking and proactive issue detection

## ✓ VALIDATION CRITERIA

### Code Quality and Review Excellence (REQUIRED)

**Pull Request Quality and Completeness (REQUIRED):**
- Code changes reviewed comprehensively with appropriate technical validation and best practice compliance
- Test coverage appropriate for change scope with unit tests, integration tests, and acceptance criteria validation
- Documentation updated including code comments, API documentation, and operational procedures
- Security validation complete with vulnerability scanning and compliance verification
- Performance impact assessed with appropriate load testing and resource utilization analysis

**Review Process and Approval (REQUIRED):**
- Manual review completed by appropriate domain experts and technical stakeholders
- Automated quality checks passed including code analysis, security scanning, and performance validation
- Deployment risk assessment completed with appropriate mitigation strategies and rollback preparation
- Stakeholder approval obtained with business impact assessment and deployment timing coordination
- Quality gates satisfied with comprehensive validation and approval documentation

### Deployment Success and Production Stability (REQUIRED)

**Deployment Execution and Validation (REQUIRED):**
- Deployment process executed successfully with appropriate staging and production rollout coordination
- Infrastructure preparation complete with monitoring setup and alerting configuration
- Performance validation confirms application stability and business functionality preservation
- Health checks active with appropriate monitoring and error detection systems
- Rollback procedures tested and available with automated triggers and manual intervention capabilities

**Post-Deployment Success and Monitoring (REQUIRED):**
- Production validation confirms successful deployment with expected functionality and performance
- Monitoring systems active with comprehensive metrics tracking and proactive issue detection
- User acceptance validation positive with stakeholder feedback and business value confirmation
- Documentation updated with release notes, operational procedures, and maintenance guidelines
- Continuous monitoring established with performance tracking and ongoing optimization capabilities

## 💡 USAGE EXAMPLES

### Critical Security Fix Deployment - React Enterprise Application

```yaml
PR Context: Security vulnerability fix in authentication system for React + TypeScript SaaS platform
Business Impact: Critical - immediate deployment required for security compliance
Technology Stack: React, Node.js Express API, PostgreSQL, AWS infrastructure with enterprise security
Review Team: Security engineer, backend engineer, and technical lead

Workflow Execution:
- PR analysis reveals authentication token handling improvements with security implications
- Quality assessment includes comprehensive security testing and vulnerability validation
- Review coordination involves security-engineer and backend-engineer specialized validation
- Deployment strategy includes staging validation followed by immediate production rollout
- Post-deployment validation includes security monitoring and user authentication verification

Key Deliverables:
- Comprehensive security review with vulnerability assessment and remediation validation
- Automated security testing with penetration testing and compliance verification
- Expedited deployment process with appropriate security validation and monitoring setup
- Production security monitoring with threat detection and incident response integration
- Security documentation with vulnerability resolution and prevention measures
```

### Feature Release Deployment - Java Microservices Platform

```yaml
PR Context: New payment processing feature for financial services microservices platform
Business Impact: High - new revenue stream with regulatory compliance requirements
Technology Stack: Java Spring Boot, Maven, PostgreSQL, Kubernetes with enterprise compliance
Review Team: Backend engineers, security specialists, and compliance reviewers

Workflow Execution:
- PR analysis reveals complex payment integration with compliance and security requirements
- Quality assessment includes comprehensive testing, security validation, and compliance verification
- Review coordination involves backend-engineer, security-engineer, and reviewer specialized validation
- Deployment strategy includes staged rollout with canary deployment and monitoring integration
- Post-deployment validation includes payment functionality testing and compliance verification

Key Deliverables:
- Comprehensive code review with enterprise Java patterns and financial services compliance
- Payment processing validation with security testing and regulatory compliance verification
- Staged deployment process with canary rollout and comprehensive monitoring integration
- Financial compliance documentation with audit trails and regulatory approval processes
- Production monitoring with payment transaction tracking and error detection systems
```

### Performance Optimization Deployment - Python ML Platform

```yaml
PR Context: Machine learning model inference performance improvements
Business Impact: Medium - user experience enhancement and infrastructure cost optimization
Technology Stack: Python FastAPI, PyTorch, Docker, Kubernetes with ML pipeline optimization
Review Team: Data engineers, backend engineers, and performance specialists

Workflow Execution:
- PR analysis reveals ML model optimization with performance and accuracy considerations
- Quality assessment includes performance benchmarking, accuracy validation, and resource utilization testing
- Review coordination involves data-engineer, backend-engineer, and qa-engineer specialized validation
- Deployment strategy includes gradual rollout with A/B testing and performance monitoring
- Post-deployment validation includes model accuracy verification and performance metrics tracking

Key Deliverables:
- ML model optimization review with performance benchmarking and accuracy preservation validation
- Comprehensive performance testing with load testing and resource utilization analysis
- Gradual deployment process with A/B testing framework and model performance monitoring
- ML performance documentation with optimization techniques and monitoring integration
- Production ML monitoring with model accuracy tracking and performance optimization
```

## 🔄 GitHub Copilot Review and Deployment Integration

**Review Phase Coordination:**
- **Code Quality Review** → **qa-engineer**: Comprehensive code analysis and quality validation
- **Security Assessment** → **security-engineer**: Security vulnerability assessment and compliance verification
- **Architecture Review** → **software-architect**: Architecture impact assessment and integration validation

**Deployment Phase Coordination:**
- **Deployment Planning** → **deployment-engineer**: Infrastructure preparation and deployment strategy coordination
- **Quality Validation** → **qa-engineer**: Performance testing and acceptance criteria validation
- **Production Monitoring** → **deployment-engineer**: Monitoring setup and health checking configuration

**GitHub Copilot IDE Integration:**
- Automated code review with intelligent suggestion and quality improvement recommendations
- Deployment coordination with infrastructure automation and monitoring integration
- Post-deployment validation with performance tracking and continuous improvement capabilities
- Risk assessment integration with automated rollback and incident response coordination

---
*This workflow provides comprehensive pull request review and deployment coordination from code analysis to production validation with enterprise-grade quality assurance and risk management.*