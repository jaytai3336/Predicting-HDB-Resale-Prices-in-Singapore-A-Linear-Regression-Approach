# HDB Resale Price Prediction: A Linear Regression Analysis

## 📌 Project Overview
This project aims to develop an optimal linear regression model to predict the resale prices of Housing and Development Board (HDB) flats in Singapore. Based on a dataset of **11,527 resale transactions** recorded between January and July 2021, the study explores how physical attributes and locational factors influence property valuation.

## 📊 Dataset Summary
- **Size:** 11,527 records
- **Timeframe:** January 2021 – July 2021
- **Response Variable:** `resale_price` (Log-transformed for the final model to stabilize variance).
- **Key Predictors:** Region, Flat Type, Floor Area (sqm), Storey Range, and Lease Commence Date.

## 🛠️ Methodology

### 1. Data Preprocessing & Feature Engineering
- **Regional Grouping:** Towns were grouped into five geographical regions: *Central, East, North, North-East, and West* to simplify the model and capture locational premiums.
- **Storey Midpoints:** Categorical storey ranges were converted into numerical midpoints and later binned into four ordinal levels: *Low, Mid, High, and Very High*.
- **Transformations:** - Log-transformation of `resale_price` to address right-skewness.
    - Log-transformation of `floor_area_sqm` to improve linearity.

### 2. Model Development
Five models were evaluated, with the final model (**M5**) being selected for its balance of simplicity and predictive power.
- **Model Confidence:** The final model achieved an **Adjusted R-squared of 0.8162**, explaining ~81.6% of the price variation.

## 📈 Key Insights
- **Size Matters:** A 1% increase in floor area corresponds to an approximately **0.88% increase** in resale price.
- **Location Premium:** Flats in the **Central region** command the highest prices. Compared to the Central region, flats in the North region sell at a significant discount (approx. -0.381 on the log scale).
- **The "High Floor" Effect:** There is a clear gradient where higher floors yield higher prices. "Very High" floors enjoy a **0.260 premium** over the baseline.
- **Lease Decay:** Newer flats (later lease commencement) consistently fetch higher prices, reflecting market sensitivity to the remaining 99-year lease.

## 💻 Technologies Used
- **R Programming**: Core statistical analysis and linear modeling.
- **ggplot2**: For Exploratory Data Analysis (EDA) and residual diagnostics.
- **Statistical Tests**: ANOVA for model comparison and GVIF for multicollinearity checks.

## 📂 Repository Structure
- `ST3131_Assignment.pdf`: The complete formal report.
- `analysis.R`: R script containing data cleaning, visualization, and modeling code.
- `data/`: (If applicable) The dataset containing 11,527 HDB records.

---
**Author:** Jay Tai Kin Heng  
**Course:** ST3131 - Principle of Statistics
