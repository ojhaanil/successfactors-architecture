# Rehire Design Pattern

## Problem space

Rehire scenarios can cross multiple lifecycle boundaries and can behave differently depending on employment history, effective dates and onboarding configuration.

## Architecture questions

Before designing a rehire solution, establish:

- Is the employee returning to the same employment or creating a new employment?
- What happens to historical employment data?
- When should the new record become active?
- Which workflow approvals must complete first?
- Which integrations consume the record?
- How should future-dated records appear in reporting?
- What should happen if approval is delayed or rejected?

## Reference sequence

```text
Rehire Event
    |
    v
Employment Decision
    |
    +--> Old Employment
    |
    +--> New Employment
    |
    v
Workflow / Approval
    |
    v
Effective-Dated EC Record
    |
    +--> Onboarding
    +--> Payroll
    +--> Reporting
    +--> Integrations
```

## Testing

Always test the timing relationship between:

**event -> approval -> effective date -> integration -> reporting**

A rehire design that works only when everything is approved immediately is not production-ready.

## Key principle

**Treat rehire as a lifecycle architecture scenario, not simply as another hire event.**
