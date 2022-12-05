# Module 12 Report - Using Supervised Learning to Predict Healthy VS High-Risk Loans

## Analysis Overview

Machine learning is a powerful tool that may be leveraged to analyse large sets of data to make accurate predictions. Especially in instances where volumes of data become considerable and the analyses required complex; training, testing and finally deploying machine learning algorithms can vastly expedite the process. In the domain of banking, analysing the creditworthiness of a borrower to make predictions regarding their risk profile using machine learning can achieve great success, and crutial as customer volumes become too large for human workers to keep up.

### Purpose
The purpose of this analysis is to the analyse a dataset of potential borrowers which is innately imbalanced, due to the fact that individuals that would be legible for healthy loans will typically outnumber the number of individuals who would otherwise be unworthy, and generate a supervised learning algorithm that is able to predict whether a potential borrower would have a healthy or high risk loan. Imbalances in datasets can create challenges in the form of biases during data processing, and so over or under sampling techniques are required to mitigate the effects of these differing data sizes.

### Available Financial Information
The available data on each of the borrowers that was used to analyse, build and predict a supervised learning algorithm included sch metrics as:
* Loan Size
* Interest Rate
* Borrower Income
* Debt to Income
* Number of Accounts
* Derogatory Marks
* Total Debt
* Loan Status

### Metric and Variables to be Predicted
Out of the above metric, the metric of interest to be predicted was 'loan status'. Specifically, whether or not the potential borrower would have a heathy loan or a high-risk loan. The variables within this analysis were '0' for healthy loan, and '1' for high-risk loan.

### Stages

1. The data, originally a CSV file, was 'read' into Jupyter Lab as a dataframe for analysis using Python.

2. As part of generating a supervised leanring algorithm, labels (y) and features (X) were identified from the dataframe.

3. The balance of healthy to high-risk values was counted using ```value_counts()``` to observe the imbalance inherent in the data.

4. The data was split into training and testing datasets using ```train_test_split```.

5. Initially, a logistic regression model was generated without oversampling the imbalanced data so as to identify a 'control' so that we may observe the improvements made through oversampling.

6. A logistical regression model was instantiated using ```LogisticRegression```. Training data was then fitted to the model, followed by the generation of predictions.

7. The model's performance was then evaluated using:
* ```balanced_accuracy_score``` to display the model's accuracy
* ```confusion_matrix``` to check the frequency of True Postives and Negatives, as well as False Positives and Negatives
* ```classification_report_imbalanced``` to observe the classification report for the model, which displays precision and recall metrics, among others

8. A random oversampler model was now used to improve upon the previous model using ```RandomOverSampler```, now resampling the data such that value counts between '0' and '1' value become equal, followed by once again calling a ```LogisticRegression``` instance, however this time instead inputting the resampled training data.

9. This new model's perforance was evaluated, again using the previously mentioned metrics (```balanced_accuracy_score```, ```confusion_matrix```, ```classification_report_imbalanced```)

## Results

#### Machine Learning Model 1
The original logistic regression model was able to predict the healthy (0) and non-healthy (1) loan labels reasonably well.

*Confusion Matrix:*
* The model was able identify 18,663 True Negatives and 563 True Positives. It did, however, wrongly identify 102 False Positives and 56 False Negatives.

*Accuracy:*
* Accuracy was good but not perfect; the model was able to achieve an accuracy of about 95.2%, meaning that this proportion of its predictions were correctly identifying both True Positives and True Negatives, as is also shown by the Confusion Matrix.

*Precision:*
* It was very precise in correctly identifying healthy loans, with a precision of 100%, however only had a precision of 85% when identifying high-risk loans.

*Recall:*
* The model's recall was also almost perfect in predicting healthy loans with a recall score of 99% for that category. Recall was otherwise lower when predicting high-risk loans, with 91% of truly positive samples being correctly identified as True Positives.

#### Machine Learning Model 2
The logistic regression model that was fit with the oversampled data did considerably better than the original model, meaning that resampling the imbalanced data to mitigate the effects of differing sample sizes made a noticable and beneficial effect on the models efficacy in generating reliable predictions.

*Confusion Matrix:*
* The model fitted with oversampled data was able identify 18,649 True Negatives and 615 True Positives. This time, it wrongly identify 116 False Positives which, while being slightly more than before, is relieved by the fact that there were only 4 False Negatives identified.

*Accuracy:*
* Accuracy from the new model using oversampled data was almost perfect, with a score of about 99.4%.

*Precision:*
* Once again, the model was able to achieve perfect precision when identifying healthy loans, with a score of 100% for that category, while precision regarding the identification of high-risk loans did in fact drop slightly, down to 84%.

*Recall:*
* Recall is massively improved; while the recall score for healthy loans remained the same at 99%, the score for high-risk loans jumped to equalise itself, and now similarly also sits at 99%.

## Summary

To conclude, resampling data when dealing with imbalanced datasets is a crucial step towards effective data analysis and generation of reliable supervised machine learning algorithms. The second model clearly performs better than the first with both improved accuracy scores and overall improved performace metrics, including precision and recall. While some metrics may have slightly decreased in the second model, the overall effect was a vast improvement.

Performace does also depend on the problem that the analyst is looking to solve. If identifying the number of healthy loans (1), then the first model did infact achieve a slightly better precision score of 85%, compared to the resampled model's score of 84%. However for the purposes of this brief, the second model is the clear winner, as is demonstrated by the accuracy scores, the confusion matrix and finally the classification report for imbalanced datasets.