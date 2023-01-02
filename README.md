# BreastCancerPrediction
In this program, we compared Logistic Regression, SVM, KNN, Voting Classifier, Polynomial Regression (with L1 regularization) to do the analysis and prediction on standardized data without CELL-SHAPE variable and outliers, and utilized k-fold cross validation.
# I.	Usage Instructions
Change the data files dictionary paths, including training data and the testing data you want to get prediction result. Then change the output dictionary into your preferred location. The programming will output the prediction result into file ‘Breast-Cancer-W.csv’, the last column will be the prediction result.
# II.	Background
Cancer has become one of the major diseases threatening human health. In the face of the increasing incidence of breast cancer and the younger population of the patients, this program intends to explore the optimal regularization parameters to improve the diagnostic accuracy.
# III.	Methodology 
First, with the given data, we exclude ‘space’ missing values and changed the variable ‘BARE’ as integer. Then changed the ‘CLASS’ variable into 0 and 1 as a cancer signal. For test data, we filled the missing values with median instead of deleting the samples with missing values. 
Then, we divided the ‘CLASS’ variable apart from other independent variables in the data sets. And standardized all independent variables. Then we excluded outliers by deleting absolute z-scores lager than 4. Here we found 10 samples as outliers. We used VIF to check multicollinearity. Without ‘CELL_SHAPE’ variable will decrease the influence of multicollinearity, and VIF will be lower than 5. Then we analyzed the relationships between independent variables and dependent variable in order to prepare interactions or polynomials. However, because the variables are not continuous, so it is hard to see the relationships directly from the pair plots. 
After preparing all the data sets, considering the small sample problem, we used K-fold cross validation to exclude the influence caused by sample sets. Because the SVM and KNN model won’t be influenced by multicollinearity, so we also compared using all 9 variables and exclude ‘CELL_SHAPE’ variable. Since there is not obvious differences between these two methods, in order to keep everything else when compared to other models, we choose to use 8 variables. Then we tried voting classifier with SVM and KNN model as two classification methods. What is more, we tried some regression models – Logistic Regression, Polynomial Regression. We utilized L1 regularization to narrow down the number of variables. When C=0.05, there would be 8 variables remained with 3 poly degrees. 
Finally, we compared all the cross valid results. 3rd degree polynomial L1 Regularization (C=0.05) model has relatively higher accuracy and recall value which is important to distinguish positive samples. It has smaller variation as well which means this model is more robust. What is more, we can see the parameters in the model and easily say which one is more influential. It is interpretable. Therefore, we used this model to get the prediction result in file ‘Breast-Cancer-W.csv’.
# IV.	Other Concerns 
There is trade-off between training error and over-fitting must be made.
