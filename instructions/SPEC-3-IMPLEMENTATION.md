# AI Guidelines for Drafting the Tasks (Implementation Plan) Document

(Only code-focused implementation steps—exclude testing, deployment, or non-coding work.)

## 1. File Creation
* Path: `{project}/specs/{###}-{feature_name}-Implementation.md`
* File name format: The set of files (Requirements, Design, etc.) are grouped by the 
  leading number, e.g. `001-FeatureName-Requirements.md`, `001-FeatureName-Design.md`, etc.
* New features should increment the leading number, not reuse existing numbers, 
  e.g., if `001-FeatureName-Implementation.md` exists, the implementation file for the next feature should be `002-AnotherFeature-Implementation.md`.

## 2. Prerequisite Check
* Confirm an approved design document exists; reference its section and requirement IDs.
* Halt if design is missing or incomplete.

## 3. Task List Layout

```markdown
## Implementation Tasks

- [ ] 1. <Epic or major module>  
  - [ ] 1.1 <Concrete coding task referencing Rqmt ID>
    - Write/modify <file(s)>
    - Add/extend tests for <functionality>
  - [ ] 1.2 <Next task>
- [ ] 2. <Epic or module>  
  - [ ] 2.1 <Task>
```

* Two hierarchy levels maximum (1, 1.1).
* Each line is a checkbox (- [ ]).

## 4. Content Rules
* Every task must:
  * Involve writing, modifying, or testing code.
  * Reference granular requirement IDs (e.g., 2.3.1).
  * Include sub-bullets for context (files, modules, test focus).
* Sequence tasks to enable incremental, test-driven progress; no large jumps.
* Ensure no orphaned code—later tasks wire earlier work together.
* Omit design details already covered elsewhere.

## 5. Task Granularity
* Scope tasks so a coding agent can complete them without clarification.
* Avoid umbrella statements like "Implement feature X."
* Prefer "Implement validateInput() in utils/validation.ts" and its unit tests.

## 6. Excluded Items
* NO user-acceptance testing, deployment, performance monitoring, documentation, or business processes.
* NO tasks that cannot be achieved solely by writing, modifying, or testing code.

## 7. Quality Checklist
* Full coverage: all requirements and design components mapped to tasks.
* Traceability: each task links to at least one requirement ID.
* Incrementality: ordering supports early verification of core logic via tests.
* Clarity: each checkbox is actionable, discrete, and code-centric.

Apply these rules exactly to generate a concise, complete, and actionable task list.