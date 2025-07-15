
# Credit Risk Dashboard

### Dashboard Link : <iframe title="Ara" width="1140" height="541.25" src="https://app.powerbi.com/reportEmbed?reportId=2f08670f-339a-498f-9834-1b1935feec1e&autoAuth=true&ctid=ae3f47d1-dd89-43b1-a9b5-f7aadd7b81af&actionBarEnabled=true" frameborder="0" allowFullScreen="true"></iframe>

## Problem Statement

This dashboard helps lenders and credit‐risk managers understand their retail loan portfolio.  It highlights overall exposure, default rates, and the key demographic or behavioural variables that drive risk.  By monitoring these indicators the business can tighten underwriting standards, adjust pricing, and proactively manage collections.  

The **overall default rate is almost 50 %**.  Half of all loans are therefore either on the brink of, or already in, default – an urgent call for action.  The interactive views enable users to drill into purpose, age, employment and account status to uncover the root causes of poor performance.

---

## Steps Followed  
*(all actions were performed in **Power BI Desktop May 2025**)*

| # | Action | Tool / Ribbon | Notes |
|---|--------|--------------|-------|
|1|Load `Credit_dataset.csv` | **Home → Get data → Text/CSV** | Rename table to  in the Navigator. |
|2|Initial data profiling | **Transform Data → View → Column quality / Column distribution** | Switch profiling to *Entire dataset*. |
|3|Group _Status of existing checking account_ | **Add Column → Conditional column** | Four buckets: **High Balance, Low Balance, Overdrawn, No Account**. |
|4|Group _Credit history_ | Conditional column | **Good / Delayed / Critical** categories. |
|5|Consolidate _Purpose_ | Conditional column | Eight business-friendly buckets (Vehicle, Electronics, Home, Education, Business, Personal, Other, Uncategorized). |
|6|Bin _Age in years_ | Conditional column → **Age Group** | Bands: 18-25 / 26-35 / 36-45 / 46-55 / 56-65 / 66+. |
|7|Bin _Duration in months_ | Conditional column → **Duration Group** | Short ≤ 12, Medium ≤ 24, Long ≤ 36, Very Long > 36. |
|8|Convert _Present employment since_ | Two columns  | **Employment Years** (numeric midpoint) & **Employment Band**. |
|9|Group _Savings account/bonds_ | Conditional column → **Savings Band** | None / Low / Medium / High / Very High. |
|10|Binary flag _Other debtors / guarantors_ | Conditional column | **With Support / None**. |
|11|Split _Personal status and sex_ | **Split Column → By Delimiter (space)** | Creates **Gender** + **Marital Status**. |
|12|Create Date table (optional) | **Modeling → New table** | Enables time intelligence if disbursement dates are available. |
|13|Create DAX Measures | **Modeling → New measure** | `Default Rate`, `Total Loans`, `Avg Credit Amount`, `High Risk Loans`, `DTI Ratio`, `Loan Size`, etc. |
|14|Design *Dashboard 1 – Credit Overview* | Cards / Donut / Bar / Column charts | KPIs, Purpose mix, Loan durations, Age distribution. |
|15|Design *Dashboard 2 – Risk Analysis* | Cards / Bar / Column / Stacked bar / Matrix | Default-rate heat-map vs Age, Purpose, Checking-account & Employment. |
|16|Publish to Power BI Service | **Home → Publish** | Copy the web link into the README (above). |
|17|Capture screenshots | **Snipping Tool** or `File → Export → PDF` | Save to `/images/` folder in the repo (filenames used below). |

---

## Folder Structure

```text
├─ Credit_dataset.csv          ← original data (anonymised)
├─ PowerBI PBIX/               ← .pbix source file
├─ images/
│  ├─ overview-dashboard.png   ← Dashboard 1 screenshot
│  └─ risk-dashboard.png       ← Dashboard 2 screenshot
└─ README.md                   ← *this* document
```

> **Tip:** keep the raw CSV under version control only if the licence permits redistribution.  Otherwise publish an excerpt or mock data.

---

## Snapshots of the Final Report

<p align="center">
  <img src="images/overview-dashboard.png" width="700" alt="Credit Overview Dashboard">
</p>

<p align="center">
  <img src="images/risk-dashboard.png" width="700" alt="Risk Analysis Dashboard">
</p>

---

## Key Insights

* **Default Rate** is 49 %.  Loans to applicants with *Overdrawn* accounts default 15 pp more often than those with *High Balance* accounts.
* *Vehicle* and *Personal* purpose loans account for **22 %** of volume but **29 %** of bad debt.
* Borrowers aged **26-35** have the highest default frequency, challenging the assumption that younger cohorts are riskier.
* **Employment Band** shows a monotonic relationship with risk – _Unemployed_ applicants default at 72 %, while _Very Long tenure_ is below 35 %.

---

## How to Reproduce

1. **Clone** the repository.
2. Open **powerbi-credit-risk.pbix** in Power BI Desktop.
3. If the file prompts for the data source, browse to `Credit_dataset.csv`.
4. Refresh, then explore the three report pages.
5. Publish to your own workspace, copy the URL, and replace the placeholder at the top of this README.

---

## Contributing

Pull requests are welcome!  Please open an issue first to discuss major changes.
