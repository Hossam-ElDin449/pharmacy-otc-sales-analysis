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
- Branch(es) **[BR-05/06/07]** show a disproportionate share of Antiseptic Cream sales, confirming the category-branch concentration hypothesis.
- Revenue-per-capita ranking **[differs / does not differ]** meaningfully from raw revenue ranking — branch **[X]** looks strong on raw totals but weaker once adjusted for local population.
- Correlation between median income and branch revenue: **[coefficient]** — [interpretation, noting the small sample size of 7 branches].
- Sales rep workload is **[even / concentrated]** across branches and categories.
- Monthly revenue trend shows **[pattern]**; note that a portion of this dataset uses randomly generated dates, so any "seasonality" here is descriptive, not a confirmed real-world pattern.
- Payment method **[does / does not]** show a meaningful difference in average order value.

---

## 📌 About This Project

This is a self-directed practice project simulating a real freelance analytics engagement, built to develop and demonstrate Power BI, Power Query, Python, and DAX skills for healthcare-adjacent business analytics work.

**Author:** Hossam ElDin — Clinical Pharmacist & Healthcare Data Analyst
