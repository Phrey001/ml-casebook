# Recommender System Case Thinking

## Business Context
- Recommender systems help users discover relevant content faster, which can improve engagement and retention in large catalogs.

## Dataset Context
- Use the MovieLens 100k dataset as a representative example of user-item interactions with ratings and timestamps.

## Problem & Goal
- Recommend items a user is likely to interact with based on historical behavior.
- Improve discovery and engagement by reducing the effort required for users to find relevant content.
- Ultimately, improvements in `Recall@K` should translate into stronger engagement metrics such as click-through rate or watch time.

## Decision
- Decide which items should be shown first under limited screen space so the most relevant options appear near the top of the list for each user.

## Hypothesis
- Personalization based on historical interaction patterns should surface more relevant items than a non-personalized popularity baseline.

## Metric & Validation
- `Recall@K` measures whether the held-out future item appears in the top-K recommendations.
- Example: if we recommend the top 10 items, a strong model should capture a meaningful share of future interactions in that list, indicating that relevant items are consistently surfaced early.
- For demo simplicity, use a single train-test split rather than a separate train-validation-test workflow.
- Use a time-aware holdout so evaluation reflects future behavior rather than random shuffling.
- Train only on interactions that happened before the held-out event. This avoids temporal leakage, but it also leaves less data available for fitting the model.

## Approach
- Popularity baseline
- Collaborative filtering with SVD
- Score recommendations with the dot product between user and item embeddings so the model can reflect both similarity and preference strength
- Deep learning retrieval and ranking models such as two-tower systems
- Start with a popularity baseline first; only adopt a more complex model if it shows clear lift.

## Key Trade-Offs
- **Popularity baseline**: simple and robust, but not personalized.
- **SVD**: learns latent user and item factors, works on sparse interaction data, and is a strong interpretable baseline, but is mostly static and offline.
- **Dot product vs cosine similarity**: dot product keeps magnitude, so it can represent how strongly a user prefers an item. Cosine similarity keeps direction only, which is less useful when ranking by preference strength.
- **Deep models**: more scalable and expressive, but more complex to train, serve, and monitor.
- **Cold start**: remains a key limitation without additional user or item features.
- **Offline vs online**: offline `Recall@K` is useful, but the real business test is whether recommendations improve engagement in production.

## How the System Works
- The notebook itself uses a simpler single-stage scoring setup. The flow below reflects how this use case would typically scale in production.
- Offline training learns user and item representations.
- Monitor model performance and retrain periodically as user behavior evolves.
- Candidate generation narrows the search space to likely items.
- Ranking scores that smaller set more precisely.
- Re-ranking can optionally adjust for diversity, freshness, or business rules.
- Serving returns the final Top-K recommendations.

`User -> candidate generation -> ranking -> Top-K recommendations`

## Recommendation
- Adopt a staged recommender approach:
  - start with a popularity baseline to establish a floor
  - validate that personalization such as SVD delivers measurable lift in `Recall@K`
  - scale toward multi-stage retrieval and ranking only if justified by clear gains
- This ensures model complexity grows only when it improves user experience and business outcomes.

## Appendix - Glossary
- **Collaborative filtering**: recommending items based on patterns across many users' past interactions.
- **Candidate generation**: narrowing a large catalog to a smaller set of likely items.
- **Ranking**: scoring that smaller set more precisely to decide final order.
- **Re-ranking**: adjusting the ranked list for additional goals such as diversity, freshness, or business rules.
- **Cold start**: the difficulty of recommending well for new users or new items with little historical data.
