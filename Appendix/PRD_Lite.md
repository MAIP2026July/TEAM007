# PRD-lite — ASPICE Compliance Checker

PM Artifact Pack

### Problem statement

Software developers and reviewers need to complete change-request and defect records in a way that is consistent with ASPICE-aligned engineering practices. Because evidence is spread across structured fields and semi-structured supporting material, teams frequently discover gaps late, leading to rework and review delays. The product will provide early, explainable compliance guidance without replacing accountable human review.

### Product requirements summary

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

### Feature prioritization

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

### MVP definition

The MVP is a review assistant, not an approval engine. It will:

- evaluate a constrained set of criteria;
- use sanitized or synthetic records;
- combine rules with retrieval-grounded classification;
- display evidence and uncertainty;
- route ambiguous findings to a human;
- record the user’s disposition and reason;
- produce a simple before/after review summary.

The MVP is successful if it demonstrates useful gap discovery, reduces reviewer search effort, and avoids false confidence on the benchmark set.

### Roadmap

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

### Success metrics

- **Product:** percentage of users who resolve or correctly justify a flagged gap before formal review.
- **Business:** reduction in avoidable rework cycles and review effort per record.
- **Technical:** precision and recall for high-risk criteria; evidence-citation accuracy.
- **Trust/guardrail:** false-clear rate, human override rate, unsupported-claim rate, and escalation completion rate.

---
