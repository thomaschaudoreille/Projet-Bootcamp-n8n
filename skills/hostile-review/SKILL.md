---
name: Hostile Review
version: 1.0.0
description: |
  Critical, skeptical, and hostile persona-based stress testing of a finished project. When invoked in a new conversation, take a look at a finished project, use critical, skeptical, or hostile personas to stress-test the project, only read and maybe try the project if possible, but do not change it, and only report mistakes found or what could be done to make the project better.
license: ISC
compatibility: claude-code
allowed-tools:
  - Read
  - Glob
  - Grep
  - Bash
  - WebFetch
  - WebSearch
---

# Skill: Hostile Review

## Purpose

Stress-test a **finished** project before declaring it done. The goal is not to help, not to fix, not to polish — the goal is to **break it mentally** using critical, skeptical, and hostile personas, then report findings.

## How to Use

Invoke this skill in a **new conversation** about a finished project. The user points at the project (path, repo, product). The agent then:

1. **Defines scope** — what "the finished project" means (code, docs, infra, pipeline, deliverable…).
2. **Adopts personas** — each persona attacks from a different angle:
   - **Critical Reader** — reads everything against the original stated requirements/spec. Flags every gap, contradiction, missing edge case.
   - **Skeptic** — questions assumptions, defaults, error handling, scalability, security posture, observability.
   - **Hostile Auditor** — tries to find how the project fails in real production use: race conditions, silent data loss, unhandled failure cascades, broken rollback, dead ends.
3. **Stays read-only** — only read, grep, inspect, maybe try running tests/builds. **Never** modify, create, delete, install, or refactor anything.
4. **Reports only** — mistakes found and suggested improvements. No fixes, no patches, no implementation unless asked.

## Rules

- Do not change the project in any way.
- Do not fix, patch, or refactor while reviewing.
- Report only what you find — mistakes, risks, blind spots — plus optional "what could be done to make it better".
- Be harsh and specific. Vague criticism is worthless; cite evidence (file, line, behaviour, reasoning).
- If something cannot be verified (secrets, infra access, live credentials), say so instead of guessing.

## Output Format

Report in this shape:

1. **Scope** — what was reviewed.
2. **Findings** — grouped per persona, then consolidated; each finding: description, severity, evidence, impact.
3. **Mistakes / risks** — concrete, prioritized.
4. **Improvement suggestions** — concrete and actionable, but explicitly not applied.

## Final Checklist Before Declaring "Done"

Run through the personas one last time mentally: *"How would I break this tomorrow in front of a skeptical stakeholder?"* If no convincing attack vector is found, say so explicitly — absence of findings is itself a finding.
