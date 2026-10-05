# Case Study: Policy-Driven Statutory Accrual Architecture

## Business problem

Design a Time Off accrual model that can support entitlement bands, seniority-based transitions, new-joiner proration, rehire scenarios and controlled booking validation without duplicating policy logic across multiple rules.

## Architecture objective

Create a deterministic and explainable calculation flow:

```text
Employee Context
      |
      +--> Eligibility
      |
      +--> Seniority / Service Date
      |
      +--> Policy Band
      |
      +--> Accrual Frequency
      |
      +--> Proration
      |
      +--> Transition Handling
      |
      v
Entitlement / Balance
      |
      v
Booking Validation
```

## Design decisions

### 1. Separate policy from calculation mechanics

The policy defines entitlement and eligibility. Business rules implement the calculation.

This prevents policy values from being scattered across unrelated rules.

### 2. Make seniority transitions explicit

When an employee crosses an entitlement band, the design must define exactly when the new entitlement becomes effective.

Questions to document:

- Which date is the source of seniority?
- Is the transition effective immediately or from the next accrual period?
- How is the transition handled for future-dated changes?
- What happens after rehire?

### 3. Treat proration as a separate concern

New-joiner proration should not be embedded invisibly inside every entitlement rule.

```text
Annual Entitlement
        |
        +--> Full-period employee
        |
        +--> Partial-period employee
                  |
                  v
             Proration
```

## Test scenarios

| Scenario | Expected result |
|---|---|
| Standard employee | Full policy entitlement |
| Mid-period new hire | Correct prorated entitlement |
| Seniority transition | Correct effective band |
| Future-dated seniority change | No premature entitlement |
| Rehire | Correct service-date treatment |
| Work schedule change | Defined downstream impact |
| Negative booking | Allowed/rejected according to policy |

## Architecture principle

**A time-off calculation should be deterministic enough that HR, implementation and support teams can explain the result from the same set of inputs.**
