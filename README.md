# GDP Prediction for ASEAN Member Countries

## Problem Statement
Gross Domestic Product (GDP) is a crucial indicator of a nation's economic activity. Several factors, such as Foreign Direct Investment (FDI), Human Development Index (HDI), and Portfolio Investment, can significantly impact GDP. This project aims to predict the GDP of ASEAN member countries based on these factors.

## Objective
The objective of this project is to identify the best predictive model for GDP to provide insightful recommendations that support economic growth and decision-making for ASEAN member countries.

## Dataset Information
The data is scraped from the World Bank Open Source and consists of 320 rows and 6 columns:
1. **Countries**: Categorical variable representing each country.
2. **Year**: Numerical variable representing the year.
3. **GDP**: Numerical variable representing the GDP in USD.
4. **FDI**: Numerical variable representing Foreign Direct Investment in USD.
5. **HDI**: Numerical variable representing the Human Development Index.
6. **Portfolio Investment**: Numerical variable representing Portfolio Investment in USD.

### Data Preprocessing
- Initially, the variables **Countries**, **GDP**, **FDI**, and **Portfolio Investment** were categorized as characters, but **GDP**, **FDI**, and **Portfolio Investment** were later converted to numerical types, while **Countries** remained categorical.
- **Portfolio Investment** had 78 missing values, **GDP** had 3 missing values, and **FDI** had 2 missing values. Missing values were replaced with the median.

## Exploratory Data Analysis (EDA)
<img width="530" alt="image" src="https://github.com/user-attachments/assets/21691d31-eae3-465a-92d3-b081ae28cf93">

 
Based on the heatmap above, the top 2 variables that have the highest correlation with GDP are Year and HDI.

<img width="625" alt="image" src="https://github.com/user-attachments/assets/cd8673ed-be90-40a4-9281-5dfdd517acb7">


Since the GDP data was right skewed, a log transformation was applied. The logged distribution shows that the GDP data is no longer right skewed and can be assumed to be normal, despite being slightly left skewed.

<img width="639" alt="image" src="https://github.com/user-attachments/assets/fc783a90-1c46-4cb0-ad57-71ea9d9599ca">


The QQ plot above shows that most of the observation points lie on the line, although some points deviate from it. This indicates a slight skewness, but the data remains suitable for predictive purposes.

<img width="639" alt="image" src="https://github.com/user-attachments/assets/7278a6f7-7341-425b-a1e7-7aad623ba695">


From the plot, it is observed that the scatter is randomly distributed around zero, forming a roughly horizontal band. As the spread of the residuals is approximately equal at each level of the fitted values, it can be concluded that the constant variance assumption is satisfied.


## Data Modeling
The dataset was split into training (80%) and validation (20%) sets.

Four models were developed to predict GDP:
1. **Linear Regression Model 1**: All numerical variables were used to predict GDP.
2. **Linear Regression Model 2**: Only the significant variables (Year, HDI, FDI) with p-values less than 0.05 were used.
3. **Decision Tree Model 1**: All numerical variables were used to predict GDP.
4. **Decision Tree Model 2**: The most important variables, **FDI** and **HDI**, were used.

## Discussion & Results
<img width="709" alt="image" src="https://github.com/user-attachments/assets/9cc58c0d-9e3e-424a-9bb4-62fcadb1ff53">

After evaluating the models, **Decision Tree Model 1** was found to be the best model based on:
- **RMSE (Root Mean Square Error)**: The lowest among all models.
- **R-squared**: The highest value, indicating a strong fit to the data.

The independent variables used in the decision tree include **Year**, **HDI**, **FDI**, and **Portfolio Investment**.

## Conclusion
- **Accuracy of Decision Tree Model 1**: 87%
- All numerical variables, including **Year**, **HDI**, **FDI**, and **Portfolio Investment**, play an important role in predicting the GDP of ASEAN member countries.
- The model outputs GDP values in natural logarithm form. To obtain the actual GDP values, an inverse logarithmic transformation using Euler's number (e) is required.

## Decision Tree Graph
<img width="605" alt="image" src="https://github.com/user-attachments/assets/0046d85d-03d5-4f33-8fea-c85caeb17dd8">

