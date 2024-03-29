## Project 1: [Credit Card Fraud Detection](https://github.com/xslittlemaggie/Machine-Learning-Projects/blob/master/CreditCard_LogisticRegression_UnderSample_OverSample.ipynb)
### Part 1: The purpose of the project
The purpose of this project is to detect the fraud for credit card records. 

### Part 2: About the data
The sample size for this project is 284807. There is a total of 30 features, Time, through V1 to V28, Amount, and the target variable is Class, while 0 indicates normal, and 1 indicates fraud.

### Part 3. Data Engineering 
Before fitting the model, the data engeering was conducted to check the features. 
1. The feature **Time** is dropped since it is not related to the target variable, Class.
2. The features through **V1** to **V28** are principal components after PCA ranging from about -3 to +3. Thus these features are the main components selected after PCA, and these features are decorrelated. The multicollinearity is not a problem for these features. 
3. The range of the feature **Amount** varys significantly from 0 to 25691. Thus the StandardScaler was applied to standaridize the feature Amount to a distribution with mean of 0 and variance of 1.

### Part 4: About the target Variable, Class
The distribution of the target variable **Class** is imbalanced (# of class = 0: 284315, # of class = 1: 492). Next, I will fit the model with three different conditions to check how the sample size will impact the model. 

Model 1: fit the logistic regression model with the original dataset (class = 0: 284315, class = 1: 492) 
Model 2: fit the logistic regression model with under_sampling to balance the dataset (class = 0: 391, class = 1: 391)
Model 3: fit the logistic regression model with over_sampling to balance the dataset (class = 0: 227454, class = 1: 227454)

### Part 5: Analysis of the three different models
Model 1: High accuracy (Accuracy = 1.0), Low recall_score (recall_score = 0.64). This is a particular weakness of imbalanced dataset.
Model 2: Accuracy (Accuracy = 0.94), recall_score (recall_score = 0.93). The accuracy and recall_score seems good. But the price is high number of false positive (FP) (3377). Take the bank as an example, the purpose is to identify the fraud for further investigation or alert. However, the cost is to identify normal records as frauds falsely. In practice, this huge number of FP will make the further investigation or alert impossible. Thus, this model becomes meaningless. 
Model 3: Accuracy (Accuracy = 0.97), recall_score (recall_score = 0.94). Both the accuracy and recall_score improve. And the number of FP (1413) decreases significantly. 

### Part 6: Discussion
The focus of this project is to practice how to deal with the imbalanced sample size, as well as how the different sample size would impact the performance of the mdoels. 

In addition, the cross validation technique was also used to cross check the performance of the models. 

To further improve the performance, some other classification models could be used, such as SVM, RandomForest, etc. or the ensembling of several classification models could be used for majority vote. 



## Project 2: [Wine Clssification with Decision Tree & Bagging & Random Forest & Boosting](https://github.com/xslittlemaggie/Machine-Learning-Projects/blob/master/Wine_DecisionTree_RandomForest_Boosting.ipynb)
### Part 1: The purpose of the project
The purpose of this project is to class the different types of wine with four different classifiers:
- **Decision Tree**: DT is the base model for all the rest 3 classifiers, its performance should be the lowest since it is included in all other classifiers.
- **Bagging**: Create n weak classifiers (decision tree) with the bootstrap method. All DTs are independent to each other, thetically.  
- **Random Forest**: similar to bagging
- **Adaptive Boosting**: Create n weak classifiers (decision tree) with the boosting method. Each tree is determined based on the previous trees. Thus, all DTs are correlated.

### Part 2: About the data
The data for this project is the sklearn built-in dataset, wine

### Part 3: About the techqniues
#### 3.1 Test_train_split to split the training and testing datasets
#### 3.2 Use cross_validation to cross check the model performance
#### 3.3 Decision tree visualization
#### 3.4. Decision Tree & Random Forest main parameters
- 1. Decision Tree visualization
- 2. Model fine tune: 
  - n_estimators (**only for random forest, and the most important parameter**)
  - Criterion
  - random_state
  - splitter
  - max_depth
  - min_samples_leaf & min_samples_split
  - max_features
#### 3.5. Print the features importances
- It could also be used for the features selection during feature engineering in other projects

### Part 4: Fine tune the parameters of Decision Tree to get the best performance 
- All other classifiers are created based on the Decision Tree, except the parameter n_estimators.

### Part 5: Comparson of the Performance of the Decision Tree, Bagging, Random Forest, and Boosting classifiers. 
Under the similar conditions, the performance of Bagging, Random Forest, and Adaptive Boosting should always be better than that of the Decision Tree since the Decision Tree is included in these classifiers. In addition, the Boosting should have the best performance. 

### Part 6: Discussion
Usually the decision tree and random forest classiers (the other two classifiers are different, they could use other weak classifier as base models) are easy to be overfitting. The parameters adjusting is usually to decrease the model complexity, to aovid overfitting.


