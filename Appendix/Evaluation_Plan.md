# Evaluation and benchmark plan

Data, Model, and Evaluation Strategy

### Problem as an AI task

This is a multi-stage decision-support task:

1. **Applicability classification:** which criteria apply to this record?
2. **Structured validation:** are required fields complete and valid?
3. **Evidence retrieval:** which approved guidance and evidence are relevant?
4. **Evidence classification:** supported, missing, unclear, or conflicting?
5. **Recommendation generation:** what is the next action, with a citation?

### Data sources

- Approved ASPICE-aligned engineering-practice guidance.
- Structured fields from sanitized change-request or defect fixtures.
- Approved evidence examples and reviewer decisions.
- Human dispositions and correction reasons from the pilot.

No production-sensitive data should be used in an experiment until access, retention, privacy, and security approvals are complete.

### Labeling and ground truth

Create a benchmark in which qualified reviewers independently label:

- applicable or not applicable;
- compliant, non-compliant, unclear, or not assessable;
- evidence supporting the label;
- risk severity;
- acceptable corrective action.

Resolve disagreements through adjudication and record the rationale. Preserve a frozen test set that is not used for prompt or rule tuning.

### Baseline

Compare the AI-assisted workflow with:

1. existing manual review;
2. deterministic field and format checks only;
3. retrieval plus rules without generative recommendations.

The AI approach should only be retained if it improves useful detection or reduces review effort without degrading safety-related precision.

### Model and architecture choice

Use a hybrid architecture:

- deterministic rules for fields, formats, and explicit workflow controls;
- retrieval from a versioned, approved knowledge base;
- a constrained language model for semantic matching and explanation;
- policy checks that reject unsupported claims;
- human review for uncertain or high-risk outputs.

For the MVP, API-first experimentation may be reasonable if data handling is approved. A later decision should compare managed services with an internally controlled deployment using measured quality, cost, latency, privacy, and operational burden.

### Evaluation framework

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

### Proposed go/no-go thresholds

The exact thresholds should be approved with domain reviewers after the benchmark is created. As a starting point:

- zero tolerance for fabricated evidence or unsupported citations;
- no automated “clear” outcome for high-risk or low-confidence findings;
- strong precision for high-impact criteria before any pilot expansion;
- repeatable results on the frozen benchmark;
- measurable reduction in review effort without an increase in missed material gaps;
- complete capture of human decisions, overrides, and escalation reasons.

These are proposed controls, not claims about achieved performance.

---

## Measurement note
All thresholds are proposed, not measured outcomes. A frozen labeled benchmark and reviewer adjudication are needed before reporting actual performance.
