# Case Study: RBP and Reporting Governance

## Business problem

As organizational structures evolve, permission roles, target populations and reporting populations can drift apart. Duplicate target groups and unclear ownership can create both security risk and inconsistent analytics.

## Reference model

```text
Business Requirement
        |
        v
Data Ownership
        |
        v
Population Definition
        |
        +-------------------+
        |                   |
        v                   v
Permission Role        Reporting Population
        |                   |
        v                   v
Effective Access      Analytics Output
```

## Design decisions

### 1. Separate role from population

A permission role should describe **what** a user can do.

A target population should describe **whose data** the user can access.

Combining these concepts unnecessarily increases governance complexity.

### 2. Treat duplicate populations as a data-quality problem

Before creating another target group, compare:

- Population criteria
- Country / legal entity
- Business unit
- Department
- Employee population
- Role assignments
- Business owner

If two groups produce the same effective population, consolidate where appropriate.

### 3. Align reporting population with security intent

A report should not silently use a population that differs from the business/security requirement.

Validate:

```text
Security Population
        =
Expected Reporting Population
```

when the business requirement requires that alignment.

## Governance checklist

- Named business owner
- Documented population criteria
- Clear role purpose
- No unnecessary duplication
- Periodic access review
- Effective-dated organizational changes considered
- Reporting population validated
- Change impact documented

## Architecture principle

**RBP and reporting should be designed as related governance layers, while keeping authorization and analytics responsibilities distinct.**
