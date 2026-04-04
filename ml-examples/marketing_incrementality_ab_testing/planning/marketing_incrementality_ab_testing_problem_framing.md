# A/B Testing for Marketing Incrementality & Budget Allocation

## Executive Summary
- **Problem:** Marketing teams need to know whether a campaign creates incremental conversions and revenue, or just takes credit for behavior that would have happened anyway.
- **Why it matters:** If incrementality is weak, scaling spend wastes budget and inflates reported ROI.
- **Approach:** Use the Hillstrom Email Marketing Dataset as a randomized experiment with treatment and control groups, then compare causal lift against a naive attribution view.
- **Decision lens:** Should the business keep spending on this campaign, scale it, or hold back budget?

## Business Context
- Growth teams need a reliable way to decide whether email spend is productive or wasteful.
- Reported conversions alone are not enough because some customers would have purchased without the campaign.
- The core business question is not "who converted?" It is "what did the campaign actually cause?"
- This directly affects marketing ROI, budget efficiency, rollout decisions, and targeting strategy.

## Dataset Context
- Use the Hillstrom Email Marketing Dataset from MineThatData as a representative retail marketing experiment.
- The dataset contains randomized assignment across `Mens E-Mail`, `Womens E-Mail`, and `No E-Mail`, which makes it suitable for causal lift measurement.
- Observed outcomes include `visit`, `conversion`, and `spend`, while customer attributes such as `recency`, `history`, and `channel` support segment-level interpretation.
- In the main notebook analysis, the two email arms are combined into a single `email` treatment and compared against the `no email` control group.

## Objective
- Estimate the **incremental lift** from sending a marketing email versus holding out a control group.
- Use the randomized treatment assignment in the dataset to frame the analysis as an A/B test rather than a correlation study.
- Translate lift into practical budget questions.
- Does the campaign generate enough incremental value to justify cost?
- Is the average effect strong enough for full rollout?
- Are there segments where the campaign is more attractive?
- What happens financially if the business scales from a small send volume to a much larger campaign?

## Experiment Design
| Element | Choice | Why it matters |
|---|---|---|
| Treatment | Customers who received any marketing email | Measures the effect of sending email at all |
| Control | Customers who received no email | Provides the causal baseline |
| Assignment | Randomized by design | Makes treatment-control comparisons credible |
| Primary outcome | `conversion` | Closest link to business value |
| Supporting outcomes | `visit`, `spend` | Adds behavioral and revenue context |
| Customer features | `recency`, `history`, `channel`, others | Useful for segment-level interpretation |

## Key Metrics
| Metric | Definition | Business use |
|---|---|---|
| Conversion Rate (`CVR`) | Share of users who convert in each group | Simplest read on whether the campaign changes behavior |
| Incremental Lift | `CVR_treatment - CVR_control` | Estimates the causal gain from sending the email |
| Relative Lift | `(CVR_treatment / CVR_control) - 1` | Makes effect size easier to communicate |
| Revenue per User | Average `spend` per user by group | Connects lift to budget allocation |
| Break-Even Cost per Send | Incremental revenue per treated user before value turns negative | Gives a direct spending threshold |
| Scaling Scenario Net Value | Projected incremental revenue minus projected campaign cost at different send volumes | Tests whether economics hold as budget expands |

## Attribution vs Incrementality
- **Naive attribution:** tends to credit all treated conversions to marketing exposure.
- **Why that is biased:** some treated users would have converted anyway.
- **Why incrementality is better:** a randomized holdout estimates the counterfactual baseline directly.
- **Attribution-style view:** treated users generated conversions.
- **Incrementality view:** only the lift above control is caused by the campaign.
- This is the right framing for ads, user acquisition, and growth science roles where causal measurement matters more than descriptive reporting.

## Unit Economics and Decision
| Question | Decision rule | Action |
|---|---|---|
| Roll out? | Lift must be positive and commercially meaningful | Roll out only if the holdout-based effect is clearly valuable |
| Scale budget? | `incremental revenue per user > cost per send` | Scale only while unit economics stay positive |
| How much can we pay? | Use break-even cost per send as the ceiling | Compare actual delivery cost or cost per send against this threshold |
| What happens at scale? | Test `100k`, `500k`, and `1M` send scenarios | Check whether projected net value remains positive |
| Who should be targeted first? | Rank segments by incremental value per user | Prioritize the highest-value groups first |

## Recommendation
- **Default recommendation format:** `Roll out`, `Scale selectively`, or `Hold`.
- **Likely readout:** `Scale selectively` if average incrementality is positive, break-even cost per send is above the assumed delivery cost, and some segments show clearly stronger value.
- **Executive takeaway:** use the holdout-based lift as the source of truth, scale only while unit economics remain positive, and prioritize the highest-value segments first.

## Limitations
- **Channel scope:** The dataset reflects an email experiment, not a full ads auction, bidding, or multi-touch attribution environment.
- **Outcome definition as evaluation:** `Spend` captures revenue, not profit, so ROI interpretation still needs cost and margin assumptions.
- **Segment confidence:** Segment-level patterns in the notebook are directional because subgroup analysis is lower power than the primary A/B test.
- **Linear scaling economics assumption:** The scaling view uses a simple linear assumption, so economics may look different in production.

## Production Considerations
- **Periodic re-measurement:** Keep a holdout or periodic experiment in place so the business can monitor whether true campaign impact remains stable over time.
- **Economics validation:** Validate cost and margin assumptions before scaling, since the notebook uses revenue and an illustrative cost-per-send input rather than full contribution profit.
- **Monitoring:** Track lift, revenue per user, and net value by segment so budget can be reallocated if performance drifts.
- **Operationalization:** If this work is operationalized, the output should feed a simple send policy: who to target, how much to spend, and when to pause or re-test.

## Potential Extensions
- **Experiment design:** Move from one binary treatment-control comparison to a fuller multi-arm experiment across mens email, womens email, and control.
- **Targeting & modeling:** Replace the simple segment-level policy with a user-level uplift model if targeting becomes the main product question.
- **Richer segmentation:** Add more customer features beyond historical spend if the business wants a more refined targeting policy.
- **Profit lens:** Extend the economics from revenue to profit or contribution margin if margin data becomes available.

## Key Takeaways
- A/B testing is the core measurement tool because it reveals incremental impact.
- Incrementality, not raw attributed conversions, should guide marketing budget decisions.
- The strongest business signal is not just whether the campaign "works," but whether it works enough to justify spend and what the break-even cost threshold is.
- A useful growth memo should also show how results scale financially as budget increases, not only whether the average treatment effect is positive.
- Heterogeneous response matters: even when average lift is positive, better targeting can improve efficiency.
- A stronger growth-facing deliverable ends with a targeting policy, not just a segmentation chart.

## References
- Hillstrom Email Marketing Dataset, MineThatData
- The companion notebook in this folder downloads and prepares the dataset programmatically
