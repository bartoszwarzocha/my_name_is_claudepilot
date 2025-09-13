# Update Project my_name_is_claudepilot from my_name_is_claude

## Overview

This document provides a comprehensive, step-by-step procedure for updating the **my_name_is_claudepilot** project based on changes in the source **my_name_is_claude** project. The update process ensures proper migration of new features, improvements, and modifications while maintaining the GitHub Copilot-specific adaptations and enterprise-grade enhancements.

## Prerequisites

### System Requirements
- Access to both project directories
- Git repository access and permissions
- GitHub Copilot framework understanding
- Knowledge of migration strategies and principles

### Directory Structure Requirements
- `my_name_is_claudepilot` project directory must exist
- `my_name_is_claude` project directory must exist
- `my_name_is_claudepilot` must be located in the parent directory of `my_name_is_claude`

## Update Execution Conditions

### Mandatory Conditions
1. **Directory Existence**: Both project directories must be accessible
2. **Directory Hierarchy**: Correct parent-child relationship between project directories
3. **Commit Freshness**: Source project must have newer commits than target project
4. **Change Detection**: Source project must contain changes not present in target project

### Validation Criteria
- Commit date comparison to ensure update necessity
- Content comparison across critical directories
- Migration strategy compatibility assessment
- Change impact analysis and risk evaluation

---

## Step-by-Step Update Procedure

### Phase 1: Environment Validation

#### Step 1: Verify Target Project Directory
```bash
# Check if my_name_is_claudepilot directory exists
if [ ! -d "my_name_is_claudepilot" ]; then
    echo "Error: Directory my_name_is_claudepilot does not exist."
    exit 1
fi
```

**Expected Outcome**: Confirmation that target project directory exists and is accessible.

#### Step 2: Verify Source Project Directory
```bash
# Check if my_name_is_claude directory exists
if [ ! -d "my_name_is_claude" ]; then
    echo "Error: Directory my_name_is_claude does not exist."
    exit 1
fi
```

**Expected Outcome**: Confirmation that source project directory exists and is accessible.

#### Step 3: Validate Directory Hierarchy
```bash
# Verify correct directory structure
CURRENT_DIR=$(pwd)
if [ ! -d "$CURRENT_DIR/my_name_is_claude" ] || [ ! -d "$CURRENT_DIR/my_name_is_claudepilot" ]; then
    echo "Error: Directory my_name_is_claudepilot must be located in the parent directory of my_name_is_claude."
    exit 1
fi
```

**Expected Outcome**: Confirmation of proper directory hierarchy for safe update execution.

### Phase 2: Change Detection and Analysis

#### Step 4: Extract Source Project Commit Information
```bash
# Get latest commit date from my_name_is_claude
cd my_name_is_claude
SOURCE_COMMIT_DATE=$(git log -1 --format="%ai")
SOURCE_COMMIT_HASH=$(git log -1 --format="%H")
cd ..
```

**Expected Outcome**: Retrieval of latest commit metadata from source project.

#### Step 5: Extract Target Project Commit Information
```bash
# Get latest commit date from my_name_is_claudepilot
cd my_name_is_claudepilot
TARGET_COMMIT_DATE=$(git log -1 --format="%ai")
TARGET_COMMIT_HASH=$(git log -1 --format="%H")
cd ..
```

**Expected Outcome**: Retrieval of latest commit metadata from target project.

#### Step 6: Perform Commit Date Comparison
```bash
# Compare commit dates
if [[ "$SOURCE_COMMIT_DATE" < "$TARGET_COMMIT_DATE" ]] || [[ "$SOURCE_COMMIT_DATE" == "$TARGET_COMMIT_DATE" ]]; then
    echo "No newer changes found in my_name_is_claude."
    exit 0
fi
```

**Expected Outcome**: Validation that source project contains newer changes requiring update.

### Phase 3: Content Analysis and Comparison

#### Step 7: Compare Agents/Chatmodes Directory Content
```bash
# Compare agents (source) vs chatmodes (target) directories
echo "Analyzing agents -> chatmodes migration requirements..."

# Check for new agents in source
SOURCE_AGENTS=$(find my_name_is_claude/.claude/agents -name "*.md" -type f)
TARGET_CHATMODES=$(find my_name_is_claudepilot/.github/chatmodes -name "*.md" -type f)

# Document differences for migration strategy application
```

**Expected Outcome**: Identification of new or modified agent files requiring chatmode migration.

#### Step 8: Compare Prompts Directory Content
```bash
# Compare prompts directories between projects
echo "Analyzing prompts migration requirements..."

# Check for new prompts in source
SOURCE_PROMPTS=$(find my_name_is_claude/.claude/prompts -name "*.md" -type f)
TARGET_PROMPTS=$(find my_name_is_claudepilot/.github/prompts -name "*.prompt.md" -type f)

# Document prompt changes for migration strategy application
```

