---
name: prp-spec-create
description: Create a specification-driven PRP that documents current state, desired state, and a hierarchical task breakdown for a code transformation or refactor. Use when you need to plan a migration, refactor, or specification-first transformation.
disable-model-invocation: true
argument-hint: "[spec-name] - description of transformation"
---

# Create SPEC PRP (Advanced)

Generate a comprehensive specification-driven PRP with clear transformation goals.

## Specification: $ARGUMENTS

## Pre-Flight: Clarify Before Analysis

**CLARIFY → PLAN → ACT.** Before assessing current or desired state, check for these ambiguities. If any apply, ask for clarification immediately and wait for a response.

| Trigger | Type | Example question |
|---|---|---|
| Current state not clearly described or files not identified | `missing_info` | "Which files or systems are being transformed?" |
| Desired state has multiple valid interpretations | `ambiguous_requirement` | "Should the refactor preserve the existing API surface or is breaking change acceptable?" |
| Multiple valid transformation paths exist | `approach_choice` | "Should I migrate incrementally (strangler fig) or do a full rewrite?" |
| The transformation touches shared infrastructure or production | `risk_confirmation` | "This modifies the shared config system — confirm before proceeding?" |
| A simpler alternative would achieve the goal | `suggestion` | "A config flag would achieve this without restructuring — prefer that?" |

Only proceed to Analysis once all pre-flight ambiguities are resolved.

---

## Analysis Process

1. **Current State Assessment**
   - Map existing implementation
   - Identify pain points
   - Document technical debt
   - Note integration points

2. **Desired State Research**
   - Best practices for target state
   - Implementation examples
   - Migration strategies
   - Risk assessment
   - Dependency mapping

3. **User Clarification**
   - Confirm transformation goals
   - Priority of objectives
   - Acceptable trade-offs

## Code Quality Principles

**Code Quality Principles:** See [references/code-quality-principles.md](references/code-quality-principles.md) if it exists. Apply to all transformation tasks.

## PRP Generation

Using the SPEC PRP template from [references/prp_spec.md](references/prp_spec.md):

### State Documentation

```yaml
current_state:
  files: [list affected files]
  behavior: [how it works now]
  issues: [specific problems]

desired_state:
  files: [expected structure]
  behavior: [target functionality]
  benefits: [improvements gained]
```

### Hierarchical Objectives

1. **High-Level**: Overall transformation goal
2. **Mid-Level**: Major milestones
3. **Low-Level**: Specific tasks with validation

### Task Specification with Information Dense Keywords

#### Keywords:

- **MIRROR**: Mirror the state of existing code to be mirrored to another use case
- **COPY**: Copy the state of existing code to be copied to another use case
- **ADD**: Add new code to the codebase
- **MODIFY**: Modify existing code
- **DELETE**: Delete existing code
- **RENAME**: Rename existing code
- **MOVE**: Move existing code
- **REPLACE**: Replace existing code
- **CREATE**: Create new code

#### Example:

```yaml
task_name:
  action: MODIFY/CREATE
  file: path/to/file
  changes: |
    - Specific modifications
    - Implementation details
    - With clear markers
  validation:
    - command: "test command"
    - expect: "success criteria"
```

### Implementation Strategy

- Identify dependencies
- Order tasks by priority and implementation order and dependencies logic
- Include rollback plans
- Progressive enhancement

## User Interaction Points

1. **Objective Validation**
   - Review hierarchical breakdown
   - Confirm priorities
   - Identify missing pieces

2. **Risk Review**
   - Document identified risks
   - Find mitigations
   - Set go/no-go criteria

## Context Requirements

- Current implementation details
- Target architecture examples
- Migration best practices
- Testing strategies

## Output

Save as: `SPEC_PRP/PRPs/{spec-name}.md`

## Quality Checklist

- [ ] Current state fully documented
- [ ] Desired state clearly defined
- [ ] All objectives measurable
- [ ] Tasks ordered by dependency
- [ ] Each task has validation that AI can run
- [ ] Risks identified with mitigations
- [ ] Rollback strategy included
- [ ] Integration points noted

Remember: Focus on the transformation journey, not just the destination.
