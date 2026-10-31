# Readiness check — the exit condition for the interview

Zero doubt is not a feeling. It is these gates, each honestly ticked. A gate
you cannot tick produces exactly one more question, aimed at that gate.

Run the check in chat before proposing the spec set. Show the state of each
gate. If a gate is open, say what is missing and ask about it.

## G1 — Goal

- [ ] The problem is stated in one sentence, in the user's terms.
- [ ] Who has this problem is identified, concretely.
- [ ] Success is measurable, with a value or a threshold.
- [ ] The consequence of not building it is understood.

**Fails if:** you would write different summaries for two different readers.

## G2 — Scope

- [ ] What is in scope for the first delivery is explicit.
- [ ] What is explicitly out of scope is explicit — and the user has confirmed
      the "not doing" side, not just the "doing" side.
- [ ] Deferred items are listed with what would trigger them.
- [ ] The size of the first delivery is plausible.

**Fails if:** two people could read the scope and build different things.

## G3 — Behaviour

- [ ] The user roles are listed, with what each may do.
- [ ] The main flows are described, from trigger to outcome.
- [ ] Every story has acceptance criteria that a tester could verify without
      asking a question.
- [ ] The unhappy paths are specified: invalid input, missing data, denied
      access, upstream failure, cancellation.
- [ ] Empty states and boundaries are specified, not assumed.

**Fails if:** you would have to invent a rule while writing the first task.

## G4 — Solution shape

- [ ] The components and their responsibilities are decided.
- [ ] The data flow between them is decided, including what is persisted.
- [ ] The main technical choices have a stated reason.
- [ ] Repository or platform conventions that constrain the design are known.

**Fails if:** the architecture section would contain the word "TBD".

## G5 — Constraints

- [ ] Legal, compliance and data-protection constraints are known, or the
      project is explicitly outside their reach.
- [ ] Budget, cost model and expected volume are known, or the answer is that
      it does not matter yet.
- [ ] Deadlines, team size, and who else must be involved are known.
- [ ] The environment the thing runs in is known: local, hosted, on-premise.
- [ ] The existing constraints that cannot be negotiated are listed.

**Fails if:** a constraint exists that you only discovered while implementing.

## G6 — Delivery

- [ ] The first increment is defined, with its own acceptance criteria.
- [ ] The order of work is decided by dependency, and the first three tasks
      are named.
- [ ] Whoever validates the result is named, with what they check.
- [ ] The definition of done for the first increment is written down.

**Fails if:** you cannot name the next concrete action to take.

## G7 — Risks and unknowns

- [ ] The risks that would hurt most are listed, with a mitigation for each.
- [ ] Every open question has an owner, a way to settle it, and a trigger.
- [ ] The riskiest assumption is identified and named as such.
- [ ] Nothing in the project depends on an unrecorded assumption.

**Fails if:** a reader could disagree with your reading of the project and
have no place to say so.

## The ledger

Behind the gates, keep a running list of doubts. Three kinds:

| Kind            | Meaning                                              | Resolution              |
| --------------- | ---------------------------------------------------- | ----------------------- |
| Open            | You do not know, and it matters                      | Ask, now                |
| Parked          | The user does not know; it is recorded and deferred  | Open question in the spec, with owner and trigger |
| Out of scope    | It does not apply to this delivery                  | Say so in the scope section |

The interview closes when every gate is ticked and no doubt remains `Open`.

Do not close it because the user is tired. Do not keep it open because a
question feels interesting. Close it when the spec can be written without
guessing anything that would change the result.
