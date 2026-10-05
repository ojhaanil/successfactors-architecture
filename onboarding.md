# Onboarding 2.0 Architecture

## Objective

Design onboarding as a controlled employee lifecycle process rather than a collection of forms.

## Reference flow

```text
Hire / Rehire Event
        |
        v
Onboarding Process
        |
        +--> Personal / Employment Data
        |
        +--> Compliance
        |
        +--> Documents
        |
        +--> E-Signature
        |
        v
Employee Central
        |
        v
Downstream Systems
```

## Architecture concerns

### New hire

Confirm:

- initiating event
- effective date
- event reason
- employment type
- country-specific forms
- data ownership
- downstream integration requirements

### Rehire

Rehire scenarios require special attention to:

- old employment vs new employment
- future-dated records
- start date behavior
- workflow completion
- payroll dependencies
- reporting visibility
- onboarding status

## Forms and compliance

Use a clear separation between:

**Business data** -> **Compliance requirement** -> **Document output** -> **Signature / completion**

This makes troubleshooting easier and prevents business logic from becoming embedded unnecessarily in form design.

## Testing

At minimum, test:

- standard new hire
- future-dated hire
- rehire with old employment
- rehire with new employment
- country-specific forms
- missing mandatory data
- workflow rejection
- document failure
- downstream integration failure

## Key principle

**Onboarding should orchestrate the employee lifecycle; it should not become the permanent owner of data that belongs in Employee Central.**
