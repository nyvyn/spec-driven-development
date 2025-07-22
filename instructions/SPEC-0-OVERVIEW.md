# Specification-Driven Development Overview

This document provides guidance for developers on using the specification workflow to systematically develop features using GitHub Copilot's AI capabilities.

## AI Model Selection Strategy

**For Specification File Creation**: Use **GitHub Edit mode** with the most capable AI model available. At the time of this writing, that is **Claude Sonnet 4**, which excels at structured document creation, requirements analysis, and design thinking.

**For Code and Test Generation**: Use **GitHub Agent mode** with a capable code editing model. At the time of this writing, that is **GPT-4.1**, which provides excellent code generation, debugging, and test automation capabilities.

> **Note**: AI model capabilities evolve rapidly. Always use the most capable model available for each phase of development.

## The Specs Directory Structure

The `specs` directory contains feature specification documents organized by numbered feature sets:

```
specs/
├── 001-FeatureName-Requirements.md
├── 001-FeatureName-Design.md
├── 001-FeatureName-Tasks.md
├── 001-FeatureName-Tests.md
├── 001-FeatureName-Documentation.md
├── 002-AnotherFeature-Requirements.md
├── 002-AnotherFeature-Design.md
└── ...
```

## Naming Convention

**Format**: `{###}-{feature_name}-{document_type}.md`

- **###**: Zero-padded 3-digit feature number (001, 002, 003...)
- **feature_name**: PascalCase feature name (e.g., `Evaluator`, `UserAuthentication`)
- **document_type**: One of: `Requirements`, `Design`, `Tasks`, `Tests`, `Documentation`

**Rules**:
- All files for a feature share the same leading number
- New features increment the number; never reuse existing numbers
- Use descriptive, unambiguous feature names

## Workflow: Collaborating with GitHub Copilot

### Phase 1: Specification Development (Use GitHub Edit Mode + Claude Sonnet 4)

Work through each specification file in order, using **GitHub Edit mode with Claude Sonnet 4**:

#### 1. Requirements (SPEC-1-REQUIREMENTS.md)
1. **Open** the requirements template: `/instructions/SPEC-1-REQUIREMENTS.md`
2. **Use GitHub Edit mode (Claude Sonnet 4)** to generate `{project}/specs/{###}-{FeatureName}-Requirements.md`
3. **Prompt**: "Create requirements for [feature description] following the template"
4. **Review** generated requirements for:
   - EARS syntax compliance
   - Complete user stories
   - Edge cases and constraints
5. **Iterate** with Claude to refine until requirements are complete

#### 2. Design (SPEC-2-DESIGN.md)
1. **Open** the design template: `/instructions/SPEC-2-DESIGN.md`
2. **Use GitHub Edit mode (Claude Sonnet 4)** with the approved requirements file in context
3. **Prompt**: "Create design document for [feature] based on requirements {###}-{FeatureName}-Requirements.md"
4. **Review** generated design for:
   - Architecture diagrams (Mermaid)
   - Component responsibilities
   - Data models
   - Error handling strategy
5. **Iterate** to ensure design addresses all requirements

#### 3. Tasks (SPEC-3-IMPLEMENTATION.md)
1. **Open** the tasks template: `/instructions/SPEC-3-IMPLEMENTATION.md`
2. **Use GitHub Edit mode (Claude Sonnet 4)** with both requirements and design files in context
3. **Prompt**: "Create implementation tasks for [feature] based on requirements and design"
4. **Review** task breakdown for:
   - Granular, actionable tasks
   - Proper sequencing
   - Requirement traceability
   - File/module specificity
5. **Iterate** until tasks are implementable

#### 4. Tests (SPEC-4-TESTING.md)
1. **Open** the testing template: `/instructions/SPEC-4-TESTING.md`
2. **Use GitHub Edit mode (Claude Sonnet 4)** with requirements, design, and tasks in context
3. **Prompt**: "Create BDD test scenarios for [feature] covering all requirements"
4. **Review** test scenarios for:
   - Gherkin syntax compliance
   - Complete requirement coverage
   - Happy path and edge cases
   - Proper tagging
5. **Iterate** to ensure comprehensive test coverage

#### 5. Documentation (SPEC-5-DOCUMENTATION.md)
1. **Open** the documentation template: `/instructions/SPEC-5-DOCUMENTATION.md`
2. **Use GitHub Edit mode (Claude Sonnet 4)** with all previous specification files in context
3. **Prompt**: "Create user documentation for [feature] based on requirements and design"
4. **Review** documentation for:
   - User-focused language
   - Complete workflow coverage
   - Troubleshooting scenarios
   - Reference materials
5. **Iterate** until documentation is user-ready

### Phase 2: Code Generation (Use GitHub Agent Mode + GPT-4.1)

Once all specification files are complete and reviewed, switch to **GitHub Agent mode with GPT-4.1**:

#### 6. Generate Implementation Code
1. **Use GitHub Agent mode (GPT-4.1)** with the Tasks document as primary context
2. **Include** Requirements and Design documents for reference
3. **Prompt**: "Generate code implementation following the tasks in {###}-{FeatureName}-Tasks.md"
4. **Work through tasks sequentially**, generating:
   - Core implementation files
   - Configuration files
   - Helper utilities
5. **Review and test** each component as generated

#### 7. Generate Test Code
1. **Use GitHub Agent mode (GPT-4.1)** with the Tests document as primary context
2. **Include** the generated implementation code for reference
3. **Prompt**: "Generate test automation code for scenarios in {###}-{FeatureName}-Tests.md"
4. **Generate**:
   - Unit tests
   - Integration tests
   - BDD step definitions (if using Cucumber/similar)
5. **Verify** tests pass and provide adequate coverage

## Best Practices

### AI Model Selection
- **Claude Sonnet 4 (Edit mode)**: Best for requirements analysis, system design, task breakdown, test planning, and documentation
- **GPT-4.1 (Agent mode)**: Best for code generation, debugging, refactoring, and test automation
- **Context Management**: Always include relevant specification files when switching between phases
- **Model Updates**: Monitor for newer, more capable models and update your workflow accordingly

### Collaboration Tips
- **Always include relevant specification files** in the AI's context when generating code
- **Reference requirement IDs** in code comments for traceability
- **Use incremental development**: implement and test core functionality before adding features
- **Review each generated artifact** before moving to the next phase

### Iteration Strategy
- **Expect multiple rounds** of refinement for each specification
- **Use Copilot's chat** to explore alternative approaches during review
- **Keep specifications updated** as implementation reveals new requirements
- **Maintain traceability** between specifications and code

## Benefits of This Approach

1. **Systematic Development**: Each phase builds on the previous, ensuring completeness
2. **Optimized AI Usage**: Different models excel at different tasks - use the right tool for each job
3. **AI-Assisted Quality**: AI helps maintain consistency and catch gaps
4. **Traceability**: Clear links from requirements through to implementation
5. **Reviewability**: Structured documents facilitate team review and approval
6. **Maintainability**: Changes can be traced back through the specification chain

Follow this workflow to leverage the best AI capabilities while maintaining rigorous software engineering practices.
