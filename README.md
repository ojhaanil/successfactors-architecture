# SAP SuccessFactors Reference Architecture

A public-safe reference architecture demonstrating how SAP SuccessFactors can be designed as a connected HR technology platform across employee lifecycle, onboarding, employee central, time management, security, analytics, and integrations.

## Scope

This reference model focuses on:

- Employee lifecycle orchestration
- SAP SuccessFactors Employee Central as the core employee system of record
- Onboarding 2.0 as the pre-hire / new-hire lifecycle layer
- Time Management and Time Off as policy-driven workforce processes
- Role-Based Permissions (RBP) as the security control layer
- Story / People Analytics / Canvas and downstream BI as reporting layers
- Integration Center and downstream integrations as controlled integration patterns

## Architecture principle

> Design the business lifecycle first, then assign ownership, security, reporting, and integration responsibilities to the appropriate platform component.

## Key design decisions

1. Employee Central owns authoritative employee master and employment data.
2. Onboarding orchestrates pre-hire and new-hire activities; it should not become a second employee master.
3. Time Management consumes governed employee attributes and applies policy-specific calculations.
4. RBP separates **who can perform an action** from **which population they can access**.
5. Reporting starts with business questions and data grain, not with available fields.
6. Integrations require validation, monitoring, and business reconciliation—not only technical success.
7. Effective dating is treated as a first-class architecture attribute.

## Included artifacts

- `reference-architecture.md` — architecture narrative and component responsibilities
- `solution-design.md` — detailed end-to-end solution design
- `architecture-diagram.mmd` — Mermaid source for the architecture diagram
