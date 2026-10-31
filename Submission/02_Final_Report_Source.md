# AI-Enhanced ASPICE Compliance Checker - Consolidated Report

# Executive Summary


## The problem I am trying to solve

A software change request may be technically complete and still get returned during review because the supporting evidence is either missing, not linked properly, or difficult for a reviewer to interpret. In an automotive software environment, development teams are expected to document their work consistently against ASPICE-aligned engineering practices. In reality, teams may follow the same enterprise workflow but capture the evidence in different ways.

The difficult part is not always a missing field. Sometimes the information exists, but it is spread between the description, test references, related items and comments. Developers then have to refer to long engineering-practice documents and interpret which criterion applies. The gap often becomes visible only when a reviewer is already involved. By that stage, rework and additional review cycles are difficult to avoid.

This is therefore a useful product opportunity because it addresses a repeated workflow problem, and not because we want to introduce an AI chatbot into an engineering process.

## Who would use it?

- **Primary user:** developer preparing a change request or defect record for review.
- **Secondary user:** technical reviewer or quality specialist checking the sufficiency of evidence.
- **Additional beneficiary:** software team leader or engineering manager looking at common gaps across a team.

The first version should focus on the developer's *pre-review* moment, rather than trying to automate an audit or issue an organizational compliance verdict.

## What the proposed product does

The ASPICE Compliance Checker is an advisory review assistant. For a permitted change record, it would identify relevant criteria, check straightforward fields with rules, examine the available evidence against a version-controlled guidance set, and return criterion-level findings. Each finding should tell the developer what was found, what is missing or unclear, and which action would help close the gap.

The user must be able to correct the record, justify an exception, or route the matter to a competent reviewer. Even when a finding looks satisfactory, the tool should not independently approve ASPICE compliance.

## Why the solution needs both rules and AI

Ordinary rules can check whether a mandatory field is blank, whether a reference has the expected format, or whether a workflow state is permissible. Building an AI model for these checks would add complexity without enough benefit. AI becomes relevant when supporting evidence is expressed in different language, spread across multiple fields, or has to be matched semantically with a large set of approved criteria.

My recommendation is a **hybrid product**: deterministic checks for hard requirements, controlled retrieval and language interpretation for evidence understanding, and mandatory human judgment for uncertain or consequential cases.

## Recommendation

**Proceed with prototype validation first, followed by a limited pilot only if the initial evaluation is acceptable.** Start with one record type, one workflow and a small set of criteria using synthetic or appropriately approved records. Benchmark against manual review and a rules-only alternative. Before expanding, confirm that evidence citations are reliable, material gaps are not being missed, reviewer effort reduces, and confidentiality and traceability requirements are satisfied.

**What I am not recommending:** autonomous compliance approval, immediate rollout across multiple teams, or a claim that the prototype has already proved business savings. The present prototype is a rules-based demonstration of the user interaction; the proposed AI retrieval and semantic assessment are not yet implemented.

---

# Product Strategy and Opportunity Framing

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

---

# PM Artifact Pack

For me, a useful PM artifact should make the next product decision easier. The PRD, prioritization and roadmap below therefore start from the work a developer actually performs. They also account for the main difference between conventional software and an AI-enabled product: the output may be uncertain even when the system is functioning as designed.

## Problem statement

Software developers and reviewers need to complete change-request and defect records in a way that is consistent with ASPICE-aligned engineering practices. Because evidence is spread across structured fields and semi-structured supporting material, teams frequently discover gaps late, leading to rework and review delays. The product will provide early, explainable compliance guidance without replacing accountable human review.

## Product requirements summary

**Functional requirements**

1. Accept a sanitized record or controlled test fixture.
2. Identify the applicable lifecycle context and criterion set.
3. Run deterministic field and format checks.
4. Retrieve relevant guidance from an approved, versioned knowledge base.
5. Match available evidence to criteria and show supporting excerpts.
6. Classify findings as supported, missing, unclear, or review-required.
7. Recommend a corrective action without inventing evidence.
8. Allow the user to accept, correct, justify, or escalate a finding.
9. Preserve a traceable record of the criterion version, evidence, recommendation, and human disposition.
10. Export a review summary for authorized stakeholders.

