# Ensembles
### The objective of this assignment is to predict whether a flight gets delayed or not.
### After assessing the dataframe, I thought to drop some columns like **'carrier', 'flight', 'tailnum' 'type','manufacturer', 'model', 'engines', 'seats', 'engine'** since arrival delay doesnt depend on them.It mostly depends on weather, distance and time.So, I chose to omit those columns.
### The dataset has 10000 observations, if we drop null values, 80% of the data is lost.So, I chose replacing the nulls with median value for preprocessing.
### Train_test_split is 0.2 i.e., 8000 Training samples and 2000 test samples.


## Logistic Regression using GridSearchCV
#### 1. Created a pipeline for logistic regression model with Ridge regression as penalty
#### 2. Used 0.001, 0.1,1,10 as penalty strengths for grid search.
#### 3. Here,  the scoring metric is Area under curve
#### 4. For Logistic Regression,ROC AUC is 68.49%,which cannot be considered a good discrimination, not much better than a coin toss.

## DecisionTreeClassifier using GridSearchCV
#### 1. Created a pipeline for logistic regression model with max_depth=1 and 'entropy' as criterion.
#### 2. Used 1,2,3,4 as max_depths for grid search.
#### 3. Here the scoring metric is Area under curve as well
#### 4.ROC AUC is 61.92%, way lesser than that for logistic regression.

## Support Vector Classifier using GridSearchCV
#### 1. Created a pipeline for SVM model with 'linear' kernel since the predicrtion id linear separable.
#### 2. Since it is linear seperable, probability parameter is set True
#### 3. Used 0.001, 0.1,1,10 aspenalty strengths for grid search.
#### 4 Here the scoring metric is ROC_AUC
#### 5.ROC AUC is 69.03,which is better compared to logistic and decision tree classifiers
#### 6. It took me aroung 7 minutes on a gpu to run this classifier, might be because of following reasons,
##### C parameter - greater the missclassification penalty, slower the process
##### kernel - more complicated the kernel, slower the process (rbf is the most complex from the predefined ones)
##### data size/dimensionality

## Ensemble of the above three classifiers
#### I tried to run this, waited for almost 2 hours.No error showed up.But I did not get any output.

## Adaboost using Decison Tree Classifer
### Ababoost classifier using Decision Tree Classifier with max_depth = 1 as base estimator
### ROC is 70.81% which is comparatively higher than all the above classifiers.ROC of 70% can be considered good but can be improved.
