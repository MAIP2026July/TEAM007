# Executive Summary

**Project:** AI-Enhanced ASPICE Compliance Checker  
**Course:** MBA ZG583 - Management of AI Products  
**Team:** TEAM007: AI Management Group  
**Prepared by:** Mayur H. Borate (2025MB26174)  
**Industry:** Automotive software development  
**Decision requested:** Approval to validate a narrow prototype and, if the evidence supports it, run a controlled pilot.

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