**AI-specific requirements**

- Every generated finding must cite the criterion and evidence used.
- The model must be constrained to approved sources.
- Uncertainty must be visible rather than hidden in a single score.
- Low-confidence or high-impact findings must route to human review.
- The system must distinguish “evidence not found” from “evidence disproved.”
- Prompts, model versions, and knowledge-base versions must be auditable.

**Non-functional requirements**

- Protect confidential engineering information.
- Provide predictable response times for the MVP test set.
- Support repeatable evaluations on a frozen benchmark.
- Fail safely when evidence is unavailable or the model cannot determine applicability.
- Keep access, retention, and audit behavior aligned with enterprise policy.

## Feature prioritization

| Feature | User value | Effort | Confidence | Priority |
|---|---|---:|---:|---|
| Deterministic field checks | High | Low | High | P0 |
| Criterion retrieval and evidence citation | High | Medium | Medium | P0 |
| Missing-gap explanation | High | Medium | Medium | P0 |
| Confidence and review routing | High | Medium | High | P0 |
| Human disposition and justification | High | Medium | High | P0 |
| Exportable review summary | Medium | Low | High | P1 |
| Team trend dashboard | Medium | Medium | Medium | P1 |
| Broad multi-workflow coverage | High | High | Low | P2 |
| Autonomous compliance approval | Not acceptable for MVP | High | Low | Out of scope |

## MVP definition

The MVP is a review assistant, not an approval engine. It will:

- evaluate a constrained set of criteria;
- use sanitized or synthetic records;
- combine rules with retrieval-grounded classification;
- display evidence and uncertainty;
- route ambiguous findings to a human;
- record the user’s disposition and reason;
- produce a simple before/after review summary.

The MVP is successful if it demonstrates useful gap discovery, reduces reviewer search effort, and avoids false confidence on the benchmark set.

## Roadmap

**Phase 1 — Discover and calibrate**

- Confirm the first workflow and criterion set.
- Create a de-identified benchmark with expert labels.
- Define risk tiers and launch thresholds.
- Prototype the reviewer experience.

**Phase 2 — Controlled MVP**

- Implement hybrid rules plus retrieval-grounded assessment.
- Add evidence citations, confidence bands, review routing, and disposition capture.
- Test with representative synthetic or approved records.

**Phase 3 — Limited pilot**

- Run alongside the existing process for one workflow.
- Compare rework, review time, precision, and override patterns.
- Conduct security, privacy, and governance review.

**Phase 4 — Expansion decision**

- Expand only if thresholds are met.
- Add additional workflows and criteria incrementally.
- Establish ownership for knowledge-base updates, model evaluation, and incident response.

## Success metrics

- **Product:** percentage of users who resolve or correctly justify a flagged gap before formal review.
- **Business:** reduction in avoidable rework cycles and review effort per record.
- **Technical:** precision and recall for high-risk criteria; evidence-citation accuracy.
- **Trust/guardrail:** false-clear rate, human override rate, unsupported-claim rate, and escalation completion rate.

## Acceptance conditions that I would insist on

A prototype demonstration will be considered convincing only if it shows a normal record, a genuinely missing field, an ambiguous evidence case, and the correct escalation behaviour. The review summary must preserve the original criterion, what the tool observed, and what the user decided. A green status on a screen must never be confused with an authorized ASPICE acceptance.

The development team should treat the product requirements in the PRD-lite under `Appendix/PRD/` as the reference for prototype scope and future implementation.

---

# UX, Workflow and Trust Design

I do not want the first screen to look like an audit verdict. It should behave more like an engineering review assistant that explains a concern and gives a practical next action. A developer who disagrees must be able to understand and challenge a finding without reverse engineering what the tool did.

## Main workflow

1. User selects or uploads a permitted test record.
2. System determines the applicable record type and criteria.
3. Deterministic checks run first.
4. Relevant guidance is retrieved from the approved knowledge base.
5. The AI assesses evidence and produces criterion-level findings.
6. The user sees status, rationale, evidence citation, confidence, and recommended action.
7. The user corrects the record, accepts the finding, provides a justification, or escalates it.
8. The system records the disposition and creates a review summary.

## Proposed screens

