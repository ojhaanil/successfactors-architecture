# Case Study: Rehire Lifecycle Architecture

## Business problem

Rehire scenarios can affect employment records, onboarding, workflow, effective dating, payroll dependencies, reporting and integrations. A technically valid rehire configuration can still create downstream inconsistency if the lifecycle sequence is not designed explicitly.

## Reference flow

```text
Rehire Event
     |
     v
Employment Decision
     |
     +--> Same / New Employment Context
     |
     v
Workflow / Approval
     |
     v
Effective-Dated Employee Record
     |
     +--------+---------+----------+
     |        |         |          |
     v        v         v          v
 Onboarding Payroll  Reporting  Integrations
```

## Key architecture questions

1. Is this a rehire into the same employment or a new employment?
2. When does the employment become effective?
3. Which process owns approval?
4. Can downstream systems receive the employee before approval is complete?
5. How should future-dated records appear in reporting?
6. Which service date should drive Time Management?
7. What happens if the rehire is cancelled or delayed?

## Design principle

**Separate the business event from the effective employment state.**

A rehire event should not automatically be treated as proof that the employee is already in the final operational state.

## Testing matrix

| Scenario | Validate |
|---|---|
| Rehire with immediate effective date | Workflow, EC and downstream sequence |
| Future-dated rehire | Future-state visibility and timing |
| Rehire pending approval | No premature downstream activation |
| Rehire after termination | Service-date treatment |
| Same employment context | Historical continuity |
| New employment context | New employment data model |
| Reporting | Correct population and effective date |

## Architecture principle

**Rehire is a lifecycle design problem, not just an Employee Central transaction.**
