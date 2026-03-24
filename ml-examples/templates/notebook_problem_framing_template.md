# Notebook Problem Framing Template

Use this for standalone `*_problem_framing.md` documents that accompany notebook-based ML examples.

This template matches framing notes such as `recommender_problem_framing.md` and `churn_problem_framing.md`: business-facing, implementation-aware, and closely aligned to a notebook, but not the notebook itself.

Intended artifact:
- Standalone `*_problem_framing.md` files
- Companion framing documents for notebook-based ML examples

## Suggested Sections

1. `Executive Summary`
- Problem
- Why it matters
- Approach
- Key Result
- Key Insight

2. `Problem Framing`
- Business question
- Decision framing
- Why it matters
- Success criteria
- Business metric bridge, such as how offline model quality should connect to product outcomes

3. `Design Considerations`
- Key modeling and evaluation trade-offs
- Explicit constraints such as screen space, budget, latency, or interpretability where relevant

4. `High-Level System Design` (when relevant)
- Offline vs online flow
- Candidate generation vs ranking
- Optional re-ranking stage
- Serving constraints

5. `Data Understanding`, `Dataset Context`, or `Data Loading & Overview`
- What data is used
- What is excluded
- Why the scope is sufficient

6. `Modeling`
- Baseline
- Main model
- Why the main model is appropriate

7. `Validation Strategy`
- Split logic
- Leakage prevention
- Why the evaluation setup is credible

8. `Performance Summary`
- Main metric
- Plain-English metric explanation
- Formula when it materially improves clarity
- One concrete interpretation anchor for what a strong result means
- Result table or compact chart

9. `Business Interpretation`
- What the result means in practice

10. `Examples` or `Walkthrough`
- Optional user-level or case-level examples when they help connect the framing to the notebook

11. `Key Takeaways`
- What worked
- What remains limited
- What matters next

12. `Limitations and Risks`
- Modeling limits
- Data limits
- Offline vs online gaps

13. `Production Considerations`
- How this would scale beyond the notebook
- Monitoring and retraining expectations where relevant

14. `References`
- Dataset
- Modeling references
- Metric references when useful

15. `Appendix - Glossary` (optional)
- Use only when a few technical terms need clarification
- Keep it short and supplemental rather than central to the memo

## Style Guidance

- Keep the document readable for non-technical stakeholders.
- Keep the technical content rigorous enough for data scientists.
- Keep the framing closely aligned to the notebook’s actual modeling and evaluation choices.
- Favor one strong metric over many weakly motivated metrics.
- Make recommendations and conclusions decision-oriented rather than purely descriptive.
- If a glossary is included, position it as `Appendix - Glossary` rather than a main section.