**Screen 1: Review queue**

- Record identifier shown only to authorized users.
- Overall status: ready, attention needed, or review required.
- Counts by finding category and risk tier.
- Clear indication that the result is advisory.

**Screen 2: Criterion detail**

- Criterion and version.
- Status and confidence band.
- Evidence excerpt and source reference.
- Explanation of the gap in plain language.
- Suggested next action.
- “Accept,” “Correct,” “Justify,” and “Escalate” actions.

**Screen 3: Review summary**

- Resolved versus outstanding findings.
- Human dispositions and reasons.
- Items requiring specialist attention.
- Exportable audit-oriented summary.

## Trust and explainability

The user must be able to see:

- which criterion was assessed;
- which evidence was used;
- whether the result came from a rule, retrieval, or model interpretation;
- what the system could not determine;
- the confidence band and risk tier;
- the knowledge-base and model versions;
- who changed or overrode the result.

The interface should avoid displaying a deceptively precise probability when the underlying evidence is weak. It should also avoid exposing irrelevant internal implementation details to ordinary users.

## Uncertainty handling

- **High confidence, low risk:** show a clear recommendation, subject to user confirmation.
- **Medium confidence:** show the evidence and request user validation.
- **Low confidence or high risk:** require human review and prevent a “clear” outcome.
- **No evidence or unavailable source:** state that evidence was not found; do not infer compliance.
- **Conflicting evidence:** show the conflict and escalate rather than selecting silently.

## Human-in-the-loop

Human review is required for ambiguous findings, high-impact criteria, conflicting evidence, and any proposed exception. Developers may provide a reasoned justification, but that justification should remain visible to the authorized reviewer. Compliance or quality specialists retain authority for policy interpretation and launch decisions.

## What a developer should see in one finding

For example, the interface may say that verification evidence has **not been located**, name the relevant illustrative check, show the available record text, and ask for a valid test-report reference or reviewer input. It should **not** say that testing was not performed simply because the attachment is missing, and it should never invent a test ID to make a record look complete. This distinction between *not found* and *disproved* is one of the important UX decisions in the product.

A GitHub-renderable workflow diagram and the intended three-screen layout are provided in `Appendix/Wireframes/Workflow.md`.

---

# Data, Model and Evaluation Strategy

The biggest risk in this product is not that the model is occasionally uncertain. The bigger risk is that the tool gives a confident-looking answer against the wrong criterion or without the right evidence. I would therefore start with the evaluation design and the approved source material before selecting a model or deciding on an API.

## Problem as an AI task

This is a multi-stage decision-support task:

1. **Applicability classification:** which criteria apply to this record?
2. **Structured validation:** are required fields complete and valid?
3. **Evidence retrieval:** which approved guidance and evidence are relevant?
4. **Evidence classification:** supported, missing, unclear, or conflicting?
5. **Recommendation generation:** what is the next action, with a citation?

## Data sources

- Approved ASPICE-aligned engineering-practice guidance.
- Structured fields from sanitized change-request or defect fixtures.
- Approved evidence examples and reviewer decisions.
- Human dispositions and correction reasons from the pilot.

No production-sensitive data should be used in an experiment until access, retention, privacy, and security approvals are complete.

## Labeling and ground truth

Create a benchmark in which qualified reviewers independently label:

- applicable or not applicable;
- compliant, non-compliant, unclear, or not assessable;
- evidence supporting the label;
- risk severity;
- acceptable corrective action.

Resolve disagreements through adjudication and record the rationale. Preserve a frozen test set that is not used for prompt or rule tuning.

## Baseline

Compare the AI-assisted workflow with:

1. existing manual review;
2. deterministic field and format checks only;
3. retrieval plus rules without generative recommendations.

The AI approach should only be retained if it improves useful detection or reduces review effort without degrading safety-related precision.

## Model and architecture choice

Use a hybrid architecture:

- deterministic rules for fields, formats, and explicit workflow controls;
- retrieval from a versioned, approved knowledge base;
- a constrained language model for semantic matching and explanation;
- policy checks that reject unsupported claims;
- human review for uncertain or high-risk outputs.

