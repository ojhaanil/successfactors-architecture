# Reporting and Analytics Architecture

## Objective

Design reporting around business questions, data grain and source ownership.

## Reference flow

```text
Business Question
       |
       v
Required Data Grain
       |
       v
System of Record
       |
       v
Reporting Layer
       |
       +--> Story
       +--> Canvas
       +--> People Analytics
       +--> External BI
       |
       v
Business Decision
```

## Before building a report

Define:

1. What decision will the report support?
2. What is the reporting grain?
3. Which object is the source of truth?
4. Which effective-dated record is required?
5. Which population should be visible?
6. What should happen with future-dated employees?
7. How should duplicates be handled?
8. What is the refresh expectation?

## Data quality controls

Reporting defects are often data-model or effective-dating problems rather than reporting-tool problems.

Check:

- duplicate records
- future-dated records
- effective dates
- event reasons
- missing organizational data
- inconsistent identifiers
- security population
- integration timing

## Key principle

**A report is only as reliable as the data model, effective-dating logic and population definition behind it.**
