# Churn Prediction Problem Framing

## Business Context
- Churn prediction helps retention teams focus limited budget on customers most likely to leave.
- Retention is often cheaper than acquisition, so better targeting can protect recurring revenue.

## Dataset Context
- Use the IBM Telco Customer Churn dataset as a representative example of customer account, service, billing, and churn outcome data.

## Problem & Goal
- Predict which customers are at the highest risk of churn.
- Improve retention decisions by helping teams prioritize outreach and match interventions to likely risk drivers.

## Decision
- Decide which customers should be contacted first when retention budget or campaign capacity is limited.

## Hypothesis
- If customers are ranked by churn risk, the business should be able to capture a meaningful share of likely churners within a relatively small outreach segment.
- Example: if the retention team can contact 20% of customers, a well-performing model should capture a majority of churners within this segment.

## Metric & Validation
- Evaluate the model mainly as a ranking tool, not just a yes/no classifier.
- Use ROC-AUC to assess overall ranking quality.
- Use Top-K evaluation to measure how many churners are captured within target segments such as the top 10% or 20%.
- Use a train-test split so evaluation reflects out-of-sample performance.

## Approach
- Logistic Regression baseline
- XGBoost comparison model
- Start with a simple, interpretable baseline first; only prefer a more complex model if it clearly improves ranking quality or business usefulness.

## Key Trade-Offs
- **Ranking vs classification**: the main business use is prioritization, so ranking quality matters more than a binary label alone.
- **Interpretability vs complexity**: simpler models are easier to explain and operationalize, while more complex models may improve performance but add maintenance cost.
- **Risk vs value**: churn risk alone is useful, but production decisions should also consider customer value and intervention cost.
- **Offline vs business impact**: good offline metrics are helpful, but the real test is whether targeted outreach improves retention outcomes.
- **Limitation**: without intervention-response data, the model can rank risk but cannot directly recommend the best retention action.

## How the System Works
- Offline training learns a churn risk model from historical customer data.
- Periodically retrain the model to reflect changes in customer behavior.
- Scoring assigns each customer a churn probability.
- Ranking orders customers from highest risk to lowest risk.
- Campaign selection chooses the top segment based on capacity and budget.
- Business rules can further prioritize high-risk, high-value customers.

`Customer data -> risk scoring -> rank customers -> select top segment -> run retention outreach`

## Recommendation
- Adopt a ranking-first retention workflow:
  - rank customers by predicted churn risk
  - target the top X-Y% segment based on campaign capacity
  - prioritize high-risk and high-value customers
- This aligns model evaluation directly with business action and helps maximize retention impact under budget constraints.

## Appendix - Glossary
- **Top-K targeting**: contacting only the highest-risk segment, such as the top 10% or 20% of customers.
- **Ranking metric**: a metric that checks whether the riskiest customers appear near the top of the list.
- **Threshold**: a cutoff used to convert a predicted probability into a yes/no action rule.
- **Churn probability**: the model’s estimated likelihood that a customer will leave.
