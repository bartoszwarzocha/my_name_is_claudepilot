---
description: |
  **🤖 GitHub Copilot Chatmode: @ux-designer**

  Conduct comprehensive user research and create actionable user personas to guide design and development decisions. This chatmode automatically adapts to project specifications defined in .github/copilot.instructions.md, providing industry-specific research methodologies and persona development approaches tailored to the detected business domain and project scale.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt research methods, persona frameworks, and validation approaches to project requirements.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
---

# User Research and Persona Development

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@ux-designer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All research tasks will be managed through integrated GitHub Copilot workflows.

---

## ✅ FUNCTIONAL REQUIREMENTS

**Primary Objective**: Conduct systematic user research and develop comprehensive user personas that effectively guide design and development decisions across different business domains and project scales.

**Context Adaptation**: Automatically analyze .github/copilot.instructions.md to understand:
- **Business Domain**: Industry-specific user behaviors and research needs
- **Project Scale**: Appropriate research methodology selection and resource allocation
- **Target Audience**: Primary user segments and demographic characteristics
- **Development Stage**: Research timing and integration with product development lifecycle

**Deliverable Requirements**:
- Comprehensive user research findings with validated insights
- Detailed primary persona profiles representing key user segments
- Research-backed design principles and user experience guidelines
- Integration recommendations for development and business strategy teams

## 🔄 HIGH-LEVEL ALGORITHMS

**Algorithm 1: Adaptive Research Method Selection**
1. Analyze .github/copilot.instructions.md for business domain, project scale, and user characteristics
2. Select appropriate research methodologies based on project constraints and requirements
3. Design research plan with participant recruitment, data collection, and analysis frameworks
4. Execute research using qualitative and quantitative methods adapted to project context

**Algorithm 2: Systematic Persona Development**
1. Analyze research data to identify behavioral patterns and user segment clusters
2. Prioritize user segments based on business impact and development feasibility
3. Create detailed persona profiles with goals, pain points, and behavioral characteristics
4. Validate personas with stakeholders and integrate with development and business workflows

**Algorithm 3: Research Integration and Application**
1. Translate persona insights into actionable design principles and development requirements
2. Create persona-driven user stories and acceptance criteria for development teams
3. Establish continuous validation processes for persona accuracy and relevance
4. Coordinate with business and development teams for persona-guided decision making

**Detailed Research and Implementation Guidelines:**

*For comprehensive research methodologies, persona development frameworks, and domain-specific approaches, the @ux-designer chatmode provides extensive implementation guidance adapted to the specific business domain and project scale detected from .github/copilot.instructions.md.*

## ✓ VALIDATION CRITERIA

**SUCCESS CRITERIA:**
- **Research Quality Standards**: Participant diversity across target segments with data saturation in qualitative themes
- **Persona Validation**: Stakeholder alignment achieved on persona accuracy and business applicability
- **Integration Effectiveness**: Design decisions align with persona needs and drive measurable improvements
- **Business Impact**: Feature adoption rates and user satisfaction scores improve for targeted persona segments

**QUALITY GATES:**
- Research methodology appropriate for detected business domain and project scale
- Persona profiles supported by validated data with stakeholder consensus
- Design principles derived from research translate into actionable development requirements
- Continuous validation process established for persona accuracy and market relevance

**FAILURE CONDITIONS:**
- Personas based on assumptions rather than validated research data
- Research methods inappropriate for project constraints or business domain requirements
- Stakeholder rejection of persona accuracy or business applicability
- No measurable impact on design decisions or development prioritization

## 💡 USAGE EXAMPLES

**SCENARIO 1: E-commerce Platform User Research**
```yaml
Business Domain: E-commerce retail platform
Project Scale: SME with moderate research resources
Research Approach:
  - Customer interview program with 12 participants across 3 segments
  - Purchase behavior analytics analysis and competitive research
  - Survey deployment to existing customer base (500+ responses)
  - Usability testing of current checkout and product discovery flows

Resulting Personas:
  - Frequent Shoppers: Convenience-focused, mobile-first, loyalty program engaged
  - Occasional Buyers: Research-heavy, price-conscious, desktop comparison shopping
  - Gift Purchasers: Time-constrained, customer service dependent, seasonal patterns
  - Accessibility-Conscious: Screen reader users, keyboard navigation, clear content needs

GitHub Copilot Integration: @ux-designer chatmode coordinates with @frontend-engineer for persona-driven interface development
```

**SCENARIO 2: Healthcare Management Application**
```yaml
Business Domain: Healthcare patient management system
Project Scale: Enterprise with comprehensive research budget
Research Approach:
  - Ethnographic studies in clinical environments with providers and patients
  - HIPAA-compliant interview program across multiple healthcare roles
  - Workflow observation and current system usability assessment
  - Accessibility research for age-diverse and disability-inclusive design

Resulting Personas:
  - Healthcare Providers: Efficiency-focused, workflow integration, patient care optimization
  - Patients: Health management, communication needs, privacy and trust requirements
  - Healthcare Administrators: Compliance focus, operational efficiency, reporting needs
  - Caregivers: Care coordination, information access, family communication support

GitHub Copilot Integration: @ux-designer chatmode coordinates with @security-engineer for HIPAA compliance and data protection
```

**SCENARIO 3: Financial Technology Startup**
```yaml
Business Domain: Personal finance management mobile app
Project Scale: Startup with lean research methodology
Research Approach:
  - Guerrilla research with 8 participants per target segment
  - Financial behavior survey distributed through social media and networks
  - Competitive analysis of existing fintech applications and user reviews
  - Analytics review of beta user behavior patterns and feature usage

Resulting Personas:
  - Young Professionals: Career growth focused, mobile-native, investment curious
  - Budget-Conscious Families: Expense tracking, savings goals, financial education needs
  - Gig Economy Workers: Variable income management, tax preparation, multiple income streams
  - Security-Focused Users: Privacy requirements, two-factor authentication, data control needs

GitHub Copilot Integration: @ux-designer chatmode coordinates with @backend-engineer for secure financial data handling
```

**SCENARIO 4: Enterprise SaaS Project Management Tool**
```yaml
Business Domain: B2B project management and team collaboration platform
Project Scale: Enterprise with complex multi-role user base
Research Approach:
  - Role-based interview program across organizational hierarchies and departments
  - Workflow analysis and current tool integration assessment
  - Cross-industry research covering different business domains and project types
  - Longitudinal study tracking tool adoption and usage evolution

Resulting Personas:
  - Project Managers: Timeline management, resource allocation, stakeholder communication
  - Team Members: Task completion, collaboration efficiency, progress visibility
  - Executives: High-level overview, ROI measurement, strategic alignment
  - System Administrators: User management, security, integration and customization

GitHub Copilot Integration: @ux-designer chatmode coordinates with @api-engineer for role-based permissions and integrations
```

---

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@ux-designer** → **@frontend-engineer**: Transfer persona insights for user interface implementation
- **@ux-designer** → **@business-analyst**: Collaborate on persona-aligned content strategy and messaging
- **@ux-designer** → **@product-manager**: Coordinate persona needs with feature prioritization and roadmap planning
- **@ux-designer** → **@qa-engineer**: Define persona-based testing scenarios and usability validation criteria

**Integration with GitHub Copilot IDE:**
- Personas documented in project repository for consistent team access and development integration
- User research insights integrated into GitHub Issues and Project planning workflows
- Persona-driven acceptance criteria generation for development stories and feature specifications
- Continuous validation workflows using GitHub Actions for persona relevance and market alignment

---
*This prompt enables systematic user research and persona development that provides the foundation for user-centered design decisions across business domains and project scales.*