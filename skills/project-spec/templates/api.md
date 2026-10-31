# <Project Name> — Interface contract

For each interface the project exposes or consumes.

## <Interface name>

- **Kind**: REST, GraphQL, webhook, CLI, queue, file
- **Owner**: which side controls the contract
- **Consumer**: who calls it
- **Base URL / endpoint**: <path>

### Requests

| Method | Path | Purpose | Required parameters |
| ------ | ---- | ------- | ------------------- |
| POST   | /…   | …       | …                   |

### Responses

| Status | Meaning | Body shape |
| ------ | ------- | ---------- |
| 200    | …       | …          |
| 400    | …       | …          |
| 404    | …       | …          |
| 429    | …       | …          |

### Errors

The error body shape every caller must handle.

```json
{
  "code": "<machine readable>",
  "message": "<human readable>"
}
```

### Idempotency

Whether a repeated call is safe, and how a caller deduplicates.

### Rate limits

| Limit | Value | Behaviour when exceeded |
| ----- | ----- | ----------------------- |
| …     | …     | …                       |

### Versioning

How breaking changes are introduced, and what deprecation looks like.

### Authentication

How the caller authenticates, and how credentials are rotated.

### Examples

One real request and one real response, per interface.
