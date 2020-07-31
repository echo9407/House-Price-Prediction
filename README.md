## House Price Prediction Project 

### 1. Introduction 

How to determine home value has been a common problem for every household. Knowing how to calculate your home’s value with the help of online valuation tools and trained professionals better prepares you to buy, sell, refinance or even negotiate lower property taxes.

There are some methods that have been used to predict house price: online valuation tools including automated valuation model with a confidence score; comparative market analysis by local real estate agent; FHFA House Price Index Calculator by Federal Housing Financing Agency; and a professional appraiser to evaluate the market, the property and comparable properties. It is important for households to know your house value, which allows you to evaluate what you can afford, determine whether a listing is priced appropriately and decide how to price your own home.

The objective of this project is to utilize data visualization, feature selection and feature engineering, and machine learning models to predict house prices. Additionally, it is aimed to minimize the difference between predicted and actual rating (RMSE /MSE) The house price prediction dataset contains 79 explanatory variables describing the majority aspects of residential homes in Ames, Iowa, and 1460 observations in training data while the testing data consists of 1459 observations.


### 2. Hypotheses 

**Hypotheses: What variables are highly relevant to determine the sales price?** To be more specific, whether the following features including LotArea, Neighborhood, OverallQual, Full Bath, YearBuilt, TotalBsmtSF, CentralAir, GrLivArea, GarageArea, will be able to predict the outcome, the housing price.


### 3. Data Processing and Exploration (more in [project report] (https://github.com/echo9407/House-Price-Prediction/blob/master/Machine%20Learning%20Final%20Report.pdf)

The training dataset has 1460 observations and 81 variables, and 1459 observations and 80 variables are in the test dataset. In order to get a better understanding and comprehensiveness of the dataset, I decided to first see the top 10 variables that have a high correlation with the SalePrice.

