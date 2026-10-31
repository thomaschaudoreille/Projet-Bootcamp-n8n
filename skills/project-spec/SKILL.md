---
name: project-spec
description: Interview the user until there is zero doubt about the project they pitched, then deliver the complete set of project specifications as files. Use whenever the user describes a project they want to build, or asks for a spec, a specification, a PRD, requirements, a design, a technical plan, or an implementation plan — before any code, workflow, or scaffold is written.
---

# Project Spec

A pitched project is a hypothesis. Your job is to turn it into a specification
the user can trust, by asking until you have zero doubt, and only then
writing anything down.

## The contract

Three rules, in priority order:

1. **Nothing gets created before the interview closes.** No code, no workflow,
   no project scaffold, no configuration, no spec file. Not even a draft. The
   deliverable of this skill is a set of specifications; producing a partial
   artifact is a failure, not a hedge.
2. **Ask as many questions as it takes to reach zero doubt.** There is no
   target number of questions. There is no fixed questionnaire. Keep asking
   until every doubt is closed, parked, or explicitly out of scope — then stop.
3. **Deliver every spec the project needs.** The interview decides which
   documents are required. Say why each one is there.

"Zero doubt" is operationalized in `references/readiness.md`. Work through it;
do not treat it as a vibe.

## Phase 1 — Open the interview

Your first turn should contain the first question. Do not delay it for
research, and do not open with a wall of context.

- Establish the project name, a `kebab-case` slug, and the target directory
  that will hold `docs/specs/<slug>/`.
- If the target directory looks volatile (a temp folder, a scratch directory,
  a cloud-synced placeholder), say so in one line and recommend a persistent
  location before continuing.
- Ask the first substantive question immediately.

One question per turn, always. Never a numbered list of questions.

## Phase 2 — Interview to zero doubt

Maintain a **doubt ledger** in your reasoning, not in a file: every thing you
are not sure of, whether it is a missing answer, an ambiguous requirement, or
an unverified assumption. The interview ends when the ledger holds no blocking
doubt.

### Question discipline

- **One question per turn.** Wait for the answer.
- **Propose a default.** Every question carries a concrete suggested answer the
  user can accept by saying "yes" or correct in a few words.
- **Keep it short.** Answerable in one to three sentences.
- **Only consequential questions.** If the answer cannot change a decision in
  the spec, do not ask it.
- **Never ask what you can find out yourself.** Read the code, the config, the
  docs, or probe the environment. The user's time is the scarce resource.
- **Never guess and never assume silently.** If you must proceed on an
  assumption, label it `Assumption` in the spec and keep it in the ledger.
- **Do not block.** "I don't know" is an answer: record it as an open question
  with a way to settle it, then move on.
- **Adapt.** Drop questions the earlier answers made irrelevant. Ask the ones
  they made urgent.

### Exploring without stalling

Exploring the existing codebase is right, and it never requires the user.
The failure mode to avoid is dumping the findings before the first question.

- Start exploration in parallel with the interview, not before it.
- Report only what changes a question you are about to ask.
- Never render a summary of the exploration before the user has been asked
  anything.
- Repository conventions — naming rules, required languages, required
  descriptions, lint or standards config — are read, not asked about. They go
  into the spec as constraints.

Use `references/interview.md` as the question bank: dimensions, what each one
decides, and when to probe deeper. It is a menu, not a script.

## Phase 3 — Close the interview

When the ledger is clear of blocking doubts:

1. Present the readiness check from `references/readiness.md`, with the current
   state of each gate. Any gate you cannot tick honestly stays open and
   produces one last question.
2. Present the proposed spec set: which documents, and why each one is needed
   for this project.
3. Ask for confirmation.

Do not write a single file before that confirmation.

## Phase 4 — Write the specs

Create `docs/specs/<slug>/` in the target directory.

Always:

| File             | Content                                                        |
| ---------------- | -------------------------------------------------------------- |
| `spec.md`        | Master specification: problem, goal, scope, users, stories with acceptance criteria, functional and non-functional requirements, risks, open questions, conventions. |
| `tasks.md`       | Ordered implementation plan: phases, tasks, acceptance, dependencies, effort, traceability. |
| `decisions.md`   | Decision log: context, decision, alternatives, consequences.    |

When the interview established that the project needs them:

| File             | When it applies                                                |
| ---------------- | --------------------------------------------------------------- |
| `technical.md`   | The project has architecture: components, data model, interfaces, integrations, failure modes, deployment, configuration. |
| `acceptance.md`  | Requirements are numerous enough to need a traceability matrix from story to requirement to task to verification. |
| `api.md`         | The project exposes or consumes an interface with a contract.     |
| `data-model.md`  | The project owns meaningful data with a lifecycle.                |
| `test-plan.md`   | Verification needs more than the acceptance criteria in `spec.md`.|
| `threat-model.md`| The project handles personal, financial, or regulated data.      |
| `runbook.md`     | The project must be operated: deploy, monitor, back up, restore.  |

Read the matching template before writing each file. Use the section order
from the template. Write "Non applicable" rather than dropping a section, so
the reader can tell it was considered.

### Writing rules

- Write in the language the user used. Keep identifiers, code, field names and
  API names in their original form.
- Number everything for traceability: `US-1`, `FR-1`, `NFR-1`, `T-1`, `D-1`.
- Every task points to the requirement or story it serves. Every requirement
  points to a story.
- Mark inferences as `Assumption`, with what would change if the assumption is
  wrong.
- Open questions carry: the question, why it matters, how to settle it, who
  owns it, and what triggers the decision.
- Respect repository conventions discovered during exploration, and state them
  in the spec so the implementation follows them.

## Phase 5 — Hand back

Report the files created, the spec set and why each document is in it, the
open questions that remain, and the first thing to build. Offer the natural
next steps without starting them.

## Interrupts

If the user says stop, enough, or similar: stop at once. Do not argue, do not
push one more question. Report where the interview stands: what is settled,
what is still open, and that nothing was written.

## Never

- Never write code, a workflow, a scaffold, or a config file. This skill ends
  at specifications.
- Never write a spec file before the user confirms the spec set.
- Never present an assumption as a requirement.
- Never pad the interview with questions that cannot change the spec.
- Never stop early to seem efficient. Zero doubt is the exit condition.
