# <Project Name> — Verification log

Optional persistent record of the checks performed. Keep it when the project
benefits from an audit trail; skip it otherwise.

## Entries

| Date | Change | Prediction | Observed | Level | Result |
| ---- | ------ | ---------- | -------- | ----- | ------ |
| YYYY-MM-DD | <what changed> | <what was expected> | <what happened> | L3 | Pass / Fixed / Gap |

**Level**: L0 believed, L1 inspected, L2 executed, L3 predicted and matched.

## Defects found and corrected

| Date | Class | Symptom | Root cause | Fix | Swept for siblings |
| ---- | ----- | ------- | ---------- | --- | ------------------ |
| YYYY-MM-DD | <catalog entry> | … | … | … | <result of the sweep> |

## Not verified

Everything that could not be executed, and what would verify it.

| Item | Why unverified | Command or action that would verify it |
| ---- | -------------- | ------------------------------------- |
| …    | …              | …                                     |

## Dependency state

External services, instances and credentials the checks depend on.

| Dependency | Configured | Reachability | Last checked |
| ---------- | ---------- | ------------ | ------------ |
| …          | …          | …            | …            |
