# ADR-001 — Effective-Dated HR Lifecycle

**Status:** Accepted

## Context

SAP SuccessFactors processes frequently combine current-state data with future-dated changes. Hire, rehire, job changes, time eligibility, reporting and integrations can therefore observe different effective states at different points in the lifecycle.

## Decision

Treat **effective date as a first-class architecture attribute**.

Every lifecycle design should explicitly define:

- event date
- effective date
- approval date
- processing date
- downstream transmission timing
- reporting visibility date

## Reference model

```text
Business Event
      |
      v
Workflow / Approval
      |
      v
Effective-Dated State
      |
      +----------+-----------+-----------+
      |          |           |           |
      v          v           v           v
   Onboarding   Time      Reporting  Integration
```

## Consequences

### Positive

- Future-dated behavior becomes explicit.
- Reporting expectations can be defined before implementation.
- Downstream timing is easier to validate.
- Rehire and correction scenarios become testable.

### Trade-off

The design requires more up-front analysis because event timing and effective timing cannot be assumed to be identical.

## Validation scenarios

| Scenario | Validate |
|---|---|
| Future-dated hire | Visibility before effective date |
| Future-dated job change | Rule and reporting behavior |
| Rehire | Employment and service-date timing |
| Approval delay | Downstream activation timing |
| Correction | Historical versus current state |
| Integration run | Correct effective record transmitted |

## Principle

**Never assume that the date an HR event is created is the date the employee's operational state should change.**
