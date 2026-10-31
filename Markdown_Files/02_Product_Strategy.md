# Product Strategy and Opportunity Framing

**MBA ZG583 | Management of AI Products | TEAM007: AI Management Group**

I am treating this as an improvement to an existing engineering workflow, not as a separate product that developers must open after doing their normal work. That matters because adoption will be weak if the checker becomes one more review step. The real value is in giving useful feedback while the developer can still correct the record easily.

## Product vision

Enable automotive software teams to identify and resolve ASPICE evidence gaps while work is still in progress, so compliance becomes a guided part of delivery rather than a late-stage rework exercise.

## Job to be done

> When I create or update a software change record, I want immediate, evidence-based feedback on likely ASPICE gaps and the next corrective action, so that I can complete the work correctly before formal review and avoid repeated rework.

## Opportunity framing

**Why the problem matters**

- Compliance gaps are discovered after effort has already been spent.
- The same criteria are interpreted repeatedly by different people.
- Review capacity is consumed by preventable omissions.
- Poor evidence traceability makes audits and customer reviews slower.

**Why current alternatives are weak**

- Static guidance documents are comprehensive but difficult to apply during active work.
- Manual checklists are useful for known controls but do not consistently interpret varied evidence.
- A dashboard can show status but cannot explain what evidence is missing or why it matters.
- Pure automation can create unacceptable false approvals when evidence is ambiguous.

**Why AI may help**

- It can retrieve relevant guidance for the current lifecycle context.
- It can interpret varied but semantically similar evidence.
- It can summarize a gap and draft a next action in language useful to a developer.
- It can prioritize review effort while preserving human accountability.

## Opportunity matrix

| Candidate capability | Business value | Feasibility | Priority |
|---|---:|---:|---|
| Required-field and format validation | High | High | MVP |
| Evidence-to-criterion matching with citations | High | Medium | MVP |
| Missing-evidence explanation and next action | High | Medium | MVP |
| Confidence-based review queue | High | Medium | MVP |
| Manager trend dashboard | Medium | Medium | Phase 2 |
| Suggested evidence text generation | Medium | Medium | Phase 2 |
| Predictive compliance-risk forecasting | Medium | Low | Later |
| Autonomous approval or closure | High theoretical value, unacceptable early risk | Low | Do not build initially |

## Build vs. buy vs. partner/API

**Recommendation: build the workflow and governance layer, using approved model/API components only where appropriate.**

The organization’s interpretation of ASPICE criteria, internal terminology, change workflow, evidence model, and approval responsibilities are domain-specific. A generic compliance product is unlikely to fit these needs without significant adaptation. A foundation model or managed service may accelerate language interpretation, but the organization should retain control of criterion definitions, retrieval sources, thresholds, audit logs, and human approvals.

**Trade-offs**

- Building provides control and customization but requires ownership of maintenance, evaluation, and security.
- A managed model can accelerate the MVP but introduces cost, dependency, data-handling, and change-management concerns.
- A rules-only solution is easier to validate but will miss meaning expressed in varied evidence.

## First wedge

Start with a small set of high-value lifecycle fields and evidence checks for one record type and one development workflow. The first wedge should answer one practical question well:

> “Before I submit this record for review, what evidence is missing, what criterion does it relate to, and what should I do next?”

## Decision from this section

For the first version, I would deliberately avoid the manager dashboard and multi-workflow coverage even though they are attractive in a final vision. The first question to prove is much smaller: **can the developer identify and resolve a likely evidence gap before submitting the change record for formal review?** If we cannot demonstrate this consistently, adding broader AI functionality will not solve the underlying problem.
