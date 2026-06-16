# Spec-Driven Development (SDD) Framework for GitHub Copilot

## Overview

This framework transforms GitHub Copilot from a code-generation assistant into an AI-powered software engineering partner that participates throughout the entire software development lifecycle.

The workflow combines:

* Spec-Driven Development (SDD)
* Test-Driven Development (TDD)
* GitHub Copilot Skills
* GitHub Copilot Agents
* Automated Documentation
* Automated Verification

The goal is to create a traceable flow from business requirements to implementation, testing, and verification.

---

# Workflow

```text
Brainstorm
    ↓
Write Spec
    ↓
Implement Epic
    ↓
Verify Epic
```

---

# Brainstorm Skill

## Purpose

Create and refine an Epic Product Requirements Document (PRD).

## Responsibilities

1. Create an Epic PRD if it does not exist.
2. Include a confidence level in the PRD header.
3. Ask clarification questions until confidence reaches 90%.
4. Maintain a decision log.
5. Convert answers into requirements and acceptance criteria.

## Question Format

Each question must:

* Provide exactly 4 options.
* Mark one option as Recommended.
* Allow answers to be selected using `x`.

Example:

```text
Question: Who can access the feature?

[ ] Administrators (Recommended)
[ ] Registered Users
[ ] Guest Users
[ ] External Systems
```

## Reconciliation

When the skill is executed again:

* Convert answered questions into requirements.
* Convert requirements into acceptance criteria.
* Remove resolved questions.
* Keep iteration history.
* Continue asking high-impact questions.

## Exit Criteria

Confidence Level ≥ 90%

---

# Write-Spec Skill

## Input

Epic Name

## Purpose

Create a detailed technical specification covering all Epic requirements.

## Responsibilities

* Read Epic PRD.
* Cover all requirements and acceptance criteria.
* Follow TDD principles.
* Define architecture and implementation strategy.
* Create step-by-step implementation plans.

## Required Sections

### Architecture

* Components
* Dependencies
* Boundaries
* Data flow

### Testing Strategy

* Unit tests
* Integration tests
* End-to-end tests

### Acceptance Criteria Mapping

Each acceptance criterion must include:

* Design approach
* Test strategy
* Implementation approach

### Implementation Plan

Provide exact implementation steps developers can follow.

## Technical Questions

At the end of the specification:

* Ask architecture and design questions.
* Provide 4 options per question.
* Mark one option as Recommended.
* Reconcile answers during future executions.

## Exit Criteria

Confidence Level ≥ 90%

---

# Implement-Epic Skill

## Input

Epic Name

## Purpose

Implement the Epic according to the approved specification.

## Workflow

### Step 1: Implement Tests

Create tests first according to TDD.

### Step 2: Implement Functionality

Implement code according to:

* Requirements
* Acceptance Criteria
* Technical Specification

### Step 3: Validate Coverage

Verify:

* Every AC has implementation.
* Every AC has tests.

### Step 4: Fix Failures

If tests fail:

1. Fix implementation.
2. Re-run relevant tests.
3. Repeat until successful.

### Step 5: Verify Epic

Execute Verify-Epic.

### Step 6: Generate Report

Produce:

* Implemented features
* AC coverage
* Test results
* Risks
* Confidence level

---

# Verify-Epic Skill

## Input

Epic Name

## Purpose

Validate implementation completeness and quality.

## Responsibilities

### Acceptance Criteria Validation

Verify:

* Every AC has implementation.
* Every AC has tests.
* Every AC passes validation.

### Test Execution

Execute:

* Relevant unit tests
* Relevant integration tests
* Relevant E2E tests

### Specification Validation

Verify implementation matches specification.

## Reporting

For every acceptance criterion report:

| Status  | Meaning               |
| ------- | --------------------- |
| PASS    | Fully implemented     |
| PARTIAL | Partially implemented |
| FAIL    | Missing or incorrect  |

Include:

* Missing tests
* Missing functionality
* Risks
* Recommendations

---

# Verification Integration

Verify-Epic must be executed as the final stage of Implement-Epic.

## During Implementation

Run:

* Only relevant tests

Avoid:

* Full test suite execution

## During Verification

Run:

* Complete Epic validation
* Full relevant test execution
* E2E validation

---

# Playwright Integration

## Purpose

Enable automated browser testing and validation.

## Responsibilities

Install and configure:

* Playwright
* Playwright MCP

Enable:

* End-to-end testing
* User journey validation
* Browser automation
* Verification workflows

Verify-Epic should use Playwright for UI validation.

---

# Project Knowledge System

## Architecture Reference

File:

```text
.github/_architecture-reference.md
```

Contains:

* System architecture
* Major design decisions
* Constraints
* Key dependencies
* Development patterns

Keep concise.

---

## Coding Guidelines

File:

```text
.github/_coding-guidelines.md
```

Contains:

* Coding standards
* Naming conventions
* Testing practices
* Design patterns

Keep concise.

---

## UX Reference

File:

```text
.github/_ux-reference.md
```

Contains:

* Design principles
* Component usage
* Brand guidelines
* Accessibility requirements

Keep concise.

---

# Advisory Agents

## Architecture Advisor

Reference:

```text
.github/_architecture-reference.md
```

Provides guidance for:

* Architecture decisions
* Scalability
* Performance
* System boundaries

---

## UX Advisor

Reference:

```text
.github/_ux-reference.md
```

Provides guidance for:

* User experience
* Accessibility
* Design consistency

---

## Codestyle Advisor

Reference:

```text
.github/_coding-guidelines.md
```

Provides guidance for:

* Code quality
* Standards compliance
* Best practices

---

# Documentation System

## Init-Docs Skill

### Input

```text
init-docs <domain>
```

### Purpose

Generate Domain-Driven documentation from the codebase.

### Responsibilities

Analyze:

* Code
* APIs
* Tests
* Components
* Business logic

Generate documentation.

---

# Documentation Structure

```text
docs/
├── domain-index.md
├── domain-<name>.md
```

---

## domain-index.md

Contains:

* Navigation map
* Domain overview
* Short descriptions

---

## domain-<name>.md

Contains:

### Domain Model

* Entities
* Value Objects
* Aggregates

### API Endpoints

* Requests
* Responses
* Contracts

### Key Behaviors

* Business rules
* Workflows

### Key Components

* Services
* Repositories
* Controllers
* UI Components

### Features

For each feature:

* Description
* Acceptance Criteria

---

# Documentation Integration

Agents and skills should use:

```text
docs/domain-index.md
```

as the primary project knowledge source.

Documentation should be consulted during:

* Brainstorming
* Specification creation
* Implementation
* Verification
* Architecture decisions

---

# Expected Benefits

* Better requirement quality
* Reduced ambiguity
* Improved architecture consistency
* Stronger test coverage
* Faster onboarding
* Better AI-generated code quality
* Traceability from requirement to implementation
* Higher delivery confidence
* Living documentation

The objective is not merely to generate code faster, but to establish a disciplined AI-assisted engineering workflow where requirements, architecture, implementation, testing, and documentation remain continuously aligned.
