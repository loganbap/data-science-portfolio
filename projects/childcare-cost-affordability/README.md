# Childcare Cost & Affordability Analysis

> Translating county-level childcare price data into actionable policy insights through clear visual storytelling.

---

## Overview

Childcare is one of the largest household expenses facing American families, yet conversations about affordability often conflate *price* with *burden* — two distinct concepts that tell very different stories depending on where you live. This project analyzes county-level childcare prices and affordability across all 50 U.S. states, challenges the assumption that the most expensive counties are always the least affordable, and models the impact of a hypothetical federal childcare subsidy.

Findings were translated into a suite of policy-facing deliverables including an executive summary, an infographic, and social-media-ready visuals — designed to be understood by decision-makers and the general public alike.

---

## Data

| Dataset | Records | Key Fields |
|---------|---------|------------|
| National Database of Childcare Prices – Pricing | 3,108 county records | County, state, care type, annual price |
| National Database of Childcare Prices – Burden | 3,186 county records | County, state, burden (% of family income) |

**Source:** U.S. Department of Labor Women's Bureau – National Database of Childcare Prices (NDCP)

Key variables used:
- `mcsa` / `mfcca` — median annual cost for center-based and family care
- `burden` — annual childcare cost as a percentage of median family income
- `mhi` — median household income by county
- Geographic identifiers: county FIPS code, state

---

## Methods

### 1. Exploratory Data Analysis
- Profiled missing values and data distributions across all pricing and burden variables.
- Mapped county-level price and burden side-by-side to surface discrepancies between the two metrics.

### 2. Statistical Analysis
- Computed Pearson correlation between:
  - Annual childcare price and burden: **r = 0.70** (moderate-to-strong positive)
  - Median family income and burden: **r = −0.16** (weak negative)
- This revealed that income alone is a poor predictor of burden — high-income counties can still carry extreme childcare burdens.

### 3. Subsidy Scenario Modeling
- Modeled the effect of a hypothetical **$2,000 annual federal childcare subsidy** on the highest-burden counties.
- Estimated post-subsidy burden levels to illustrate policy impact at the county level.

### 4. Visual Communication
- Executive summary: 1-page brief summarizing key findings and recommendations.
- Infographic: Single-page visual narrative contrasting price and burden maps.
- Social media visuals: Shareable graphics designed for general audiences.

---

## Key Results

- **Price ≠ Burden:** Several counties with the highest absolute childcare prices ranked mid-tier in burden because of high local incomes — and vice versa. This distinction is critical for policy targeting.
- **Correlation (price vs burden):** r = 0.70 — price is a useful but imperfect proxy for burden.
- **Correlation (income vs burden):** r = −0.16 — income explains very little of the variation in burden once geography is accounted for.
- **Subsidy impact:** A $2,000 annual subsidy would meaningfully reduce burden in the highest-burden counties, lowering some counties from above 30% of income to below 25%.
- **Geographic patterns:** Rural counties in certain states showed disproportionately high burden despite moderate absolute prices, pointing to a supply-side (childcare availability) problem as much as a price problem.

---

## Deliverables

| Deliverable | Description |
|------------|-------------|
| Executive Summary | 1-page policy brief with findings and recommendations |
| Infographic | Visual contrast of price vs. burden maps with callout statistics |
| Social Media Graphics | Shareable panels for general audience communication |
| Analysis Report | Full methodology, correlation results, and subsidy model |

---

## How to Reproduce

1. Download the National Database of Childcare Prices from the [U.S. DOL Women's Bureau](https://www.dol.gov/agencies/wb/topics/childcare/ndcp).
2. Load the pricing and burden CSV files into your preferred environment (Python/pandas or R recommended).
3. Merge on county FIPS code.
4. Run correlation analysis between price, burden, and median household income.
5. Apply the subsidy adjustment (`burden_adjusted = (price - 2000) / mhi`) to model subsidy scenarios.
6. Produce county-level choropleth maps using GeoPandas, Plotly, or Tableau.

**Recommended environment:** Python 3.9+, pandas, matplotlib/seaborn, GeoPandas or Tableau Public.

---

## Repository Structure

```
childcare-cost-affordability/
├── README.md                   # This file
├── data/                       # Raw NDCP CSV files (not included; see link above)
├── analysis/
│   └── childcare_analysis.ipynb # Main analysis notebook
├── visuals/
│   ├── infographic.pdf
│   ├── social_media_panels/
│   └── price_vs_burden_maps/
└── deliverables/
    ├── executive_summary.pdf
    └── full_report.pdf
```

---

## Future Work

- Expand the subsidy model to test multiple subsidy tiers ($1,000 / $2,000 / $5,000) and visualize the distributional impact.
- Incorporate childcare provider density data to disentangle price effects from availability effects.
- Build an interactive Tableau or Plotly Dash dashboard so policymakers can explore county-level data directly.
- Longitudinal analysis: repeat the burden calculation across multiple NDCP release years to track trends.

---

*Part of the [Data Science Portfolio](https://github.com/loganbap/data-science-portfolio) | Analysis and visualization project focused on public policy and data storytelling.*
