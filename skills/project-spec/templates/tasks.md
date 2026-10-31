# <Project Name> — Implementation plan

Derived from `spec.md` and `technical.md`. Ordered by dependency.

## Legend

- **Effort**: S (hours), M (a day or two), L (more than two days).
- **Acceptance**: the condition that lets the task close.
- **Spec ref**: the requirement or story the task serves.

## Phase 0 — Foundations

What must exist before any feature can be built.

### T-1 <task title>

- **Description**: <what to build>
- **Acceptance**: <verifiable condition>
- **Depends on**: —
- **Effort**: S
- **Spec ref**: NFR-1

## Phase 1 — <first increment>

Goal of the phase: <one line>. This increment should be demonstrable.

### T-2 <task title>

- **Description**: …
- **Acceptance**: …
- **Depends on**: T-1
- **Effort**: M
- **Spec ref**: US-1, FR-1

## Phase 2 — <next increment>

### T-3 <task title>

## Traceability

Every requirement is covered by at least one task, and every task serves at
least one requirement.

| Requirement | Covered by |
| ----------- | ---------- |
| FR-1 | T-2 |
| US-1 | T-2, T-3 |

## Verification

- [ ] Every `Must` acceptance criterion is covered by a test or a documented
      manual check.
- [ ] The edge cases in `spec.md` are exercised.
- [ ] The failure modes in `technical.md` are exercised.
- [ ] Repository conventions in `spec.md` are respected and validated by the
      project's own tooling.

## Later phases

| Phase | Content | Entry condition |
| ----- | ------- | --------------- |
| …     | …       | …               |
