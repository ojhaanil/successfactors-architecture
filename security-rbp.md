# Security and RBP Architecture

## Objective

Create role-based access that is secure, understandable and maintainable as the organization grows.

## Reference model

```text
Business Requirement
        |
        v
Data Ownership
        |
        v
Target Population
        |
        v
Permission Role
        |
        v
Permission Group / Assignment
        |
        v
Effective Access
```

## Design principles

### Least privilege

Grant only the access required to perform the business responsibility.

### Separate population from permission

A permission role defines **what** a user can do.

A target population defines **whose data** they can access.

Keeping those concepts separate makes governance easier.

### Avoid duplicate roles

Duplicate roles with slightly different names create:

- maintenance overhead
- inconsistent access
- difficult audit analysis
- accidental over-permissioning

## Governance checklist

- [ ] Business owner identified
- [ ] Permission purpose documented
- [ ] Target population defined
- [ ] Sensitive data assessed
- [ ] Role naming standard applied
- [ ] Duplicate role analysis completed
- [ ] Regression test completed
- [ ] Joiner / mover / leaver impact considered

## Key principle

**RBP is an architecture concern, not an administration afterthought.**
