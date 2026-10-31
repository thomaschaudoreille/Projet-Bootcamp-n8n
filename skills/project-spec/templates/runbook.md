# <Project Name> — Operations

How the project is run once it exists.

## 1. Deployment

| Environment | Purpose | Trigger | Process |
| ----------- | ------- | ------- | ------- |
| …           | …       | …       | …       |

Rollback procedure, and how long a rollback takes.

## 2. Configuration

| Setting | Where it comes from | Change process |
| ------- | ------------------ | -------------- |
| …       | …                  | …              |

Which settings require a restart, and which are hot-reloadable.

## 3. Monitoring

| Signal | Meaning | Threshold | Where it is seen |
| ------ | ------- | --------- | ---------------- |
| …      | …       | …         | …                |

## 4. Alerting

| Alert | Condition | Severity | Who is notified | Action expected |
| ----- | --------- | -------- | --------------- | --------------- |
| …     | …         | …        | …               | …               |

## 5. Logs

| Log | Purpose | Retention | Access |
| ---- | ------- | --------- | ------ |
| …    | …       | …         | …      |

What must never be logged: credentials, personal data, tokens.

## 6. Backup and restore

| Data | Backup method | Frequency | Retention | Restore tested |
| ---- | ------------- | ---------- | --------- | -------------- |
| …    | …             | …          | …         | …              |

## 7. Dependency outage

| Dependency | Degraded behaviour | User impact | Mitigation |
| ---------- | ----------------- | ----------- | ---------- |
| …          | …                 | …           | …          |

## 8. Incidents

| Severity | Definition | First response | Escalation |
| -------- | ---------- | -------------- | ---------- |
| …        | …          | …              | …          |

## 9. Maintenance

| Task | Frequency | Owner |
| ---- | --------- | ----- |
| …    | …         | …     |

Dependency updates, certificate renewal, credential rotation, and capacity
review.
