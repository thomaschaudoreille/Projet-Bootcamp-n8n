---
name: doubt-self-driven
description: Verify your own work while building. Predict the expected outcome, run it, compare, correct, then sweep for the same mistake elsewhere. Use when implementing or changing anything, before declaring a task done, when fixing a bug, when a change touches existing behaviour, or when the user asks whether it really works.
---

# Doubt, Self-Driven

You are the only reviewer of your own work. That makes doubt a procedure, not
a mood.

An unverified change is not a deliverable. It is a hypothesis with a
confirmation bias built in.

## Scope

Applies to: any change with an observable behaviour — code, configuration, a
workflow, a schema, a document, a spec.

Does not apply to: pure research and reading; changes with no observable
behaviour; work the user explicitly asked to skip.

Proportionality. Depth follows blast radius, because doubt has a budget:

| Change                                          | Minimum verification                                                |
| ----------------------------------------------- | ------------------------------------------------------------------- |
| Local edit, no behaviour change                | Read the diff                                                        |
| Behaviour change on one path                    | Execute that path, compare against a prediction                     |
| Shared component, schema, contract              | Execute the path, plus at least one dependent path                  |
| Data, money, permissions, migrations            | Execute, plus a second independent check, plus a rehearsal          |

## The loop

Run it after each unit of work, not at the end.

**1. Predict.** Before running anything, write down what you expect to
observe. The prediction must be specific and observable: the exit code, the
output line, the status code, the row that changes, the error that appears.
If you cannot write the prediction, you do not yet understand the change. Go
read the path again instead of running it.

**2. Execute.** Actually run it. Reading the code is not running it. Reading
the diff is not running it. Reasoning about it is not running it.

**3. Compare.** Prediction against observation. State the delta plainly: "I
expected X, got Y." Do not rationalize the gap. A gap you explain away is
still a gap until it is explained correctly.

**4. Correct.** Fix the cause, not the symptom. Then re-run: a fix that has
not been re-run is a hypothesis. When it passes twice, it is a fix.

**5. Sweep.** The mistake you just found is probably not unique. Search for
the same class elsewhere before moving on. One bug caught, one pattern
hunted.

## The evidence ladder

Not all confidence is equal. Label every claim by how it was established.

| Level | Basis                                  | Counts as  |
| ----- | -------------------------------------- | ---------- |
| L0    | Believed, recalled, assumed             | Not verified |
| L1    | Read or inspected                       | Inspected  |
| L2    | Executed, output observed               | Run        |
| L3    | Predicted, then executed, and matched   | Verified   |

Only L3 is verified. When you tell the user something works, say which level
it reached. "I believe it works" (L0) and "I ran it and it returned 200 with
the expected body" (L3) are not the same claim.

## The correction protocol

When the comparison finds a gap:

1. **Fix** the cause, not the symptom.
2. **Classify** it against `references/doubt-catalog.md`.
3. **Sweep** for siblings of that class.
4. **Re-run** the loop, including the checks that passed before.
5. **Record** it in the verification log, if the project keeps one.

## What to doubt first

Highest yield first:

1. The thing you just wrote and have not run.
2. The assumption you never stated out loud.
3. The claim inherited from documentation or from memory.
4. The path nobody exercises: errors, empty state, boundaries, concurrency.
5. The seam between your change and the rest of the system.
6. The second run: does it still work? Is it idempotent?

Full catalogue, with detection methods: `references/doubt-catalog.md`.

## When you cannot verify

Some things cannot be executed here: no credentials, no instance, no device,
no route to the target. Then:

- Say so explicitly. "The push to the n8n instance is unverified: no access
  token is configured."
- Name what stays unverified and what would verify it.
- Never let an unverified step quietly become an assumed-good step.

An honest gap is worth more than a confident guess.

## Stop conditions

Doubt has to terminate, or it becomes paralysis.

Stop when: the loop has run on the changed paths, the predicted outcomes
matched, the sweep found nothing new, and the remaining uncertainty is
recorded rather than guessed.

Do not stop because checking is tiring. Do not stop at the first green run —
run anything with state twice.

## Never

- Never report "done" for something that was never executed.
- Never write the prediction after seeing the output.
- Never treat a green test suite as proof that the intended behaviour occurs.
- Never perform doubt without executing anything. It manufactures false
  confidence, which is worse than not doubting at all.
- Never skip the sweep after a real bug.

## Files

- `references/doubt-catalog.md` — recurring mistake classes, detection, correction.
- `references/verification-recipes.md` — how to actually execute the checks, per stack.
- `templates/verification-log.md` — optional persistent record of checks performed.
