# SAP SuccessFactors Reference Architecture

## 1. Business lifecycle

The reference lifecycle is:

**Hire / Rehire Event → Onboarding → Employee Central → Time / Talent / Reporting → Downstream Integrations**

The architecture deliberately treats the lifecycle as connected rather than as isolated module implementations.

## 2. Logical layers

### Experience layer
- Employee
- Manager
- HR / HR Operations
- HRIS / Support
- Reporting consumers

### Process orchestration layer
- Onboarding 2.0
- Employee Central business processes
- Time Off / Time Management processes
- Workflow and approval mechanisms

### System-of-record layer
**Employee Central** is the authoritative source for core employee and employment attributes used across the HR landscape.

Typical governed attributes include:
- Person / employment identity
- Job information
- Organizational assignment
- Employment status
- Manager relationship
- Effective-dated changes

### Policy and rules layer
Business rules should implement explicit business decisions such as:
- Eligibility
- Data validation
- Time profile determination
- Accrual calculation
- Event-driven updates
- Workflow routing

Rules should have clear ownership and should not combine unrelated responsibilities.

### Security layer
RBP should be designed through:

**Business requirement → Data ownership → Target population → Permission role → Assignment → Effective access**

The permission role and target population are separate architectural concerns.

### Analytics layer
Reporting architecture should follow:

**Business question → Data grain → System of record → Reporting layer → Decision**

Before building a report, validate:
- Effective date
- Population
- Future-dated records
- Duplicate grain
- Source of truth
- Refresh behavior

### Integration layer
Integration pattern:

**Source → Extract → Validate / Transform → Transmit → Reconcile → Monitor**

Technical completion is not equivalent to successful business processing.

## 3. Cross-cutting architecture controls

### Effective dating
Every major lifecycle event should distinguish:
- Event creation date
- Effective date
- Workflow approval date
- Processing date
- Downstream processing date
- Reporting/as-of date

### Observability
Critical processes should provide:
- Processing status
- Error visibility
- Exception ownership
- Reprocessing approach
- Reconciliation evidence

### Governance
Every significant configuration should have:
- Business owner
- Technical owner
- Trigger
- Inputs
- Effective-date dependency
- Exception behavior
- Downstream dependency
- Test coverage

## 4. Architecture quality test

A solution is not considered complete until the following questions can be answered:

1. What is the system of record?
2. What event starts the process?
3. When does the business state actually become effective?
4. Who owns the business decision?
5. Which population is affected?
6. What happens when the normal path fails?
7. How is the result reported?
8. How is downstream processing reconciled?

## 5. Public-safe scope

This model intentionally avoids client-specific configuration, credentials, production identifiers, proprietary integration mappings, or confidential implementation details.
