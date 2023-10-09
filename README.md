# credit-risk-classification
UniSA_bootcamp_Module20_Challenge


# Module 12 Report Template

## Overview of the Analysis

This analysis applied logistic regression modelling to examine a number of parameters of potential loan risk as documented in the lending_data.csv file. These parameters included variables such as loan size, interest rate,  loan_size, borrower income, debt to income ratio, number of accounts, derogatory marks and total debt. These variables were modelled against the binary outcome variable of loan status. Loan status being indicated as either healthy (status=0), or unhealthy (status=1).

From a banking institution's perspective, correctly identifying loans as either healthy or unhealthy (ie. high risk) is critical to risk management. 

There are two elements to this risk analysis. Firstly, the bank needs to correctly identify if a loan is healthy via its prediction model. If in fact the loan is unhealthy, but the prediction model predicts it as being healthy then this places the bank at risk since there will be loans in the system that seem 'safe' from the institution's perspective, but are in reality placing the institution at risk.

The second element of this analysis is to accurately identify these risky loans (unhealthy), using the prediction models it is more important to the bank that they correctly identify all actual unhealthy loans as these are the risk. This means that the model must correctly predict unhealthy loans that are actually unhealthy, even if this is at the expense of some false positive calls, where a loan predicted to be unhealthy actually turns out to be healthy. This situation is a much 'safer' one than the converse, whereby unhealthy loans are missed because they are predicted to be healthy.

This analysis uses the Scikit-learn logistic regression method to train a model allowing testing of data against that model. Typically the model is trained on 70% of the dataset, with the remaining 30% used to test the model.


## Results

The logistic regression model yielded the following results:

                           precision    recall  f1-score   support

  loan status 0 (healthy)       1.00      1.00      1.00     18759
loan status 1 (unhealthy)       0.87      0.89      0.88       625

                 accuracy                           0.99     19384
                macro avg       0.94      0.94      0.94     19384
             weighted avg       0.99      0.99      0.99     19384



## Summary

The logistic regression model predicts with 100% precision, all loans that are predicted to be healthy and that are actually healthy. This is the precision. Importantly, the recall for these loans (healthy) is also 100% which indicates that of loans that are actually healthy, all of them are predicted to be so. 

For unhealthy loans (status 1), precision and recall are reduced. The precision of 0.87 indicates that for all loans predicted to be unhealthy, 87% of them will be correct (i.e. unhealthy), however this also means that a proportion of the loans detected as unhealthy will actually be false positives, and therefore although detected as 'unhealthy' those false positives will actually mean those loans are 'healthy'.

My interpretation of this result is that the bank wants to 'overcall' it. That is, they are prepared to identify a proportion of false positives in the unhealthy loan group (ie. loans predicted as unhealthy, that are actually healthy) as this means that the pick up unhealthy loans is higher. Of note is the higher prediction and recall for healthy loans that indicates if the loan is predicted as 'healthy' it is extremely unlikely that it is in fact 'unhealthy' (and wrongly reassuringly identified as healthy by the model), as this would be a dangerous situation for the bank to be in (ie. unrecognised high risk loans present).

From the banking institution's perspective, the model has several benefits. Firstly, loans that are predicted to be healthy are virtually always actually healthy, meaning that very few if any loans that are actually unhealthy are missed as being predicted healthy (these are high risk unknowns). Secondly, the model picks up most if not all unhealthy loans, at the expense of 'overcalling' a small proportion of (actually) healthy loans that are incorrectly identified as unhealthy (false positives). This is of little consequence to the bank, as it is the unhealthy loans - particularly those that are not predicted but actually present, that represent the highest risk. The model appears to perform to minimise that risk.