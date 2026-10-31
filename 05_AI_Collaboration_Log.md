# AI Collaboration Log

**MBA ZG583 | TEAM007 - AI Management Group**

## Tools actually identified in my working material

My Word write-up identifies **Microsoft Copilot** and **Claude** among the AI tools considered or used during the work. It also identifies **RV&S (PTC Integrity), Microsoft Excel and Java** as part of the engineering and prototyping context; I am not representing these three as generative AI tools. In preparing the GitHub submission files, I additionally used **ChatGPT** to help reorganize and prepare a few supporting deliverables.


## Where AI helped and where it was useful

The main benefit was not obtaining a ready-made ASPICE answer. AI helped in coming up with guidelines to evaluate compliance to ASPICE standards, comparing alternative ways to describe the problem, organizing the backend to support the prototype implementation of deliverables, converting the concept into PRD-style requirements, and suggesting test situations that a normal checklist may overlook. It was also useful in challenging whether the proposed product was becoming too ambitious for an MVP.

The technical interpretation still needed checking. In particular, the source of each compliance criterion must be approved; a fluent explanation from a model is not the same as an applicable engineering requirement.

## Example prompts and workflow

Two example prompts recorded in my working document are:

> Convert these approved, sanitized criteria into a testable evaluation table without inventing requirements.

> Review this prototype workflow for uncertainty handling, human override, auditability, and unsafe automation.



## What AI got wrong or did not establish

AI assistance can suggest a credible-looking criterion when the actual approved criterion was never supplied. It may also assume that a reference in a record proves an activity was completed, exaggerate the level of automation, or propose attractive performance targets without any baseline measurements. These are material weaknesses for a compliance-related product.

I have therefore kept the implementation claim limited to a **rules-based, synthetic demonstrator**. The retrieval and AI classification pieces are part of the proposed architecture, not already validated features. Likewise, business savings, precision, recall and false-clear rates remain measurements for the controlled evaluation.

## Human decisions and corrections

I would not replace accountable reviewer judgment with an automated approval. The decision in this report is to narrow the first scope, preserve source and evidence traceability, route uncertainty to human reviewers, and evaluate against manual and rules-only baselines before a pilot. Those are product and risk decisions, not results obtained by asking an AI assistant to choose a launch recommendation.

## My reflection

For this assignment, AI was useful as a drafting and challenge partner, particularly when connecting a real engineering problem to formal product-management artifacts. But I found that the more important work was deciding what **not** to automate, defining how a reviewer can challenge the system, and making sure we do not present an assumption as tested evidence. The project should be judged on those decisions as much as on the demonstration screen.