For the MVP, API-first experimentation may be reasonable if data handling is approved. A later decision should compare managed services with an internally controlled deployment using measured quality, cost, latency, privacy, and operational burden.

## Evaluation framework

| Metric type | Metric | Why it matters |
|---|---|---|
| Technical | Precision for high-risk non-compliance findings | Limits noisy escalations |
| Technical | Recall for material evidence gaps | Avoids missed issues |
| Technical | Evidence-citation accuracy | Makes findings verifiable |
| Technical | Repeatability on identical inputs | Tests consistency |
| Business | Rework cycles per record | Measures operational value |
| Business | Review time per record | Measures efficiency |
| Business | Time to resolve a finding | Measures workflow improvement |
| Trust | False-clear rate | Detects unsafe reassurance |
| Trust | Unsupported recommendation rate | Detects hallucinated guidance |
| Trust | Override and escalation rate | Reveals calibration and usability |
| Governance | Audit-log completeness | Supports accountability |

## Proposed go/no-go thresholds

The exact thresholds should be approved with domain reviewers after the benchmark is created. As a starting point:

- zero tolerance for fabricated evidence or unsupported citations;
- no automated “clear” outcome for high-risk or low-confidence findings;
- strong precision for high-impact criteria before any pilot expansion;
- repeatable results on the frozen benchmark;
- measurable reduction in review effort without an increase in missed material gaps;
- complete capture of human decisions, overrides, and escalation reasons.

These are proposed controls, not claims about achieved performance.

## How I would evaluate it in practice

I would form a small, frozen set of synthetic or approved sanitized records where subject-matter reviewers have independently labelled the applicable criterion, the evidence gap (if any), the risk and the acceptable next action. Where two reviewers disagree, I would record the reason and get an adjudicated label instead of forcing agreement silently.

I would run **manual review**, **rules-only validation**, and the **proposed hybrid AI-assisted flow** on the same set. It is important to measure not just precision or recall but also how often a record was incorrectly treated as clear. Review time, the extra effort caused by false alarms, and the rate of unsupported citations would influence the pilot decision. None of these measurements has been reported as an achieved result in this submission.

The metrics and benchmark template under `Appendix/Metrics/` are preparation material for this evaluation, not experimental results.

---

# Business, Economics and Scaling

I see this primarily as an internal productivity and quality initiative. Charging a subscription per developer is not the right way to assess it. The more meaningful comparison is whether the total effort spent preparing, reviewing and correcting a change record goes down without increasing the risk of missed evidence.

## Monetization and value model

This is primarily an internal enterprise value case rather than a standalone external subscription. Value comes from:

- fewer avoidable rework cycles;
- faster preparation for formal reviews;
- reduced reviewer search and interpretation effort;
- more consistent evidence quality;
- earlier visibility into recurring process gaps;
- lower risk of delivery disruption or customer dissatisfaction.

## Cost drivers

- model or API inference;
- retrieval and storage;
- integration with the enterprise workflow;
- security and access controls;
- knowledge-base maintenance;
- expert labeling and evaluation;
- human review of uncertain findings;
- support, monitoring, and incident response.

## Unit economics view

For each assessed record, compare the total operating cost of the checker with the value of review time saved and rework avoided. The business case is positive only if the tool reduces net effort while maintaining acceptable risk. Token reduction, caching, staged checks, and deterministic pre-filters can control cost, but should not weaken evidence quality.

## Scaling constraints

- Criteria and guidance change over time.
- New workflows may require different applicability logic.
- Evidence formats and terminology vary across teams.
- More records increase model cost and review queues.
- Model behavior can change after provider updates.
- Broad deployment increases privacy, access, and audit obligations.

Scale should therefore be staged by workflow and risk tier, with regression evaluation whenever guidance, prompts, rules, models, or integrations change.

## Simple unit-economics logic

For a pilot, I would compare the cost **per record reviewed** with the value of time saved and avoidable rework reduced. A working model is:

`Net value per record = (reviewer minutes saved + avoidable rework minutes saved) x loaded cost per minute - (model/API + retrieval + infrastructure + additional human-check cost per record)`

The monetary outcome should only be computed after observing a representative baseline; inserting a speculative savings percentage would make the business case look stronger without making it more credible.

