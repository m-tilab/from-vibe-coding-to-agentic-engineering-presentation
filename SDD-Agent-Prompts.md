# SDD Agent Prompts

Paste these blocks one by one into an agent to define the SDD workflow behaviors.

## 1. Brainstorm skill

```text
Create a skill named brainstorm.

Purpose:
Create and refine an Epic Product Requirements Document (PRD).

Behavior:
- If the Epic PRD does not exist, create it.
- Include a Confidence Level in the PRD header.
- Ask clarification questions until confidence reaches at least 90%.
- Maintain a Decision Log.
- Convert answered questions into requirements.
- Convert requirements into acceptance criteria.
- Keep iteration history.
- Remove resolved questions after reconciliation.
- Continue asking only high-impact unresolved questions.

Question format:
Every question must provide exactly 4 options.
One option must be marked as Recommended.
Options must be selectable with x.

Example:
Question: Who can access the feature?

[ ] Administrators (Recommended)
[ ] Registered Users
[ ] Guest Users
[ ] External Systems

Exit criteria:
Confidence Level >= 90%.

Output:
Produce or update an Epic PRD with:
- Epic title
- Confidence Level
- Problem statement
- Goals
- Non-goals
- Requirements
- Acceptance Criteria
- Decision Log
- Open Questions
- Iteration History
```

## 2. Write-spec skill

```text
Create a skill named write-spec.

Input:
Epic name.

Purpose:
Create a detailed technical specification from the approved Epic PRD.

Behavior:
- Read the Epic PRD.
- Cover every requirement and acceptance criterion.
- Follow TDD principles.
- Define architecture and implementation strategy.
- Create exact implementation steps.
- Ask technical questions when design confidence is below 90%.

Required sections:
- Confidence Level
- Architecture
- Components
- Dependencies
- Boundaries
- Data flow
- Testing Strategy
- Unit tests
- Integration tests
- End-to-end tests
- Acceptance Criteria Mapping
- Implementation Plan
- Technical Questions
- Risks

For every acceptance criterion, include:
- Design approach
- Test strategy
- Implementation approach

Technical question format:
Every question must provide exactly 4 options.
One option must be marked as Recommended.
Options must be selectable with x.

Exit criteria:
Confidence Level >= 90%.
```

## 3. Implement-epic skill

```text
Create a skill named implement-epic.

Input:
Epic name.

Purpose:
Implement the Epic according to the approved specification.

Behavior:
Follow this workflow exactly:

Step 1: Implement Tests
- Create tests first according to TDD.
- Tests must map to acceptance criteria.

Step 2: Implement Functionality
- Implement code according to requirements, acceptance criteria, and technical specification.

Step 3: Validate Coverage
Verify:
- Every acceptance criterion has implementation.
- Every acceptance criterion has tests.

Step 4: Fix Failures
If tests fail:
- Fix implementation.
- Re-run relevant tests.
- Repeat until successful.

Step 5: Verify Epic
- Execute verify-epic as the final stage.

Step 6: Generate Report
Produce:
- Implemented features
- Acceptance criteria coverage
- Test results
- Risks
- Confidence level
```

## 4. Verify-epic skill

```text
Create a skill named verify-epic.

Input:
Epic name.

Purpose:
Validate implementation completeness and quality.

Behavior:
- Verify every acceptance criterion has implementation.
- Verify every acceptance criterion has tests.
- Verify every acceptance criterion passes validation.
- Execute relevant unit tests.
- Execute relevant integration tests.
- Execute relevant end-to-end tests when applicable.
- Verify implementation matches the specification.

For every acceptance criterion, report one status:

PASS = Fully implemented
PARTIAL = Partially implemented
FAIL = Missing or incorrect

Output:
Generate a verification report containing:
- Acceptance criterion status table
- Missing tests
- Missing functionality
- Risks
- Recommendations
- Final confidence level
```

## 5. Project knowledge setup

```text
Set up the SDD project knowledge system.

Create or use these files:

.github/_architecture-reference.md
Contains:
- System architecture
- Major design decisions
- Constraints
- Key dependencies
- Development patterns

.github/_coding-guidelines.md
Contains:
- Coding standards
- Naming conventions
- Testing practices
- Design patterns

.github/_ux-reference.md
Contains:
- Design principles
- Component usage
- Brand guidelines
- Accessibility requirements

Keep all files concise.
Agents and skills must consult these files during brainstorming, specification creation, implementation, verification, and architecture decisions.
```

## 6. Advisory agents

```text
Create three advisory agents for the SDD workflow.

Architecture Advisor:
Uses .github/_architecture-reference.md.
Provides guidance for:
- Architecture decisions
- Scalability
- Performance
- System boundaries

UX Advisor:
Uses .github/_ux-reference.md.
Provides guidance for:
- User experience
- Accessibility
- Design consistency

Codestyle Advisor:
Uses .github/_coding-guidelines.md.
Provides guidance for:
- Code quality
- Standards compliance
- Best practices

These agents advise during brainstorming, specification, implementation, and verification.
They should surface risks and recommendations, not silently change requirements.
```

## 7. Init-docs skill

```text
Create a skill named init-docs.

Input:
init-docs <domain>

Purpose:
Generate domain-driven documentation from the codebase.

Behavior:
Analyze:
- Code
- APIs
- Tests
- Components
- Business logic

Generate:

docs/domain-index.md
Contains:
- Navigation map
- Domain overview
- Short descriptions

docs/domain-<name>.md
Contains:
- Domain Model
- Entities
- Value Objects
- Aggregates
- API Endpoints
- Requests
- Responses
- Contracts
- Key Behaviors
- Business rules
- Workflows
- Key Components
- Services
- Repositories
- Controllers
- UI Components
- Features
- Acceptance Criteria

Agents and skills must use docs/domain-index.md as a primary project knowledge source.
```
