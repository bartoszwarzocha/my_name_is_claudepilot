---
# YAML HEADER CONFIGURATION - Complete Reference
# This template contains ALL possible YAML header values for GitHub Copilot prompts

# MANDATORY FIELDS
name: [unique-prompt-name]
description: |
  [Brief description of what this prompt accomplishes]

  [Optional additional context or usage notes]

# MODEL CONFIGURATION
model: [CHOOSE ONE or OMIT for default]
  # Available models:
  # - claude-sonnet-4        # Anthropic Claude Sonnet 4 (recommended for complex tasks)
  # - gpt-4o                 # OpenAI GPT-4o (general purpose)
  # - o1-preview             # OpenAI o1-preview (reasoning tasks)
  # - gemini-2.0-flash       # Google Gemini 2.0 Flash (fast responses)
  # - github-copilot         # Default GitHub Copilot model
  # - auto                   # Automatic model selection based on task

# TOOLS CONFIGURATION - Complete List of Available Tools
tools: [LIST_OF_TOOLS or "all"]
  # Core GitHub Copilot Tools:
  # - "codebase"             # Search and analyze codebase files
  # - "search"               # General search functionality
  # - "githubRepo"           # GitHub repository operations and code search
  # - "fetch"                # Fetch content from web pages and URLs
  # - "problems"             # Access VS Code problems, test failures, terminal output
  # - "vscodeAPI"            # VS Code API operations and workspace management
  # - "usages"               # Find symbol usages and references in codebase
  #
  # GitHub-specific Tools:
  # - "github"               # General GitHub operations
  # - "get_me"               # Get current GitHub user information
  # - "get_pull_request"     # Retrieve pull request details
  # - "get_pull_request_comments" # Get PR comments and discussions
  # - "get_pull_request_diff"     # Get PR diff and changes
  # - "get_pull_request_files"    # List files changed in PR
  # - "get_pull_request_reviews"  # Get PR reviews and feedback
  # - "get_pull_request_status"   # Check PR status and checks
  # - "list_pull_requests"        # List repository pull requests
  # - "request_copilot_review"    # Request AI code review
  #
  # Database Tools (if extensions installed):
  # - "pgsql_connect"        # PostgreSQL connection management
  # - "pgsql_query"          # Execute PostgreSQL queries
  #
  # Development Tools:
  # - "terminal"             # Terminal command execution (requires auto-approve config)
  # - "file-system"          # File system operations
  # - "test-runner"          # Test execution and management
  # - "debug"                # Debugging operations
  # - "git"                  # Git version control operations
  #
  # Special Values:
  # - "all"                  # Enable all available tools
  # - []                     # No specific tools (use default set)

# OPERATIONAL MODE
mode: [CHOOSE ONE or OMIT for default]
  # Available modes:
  # - "agent"                # Agent mode with autonomous reasoning and tool usage
  # - "chat"                 # Interactive chat mode
  # - "completion"           # Code completion mode
  # - "review"               # Code review mode
  # - "workflow"             # Multi-step workflow orchestration

# CONTEXT CONFIGURATION
context_adaptation: [true/false]
  # true  - Automatically adapt to project context from .github/copilot-instructions.md
  # false - Use prompt as-is without context adaptation

# WORKFLOW CONFIGURATION (for workflow-type prompts)
workflow_type: [WORKFLOW_TYPE or OMIT]
  # Workflow types:
  # - "end-to-end"           # Complete development lifecycle workflow
  # - "coordination"         # Multi-chatmode coordination workflow
  # - "incident-response"    # Bug fixing and incident management
  # - "strategic"            # Long-term planning and architecture
  # - "governance"           # Compliance and quality governance
  # - "integration"          # System integration and deployment

# SPECIALIZATION CONFIGURATION
specialization: [DOMAIN or OMIT]
  # Domain specializations:
  # - "frontend"             # Frontend development specialization
  # - "backend"              # Backend development specialization
  # - "fullstack"            # Full-stack development
  # - "devops"               # DevOps and infrastructure
  # - "data"                 # Data engineering and analytics
  # - "mobile"               # Mobile application development
  # - "security"             # Security and compliance
  # - "ml"                   # Machine learning and AI
  # - "enterprise"           # Enterprise development patterns

# QUALITY CONFIGURATION
validation_level: [LEVEL or OMIT]
  # Validation levels:
  # - "strict"               # Strict quality validation and compliance
  # - "standard"             # Standard quality checks
  # - "permissive"           # Relaxed validation for rapid prototyping

# INTEGRATION CONFIGURATION
chatmode_integration: [true/false or OMIT]
  # true  - This prompt integrates with chatmode ecosystem
  # false - Standalone prompt without chatmode dependencies

# BUSINESS DOMAIN CONFIGURATION
business_domain: [DOMAIN or OMIT]
  # Business domains:
  # - "saas"                 # Software as a Service
  # - "enterprise"           # Enterprise software
  # - "fintech"              # Financial technology
  # - "healthcare"           # Healthcare and medical
  # - "ecommerce"            # E-commerce platforms
  # - "education"            # Educational technology
  # - "gaming"               # Gaming and entertainment
  # - "iot"                  # Internet of Things
  # - "blockchain"           # Blockchain and cryptocurrency

