# Accrual Design Pattern

## Purpose

A reusable framework for designing policy-driven Time Off accruals.

## Inputs

```text
Employee
  |
  +--> Eligibility
  +--> Seniority
  +--> Country / Location
  +--> Work Schedule
  +--> Policy Band
  +--> Effective Date
```

## Calculation layers

1. Determine eligibility.
2. Determine entitlement band.
3. Determine accrual frequency.
4. Apply proration where required.
5. Apply transition logic.
6. Apply rounding.
7. Publish or calculate the resulting balance.
8. Validate booking behavior.

## Design rule

Do not mix all policy decisions into a single opaque calculation.

Prefer:

```text
Eligibility
   |
Policy Band
   |
Entitlement
   |
Proration
   |
Balance
   |
Booking Validation
```

## Test scenarios

- first day of eligibility
- mid-month joiner
- seniority boundary
- policy transition
- rehire
- termination
- future-dated change
- negative booking
- work schedule change

## Key principle

**Accrual logic should be deterministic, explainable and testable from business policy.**
