## House Price Prediction Project 

### 1. Introduction 

How to determine home value has been a common problem for every household. Knowing how to calculate your home’s value with the help of online valuation tools and trained professionals better prepares you to buy, sell, refinance or even negotiate lower property taxes.

There are some methods that have been used to predict house price: online valuation tools including automated valuation model with a confidence score; comparative market analysis by local real estate agent; FHFA House Price Index Calculator by Federal Housing Financing Agency; and a professional appraiser to evaluate the market, the property and comparable properties. It is important for households to know your house value, which allows you to evaluate what you can afford, determine whether a listing is priced appropriately and decide how to price your own home.

The objective of this project is to utilize data visualization, feature selection and feature engineering, and machine learning models to predict house prices. Additionally, it is aimed to minimize the difference between predicted and actual rating (RMSE /MSE) The house price prediction dataset contains 79 explanatory variables describing the majority aspects of residential homes in Ames, Iowa, and 1460 observations in training data while the testing data consists of 1459 observations.

---
### 2. Hypotheses 

**Hypotheses: What variables are highly relevant to determine the sales price?** To be more specific, whether the following features including LotArea, Neighborhood, OverallQual, Full Bath, YearBuilt, TotalBsmtSF, CentralAir, GrLivArea, GarageArea, will be able to predict the outcome, the housing price.

---
### 3. Data Processing and Exploration (more information and graphs are in the final report) 
The training dataset has 1460 observations and 81 variables, and 1459 observations and 80 variables are in the test dataset. In order to get a better understanding and comprehensiveness of the dataset, I decided to first see the top 10 variables that have a high correlation with the SalePrice.

From analysis, we can see that there are 10 out of 38 variables with a positive correlation of at least 0.5 with SalePrice. It also shows the multicollinearity issue which we will discuss in the limitation part. If we think about these variables, we can conclude that they give almost the same information so we only need to choose one of them as key variables.

The scatter plot confirms my opinion.GrLivArea, TotalBsmtSF, TotRmsAbvGrd, and GarageArea are positively correlated with SalePrice, which means that as one variable increases, the other also increases. In the case of 'TotalBsmtSF', we can see that the slope of the linear relationship is particularly high, and it makes sense that big houses are generally more expensive.

One of the figures we may find interesting is the one between 'TotalBsmtSF' and 'GrLiveArea'. In this figure, we can see the dots drawing a linear line, which almost acts like a border. It totally makes sense that the majority of the dots stay below that line. Basement areas can be equal to the above-ground living area, but it is not expected a basement area bigger than the above-ground living area.

In addition, I take an extra look at OverallQual since it has the highest correlation rate with SalePrice.

To summarize, I decide to use 8 key variables to predict the models: OverallQual, GrLivArea, TotalBsmtSF, TotRmsAbvGrd, GarageArea, FullBath, YearBuilt, YearRemodAdd.

The next step is checking missing data. Many real-world data-sets may contain missing values for various reasons. They are often encoded as NaNs, blanks or any other placeholders. Training a model with a data-set that has a lot of missing values can drastically impact the machine learning model’s quality.

We'll consider that when more than 15% of the data is missing, we should delete the corresponding variable and pretend it never existed. This means that we will not try any trick to fill the missing data in these cases. According to this, none of these variables seems to be very important since most of them are not aspects in which we think about when buying a house (maybe that's the reason why data is missing?). Moreover, looking closer at the variables, we could say that variables like 'PoolQC', 'MiscFeature' and 'FireplaceQu' are strong candidates for outliers, so we'll be happy to delete them. In addition, there are no NA values in my selected variables, I skipped the part of handling Null Values. However, it brings some major issue that I will discuss in the limitation part.


---
### 4. Modeling

SalePrice is our target variable and also the dependent variable for prediction. Before building models to predict the outcome, SalePrice, there is a need to analyze the outcome itself.

As we can see, the sale prices are right-skewed, this was expected because few people can afford highly expensive houses.

