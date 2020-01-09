# Caravan Insurance Challenge
Predict who would be interested in buying a caravan insurance policy

### Project Description
This project focuses on extracting knowledge from the caravan insurance data. The task is to analyse the customer data collected by the caravan insurance company and use the knowledge from the analysis to help the company implement a targeted marketing strategy.
The goal of this project is:
* Predict who would be interested in buying a caravan insurance policy
* Describe the actual or potential customers; and explain why these customers buy a caravan policy.

### Dataset
The data set was previously used in a KDD data challenge and is freely available online. It contains about 10K customer records, each of which have 86 attributes. The last attribute indicates if a customer actually bought the caravan insurance. Those features have originally been discretised. It has been split into training and testing sets. The training set contains 5822 records, and the testing set contains 4000 records.
* __TICDATA2000.txt__ : Dataset to train and validate prediction models and build a description _(5822 customer records)_. Each record consists of 86 attributes, containing socio-demographic data (attribute 1-43) and product ownership (attributes 44-86). Attribute 86,CARAVAN: Number of mobile home policies", is the target variable, indicated by \V86" in the txt file.
* __TICEVAL2000.txt__ : Dataset for predictions _(4000 customer records)_. It has the same format as TICDATA2000.txt, only the target is missing. All datasets are in tab delimited format. The meaning of the attributes and attribute values can be found in the data dictionary.
* __TICTGTS2000.txt__ : Targets for the evaluation set.
#### [Data Dictionary](http://liacs.leidenuniv.nl/~puttenpwhvander/library/cc2000/data.html)

### Findings and Model Comparison
#### PREDICTION COMPARISON SUMMARY
* __Prediction 1 (Logistic Regression with 27 variables taken from forward step)__
Overall Accuracy: 0.795
Probability threshold / boundary: 0.092
Total number of predicted customers: 800
Number of Correctly predicted (True Positive - predict 1 ; true 1): 109
Number of Incorrectly predicted (False Positive - predict 1 ; true 0): 691
Sensitivity: 0.45798
* __Prediction 2 (Logistic Regression with 20 variables taken from forward step)__
Overall Accuracy: 0.797
Probability threshold / boundary: 0.0906
Total number of predicted customers: 800
Number of Correctly predicted (True Positive - predict 1 ; true 1): 113
Number of Incorrectly predicted (False Positive - predict 1 ; true 0): 687
Sensitivity: 0.47479
* __Prediction 3 (Lasso Regression with 57 variables from excluding multicollinearity and including high response variable correlation)__
Overall Accuracy: 0.7972
Probability threshold / boundary: 0.0889
Total number of predicted customers: 799
Number of Correctly predicted (True Positive - predict 1 ; true 1): 113
Number of Incorrectly predicted (False Positive - predict 1 ; true 0): 686
Sensitivity: 0.47479
* __Prediction 4 (Ridge Regression with 27 variables taken from forward step)__
Overall Accuracy: 0.7932
Probability threshold / boundary: 0.0865
Total number of predicted customers: 799
Number of Correctly predicted (True Positive - predict 1 ; true 1): 105
Number of Incorrectly predicted (False Positive - predict 1 ; true 0): 694
Sensitivity: 0.44118
#### Findings
In general, we want a prediction that has as high probability threshold as possible, with high number of correctly predicted, which resulted in higher sensitivity. From the prediction summary of 4 tested types of model types, Prediction 4 using Ridge Regression had the lowest Overall Accuracy, Probability Threshold, as well as the number of correctly predicted. Thus, this prediction does not have a good result.

The second lowest prediction is Prediction 1 which used Logistic Regression using 27 variables taken from forward step feature selection. Although the probability threshold of this model is the highest compared to the others, it only gave 109 correctly predicted customers out of 800. This means there was a trade off of a higher probability to get 800 customers, but fewer people who got correctly predicted. And in general we wanted to pump up this number.

Prediction 2 using Logistic regression using 20 variables taken from lowest Cp Error in forward step and Prediction 3 using Lasso Regression are NECK AND NECK. They were both had the same overall accuracy of 0.7972, they had the same correctly predicted 113 customers out of roughly 800 customers, and following that they both had the same sensitivity rate. The only difference is the probability threshold between them. The Prediction 3 of Lasso only had 0.0889 chance that the predicted number of customers were correct. Meanwhile, Prediction 2 of Logistic Regression had a higher chance with 0.0906 that the prediction was correct. To put it into perspective, people would prefer 9.1% chance of getting the prediction correct rather than only 8.9%.

### By comparing these 4 predictions, Prediction 2 come up as the winner compared to the other 3.
