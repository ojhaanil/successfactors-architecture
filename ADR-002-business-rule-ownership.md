# ADR-002 — Business Rule Ownership

**Status:** Accepted

## Context

Complex SuccessFactors implementations can accumulate business rules across multiple objects and events. The same policy may then be implemented more than once, producing inconsistent behavior and difficult troubleshooting.

## Decision

Assign every significant business rule a clear **functional owner and responsibility**.

Before implementing a rule, document:

1. Business decision being made
2. Triggering event
3. Input fields
4. Effective-date dependency
5. Lookup or reference data
6. Expected output
7. Downstream dependency
8. Exception behavior

## Responsibility model

```text
Business Policy
      |
      v
Functional Ownership
      |
      v
Rule Responsibility
      |
      v
Trigger / Object
      |
      v
Output
      |
      v
Downstream Process
```

## Design test

A rule should be challenged when:

- its purpose cannot be stated in one sentence
- the same decision exists in another rule
- the trigger is broader than necessary
- future-dated behavior is undefined
- contingent-worker behavior is undefined
- integrations can invoke it unexpectedly
- support teams cannot explain its output

## Consequences

### Positive

- Less rule duplication
- Easier impact analysis
- More predictable event behavior
- Better production support

### Trade-off

Rule inventory and ownership documentation require ongoing governance.

## Principle

**A rule is an implementation of a business decision, not a container for unrelated logic.**