**Scaling decision:** add one workflow at a time. Each new criterion set needs a named owner, a regression test and a clear rollback route if the interpretation changes.

---

# Ethics, Governance and Risk Note

In this use case, a false positive is inconvenient, but a false assurance may have a much wider impact. If an AI-assisted checker creates confidence that a record is acceptable when critical evidence is absent, we have made the review process worse rather than better. Governance therefore needs to be built into the workflow, not added as a final disclaimer.

## Main risks

1. **False assurance:** the tool marks a record as acceptable when material evidence is missing.
2. **False positives:** excessive alerts cause fatigue and reduce trust.
3. **Hallucinated guidance:** the system invents a criterion, evidence, or corrective action.
4. **Inconsistent assessment:** similar records receive materially different results.
5. **Confidentiality exposure:** sensitive engineering information is sent to an unapproved service or retained improperly.
6. **Automation bias:** users accept a recommendation without reviewing evidence.
7. **Knowledge drift:** guidance changes but the tool continues using outdated interpretations.
8. **Accountability ambiguity:** responsibility becomes unclear after a human accepts an AI recommendation.

## Harm scenarios

- A developer relies on a false-clear result and a material gap is discovered during customer review.
- A noisy tool creates unnecessary rework and delays a critical release.
- Sensitive product or customer information is exposed through logs or external inference.
- A team is unfairly compared with another team because workflow differences are not modeled.

## Controls

- Approved-source retrieval with source citations.
- Deterministic checks for hard controls.
- Risk-tiered thresholds and mandatory review.
- No autonomous compliance approval.
- Clear uncertainty labels and anti-automation-bias UX.
- Versioned criteria, prompts, models, and evaluation sets.
- Access control, retention limits, encryption, and redacted logging.
- Human override with reason capture.
- Monitoring for drift, false clears, unsupported claims, and inconsistent results.
- A documented incident and rollback process.

## Launch blockers

Pause or reject launch if:

- the tool cannot reliably cite approved evidence;
- false-clear performance is unacceptable for material criteria;
- sensitive data handling is not approved;
- human reviewers cannot understand or challenge the result;
- audit logs are incomplete;
- guidance updates cannot be propagated and regression-tested;
- the tool is being treated as an autonomous approval authority.

## A deliberately conservative launch rule

No source citation, no defensible finding. No reliable evidence, no automated clear status. No approval from the appropriate reviewer, no compliance approval. Even a very well-presented demo should not override these decisions.

I would also avoid comparing individual teams through a dashboard until differences in their workflows and evidence responsibilities have been understood. Otherwise, the tool could unintentionally make a good-faith team look less compliant just because it records evidence differently.

---

# Functional Prototype / MVP

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

---

# AI Collaboration Log

## Tools actually identified in my working material

My Word write-up identifies **Microsoft Copilot** and **Claude** among the AI tools considered or used during the work. It also identifies **RV&S (PTC Integrity), Microsoft Excel and Java** as part of the engineering and prototyping context; I am not representing these three as generative AI tools. In preparing the GitHub submission files, I additionally used **ChatGPT** to help reorganize and review the supplied assignment materials and prepare supporting deliverables.

This section should remain accurate to the work actually performed. Dates, the specific application in which a prototype was created, and unrecorded team activity are not being invented for the purpose of completing a table.

## Where AI helped and where it was useful

The main benefit was not obtaining a ready-made ASPICE answer. AI helped in comparing alternative ways to describe the problem, organizing the long assignment brief into PM deliverables, converting the concept into PRD-style requirements, and suggesting test situations that a normal checklist may overlook. It was also useful in challenging whether the proposed product was becoming too ambitious for an MVP.

The technical interpretation still needed checking. In particular, the source of each compliance criterion must be approved; a fluent explanation from a model is not the same as an applicable engineering requirement.

## Example prompts and workflow

Two example prompts recorded in my working document are:

> Convert these approved, sanitized criteria into a testable evaluation table without inventing requirements.

> Review this prototype workflow for uncertainty handling, human override, auditability, and unsafe automation.

