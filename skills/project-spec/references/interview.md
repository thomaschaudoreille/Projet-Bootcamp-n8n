# Question bank

A menu, not a script. Work through it in order, but adapt hard: the point is
to close doubts, not to cover sections.

**Rules that apply to every question**

- One question per turn. Wait for the answer.
- Always propose a concrete default, so the user can say "yes" and move on.
- Keep it answerable in one to three sentences.
- Skip anything whose answer cannot change a decision in the spec.
- Prefer specific options over open prompts when the shape of the answer is
  bounded.

**Depth is earned, not assumed.** A one-line project needs three questions. A
product with users, money and a deadline needs thirty. The bank below lists
what each dimension decides and when it is worth going deeper.

---

## A. Problem and goal

Decides: what the spec is for, and the summary paragraph.

- What breaks today, and who feels it?
- What does success look like, measured how?
- Why now — what forces this to happen at this moment?
- What happens if it is never built?
- Is this replacing something, or adding to what exists?

**Go deeper when** the project has more than one stakeholder with different
success measures, or when the problem statement is a symptom of a deeper one.

## B. Users and roles

Decides: the stories, the permissions, the interface.

- Who uses this? Name the distinct roles, not "users".
- What can each role do that the others cannot?
- Is there an admin, an operator, a support person, or only end users?
- How many real users, roughly, and do they differ by segment?
- Does an admin need to see or change what a user sees?

**Go deeper when** roles carry different data access, different permissions, or
different views of the same underlying thing.

## C. Scope

Decides: the boundary of the first delivery, and every non-goal.

- What is in scope for the first version?
- What is explicitly out of scope?
- Which part lands first?
- What would make you abandon this project?
- Is anything already decided and non-negotiable: a deadline, a budget, a
  partner, a regulator, a legal obligation?

**Go deeper when** the project could be delivered in three different sizes and
nobody has picked one.

## D. Behaviour

Decides: the stories, the acceptance criteria, the flows.

- What are the main flows, from trigger to outcome?
- What happens on invalid input, missing data, denied access, upstream failure?
- What does the user see when there is nothing to show yet?
- What can be undone, and what cannot?
- Which rules, calculations, or state transitions matter enough to be wrong?
- Are there limits, quotas, caps, or deadlines?

**Go deeper when** the domain has rules that a developer would otherwise
misimplement: pricing, eligibility, quotas, matching, scoring.

## E. Data

Decides: the data model, the migrations, the storage.

- What are the core objects and their fields?
- What is stored, and what is only passed through?
- How much volume, and how fast does it grow?
- What is the retention, archiving, or deletion policy?
- Does any of it contain personal, financial, or regulated data?
- Is there data that already exists elsewhere and must be imported?

**Go deeper when** the volume, the sensitivity, or the migration decides the
architecture.

## F. Integrations

Decides: the boundaries, the failure handling, the project plan.

- Which external systems are involved?
- For each: read, write, or both? Synchronous or asynchronous?
- What is the system of record?
- What happens when an integration is slow, down, or returns garbage?
- Which side owns the retry, the idempotency, the reconciliation?

**Go deeper when** more than one external system is involved, or when data
flows both ways.

## G. Interface

Decides: the surface the user or the caller actually touches.

- Is there a user interface? Web, mobile, desktop, terminal, chat?
- Is there a public or internal API? Who calls it?
- What does the user type, click, or upload?
- What do they need to see, and what do they need to do about it?
- Do they need to search, filter, sort, export, print?

**Go deeper when** the interface carries most of the product's value, or when
an API contract is the deliverable.

## H. Technical direction

Decides: the architecture section.

Confirm only what exploration did not already settle.

- Confirm the stack, and what is fixed by the organisation.
- Where does it run: local, hosted, serverless, on-premise?
- How is state persisted, and what happens if that store is empty at first
  run?
- Which part is expected to be hard, and why?
- Are there existing components to reuse rather than rebuild?

**Go deeper when** the technical choice is expensive to reverse.

## I. Quality bar

Decides: the non-functional requirements, which are testable or untestable.

- Expected volume, and the latency that matters.
- What must never break, and acceptable downtime.
- Security requirements, especially around sensitive data.
- Accessibility target, if there is an interface.
- Observability: logs, metrics, alerts, audit trail.
- How would the user report a problem, and what would they see?

**Go deeper when** the project handles money, personal data, or anything that
would be costly to get wrong.

## J. Delivery

Decides: the task plan.

- What is the priority order of the phases?
- What is the first increment that proves value?
- Who builds it, and what is already known about the team?
- What does the team already have: CI, environments, tests, a deployment
  pipeline?
- What is the definition of done for the first release?

**Go deeper when** more than one person works on it, or when the plan must fit
a real calendar.

## K. Risks and unknowns

Decides: the risk table, the open questions.

- What is the riskiest assumption you are making?
- What would make this fail in a way you did not plan for?
- Who is responsible for answering the open questions?
- What is the plan if the scope must be halved?

**Go deeper when** the project depends on something outside the team's
control: a partner, a regulator, a third-party API, a budget.

---

## Optional depth probes

Use these only when the dimension above proved fragile.

**Roles and permissions**
- Can a role be changed after creation? Does it take effect immediately?
- Who grants access? Is it self-service or approved?
- What happens to a user's access when they leave?

**State and lifecycle**
- What are the states an object can be in? What moves it between them?
- Can a transition be reversed? By whom?
- What is the terminal state, and what happens to the data then?

**Failure and recovery**
- What is the worst failure mode: wrong data, missing data, or wrong
  recipient?
- What has to be reconciled by hand? How often?
- Is there a point where a human must decide?

**Numbers**
- What is the unit, and what is the rounding?
- Are there thresholds, tiers, or brackets?
- What happens at exactly the boundary?

**Time and recurrence**
- What is the schedule, and whose timezone?
- Does it run per user, per tenant, per document, or globally?
- What happens to a run that was missed?

**Scale of change**
- How many users act on the same object at once?
- Does the order of actions matter to the result?
- What happens if two people act at the same moment?

**Cost**
- What does it cost per unit of volume?
- What makes the cost jump: volume, seats, compute time, API calls?
- What is the ceiling, and what happens when it is reached?

## Last-resort questions

When a dimension resists, ask these instead of repeating yourself:

- "Which of these two would you rather have?" — forces a trade-off.
- "What would you do if this were your only option?" — reveals priority.
- "Who else has an opinion on this?" — surfaces the stakeholder.
- "What would make you reject this spec?" — surfaces the acceptance bar.
- "Is this a real constraint or a preference?" — separates the two.
