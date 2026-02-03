# NudgeEngine
**Execution engine for modern schedules.**

NudgeEngine is a reliability-first reminder backend with a dedicated planning engine.
This repo is built to demonstrate production-quality engineering: idempotent scheduling,
retries, observability, load testing, and chaos testing.

## Architecture

```mermaid
flowchart TD
  U[User] --> A[Go API]
  A --> R[Rust Engine /plan]
  A --> DB[(DB)]
  S[Go Scheduler] --> DB
  S --> N[Notifier]
  N --> DB
  A --> M[Metrics/Logs]
  S --> M
  N --> M
  M --> P[Prometheus]
  P --> G[Grafana]
