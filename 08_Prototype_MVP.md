# Functional Prototype / MVP

**MBA ZG583 | Management of AI Products | TEAM007: AI Management Group**

I have kept the demonstrator focused on the decision loop rather than trying to build a fully connected enterprise application. Its purpose is to make the future interaction visible: what happens when a field is missing, when evidence is ambiguous, and when a developer wants to record a justification or escalate the finding.

## Prototype type

A local or controlled web prototype using sanitized/synthetic records and a small, versioned criterion set.

## What it demonstrates

- record submission;
- deterministic field checks;
- retrieval of relevant criteria;
- criterion-level status and evidence citation;
- confidence and risk routing;
- recommended next action;
- user correction, justification, and escalation;
- review-summary export.

## What it does not yet prove

- production-scale integration;
- complete coverage of every engineering practice;
- customer audit acceptance;
- enterprise-wide economics;
- performance on every record type;
- long-term model or guidance stability.

## Demonstration script

1. Submit one complete record and show a supported criterion.
2. Submit a record with a missing field and show deterministic feedback.
3. Submit ambiguous evidence and show human-review routing.
4. Show an evidence citation and the user’s ability to override it.
5. Show a fabricated/unsupported evidence attempt being blocked.
6. Export the final review summary.
7. Close with the pilot decision and explicit limitations.

## Demonstrator available in this repository

Open [`prototype/index.html`](prototype/index.html) locally in a modern browser. It is intentionally independent of enterprise services and contains only synthetic data. It implements deterministic examples and an illustrative review disposition / JSON export. The intended retrieval-grounded AI assessment is a **product design proposal**, not a feature claimed to be running in this browser demo.

A working prototype is useful here only if a reviewer can tell the difference between **a supplied reference** and **verified compliance evidence**. The demo therefore labels supplied test/reviewer references as unverified.
