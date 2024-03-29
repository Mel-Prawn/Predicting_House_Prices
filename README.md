# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Predicting housing prices with Regression

# Overview
Purchasing a house is a big decision for both investors and those looking for a place to stay. One of the key considerations behind this decision is the price of the property is reasonable.

**Goal**
To build an accurate model to predict the expected sale price of a house in Ames. The key metric used will be root mean squared error.

---

## Methods

#### Background Research
Several known factors which affect housing prices are available in our dataset (e.g. location, home size, age, condition). These variables will be used to form our base model.

#### Datasets
The Ames Housing dataset was used. This dataset contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, Iowa from 2006 to 2010.

This version of the dataset includes 2051 observations with 82 features.

#### Data Processing
Missing data was converted to appropriate scores or categories. All features were checked to be within the prescribed range, or having the correct categories according to the data dictionary. Features were transformed where appropriate (e.g. ordinal to continuous scale, log transformations). Datapoints that were extreme outliers were dropped.

#### Analysis
Summary statistics for all variables were computed. Data distributions were visualised using  histograms. Relationships between the predictors and house sale prices were assed via scatterplots and correlations

Linear Regression and regularisation techniques(Lasso, Ridge and ElasticNet) were used to build a home saleprice prediction model. Accuracy of the model was determined through cross validation, mean squared error (mse) and root mean squared error (rmse) scores. Models with a lower mse and rmse are more accurate. Model building was performed in a step-wise process where poor features were first dropped before adding new features.

---

## Key findings

| Model    | Variables included                       | Ridge(cvs) | Lasso(cvs) | Ridge        | Lasso        |
|:---------|------------------------------------------|------------|------------|--------------|--------------|
|          |                                          | train data | train data | holdout data | holdout data |
| Model 1  | Base features supported by research      | 26980      | 27431      | 28580        | 28541        |
| Model 2  | All other numeric features + Model 1     | 25972      | 25906      | 22878        | 23196        |
| Model 3  | All other categorical features + Model 2 | 21239      | 21272      | 24347        | 24015        |
| Model 3I | Model 3 minus poor performing features   | 22867      | 22848      | 24022        | 23897        |
| Model 4  | Model 3I plus select polynomial features | 18592      | 18739      | 19948        | 19477        |
| Model 4I | Model 4 minus poor performing features   | 17470      | 17691      | 21202        | 20758        |

cvs = cross validated score<br/>
all scores are root mean square errors


The above models were built and the corresponding root mean square errors are displayed. In general, subsequent models are better than their predeccessors and there is little evidence of overfitting for each model. 

---

## Conclusion and recommendations
The models above will be able to predict the saleprice of houses to reasonable accuracy. We would reccomend users to use Model 4I using enet regression to predict sale prices as it has the best accuracy.

If future staff need to develop other models for a price prediction model in other neighborhoods with little time or resources, it is reccomended to start with variables similar to that in the base model (Model 1). This will require the least number of variables for a reasonable model.
