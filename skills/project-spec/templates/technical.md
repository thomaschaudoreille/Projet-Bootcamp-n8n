# <Project Name> — Technical design

Companion to `spec.md`. Only the parts the interview established as needed.

## 1. Architecture

The components, their responsibilities, and how they talk to each other.

| Component | Responsibility | Depends on |
| --------- | -------------- | ---------- |
| …         | …              | …          |

Include a diagram when it carries more than the table does.

## 2. Data flow

The path of the main flow, end to end, including what is persisted and when.

1. <step>
2. <step>

## 3. Data model

### <Entity>

| Field | Type | Required | Meaning |
| ----- | ---- | -------- | ------- |
| …     | …    | …        | …       |

Relationships between entities, and the constraints that apply.

## 4. Interfaces

### <Interface name>

- **Kind**: API, UI, CLI, webhook, queue
- **Consumer**: who calls it
- **Contract**: request shape, response shape, error shape
- **Idempotency**: whether a repeated call is safe

## 5. Integrations

| System | Direction | Data | Failure behaviour | Retry |
| ------ | --------- | ---- | ----------------- | ----- |
| …      | …         | …    | …                 | …     |

Which side owns retries, idempotency and reconciliation.

## 6. Failure modes

| Failure | Detection | Response | Owner |
| ------- | --------- | -------- | ----- |
| …       | …         | …        | …     |

## 7. Stack and technical choices

| Layer | Choice | Reason | Cost of reversing |
| ----- | ------ | ------ | ----------------- |
| …     | …      | …      | …                 |

## 8. Deployment and environment

Where it runs, how it is configured, which environments exist, and how
configuration differs between them.

| Variable | Purpose | Environment | Secret |
| -------- | ------- | ----------- | ------ |
| …        | …       | …           | …      |

## 9. Security and privacy

Threats considered, data sensitivity, access control, retention, and the
measures decided for this project.

## 10. Operational considerations

Monitoring, alerting, backups, restore, log retention, and what happens when
a dependency is down.
