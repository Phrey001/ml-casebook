# Case Thinking Template

Use this for a short strategy or decision memo that does not include notebook implementation details.

This is for pure-thinking work: problem structuring, decision logic, trade-offs, and recommendation without being tied to a specific notebook.

Intended artifact:
- Standalone memo-style documents
- Pure problem-structuring or case-thinking notes that are not notebook companions

## Suggested Sections

1. `Business Context`
- Why the problem matters
- What business outcome is being improved

2. `Dataset Context` (optional)
- What dataset or data source is being used as the working example
- Why it is representative enough for the problem

3. `Problem & Goal`
- What the system is trying to do
- What “good” looks like
- How better model performance should connect to a product or business outcome

4. `Decision`
- What decision the model or system supports
- What operational constraint shapes that decision, such as screen space, budget, or campaign capacity

5. `Hypothesis`
- What you expect to be true and why
- Include one concrete anchor when useful, such as what a strong result would look like in practice

6. `Metric & Validation`
- Main metric
- How to validate it credibly
- One line connecting the offline metric to the business outcome it is meant to support

7. `Approach`
- Baseline
- Main modeling options
- Why to start simple

8. `Key Trade-Offs`
- Simplicity vs complexity
- Offline vs online
- Accuracy vs operational constraints

9. `How the System Works`
- High-level flow only
- Candidate generation, ranking, re-ranking if relevant
- Monitoring or retraining if that matters for the system

10. `Recommendation`
- What to do first
- What to do next if results are promising
- Phrase this as a decision, not just a summary

11. `Glossary` (optional)
- Only for domain-specific terms that would otherwise slow readers down

## Style Guidance

- Keep it concise and highly scannable.
- Prefer bullets over long paragraphs.
- Make section names readable for non-technical stakeholders.
- Keep enough technical specificity to signal sound ML judgment.
- Prefer a decision-oriented tone over a purely descriptive tone.
