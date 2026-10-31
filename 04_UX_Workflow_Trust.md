# UX, Workflow and Trust Design

**MBA ZG583 | Management of AI Products | TEAM007: AI Management Group**

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
