# Module 12 Report Template

## Overview of the Analysis

This analysis was performed to evaluate a model that can identify the creditworthiness of borrowers for a lending service company.

The data provided for each credit included the loan size, interest rate charged and the borrower income. It also provides the total debt, number of accounts and debt to income ratio of the borrower that asked for each credit. 

Using this variables we aim to predict the safety of the new loans given by the company. 

Analyzing the database we find a consistent set of data. We didn't find missing data in the sample nor inconsistency in datatypes. However the proportion of the healthy against the high risk credits is quite big. This is: 785036 of a total of  77,536 (97% of the sample) are healthy credits, fact that can affect the results of the model.

As a first step we split the dataset into training and testing subsamples, using the standard propotion of 75% being the training credits. We also shuffled the sample as the credits were ordered by class in the original file.

After running a first model using a logistic regression  it was evident the model misplaced a big proportion (around 10%) of the testing 'bad credits' due to imbalances in classes. Thus, even though the model throws an accuracy of 95%, the precision and recall for bad credits is low, considering we are talking about lending money.

As a results the next step was resampling the training set using the Over Sampler method to try to equilibrate classes. Once this was done we proceed to run another logistic regression

Over sampling is a method that allows repetition of the sample data. In special, as this dataset is biased towards 'good' credits, the sample allows the 'bad' ones have a better chance to appear and helps calibrate the model to a better one. 

## Results
Below you will find the results of the two model applied. The first one using the raw data and the second considering over sampling.

* Machine Learning Model 1:
  * Description of Model 1: Logistic Regression, normal sampling, stratified.
  Model overall accuracy .9520
   Precision for group 0 (healthy credits) =1.00, group 1 (risky credits) = 0.85
   Recall score for group 0 = 0.85, group 1 = 0.91

This model underestimate risky credits and tend to assign a 'good rating' to a big proportion opf them. That situation can lead to possible losses for the lender. 

* Machine Learning Model 2:
  * Description of Model 2:  Logistic Regression, over sampling (sampling with replacements).
Model overall accuracy .9937
   Precision for group 0 = 0.99, group 1 = 0.99
   Recall score for group 0 = 0.84, group 1 = 0.99

While the model doesnt improve the precision of risky credits it is less susceptible to assign a 'good' rating to them, thus making this model a better one for the lender. 
## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Model 2 performs better overall, with it we expect to have a high accuracy in determining good credits while haveing a decent performance rejecting credits that won't be worthy.
* In the case of this company it is important to really lend money to those borrowers that have a high chance to pay. While it is important not to reject credits that can lead to revenues it is more important to avoid unnecesary risks. Thus Model 2 delivers better performance and, while it doesn't surpress the risk, it diminishes it as the number of 'bad credits' that are asigned as 'good ones' is a small percentage.   
