# Predicting HDB Resale Prices in Singapore: A Linear Regression Approach

A statistical analysis project exploring how physical attributes and locational factors drive HDB flat resale prices in Singapore. Built and compared five progressively refined linear regression models, arriving at a final model with an **Adjusted R² of 0.8162** on 11,527 transactions.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Repository Structure](#repository-structure)
- [License](#license)

---

## Overview

This project models HDB flat resale prices using data from January to July 2021. Starting from a baseline OLS model, five iterations of feature engineering and transformation were evaluated using ANOVA, residual diagnostics, Cook's Distance, and GVIF (multicollinearity checks), converging on a log-log model as the best fit.

---

## Dataset

- **Source:** [data.gov.sg — HDB Resale Flat Prices](https://data.gov.sg/dataset/resale-flat-prices)
- **Records:** 11,527 transactions (January – July 2021)
- **Key variables:** `resale_price`, `town`, `flat_type`, `floor_area_sqm`, `storey_range`, `lease_commence_date`, `remaining_lease`

> The raw data file (`hdb-resale-Jan-Jun2021.csv`) is not committed to this repo. Download directly from data.gov.sg and place it in the project root before running the analysis.

---

## Methodology

### Feature Engineering
- **Regional grouping:** 26 towns consolidated into 5 geographical regions (Central, East, North, North-East, West)
- **Flat type grouping:** 7 flat types merged into 2 categories (Small-Medium, Large) based on ANOVA significance
- **Storey binning:** Continuous storey midpoints converted to 4 ordinal levels (Low, Mid, High, Very High)
- **Transformations:** Log-transformation of `resale_price` and `floor_area_sqm` to address skewness and improve linearity

### Model Progression

| Model | Description | Adj. R² |
|-------|-------------|---------|
| M0 | Baseline — all raw predictors | — |
| M1 | Flat type grouped into Small / Medium / Large | — |
| M2 | Flat type simplified to Small-Medium / Large | — |
| M3 | Storey modelled with power transformation (^1.34) | — |
| M4 | Storey binned into 4 ordinal levels | — |
| **M5** | **Log(floor area) + ordinal storey — final model** | **0.8162** |

### Diagnostics
Each model was assessed using: QQ plots, Residuals vs Fitted plots, Cook's Distance (influential points), and GVIF (variance inflation factors).

---

## Key Findings

- **Floor area:** A 1% increase in floor area corresponds to a ~0.88% increase in resale price (near-unit elasticity)
- **Location premium:** Central region commands the highest prices; North region flats sell at approximately −0.381 on the log scale compared to Central
- **High-floor effect:** "Very High" floors (>20th storey) carry a +0.260 log-scale premium
- **Lease decay:** Later lease commencement dates consistently fetch higher prices, reflecting market sensitivity to the remaining 99-year lease

---

## Prerequisites

- **R** (≥ 4.0)
- **RStudio** (recommended for knitting the R Markdown file)
- Required packages:

```r
install.packages(c("dplyr", "stringr", "car"))
```

---

## Usage

1. Download the HDB resale data from [data.gov.sg](https://data.gov.sg/dataset/resale-flat-prices) and save it as `hdb-resale-Jan-Jun2021.csv` in the project root.
2. Open `HDB_Resale_Price_Analysis.Rmd` in RStudio.
3. Click **Knit** to run the full analysis and generate the PDF report, or run individual chunks interactively.

---

## Repository Structure

```
Predicting-HDB-Resale-Prices/
├── HDB_Resale_Price_Analysis.Rmd      # Full analysis: EDA, model building, diagnostics
├── HDB_Resale_Analysis_Report_Part1.pdf   # Written report — Part 1
├── HDB_Resale_Analysis_Report_Part2.pdf   # Written report — Part 2
├── .gitignore
├── LICENSE
└── README.md
```

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

**Author:** Jay Tai Kin Heng
