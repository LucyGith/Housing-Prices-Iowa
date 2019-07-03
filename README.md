# Housing-Prices-Iowa
Exploring data set and find a good model of housing prices based on house characteristics.

This project is a subject of data exploration and modeling by analyzing a given dataset and running multiple regressions using machine learning. The goal is to build a predictive model of housing prices in Ames, Iowa. 
The house price dataset was from one of the Kaggle competitions “House Prices: Advanced Regression Techniques” and was compiled by Dean De Cock. 

<h2> Data Preparation, and Exploration </h2>
The original dataset included 81 variables, 43 categorical and 38 numerical. There were five variables with more than 50% of missing data which were decided to be removed. 

Then, the house sale price was defined as the target variable. Due to the right skewness of the price distribution, applying the Natural Log (LN) on sales price was more appropriate to be used as the target variable for the regression.

<h2>  Data Wrangling </h2>
First, the percentage of NAs among the 38 categorical variables remained and the 38 numerical variables were examined. For categorical variables, the NAs were replaced by “none” and for numerical variables, the missing data were filled with the average value of the existing data.

Second, the skewness and kurtosis of the numerical variables were analyzed. Two variables “GrLivArea” and “LotArea” with significant skewness and kurtosis were normalized in order to improve the results of the regression model.

Third, the unrealistic observations with lower SalePrice_Log than 12.3 and higher GrLivArea_Log value than 8.3 were defined as outliers and removed accordingly.

After removing the outliers, the correlation between the target variable and the independent variables were explored using heatmap. The variables with stronger correlation, larger than a threshold value of 0.4 to the target variable SalePrice_Log, were selected. The variables with a correlation below 0.4 were dropped in the subsequent part.

Last but not least, the independent variables with multicollinearity relationship were identified and cleaned.

The final list of independent variables used for the modeling was: 
“OverallQual”, “GrLivArea”, “NbHd_num”, “GarageCars”, “ExtQ_num”, “KiQ_num”, “BsQ_num”, “TotalBsmtSF”, “FullBath”, “YearBuilt”, “YearRemodAdd”, “Fireplaces”, “MasVnrArea”, “MSZ_num”.

<h2>  Modeling </h2>
By using Scikit-learn, six models were built to predict the housing prices: 
<ul>
<li> Linear Regression </li>
<li> Ridge </li>
<li> Lasso </li>
<li> ElasticNet </li>
<li> Decision Tree Regressor </li>
<li> Random Forest Regressor </li>
</ul>

After building the models and running the cross-validation for each model, their performance was compared by calculating the Root-Mean-Squared-Error (RMSE). The Linear Regression model had a slightly better result compared to the other five models with an RMSE value at about 0.135 and 0.1515 and, therefore, was chosen for the final model. 
