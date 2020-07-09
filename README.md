# Modeling_Car_Sales
## Introduction
I set out to build a model that could forecast the sales of a vehicle based upon its features.  This would help automakers to solve the business problem of producing automobiles that consumers want in order to drive sales in the competitive car industry.  I scraped my auto feature data from Consumer Reports, while I obtained monthly model level sales data in csv form from Automotive News.  I merged the 2 data sets together, dropped models months with incomplete sales data and filled in missing datapoints based on the context.  I modeled the data with Decision Tree Regression, Random Forest Regression, and Support Vector Machine Regression.  All 3 models outperformed the baseline model considerably, with Random Forest Regression performing best on my chosen metrics of RMSE, with a Testing score of 2,724.

## Obtain Data
I scraped around 80 features from Consumer Reports for approximately 200 models per year from the 2010-2020 model years.  I only scraped models for which most or all of the important features were available.  I obtained 120 months of model-level unit sales data per year from 2010-2019 in CSV form from Automotive News.  Merging independent variable feature data from Consumer Reports with depedent variable sales data from Automotive News yielded my final data set.

## Scrub Data
I went through several steps to scrub my data into a usable format.  First, I dropped model months with sales of less than 500 as these predominantly represented sales for discontinued models or other incomplete data.  I filled in missing values with either the feature mean, feature minimum value or otherwise based on what was appropriate in the context.  I dropped features with sparse data that would not be usable in my final modeling.  I mapped 
text data into quantitative values when necessary to make it useable in regression modeling.  Finally, I updated the data types for all of my features into a quantitative data type.

## Explore Data
My principal objective in EDA was to determine the descriptive statistics of the monthly model sales data in order to better contextualize my subsequent model RMSEs.  The monthly sales data had high dispersion with a standard deviation of 5,611, compared to a mean of 6,990.  There were also a large number of outliers above the upper whisker of my Box Plot, compared to no outliers below the bottom whisker of my box plot.

## Model Data
I used RMSE as my principle evaluation metric in order to measure the difference between my model predictions and the actual values, while disproportionately punishing large prediction misses.  I used an 80/20 Train Test Split to validate my models.  My baseline model was a Dummy Regressor using a mean strategy, which produced a Testing RMSE of 5,095.  I next ran a GridsearchCV Decision Tree Regressor, which significantly improved the Testing RMSE to 3,100.  I improved upon my Decision Tree model by running a more computationally complex Random Forest Model, which improved my Testing RMSE to 2,744.  Finally, I ran an SVM Regressor model using GridsearchCV, which produced a Testing RMSE of 2,897.  At this point, my 3 models had produced similar RMSE scores, which led me to believe that I had reached the point of diminishing returns on running additional models without increasingly computation complexity considerably, which I did not have time for.

## Interperate Results
The Decision Tree Regressor was my best performing model with a Testing RMSE of 2,897, a testing MAE of 1,534 and an R-Squared of .83, which significantly outperformed my Baseline Model's performance of 5,095, 3,547 and .41 respectively.  Because my model significantly outperformed the Baseline Model and my RMSE performed well relative to the Monthly Sales Mean(6,991) and Standard Deviation(6,699), I believe I was succesful in my modeling objective of predicting an auto model's sales based on it's features.  The three models that I ran performed relatively similarly, which led me to believe that my Decision Tree Regressor results reached the point of diminishing marginal returns on model performance without significantly increasing model complexity and computational resources required.  Although it was not part of my modeling objective, I pulled the feature importances from my Decision Tree Model.  The two most important features were both comfort based with space and performance also being important predictors of sales with 7 and 5 features respectively in the top 20 most important.  Interestingly, Reliability was not included in the top 20 most important features.

## Next steps
I would like to train a neural network, which I believe has a strong potential to outperform my existing models.  I would also like to engage in feature engineering in order to reduce the number of features in my model and make the feature importance results more interpretable.  Finally, I would like to continue updating my model with new model years and sales data as they become available.

# Github Files
[Scrape.ipynb](https://github.com/blantj/Modeling_Car_Sales/blob/master/Scrape.ipynb) :  Consumer Reports Scrape

[Final_Modeling.ipynb](https://github.com/blantj/Modeling_Car_Sales/blob/master/Final_Modeling.ipynb) :  OSEMN Data Science Process

[Modeling Car Sales_v2.pptx](https://github.com/blantj/Modeling_Car_Sales/blob/master/Modeling%20Car%20Sales_v2.pptx) :  Project Presentation

# Sources
Consumer Reports: https://www.consumerreports.org/

Auto News: https://www.autonews.com/

# Reproduction Instructions
Please contact Jesse Blant (https://www.linkedin.com/in/jesse-blant-372a523a/) for reproduction permission.
