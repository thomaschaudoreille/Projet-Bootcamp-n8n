# <Project Name> — Data model

Companion to `technical.md`. The persistence side of the project.

## 1. Entities

### <Entity name>

Purpose: <what this represents>.

| Field | Type | Required | Default | Meaning |
| ----- | ---- | -------- | ------- | ------- |
| id    | …    | yes      | …       | …       |
| …     | …    | …        | …       | …       |

### Relationships

| From | To | Cardinality | Via |
| ---- | -- | ----------- | --- |
| …    | …  | …           | …   |

## 2. Lifecycle

| Entity | Created by | States | Terminal state | Deleted or archived |
| ------ | ---------- | ------ | -------------- | ------------------- |
| …      | …          | …      | …              | …                   |

## 3. Volume and growth

| Entity | Current size | Growth | Retention | Archive policy |
| ------ | ------------ | ------ | --------- | -------------- |
| …      | …            | …      | …         | …              |

## 4. Sensitive data

| Entity | Field | Classification | Protection | Retention limit |
| ------ | ----- | -------------- | ---------- | --------------- |
| …      | …     | …              | …          | …               |

## 5. Migrations

| Change | Backward compatible | Strategy | Rollback |
| ------ | ------------------- | -------- | -------- |
| …      | …                   | …        | …        |

## 6. Existing data import

| Source | Volume | Format | Cleaning needed | Idempotent |
| ------ | ------ | ------ | --------------- | ----------- |
| …      | …      | …      | …               | …          |

## 7. Consistency rules

What must always be true, and which component guarantees it.
