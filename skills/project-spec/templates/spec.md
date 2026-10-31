# <Project Name> — Specification

- **Slug**: `<kebab-case-slug>`
- **Status**: Draft
- **Date**: <YYYY-MM-DD>
- **Target codebase**: <path>

## 1. Problem

What is broken or missing today. Who feels it. Evidence, if any. The cost of
leaving it as is.

## 2. Goal

One paragraph: the problem, the intended change, and who benefits. How
success is measured, with the value or threshold.

## 3. Scope

### In scope

- <what the first delivery contains>

### Out of scope

- <what it explicitly does not contain, and why>

### Deferred

| Item | Trigger to bring it back |
| ---- | ------------------------ |
| …    | …                        |

## 4. Users and roles

| Role | Description | Capabilities | Cannot |
| ---- | ----------- | ------------ | ------ |
| …    | …           | …            | …      |

## 5. Stories and acceptance criteria

### US-1 — <short title>

**As a** <role>, **I want to** <capability>, **so that** <benefit>.

- [ ] <criterion a tester can verify without asking a question>
- [ ] <criterion>

### US-2 — <short title>

…

### Edge cases

| Case | Expected behaviour |
| ---- | ------------------ |
| No data yet | … |
| Invalid input | … |
| Upstream failure | … |
| Access denied | … |
| Operation cancelled | … |

## 6. Functional requirements

| ID | Requirement | Story | Priority |
| -- | ----------- | ----- | -------- |
| FR-1 | …           | US-1  | Must     |

Priority: `Must`, `Should`, `Could`.

## 7. Non-functional requirements

| ID | Category | Requirement | How it is verified |
| -- | -------- | ----------- | ------------------ |
| NFR-1 | Performance | … | … |
| NFR-2 | Security | … | … |
| NFR-3 | Reliability | … | … |
| NFR-4 | Accessibility | … | … |
| NFR-5 | Observability | … | … |
| NFR-6 | Cost | … | … |

Write "Non applicable" rather than leaving a row out.

## 8. Assumptions

Inferences made during the interview, not stated by the user.

| ID | Assumption | If wrong |
| -- | ---------- | -------- |
| A-1 | …          | …        |

## 9. Risks

| ID | Risk | Impact | Likelihood | Mitigation |
| -- | ---- | ------ | ---------- | ---------- |
| R-1 | …    | …      | …          | …          |

## 10. Open questions

| ID | Question | Why it matters | How to settle it | Owner | Trigger |
| -- | -------- | -------------- | ---------------- | ----- | ------- |
| Q-1 | …        | …              | …                | …     | …       |

## 11. Constraints and conventions

Constraints that shape the implementation, including repository conventions
discovered during exploration.

- <constraint, and where it comes from>

## 12. Glossary

Terms used here that are not obvious from the project itself.
