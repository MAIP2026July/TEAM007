# Risk and launch-blocker register

Ethics, Governance, and Risk Note

### Main risks

1. **False assurance:** the tool marks a record as acceptable when material evidence is missing.
2. **False positives:** excessive alerts cause fatigue and reduce trust.
3. **Hallucinated guidance:** the system invents a criterion, evidence, or corrective action.
4. **Inconsistent assessment:** similar records receive materially different results.
5. **Confidentiality exposure:** sensitive engineering information is sent to an unapproved service or retained improperly.
6. **Automation bias:** users accept a recommendation without reviewing evidence.
7. **Knowledge drift:** guidance changes but the tool continues using outdated interpretations.
8. **Accountability ambiguity:** responsibility becomes unclear after a human accepts an AI recommendation.

### Harm scenarios

- A developer relies on a false-clear result and a material gap is discovered during customer review.
- A noisy tool creates unnecessary rework and delays a critical release.
- Sensitive product or customer information is exposed through logs or external inference.
- A team is unfairly compared with another team because workflow differences are not modeled.

### Controls

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

### Launch blockers

Pause or reject launch if:

- the tool cannot reliably cite approved evidence;
- false-clear performance is unacceptable for material criteria;
- sensitive data handling is not approved;
- human reviewers cannot understand or challenge the result;
- audit logs are incomplete;
- guidance updates cannot be propagated and regression-tested;
- the tool is being treated as an autonomous approval authority.

---
