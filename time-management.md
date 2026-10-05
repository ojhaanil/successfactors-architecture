# Time Management Architecture

## Objective

Design Time Off solutions that remain accurate when eligibility, seniority, work schedules and policy bands change.

## Reference model

```text
Employee Data
    |
    +--> Eligibility
    |
    +--> Seniority
    |
    +--> Work Schedule
    |
    +--> Holiday Calendar
    |
    v
Entitlement / Accrual
    |
    +--> Proration
    |
    +--> Band Transition
    |
    v
Available Balance
    |
    v
Booking Validation
    |
    v
Approved Absence
```

## Accrual design

A robust accrual design should explicitly define:

1. eligibility date
2. entitlement period
3. accrual frequency
4. seniority source
5. proration method
6. transition behavior
7. rounding policy
8. termination / rehire behavior
9. negative balance behavior
10. recalculation expectations

## Example policy abstraction

Instead of hard-coding a policy throughout multiple rules:

```text
Seniority Band
    |
    +-- Band A -> entitlement rule A
    +-- Band B -> entitlement rule B
    +-- Band C -> entitlement rule C
```

The exact values should remain configurable and documented as business policy.

## Booking validation

Validation should be separated into distinct concerns:

- employee eligibility
- date restrictions
- balance availability
- work schedule
- holiday interaction
- minimum / maximum duration
- duplicate or restricted booking
- manager approval

## Testing matrix

| Scenario | Expected validation |
|---|---|
| New hire | Correct eligibility and proration |
| Mid-period joiner | Correct partial entitlement |
| Seniority transition | Correct effective band |
| Rehire | Correct service-date treatment |
| Future-dated change | No premature entitlement |
| Negative balance | Controlled according to policy |
| Work schedule change | Correct downstream effect |

## Key principle

**Time Management rules should make the policy visible. If the policy cannot be explained clearly from the design, the configuration is probably too complex.**
