# Hillstrom Email Marketing Dataset: Data Dictionary

This case study uses the Hillstrom Email Marketing Dataset from MineThatData.

- Dataset description: [MineThatData dataset page](https://blog.minethatdata.com/2008/03/minethatdata-e-mail-analytics-and-data.html)
- Direct CSV file used in the notebook: [Hillstrom CSV](http://www.minethatdata.com/Kevin_Hillstrom_MineThatData_E-MailAnalytics_DataMiningChallenge_2008.03.20.csv)

## Dataset Overview

- The dataset contains `64,000` customers.
- Customers last purchased within the previous `12 months`.
- The dataset comes from an email marketing experiment.
- Assignment was randomized across three groups:
  - `1/3` received a men's merchandise email
  - `1/3` received a women's merchandise email
  - `1/3` received no email
- Outcomes were tracked over the `2 weeks` following the email campaign.
- The original challenge asks whether the email campaigns generated incremental visits, conversions, and spend, which is why the dataset fits this notebook well.

## Column Definitions

| Column | Meaning | Role in this case |
|---|---|---|
| `recency` | Months since the customer's last purchase | Used to describe how recently the customer bought |
| `history_segment` | Bucketed prior-year spend band | Quick summary of past customer value |
| `history` | Actual dollars spent in the prior year | Used for simple targeting splits |
| `mens` | `1/0` flag for whether the customer bought men's merchandise in the prior year | Shows past interest in men's products |
| `womens` | `1/0` flag for whether the customer bought women's merchandise in the prior year | Shows past interest in women's products |
| `zip_code` | Customer area type, categorized as urban, suburban, or rural | Customer profile detail |
| `newbie` | `1/0` flag for whether the customer is new within the past twelve months | Shows whether the customer is relatively new |
| `channel` | Channel or channel mix used in the prior year | Gives extra context on prior buying behavior |
| `segment` | Original experiment group: `Mens E-Mail`, `Womens E-Mail`, or `No E-Mail` | Used to build treatment and control groups |
| `visit` | `1/0` indicator for whether the customer visited the website in the two weeks after the campaign | Supporting outcome |
| `conversion` | `1/0` indicator for whether the customer purchased in the two weeks after the campaign | Main outcome used in the analysis |
| `spend` | Dollars spent in the two weeks after the campaign | Revenue outcome used for budget decisions |

## Notebook-Specific Derived Field

| Derived field | Meaning | Role in this case |
|---|---|---|
| `treatment` | Created from the original `segment` column for this notebook's main A/B comparison. Set to `1` for any email group (`Mens E-Mail` or `Womens E-Mail`) and `0` for the no-email control group. | Main treatment flag for the A/B comparison |