**Expected Outcome**: Identification of new or modified prompt files requiring adaptation.

#### Step 9: Compare Examples Directory Content
```bash
# Compare examples directories between projects
echo "Analyzing examples migration requirements..."

# Check for new examples in source
SOURCE_EXAMPLES=$(find my_name_is_claude/examples -name "*.md" -type f)
TARGET_EXAMPLES=$(find my_name_is_claudepilot/examples -name "*.md" -type f)

# Document example changes for migration strategy application
```

**Expected Outcome**: Identification of new or modified example files requiring Copilot-native adaptation.

### Phase 4: Migration Planning and Documentation

#### Step 10: Generate Update Checklist
```bash
# Create comprehensive checklist in work directory
cat > my_name_is_claudepilot/work/update_checklist_$(date +%Y%m%d_%H%M%S).md << EOF
# Update Checklist - $(date +"%Y-%m-%d %H:%M:%S")

## Source Information
- **Source Commit**: $SOURCE_COMMIT_HASH
- **Source Date**: $SOURCE_COMMIT_DATE
- **Target Commit**: $TARGET_COMMIT_HASH
- **Target Date**: $TARGET_COMMIT_DATE

## Identified Changes

### New/Modified Agents
[List of agent files requiring chatmode migration]

### New/Modified Prompts
[List of prompt files requiring adaptation]

### New/Modified Examples
[List of example files requiring rewrite]

### Other Changes
[Additional files and modifications detected]

## Migration Tasks
- [ ] Apply agent-to-chatmode migration for new agents
- [ ] Adapt new prompts using prompt migration strategies
- [ ] Rewrite examples using Copilot-native approach
- [ ] Update documentation and references
- [ ] Validate enterprise compliance and quality standards
EOF
```

**Expected Outcome**: Comprehensive checklist documenting all required migration tasks.

### Phase 5: Migration Strategy Application

#### Step 11: Execute Comprehensive Project Update

Apply migration strategies based on established guidelines:

##### A. Agent to Chatmode Migration
```bash
# Apply agent-to-chatmode migration strategy
echo "Applying agent-to-chatmode migration..."

# Reference: work/agent-to-chatmodel-migration-guide.md
# For each new agent:
# 1. Convert agent prompt to chatmode format
# 2. Add YAML frontmatter with chatmode metadata
# 3. Adapt content for manual chatmode switching
# 4. Update technology adaptivity sections
# 5. Add GitHub Copilot integration points
```

##### B. Prompt Migration and Adaptation
```bash
# Apply prompt migration strategy
echo "Applying prompt migration strategy..."

# Reference: work/prompt-migration-guide.md
# For each new prompt:
# 1. Assess migration approach (adapt vs rewrite)
# 2. Apply technology-adaptive patterns
# 3. Add enterprise-grade quality requirements
# 4. Integrate GitHub Actions workflows
# 5. Add comprehensive testing specifications
```

##### C. Workflow Prompt Enhancement
```bash
# Apply workflow migration strategy
echo "Applying workflow migration strategy..."

# Reference: work/workflow-migration-strategy.md
# For workflow prompts:
# 1. Complete rewrite for GitHub Copilot (Przepisz Od Nowa)
# 2. Chatmode-centric orchestration design
# 3. Enterprise governance integration
# 4. Cross-chatmode context handoff implementation
```

##### D. Example Rewrite and Enhancement
```bash
# Apply examples migration strategy
echo "Applying examples migration strategy..."

# Reference: work/examples-migration-strategy.md
# For each example:
# 1. Complete rewrite for GitHub Copilot ecosystem
# 2. Enterprise-grade workflow demonstration
# 3. Technology-adaptive implementation patterns
# 4. Comprehensive quality and security standards
```

##### E. Documentation Update and Enhancement
```bash
# Apply documentation migration strategy
echo "Applying documentation migration strategy..."

# Reference: work/documentation-migration-strategy.md
# For documentation:
# 1. Update all references to reflect GitHub Copilot approach
# 2. Enhance enterprise features and capabilities
# 3. Add comprehensive usage examples and patterns
# 4. Update attribution and derivative work information
```

##### F. Quality Assurance and Validation
```bash
# Apply comprehensive quality assurance
echo "Applying quality assurance and validation..."

# Reference: .github/prompts/TESTING.md
# Quality validation:
# 1. Validate all prompts against testing framework
# 2. Ensure enterprise compliance requirements
# 3. Verify technology adaptivity across all stacks
# 4. Validate security and performance standards
```

**Expected Outcome**: Complete application of all migration strategies with enterprise-grade quality standards.

### Phase 6: Update Completion and Documentation

