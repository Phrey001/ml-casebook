# Notebook Template

Use this as a shared structure for actual notebook files such as `*.ipynb` in `ml-examples/`.

The goal is consistency across projects without forcing every notebook into the exact same mold.

Intended artifact:
- Jupyter notebooks
- End-to-end notebook workflows that include data work, modeling, evaluation, and interpretation

## Recommended Core Sections

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

3. `Design Considerations`
- Key modeling and evaluation tradeoffs

4. `Data Understanding` or `Data Loading & Overview`
- What data is used
- What is excluded
- Why the chosen data is sufficient for the notebook scope

5. `Modeling`
- Baseline first
- Main model(s)
- Clear explanation of why the chosen method is appropriate

6. `Performance Summary`
- Primary evaluation metric
- Short plain-English metric explanation
- Result table or compact chart

7. `Business Interpretation`
- Translate model output into practical business meaning

8. `Examples` or `Case Walkthrough`
- Optional, when concrete examples help make predictions or recommendations easier to interpret

9. `What This Notebook Shows` / `What This Notebook Does Not Cover`
- Optional, especially useful for companion demos or lightweight framework illustrations
- Clarifies scope so supporting notebooks are not mistaken for the main business-facing workflow

10. `Key Takeaways`
- What worked
- What the result means
- What remains unresolved

11. `Limitations and Risks`
- Modeling limits
- Data limits
- Offline vs online gaps

12. `Production Considerations`
- What would need to change beyond the notebook

13. `References`
- Dataset
- Core modeling references
- Metric references when useful

## Writing Style

- Use plain language first, then technical detail where needed.
- Make the top of the notebook readable for non-technical stakeholders.
- Keep technical sections clear enough for a first-time data scientist reader.
- Prefer one primary metric unless multiple metrics are necessary for the decision.
- Explain why a baseline is included and what it means to beat it.
- Prefer concise markdown over long essays.

## Domain-Specific Additions

Add specialized sections only when they matter for the problem:

- **Churn / risk models**:
  - Decision policy
  - Threshold analysis
  - Top-K targeting

- **Recommender systems**:
  - High-level system design
  - Candidate generation vs ranking
  - Recommendation examples

- **Framework demos / companion notebooks**:
  - What the demo shows
  - What the demo does not cover
  - Explicit note that the main notebook remains the primary business-facing artifact

- **Forecasting**:
  - Forecast horizon
  - Error tradeoffs
  - Operational planning use

## Principle

Use a shared spine across notebooks, but allow problem-specific sections where they improve the story.
