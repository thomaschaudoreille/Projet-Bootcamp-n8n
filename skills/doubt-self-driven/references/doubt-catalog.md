# Doubt catalogue

Recurring classes of mistake an agent makes while building. Use it to name a
gap you found, then to hunt for siblings of the same class.

Each entry: how it hides, how to detect it, how to correct it.

Detection methods name the concrete command to run. The stack-specific
commands live in `verification-recipes.md`; look there when a class says
"run it" without naming the tool.

---

## 1. The unexecuted deliverable

**How it hides.** You wrote a template, a config, a skill, a schema, a
generator, and you announced it as done because it looked right. Nobody ran
it. The user finds the gap first.

**Detect.** Ask: "can I execute this right now, in this session?" If the
answer is no and the artifact is meant to be run, it is unverified. Find the
consumer of the artifact and run it.

**Correct.** Run it against a realistic input. Fix what breaks. Re-run.

**Sweep.** Other artifacts you produced in the same session that were also
never executed.

---

## 2. The claim from memory

**How it hides.** An API path, a parameter name, a flag, a default value, a
version number, an API shape — stated from recall, never checked. It is
usually plausible, and usually wrong in a detail.

**Detect.** Run the command. Read the actual response, the actual schema, the
actual `--help`. A 404 or a 400 is as informative as a 200: it proves the
thing you remembered is not there.

**Correct.** Replace the recalled value with the observed one. If it cannot
be checked, downgrade the claim to L0 and say so.

**Sweep.** Every other recalled detail in the same answer.

---

## 3. The unreachable path

**How it hides.** The happy path works. The error branch, the empty state,
the boundary value, the concurrent case, the "user has no permission" case
— never executed, because executing them takes effort.

**Detect.** For each branch you wrote, name the input that reaches it. If you
cannot name one, the branch is untested. Check coverage output if the project
has it.

**Correct.** Write the input, run it, observe. Repeat for each branch.

**Sweep.** Other branches in the same file or module.

---

## 4. The silent scope drift

**How it hides.** The change works, and it also changed something you did not
intend. A shared helper modified for one caller. A constant reused where a
local value belonged. A file rewritten more broadly than the request.

**Detect.** Read the diff line by line and account for every hunk. Ask: "is
there a line here that I cannot justify by the request?" If the answer is
yes, it is drift.

**Correct.** Revert unjustified hunks. Keep the change minimal.

**Sweep.** Other shared files you touched in the same session.

---

## 5. The interface drift

**How it hides.** You changed one side of a contract. The caller still sends
the old shape, or the callee now returns a different shape. It passes
locally because only one side exists in your test.

**Detect.** Find every producer and every consumer of the changed field or
endpoint. Execute one full round trip through the real seam, not a mock.

**Correct.** Update both sides, or version the contract.

**Sweep.** Other consumers of the same contract, including undocumented ones.

---

## 6. The non-idempotent second run

**How it hides.** The first run works. The second duplicates, double-counts,
sends a second notification, appends twice, or fails on a uniqueness
constraint. Only visible on a second execution.

**Detect.** Run it twice, against the same state. Compare the two results.
For anything that writes, run it twice deliberately.

**Correct.** Make the operation idempotent, or make the repeat detectable.

**Sweep.** Every write path in the change, not just the main one.

---

## 7. The wrong thing, built correctly

**How it hides.** Every test passes, the code is clean, and it solves a
slightly different problem than the one requested. The acceptance criterion
was misread, and the implementation faithfully matched the misreading.

**Detect.** Re-read the requirement, then the implementation, side by side.
Better: state the requirement as a sentence, then point at the code that
satisfies it. If no code satisfies it, the tests are testing the wrong thing.

**Correct.** Fix the intent, not the code.

**Sweep.** Other requirements in the same request that could be misread the
same way.

---

## 8. The destructive action without rehearsal

**How it hides.** A delete, a migration, a reset, a bulk update. It works on
the sample and destroys the real data.

**Detect.** Run it in a dry-run or against a copy first. Confirm the row
count before and after. For migrations, run up and roll back.

**Correct.** Stop, rehearse, then execute against the target.

**Sweep.** Other destructive steps queued in the same plan.

---

## 9. The environment gap

**How it hides.** It works on your machine and fails on the real one:
different credentials, a missing instance, a different working directory, a
case-sensitive path, a different locale, a different permission.

**Detect.** Run it in the target environment, or enumerate the differences
between local and target and check each one.

**Correct.** Make the differences explicit in configuration, not in habits.

**Sweep.** Other environment assumptions in the same change.

---

## 10. The unconfigured dependency

**How it hides.** The step needs an instance, a token, a key or a service
that is not set up. You skip it because it is impossible right now, and the
gap quietly becomes "assumed fine".

**Detect.** List the external dependencies the change touches. Check each one
is actually present and reachable. This is the gap class most likely to be
hidden in an automated environment.

**Correct.** Configure it, or record it explicitly as unverified with the
command that would verify it.

**Sweep.** Every other dependency the same feature assumes.

---

## 11. The stale artifact

**How it hides.** The documentation, the template, the schema or the example
says one thing; the implementation does another. The spec drifted from the
code during the work.

**Detect.** Grep for the values in the docs and compare with the code. Read
the artifact you wrote against the behaviour you implemented.

**Correct.** Update the artifact. It is part of the deliverable.

**Sweep.** Other artifacts describing the same behaviour.

---

## 12. The swallowed error

**How it hides.** A catch block, a fallback, a default value, a
`try {} catch {}`. The operation fails, the failure is absorbed, and the
result looks like success.

**Detect.** Force the failure. Make the dependency unavailable and observe
what the system does. A silent default that masks an outage is worse than a
loud error.

**Correct.** Propagate the failure, or report it in an observable way.

**Sweep.** Every other catch, fallback and default in the change.

---

## 13. The over-confident summary

**How it hides.** You describe the work in prose that claims more than you
verified. "Works", "handled", "tested" — written from intent, not from
observation.

**Detect.** Re-read your own summary and locate every claim of completion.
For each one, name the evidence. Downgrade or delete the ones with none.

**Correct.** Report at the level you actually reached: L0, L1, L2 or L3.
Name what could not be verified and why.

**Sweep.** Every claim in the same summary.
