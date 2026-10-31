# Course Case Connection

**MBA ZG583 | TEAM007 - AI Management Group**

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
