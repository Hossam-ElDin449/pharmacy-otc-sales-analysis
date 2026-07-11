# OTC Pharmacy Multi-Branch Sales Analysis
**Simulated freelance analytics project — EDA & Power BI Dashboard**

A simulated Upwork engagement for a fictional client, *Meridian Health Retail Group*, a 7-branch OTC pharmacy chain. The project combines a 2022 sales dataset with branch-level demographic data (population, median income, nearby healthcare centers) to answer real business questions a pharmacy retail operator would actually ask: which branches are outperforming for their market size, where dermatology/topical demand concentrates, and how pricing and payment behavior vary across locations.

> ⚠️ **Note on data:** The dataset is synthetic, built for practice purposes. Sales figures, branch demographics, and client details are simulated — this is a portfolio project, not real client work.

---

## 🎯 Business Questions Answered

This project was scoped around a simulated client brief (see [`docs/upwork_simulated_brief.md`](docs/upwork_simulated_brief.md)). The core questions:

1. Do dermatology/topical products (creams) disproportionately sell at specific branches?
2. Are high-population branches actually underperforming relative to their market size?
3. Is there a relationship between a branch's local median income and its revenue?
4. Are sales reps unevenly distributed across branches/categories?
5. How does revenue move month-to-month — is there seasonality?
6. Does payment method (cash/card/insurance) affect basket size or category mix?
7. Which category is the strongest revenue driver, and which underperforms?

---

## 🛠️ Tools & Skills Used

| Stage | Tool |
|---|---|
| Data cleaning & merge | Power Query (M) |
| Exploratory analysis | Python (pandas, matplotlib/seaborn) |
| Statistical checks | Python (scipy — correlation, chi-square) |
| Dashboard & measures | Power BI Desktop (DAX) |
| Version control / portfolio | GitHub |

---

## 📁 Repository Structure

```
├── data/                     # Raw and cleaned/merged datasets
├── power_query/              # Documented M-code / cleaning & merge steps
├── notebooks/                 # Python EDA notebook
├── powerbi/                   # .pbix dashboard file
├── screenshots/                # Dashboard page images (shown below)
└── docs/
    ├── upwork_simulated_brief.md   # The simulated client brief that scoped this project
    └── findings_summary.md          # Full written findings (1-2 pages)
```

---

## 🧹 Data Preparation

- Merged raw OTC sales transactions (2022, 3,000 rows, 7 branches) with a branch demographics table (population, median income, healthcare center count) on `Branch ID`.
- Documented cleaning logic in Power Query (type conversions, join validation, no post-merge duplication).

---

## 📊 Key Measures Built

```DAX
Price Per Unit = 
DIVIDE(SUM('Sales'[Amount ($)]), SUM('Sales'[Boxes Shipped]), 0)

Revenue per Capita = 
DIVIDE(SUM('Sales'[Amount ($)]), SELECTEDVALUE('BranchDemographics'[Population]), 0)

Revenue per Healthcare Center = 
DIVIDE(SUM('Sales'[Amount ($)]), SELECTEDVALUE('BranchDemographics'[Total Healthcare Centers]), 0)
```

---

## 🖥️ Dashboard Preview

<!-- Replace these with your actual screenshots once exported -->
| Overview | Branch Performance |
|---|---|
| Category Analysis | Recommendations|
|---|---|


🎥 **Video walkthrough:** [Link to Loom/YouTube recording] *(add once recorded)*

---

## 🔍 Key Findings

<!-- Replace placeholders below with your actual results once your EDA/dashboard is finalized -->
📌 Key Findings
1. Raw revenue hides true branch performance
 Westfield ($71K) and Northside ($68K) lead in raw sales, but neither tops the per-capita or per-healthcare-center rankings. Eastgate Pharmacy ($2.40 revenue/capita, $11K+ revenue/healthcare center) and Skinhealth Pharmacy ($2.20/capita, $8K/healthcare center) are the true efficiency leaders — they extract far more value per resident and per competing healthcare facility despite smaller raw totals.
2. Westfield is underperforming for its market size
 Westfield serves the largest population (96,000) but ranks near the bottom on revenue-per-capita ($0.70). This suggests untapped demand rather than a saturated market.
3. Category mix is fairly balanced, with Digestive Enzyme leading
 Categories range narrowly from 12.4%–16.4% of revenue, with Digestive Enzyme (16.4%) as the top performer and Allergy Pills (12.4%) the lowest. As designed, Antiseptic Cream sales concentrate heavily at Dermacare, Skinhealth, and MedTopical — confirming these branches' dermatology-focused customer base.
4. Higher local income does not predict higher sales
 The income-vs-revenue scatter shows a downward trend — branches in higher-income areas (e.g., Skinhealth in Gold Coast, $121K median income) don't necessarily out-sell branches in lower-income areas. Caveat: this is based on only 7 branches, so treat it as directional, not statistically confirmed.
5. Sales rep performance is evenly distributed
 Top reps (Ethan Ross, Olivia Grant, Grace Mitchell, Sophia Brooks) cluster within a $3-4K revenue band of each other, with average order values all in the $132–$145 range. No single rep is over- or under-utilized.
6. No confirmed seasonality in 2022 revenue
 Monthly trends across categories fluctuate without a consistent recurring pattern. This may reflect genuine demand variability, but part of the underlying dataset was generated with randomized dates, so any apparent "seasonality" should not be treated as a confirmed real-world pattern.
---
✅ Recommendations
1. Reallocate marketing/inventory investment toward Eastgate and Skinhealth — their high per-capita and per-healthcare-center efficiency suggests room to scale without market saturation risk.
2. Investigate Westfield's underperformance — audit local competition, product awareness, and pricing fit for its lower-income demographic ($39,400 median income) before assuming the market is simply weak.
3. Maintain current dermatology-focused inventory strategy at Dermacare/Skinhealth/MedTopical — the Antiseptic Cream concentration validates the branch specialization approach.
4. Treat the income-revenue relationship as a hypothesis, not a conclusion — expand analysis with a larger branch sample or transaction-level income data before adjusting strategy based on this alone.
5. No immediate sales rep reassignment needed — performance is balanced; continue monitoring quarterly rather than reacting to this single snapshot.
6. Collect real transaction timestamps in future data to properly test for seasonal demand (e.g., cold/flu season stocking) — this year's data isn't reliable for that decision yet.



## 📌 About This Project

This is a self-directed practice project simulating a real freelance analytics engagement, built to develop and demonstrate Power BI, Power Query, Python, and DAX skills for healthcare-adjacent business analytics work.

**Author:** Hossam ElDin — Clinical Pharmacist & Healthcare Data Analyst