A further instruction used in preparing this GitHub package was to take the existing Word report, Markdown notes, and faculty assignment packet, then organize the content into **section-specific Markdown files and the required submission artifacts**, keeping the engineering details and a student-written tone. These examples illustrate the collaboration process; the two earlier prompts should be confirmed against the original tool history if they are to be described as verbatim historical prompts.

## What AI got wrong or did not establish

AI assistance can suggest a credible-looking criterion when the actual approved criterion was never supplied. It may also assume that a reference in a record proves an activity was completed, exaggerate the level of automation, or propose attractive performance targets without any baseline measurements. These are material weaknesses for a compliance-related product.

I have therefore kept the implementation claim limited to a **rules-based, synthetic demonstrator**. The retrieval and AI classification pieces are part of the proposed architecture, not already validated features. Likewise, business savings, precision, recall and false-clear rates remain measurements for the controlled evaluation.

## Human decisions and corrections

I would not replace accountable reviewer judgment with an automated approval. The decision in this report is to narrow the first scope, preserve source and evidence traceability, route uncertainty to human reviewers, and evaluate against manual and rules-only baselines before a pilot. Those are product and risk decisions, not results obtained by asking an AI assistant to choose a launch recommendation.

## My reflection

For this assignment, AI was useful as a drafting and challenge partner, particularly when connecting a real engineering problem to formal product-management artifacts. But I found that the more important work was deciding what **not** to automate, defining how a reviewer can challenge the system, and making sure we do not present an assumption as tested evidence. The project should be judged on those decisions as much as on the demonstration screen.

---

# Individual Contribution Statement

**Mayur H. Borate | Student ID: 2025MB26174**  
**Course:** MBA ZG583 - Management of AI Products  
**Team:** TEAM007: AI Management Group

I led the framing of the ASPICE Compliance Checker opportunity, starting from the practical difficulty of preparing engineering change records that are complete and reviewable. My focus was on identifying the user and the point in the workflow where the tool could make a meaningful difference, rather than treating AI as an end in itself.

I worked on the product vision, the job-to-be-done statement, the initial MVP boundary and the decision to combine deterministic checks with retrieval-grounded interpretation. I also contributed to the product requirements, feature prioritization, roadmap, evaluation approach and risk discussion. A key decision I retained through the project was that the assistant must show its evidence and must not become an autonomous ASPICE approval mechanism.

I reviewed the AI-assisted drafting against the engineering context and the faculty assignment requirements. In particular, I kept the proposed controls and the measured results separate, and recommended a controlled pilot only after benchmark and prototype validation.

**Team disclosure:** The supplied material identifies only my contribution.

---

# Course Case Connection

I found three course case lenses particularly relevant to how I would make decisions for this product. These are comparisons of the product principles discussed in the course, not claims that those companies operate an ASPICE checker.

## 1. Google Maps - value depends on an entire product system

The product lesson I draw is that a useful AI experience is rarely only a trained model. In this project, an answer is usable only when the record is correctly interpreted, the appropriate criterion can be retrieved, the supporting evidence is shown, and the finding reaches the right reviewer. The model can be technically competent and the product can still fail if those workflow pieces are missing.

**What I would do differently here:** keep a rule-based layer for deterministic checks and explicitly identify who owns the criteria and the human decisions. A sophisticated model would not compensate for missing governance.

## 2. iMerit - trustworthy labels require data operations

The relevant lesson is the importance of good labeling and adjudication rather than assuming that historical outcomes form a clean ground truth. Different reviewers may reasonably disagree on what counts as sufficient evidence. I would resolve and document those differences in a controlled benchmark rather than training the model on inconsistent decisions.

**Difference:** the data in this capstone is not an open image-labeling task. It is domain-specific, partially confidential engineering evidence and therefore requires stricter source control and reviewer qualification.

## 3. Instacart / Tesla - product quality is not frozen at launch

Criteria, record templates, engineering terminology and model behaviour can change. A pilot that works on today's synthetic examples can become unreliable after one workflow update. I would consequently version the guidance set, test against a frozen benchmark and apply regression checks whenever rules, prompts, models or criteria change.

## What these comparisons changed in my recommendation

The decision is still to **validate the first wedge and then consider a controlled pilot**, not to promise broad compliance automation. For this product, the higher-value PM judgment is knowing when evidence is not good enough to move forward.