#### Step 12: Generate Update Summary
```bash
# Create comprehensive update summary
cat > my_name_is_claudepilot/work/update_summary_$(date +%Y%m%d_%H%M%S).md << EOF
# Update Summary - $(date +"%Y-%m-%d %H:%M:%S")

## Update Metadata
- **Execution Date**: $(date +"%Y-%m-%d %H:%M:%S")
- **Source Project**: my_name_is_claude
- **Target Project**: my_name_is_claudepilot
- **Source Commit**: $SOURCE_COMMIT_HASH
- **Source Date**: $SOURCE_COMMIT_DATE

## Changes Applied

### Chatmodes Updated
[List of chatmodes that were created or modified]

### Prompts Updated
[List of prompts that were created or modified]

### Examples Updated
[List of examples that were created or modified]

### Documentation Updated
[List of documentation files that were updated]

## Migration Strategies Applied
- [x] Agent-to-Chatmode Migration Strategy
- [x] Prompt Migration and Adaptation Strategy
- [x] Workflow Migration Strategy (Przepisz Od Nowa)
- [x] Examples Migration Strategy (Copilot-Native Rewrite)
- [x] Documentation Migration Strategy
- [x] Enterprise Quality Assurance Validation

## Quality Validation Results
- [x] All prompts validated against testing framework
- [x] Enterprise compliance requirements verified
- [x] Technology adaptivity confirmed across all stacks
- [x] Security and performance standards validated
- [x] GitHub Copilot integration verified

## Post-Update Statistics
- **Total Files**: [count]
- **Chatmodes**: [count]
- **Prompts**: [count]
- **Examples**: [count]
- **Documentation Files**: [count]

## Recommendations for Next Update
[Suggestions for future update improvements]

EOF
```

**Expected Outcome**: Comprehensive documentation of all changes applied during update process.

#### Step 13: Final Validation and Completion
```bash
# Perform final validation
echo "Performing final validation..."

# Validate project structure
# Verify all migration strategies were applied
# Confirm enterprise quality standards
# Validate GitHub Copilot integration

echo "Update completed successfully."
```

**Expected Outcome**: Confirmation of successful update completion with all quality standards met.

---

## Migration Strategy References

### Core Strategy Documents
The update process relies on the following established migration strategies:

1. **agent-to-chatmodel-migration-guide.md** - Guidelines for converting Claude Code agents to GitHub Copilot chatmodes
2. **copilot-migration-principles.md** - Core principles for GitHub Copilot ecosystem adaptation
3. **documentation-migration-strategy.md** - Documentation update and enhancement strategies
4. **examples-migration-strategy.md** - Example rewrite and Copilot-native adaptation
5. **prompt-migration-guide.md** - Prompt adaptation and enhancement guidelines
6. **workflow-migration-strategy.md** - Workflow prompt complete rewrite strategy

### Quality Assurance Framework
- **Testing Framework** (.github/prompts/TESTING.md) - Enterprise-grade validation requirements
- **Quality Standards** - >95% test coverage, security compliance, performance benchmarks
- **Enterprise Compliance** - SOC2, GDPR, HIPAA, PCI-DSS validation requirements

## Error Handling and Recovery

### Common Error Scenarios
1. **Directory Access Issues** - Verify permissions and path correctness
2. **Git Repository Problems** - Ensure repositories are properly initialized and accessible
3. **Migration Strategy Conflicts** - Apply conflict resolution based on GitHub Copilot priorities
4. **Quality Validation Failures** - Address validation issues before proceeding

### Recovery Procedures
- **Rollback Capability** - Maintain backup of target project before update
- **Incremental Application** - Apply changes in phases for better error isolation
- **Validation Checkpoints** - Verify each phase before proceeding to next
- **Documentation Trail** - Maintain complete audit trail for troubleshooting

## Success Criteria

### Technical Success Indicators
- ✅ All new source changes successfully migrated
- ✅ GitHub Copilot chatmode compatibility maintained
- ✅ Enterprise quality standards validated
- ✅ Technology adaptivity preserved across all stacks
- ✅ Security and compliance requirements met

### Quality Assurance Validation
- ✅ Comprehensive testing framework validation passed
- ✅ Performance benchmarks maintained or improved
- ✅ Documentation accuracy and completeness verified
- ✅ Attribution and derivative work information updated

### Business Continuity Assurance
- ✅ Zero functional regression from previous version
- ✅ Enhanced enterprise capabilities and features
- ✅ Improved GitHub Copilot integration and optimization
- ✅ Maintained backward compatibility where applicable

---

**Update Process Completion**: Upon successful execution of all steps, the my_name_is_claudepilot project will be fully updated with all new changes from my_name_is_claude, properly adapted for GitHub Copilot ecosystem with enterprise-grade enhancements.