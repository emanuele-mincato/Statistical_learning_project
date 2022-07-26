# Statistical_learning_project
The purpose of this work is to learn how to use R, RMarkdown and the most famous statistical methodologies to solve real problems.
## INTRODUCTION

The goal of this project is to check if a person (potential customer) will take a coupon or not. To do so, we relied on a dataset that includes details about the destination, the number of people in the car, the weather, the temperature, and other useful information that helps us know the problem and predict better the results.
We analyzed and found out how these variables interact with each other, which helped us predict if a new customer will take the coupon or not. In order to answer the question mentioned, we tried many models such as Lasso, Ridge and Elastic Net, which are explain better in the RMarkdown file, finally we have chosen the best one to solve our problem.

## Dataset
This data was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. For more information about the dataset, please refer to the paper: Wang, Tong, Cynthia Rudin, Finale Doshi-Velez, Yimin Liu, Erica Klampfl, and Perry MacNeille. 'A bayesian framework for learning rule sets for interpretable classification.' The Journal of Machine Learning Research 18, no. 1 (2017): 2357-2393. 

## Clean and filter data
Our main goal was getting the best out of the data we had. The better the data, the more efficient the analysis. So, we first focused on getting high-quality data. To do so, we followed many steps as follows:

-	Converting variables into factors: 
Before starting with MICE, we converted the variables to factors. This is more practical in statistical modelling, graphics and memory storing.

-	Categories Combination:
Some variables had many categories, some of which were useless. For this reason, we decided to reduce them, in a way that does not affect the results. 

- Checking for missing values: 
Missing values were an obstacle for our analysis. In order to estimate them in the best possible way and to avoid a bad influence of this estimation on our forecasting process, we have chosen the R 'MICE' package.


## MICE
MICE stands for Multivariate Imputation via Chained Equations. It predicts missing values an it assumes that they are missing at random (MAR). It creates multiple imputations comparing it to one. Every variable is specified a model which makes the prediction in a variable-by-variable way. In our case, and since our variables are factors, we chose “polyreg” for all our variables’ missing values. MICE function takes the following arguments:

•	Corresponding dataset’s 

•	m: number of imputed datasets

•	maxit: number of iterations taken to impute missing values.

•	methods used in imputation for each variable that has missing values.

We were able to reach a certain level of accuracy with MICE prediction and a zero number of missing values.

## Conclusion
To conclude, our best model for predicting whether the driver will take the coupon or not between Ridge, Lasso and Elastic Net was the Lasso architecture with lambda 0.00049 and accuracy 68% on test data.
Either with or without eliminating half of the variables, and with or without some preprocessing steps, the model gave almost similar accuracies. Therefore, 15 variables were eliminated as they did not affect our results. Results were also compared with SVM. Our best model was still Lasso.
In order to get the best out of our model, we set a treshold of 0.65 (Standard Treshold: 0.5) that was able to decrease the error among the ones who will accept the coupon (False Negative) despite increasing a little the overall error rate. It also increased the False Positive rate, but this was not our main concern, as we were more interested in how to decrease the False Negative.
