# Integration Patterns

## Objective

Design reliable movement of HR data between SuccessFactors and downstream systems.

## Reference model

```text
Source System
     |
     v
SuccessFactors
     |
     +--> Validation
     |
     +--> Transformation
     |
     +--> Integration
     |
     v
Downstream System
     |
     v
Monitoring / Reconciliation
```

## Design questions

- What is the source of truth?
- What event or schedule starts the integration?
- What is the required data grain?
- Which fields are mandatory?
- How are effective-dated records handled?
- How are failures detected?
- How are retries handled?
- How is reconciliation performed?

## Integration Center considerations

Before building an integration, define:

- source object
- filters
- joins
- calculated fields
- output format
- destination
- schedule
- error handling
- monitoring owner

## Data reconciliation

A successful file or API response does not necessarily mean the business data is correct.

Reconcile:

```text
Source Count
     =
Extract Count
     =
Destination Accepted Count
```

Investigate differences explicitly.

## Key principle

**Integration architecture includes monitoring and reconciliation, not just data extraction.**