# COMPLIANCE CONFIGURATION
compliance_requirements: [LIST or OMIT]
  # Compliance frameworks:
  # - "sox"                  # Sarbanes-Oxley compliance
  # - "hipaa"                # Healthcare data protection
  # - "gdpr"                 # General Data Protection Regulation
  # - "pci-dss"              # Payment Card Industry standards
  # - "soc2"                 # Service Organization Control 2
  # - "iso27001"             # Information Security Management
  # - "fda"                  # FDA medical device compliance

# PERFORMANCE CONFIGURATION
performance_mode: [MODE or OMIT]
  # Performance modes:
  # - "fast"                 # Optimize for speed
  # - "balanced"             # Balance speed and quality
  # - "thorough"             # Optimize for completeness and quality

# LANGUAGE CONFIGURATION
primary_language: [LANGUAGE or OMIT]
  # Programming languages:
  # - "typescript"           # TypeScript/JavaScript
  # - "python"               # Python
  # - "java"                 # Java
  # - "csharp"               # C#/.NET
  # - "go"                   # Go
  # - "rust"                 # Rust
  # - "php"                  # PHP
  # - "ruby"                 # Ruby
  # - "kotlin"               # Kotlin
  # - "swift"                # Swift
  # - "cpp"                  # C++

# EXPERIMENTAL FEATURES
experimental: [true/false or OMIT]
  # true  - Enable experimental GitHub Copilot features
  # false - Use stable features only

---

# [Prompt Title - Descriptive Name of What This Prompt Does]

**🤖 [TYPE] ACTIVATION**: [Brief description of what this prompt activates or orchestrates]
**📋 CONTEXT ADAPTATION**: [Description of how prompt adapts to project context]
**🔄 [UNIQUE_FEATURE]**: [Description of special capability or workflow coordination]

## ✅ FUNCTIONAL REQUIREMENTS

[Comprehensive description of WHAT needs to be accomplished - never HOW to implement it. Focus on outcomes, requirements, and business objectives. This section should be written using functional language that describes the desired end state.]

**Context Integration Requirements:**
- [Requirement 1: How prompt should read and adapt to .github/copilot-instructions.md]
- [Requirement 2: What project context should be analyzed and incorporated]
- [Requirement 3: How prompt should coordinate with other chatmodes or workflows]
- [Requirement 4: What quality standards and validation should be applied]
- [Requirement 5: How progress should be tracked and reported]

## 🔄 HIGH-LEVEL ALGORITHMS

### [Main Process Name]

1. **[Phase 1 Name - Analysis and Planning]**
   - [Step 1: What analysis should be performed]
   - [Step 2: What planning activities should occur]
   - [Step 3: What context should be gathered]
   - [Step 4: What decisions should be made]
   - [Step 5: What preparation should be completed]

2. **[Phase 2 Name - Implementation Strategy]**
   - [Step 1: What approach should be designed]
   - [Step 2: What coordination should be established]
   - [Step 3: What resources should be allocated]
   - [Step 4: What quality measures should be implemented]
   - [Step 5: What monitoring should be established]

3. **[Phase 3 Name - Execution and Coordination]**
   - [Step 1: What execution should be coordinated]
   - [Step 2: What validation should be performed]
   - [Step 3: What monitoring should be maintained]
   - [Step 4: What adjustments should be made]
   - [Step 5: What handoffs should be managed]

4. **[Phase 4 Name - Validation and Optimization]**
   - [Step 1: What validation should be performed]
   - [Step 2: What optimization should be applied]
   - [Step 3: What documentation should be created]
   - [Step 4: What lessons should be captured]
   - [Step 5: What improvements should be established]

## ✓ VALIDATION CRITERIA

### [Validation Category 1] (REQUIRED)

**[Subcategory 1 Name] (REQUIRED):**
- [Criterion 1: Measurable success condition that must be met]
- [Criterion 2: Quality standard that must be achieved]
- [Criterion 3: Performance requirement that must be satisfied]
- [Criterion 4: Integration requirement that must be validated]
- [Criterion 5: Documentation requirement that must be completed]

**[Subcategory 2 Name] (REQUIRED):**
- [Criterion 1: Business value that must be delivered]
- [Criterion 2: Stakeholder satisfaction that must be achieved]
- [Criterion 3: Process improvement that must be demonstrated]
- [Criterion 4: Risk mitigation that must be implemented]
- [Criterion 5: Compliance requirement that must be satisfied]

### [Validation Category 2] (REQUIRED)

**[Subcategory 3 Name] (REQUIRED):**
- [Criterion 1: Long-term success factor that must be established]
- [Criterion 2: Scalability requirement that must be validated]
- [Criterion 3: Maintainability standard that must be achieved]
- [Criterion 4: Knowledge transfer that must be completed]
- [Criterion 5: Continuous improvement that must be established]

