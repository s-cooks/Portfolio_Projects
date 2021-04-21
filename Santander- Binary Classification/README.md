# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)Santander Bank Customer Transaction Prediction

by Sheena Cook

### Executive Summary

Data Science is solving a number of problems in the Finance Sector. Some of those problems include managing customer data, predictive analytics, fraud detection, and consumer analytics. Consumer analytics is the process of collecting and analyzing customer data to learn customer behavior and preferences for making strategic and tactical business decisions, as well as automatically forming personalized recommendations. Gaining this insight into customers, is vital for product management, marketing, and sales. As a result, Santander bank has tasked Data Scientists via Kaggle to deploy Machine Learning models to gain insights into its customers to predict future transactions. 

---

### Data Sources
Data provided by Kaggle:
- [Santander Customer Transaction Prediction](https://www.kaggle.com/c/santander-customer-transaction-prediction)
- [Research Sources](https://www2.deloitte.com/content/dam/Deloitte/us/Documents/process-and-operations/us-cons-customer-analytics-102711.pdf)

---


### Notebook Index

- [01 | EDA Visualization]()

- [02 | Supervised Models]()

- [03 | Unsupervised Models]()



---

### EDA 
EDA consisted of checking the data types of the features, checking null values, determining any correlations, and feature importance. My findings are below:

- dataset consisted of a train and test csv, both files contained 200k rows, with 200 features 
- no correlation between features 
- no null values 
- could not highlight any important features
- class imbalanced with target variable, minority class totaling .10 while majority class totaled .89, as a result applied SMOTE
- attempted PCA for dimensionality reduction but could not determine any feature elimination or feature importance


---

### Models


#### Supervised Models: Predicting a Customer Transaction w/ SMOTE 

|Model|Train Score|Test Score|AUC Score|
| --- | ---  ---  | ----  -- | ------  |
|LR   | .799.     | .790     | .86     |
|RF   | .1        | .893     |.70      |
|NB   | .864.     | .870     |.60      | 


#### Unsupervised Models: Predicting a Customer Transaction w/ SMOTE

|Model|Train Score|Test Score|AUC Score|
| --- | --- | --- |
|Neural Net - dropout| .888 | .855 | .95 |
|Neural Net - early stop| .825 | .797 | .80 | 

---

### Conclusion

#### Results

Logistic Regression - outperformed the attempted supervised models with a .86 AUC Score. Naive Bayes AUC score performed
poorly compared to the other supervised models because NB assumes that points close to the centroid of class are likely to be members of that class, which leads it to mislabel positive training points with features. This explains why it underperformed compared to Logistic regression, as Logistic Regression is only concerned with correctly classifying points so the signal from outliers is more influential. Logistic Regression is also known to outperform NB on larger datasets. For supervised models, Logistic Regression performed the best. 

Neural Network - to combat overfitting I used regularized techniques to fit a NN. The Dropout Neural Network returned the highest AUC score. Tuning additional hyperparameters to increase AUC score. For unsupervised models, the dropout method returned the best AUC score of .95. 

The Kaggle submission results from my models returned an AUC score between .50 to .60. These low scores indicate the models created overfit and not able to generalize to Santander's holdout set. Future work will include continual refining of models by tuning hyperparameters and attempting to undersample may return a better AUC score. 

---

### Take away and Next steps 

#### To improve analysis:
- Attempt additional supervised and unsupervised models. 
- Additional tuning of hyperparameters to current models to optimize AUC score.
- Undersample data to decrease run time.
- Collecting additional data for customer segmentation since we’ve determined customers who will make a future transaction.


