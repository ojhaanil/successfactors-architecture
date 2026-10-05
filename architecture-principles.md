# Architecture Principles

## 1. Start with the business process

Do not begin with a configuration object. Begin with the process, actors, decisions and outcomes.

## 2. Identify the system of record

Every important data element should have a clear source of truth.

## 3. Prefer standard capabilities

Use standard platform behavior before introducing additional custom logic.

## 4. Minimize rule duplication

One business policy should have one clear implementation wherever practical.

## 5. Design for effective dating

Future-dated changes can affect workflows, reporting, security and integrations before the effective date.

## 6. Treat security as part of solution design

Access requirements should be captured during design, not after configuration is complete.

## 7. Make integration dependencies explicit

Document upstream triggers, payload ownership, timing, failure handling and downstream expectations.

## 8. Test the exception path

A design is incomplete if it only works for the happy path.

## 9. Document why, not only what

Configuration documentation should explain the business reason and design decision, not merely list field values.

## 10. Optimize for production support

A technically clever solution is not necessarily a good solution if another consultant cannot understand or troubleshoot it.

## Architecture decision test

Before approving a design, ask:

> Is it correct, secure, maintainable, testable, supportable and explainable?

If any answer is no, revisit the design.