**[Subcategory 4 Name] (REQUIRED):**
- [Criterion 1: Operational excellence that must be demonstrated]
- [Criterion 2: Business continuity that must be maintained]
- [Criterion 3: Quality assurance that must be validated]
- [Criterion 4: Performance optimization that must be achieved]
- [Criterion 5: Strategic alignment that must be confirmed]

## 💡 USAGE EXAMPLES

### [Example 1 Name - Technology Stack Context]

```yaml
[Context Type]: [Description of business context and technical environment]
[Business Value]: [Description of business impact and value proposition]
[Technology Stack]: [Specific technologies, frameworks, and infrastructure involved]
[Team Structure]: [Description of team composition and expertise areas]

[Process Name]:
- [Step 1: Description of what analysis or planning reveals]
- [Step 2: Description of coordination and strategy development]
- [Step 3: Description of implementation and execution activities]
- [Step 4: Description of validation and optimization activities]
- [Step 5: Description of outcomes and value realization]

Key Deliverables:
- [Deliverable 1: Specific outcome with business value and technical details]
- [Deliverable 2: Process improvement with quality and efficiency gains]
- [Deliverable 3: Technical implementation with integration and functionality]
- [Deliverable 4: Documentation and knowledge transfer with maintenance procedures]
- [Deliverable 5: Strategic enhancement with long-term benefits and optimization]
```

### [Example 2 Name - Different Business Domain Context]

```yaml
[Context Type]: [Description of different business domain and technical challenges]
[Business Value]: [Description of different business impact and success metrics]
[Technology Stack]: [Different technology frameworks and infrastructure requirements]
[Team Structure]: [Different team composition and specialization requirements]

[Process Name]:
- [Step 1: Domain-specific analysis and context discovery]
- [Step 2: Business-specific strategy development and planning]
- [Step 3: Technology-specific implementation and coordination]
- [Step 4: Domain-specific validation and quality assurance]
- [Step 5: Business-specific optimization and value measurement]

Key Deliverables:
- [Deliverable 1: Domain-specific solution with specialized requirements and outcomes]
- [Deliverable 2: Business-specific process with industry standards and compliance]
- [Deliverable 3: Technology-specific implementation with integration and scalability]
- [Deliverable 4: Comprehensive documentation with domain expertise and procedures]
- [Deliverable 5: Strategic business enhancement with measurable value and growth]
```

### [Example 3 Name - Enterprise Scale Context]

```yaml
[Context Type]: [Description of enterprise-scale challenges and governance requirements]
[Business Value]: [Description of enterprise business impact and organizational benefits]
[Technology Stack]: [Enterprise technology ecosystem and infrastructure complexity]
[Team Structure]: [Large team coordination and cross-functional collaboration requirements]

[Process Name]:
- [Step 1: Enterprise-scale analysis with comprehensive organizational context]
- [Step 2: Strategic planning with enterprise governance and compliance integration]
- [Step 3: Large-scale implementation with coordination across multiple teams and systems]
- [Step 4: Enterprise validation with comprehensive quality assurance and risk management]
- [Step 5: Organizational optimization with change management and continuous improvement]

Key Deliverables:
- [Deliverable 1: Enterprise solution with organizational alignment and strategic value]
- [Deliverable 2: Governance integration with compliance validation and audit trail]
- [Deliverable 3: Large-scale technical implementation with enterprise architecture and security]
- [Deliverable 4: Comprehensive enterprise documentation with governance and operational procedures]
- [Deliverable 5: Organizational enhancement with measurable enterprise value and transformation]
```

## 🔄 GitHub Copilot [Integration Type] Integration

**[Phase 1 Name]:**
- **[Activity 1]** → **[chatmode-name]**: [Description of chatmode responsibility and coordination]
- **[Activity 2]** → **[chatmode-name]**: [Description of specialized expertise and deliverables]
- **[Activity 3]** → **[chatmode-name]**: [Description of validation and quality assurance]

**[Phase 2 Name]:**
- **[Activity 4]** → **[chatmode-name]**: [Description of implementation and technical execution]
- **[Activity 5]** → **[chatmode-name]**: [Description of coordination and integration management]
- **[Activity 6]** → **[chatmode-name]**: [Description of optimization and performance enhancement]

**[Phase 3 Name]:**
- **[Activity 7]** → **[chatmode-name]**: [Description of validation and quality verification]
- **[Activity 8]** → **[chatmode-name]**: [Description of deployment and operational readiness]
- **[Activity 9]** → **[chatmode-name]**: [Description of monitoring and continuous improvement]

**GitHub Copilot IDE Integration:**
- [Integration Feature 1: Description of IDE-specific functionality and workflow enhancement]
- [Integration Feature 2: Description of automation and productivity optimization]
- [Integration Feature 3: Description of quality assurance and validation integration]
- [Integration Feature 4: Description of collaboration and knowledge sharing enhancement]

---
*[Brief summary of what this prompt provides and its value proposition for enterprise-grade development workflows.]*