In data normalization, I split the training, test, and validation data.

Once the data is processed we will now proceed further to make our machine learning model. Next step would be the feature selection detailed in section c, and building models, including linear regression model, random forest model, and neural network model.

**Linear Regression Model:**

As our target variable is continuous we will fit a regression model to the dataset. The aim of this model is to minimize the sum of the squared residuals. Here I select 8 variables to fit into this model: OverallQual , GrLivArea , TotalBsmtSF , TotRmsAbvGrd , GarageArea , FullBath , YearBuilt , YearRemodAdd. I first find outliers and remove them in the dataset. Then I divide datasets into three parts -- training, test, and validation, to prepare for prediction later. Then I ran the model to calculate the RMSE. The RMSE for test data is the best result comparing to the other two.

**Random Forest Model:**

**Neural Network Model:**

Variable used: OverallQual , GrLivArea , TotalBsmtSF , TotRmsAbvGrd , GarageArea , FullBath , YearBuilt , YearRemodAdd.

---
### 5. Consideration of feature Selection, transformations, or feature engineering steps

As we discussed above, the distribution of 'SalePrice' is right-skewed which is positive. We would like to get the skewness factor as close to zero as possible. This can be accomplished by either removing outliers or transforming the variable. Removing outliers may be tricky as expertise in real estate is needed to assess whether outliers should be removed or not. Applying transformations is typically a safer option if it can deliver the desired outcome. In the case of positive skewness, log transformation does the trick.

In addition, I use forward stepwise feature selection so that after each step in which a variable was added, all candidate variables in the model are checked to see if their significance has been reduced below the tolerance level. If a nonsignificant variable is found, it is removed from the model.

---
### 6. Results
All three models result in very high RMSE score. Large RMSE indicates that there is a need to include more variables instead of only 8 out of 80 to reduce the RMSE. On the other hand, it indicates that all variables I select are essential for house price prediction. The overall material and finish of the house, original construction date, remodel date, total square feet of basement area, above grade living area square feet, full bathrooms above grade, total rooms above grade and size of a garage in square feet are the most important features when purchasing a house. It solves the problem that people get lost when considering all aspects of a house, which provides a clear and statistical proven range on aspects that really matters for house price.

For the linear regression model, the Adjusted R-squared value is 0.7983, meaning adjusts the R-squared based on the number of independent variables in the model.

For random forest model and neural network, validation data has the smallest RMSE, indicating there is no overfitting problem.

---
### 7. Limitations

**Variable Selection:**
The number of variables I selected is small, although they are highly correlated with the outcome, it is not comprehensive and fully representative and there are lots more correlated variables I failed to analyze.

**Handling missing value:**
For time-saving and convenience consideration, I got rid of the observations that have missing data. However, I risk losing data points with valuable information. There are some important and correlated variables with missing values such as BsmtQual,BsmtCond, and GarageQual. The results would be more accurate if I filled in median numbers in NA values or impute them by proceeding sequentially through features with missing values.

**Multicollinearity:**
The corrplot above shows the multicollinearity issue. For instance, the correlation between GarageCars and GarageArea is very high at 0.89, and both have similar correlations with SalePrice. Same with TotRmsAbvGrd and GrLivArea, TotalBsmtSF and X1stFlrSF. These cases show how significant the correlation is between these variables, this correlation is so strong that it can indicate a situation of multicollinearity. 

**Outliners:**
Outliers is also something that we should be aware of, because outliers can markedly affect our models and can be a valuable source of information, providing us insights about specific behaviours. Outliers is a complex subject and it deserves more attention. However, due to the limit of time and energy, I failed to analyze the outliers through the standard deviation of SalePrice. If time is generous, I would like to do som univariate analysis and bivariate analysis.

**Variable transformation:**
There are some numerical variables that are really categorical such as OverallCond, YrSold and MoSold. I can also do some label encoding to some categorical variable that may contain information in their ordering sets, such as ExterQual, PoolQC, and CentralAir.
