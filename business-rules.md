# Business Rule Design Patterns

## Purpose

Reusable principles for designing maintainable SAP SuccessFactors Business Rules.

## Pattern: single responsibility

A rule should ideally answer one business question.

Bad pattern:

```text
One rule -> eligibility + accrual + security + notification + integration
```

Better:

```text
Eligibility rule
      |
Accrual rule
      |
Validation rule
      |
Notification / downstream action
```

## Pattern: explicit inputs

Document:

- triggering object
- event
- effective date
- fields read
- lookup tables
- expected output
- downstream dependency

## Pattern: event awareness

Always ask:

- Which event triggers the rule?
- Does it execute on create, insert, save or change?
- Is it effective-dated?
- Can it trigger for future-dated records?
- Are contingent workers included?
- Are imports and integrations included?

## Pattern: avoid hidden dependencies

If a rule depends on a lookup table, permission structure or another rule, document the dependency.

## Review checklist

- [ ] Trigger is explicit
- [ ] Inputs are explicit
- [ ] Outputs are explicit
- [ ] No unnecessary duplication
- [ ] Future-dated behavior understood
- [ ] Negative scenarios tested
- [ ] Import / integration behavior tested
- [ ] Naming is meaningful
