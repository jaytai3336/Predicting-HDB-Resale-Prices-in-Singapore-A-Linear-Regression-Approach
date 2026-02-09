Overview

This project aims to develop an optimal linear regression model to predict the resale prices of Housing and Development Board (HDB) flats in Singapore. Using a dataset of 11,527 resale transactions from January to July 2021, the study explores how various factors like location, size, and lease duration influence property values.



Key Features

Exploratory Data Analysis (EDA): Detailed visualization of price distributions and correlations with predictors such as region and flat type.



Data Preprocessing: Implementation of log-transformations for the response variable (resale price) and floor area to stabilize variance and improve linearity.


Feature Engineering: Conversion of categorical "Storey Range" into numerical midpoints and grouping of towns into five major regions (Central, East, North, North-East, and West).


Statistical Modeling: Development of multiple linear regression models, culminating in a final model (M5) with an Adjusted R-squared of 0.8162.


Key Insights

Floor Area: This is the strongest positive predictor; a 1% increase in floor area is associated with an approximately 0.88% rise in resale price.

Location: Flats in the Central region command the highest premiums compared to other regions.

Floor Height: There is a clear price gradient where buyers pay more for higher floors, with "Very High" floors enjoying a 0.260 premium on the log scale.

Flat Age: Newer flats (later lease commencement dates) consistently command higher resale values.


Technologies Used

R (Linear Modeling and ANOVA) 


ggplot2 (for EDA and residual analysis) 


Statistical Tests (Multicollinearity checks via GVIF, Normality via QQ plots)
