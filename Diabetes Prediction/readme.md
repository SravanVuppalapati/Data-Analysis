# Diabetes prediction on PIMA INDIAN DATASET.
### This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases. The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.
### The datasets consists of several medical predictor variables and one target variable, 'Class'. Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.

### Since, all the columns are numerical, and this being a small dataset, we don't need to do any principal component analysis(PCA)
I prefered using L2(Ridge) regularization for modeling pipelines since L1 tends to shrink coefficients to zero whereas L2 tends to shrink coefficients evenly. L1 is therefore useful for feature selection, as we can drop any variables associated with coefficients that go to zero. L2, on the other hand, is useful when you have collinear/codependent features
## Choosing Regularization Strengths for grid search
For hyperparameters with that type of bounds, you'll likely want to start with a handful of values that are spacing on a logarithmic scale, e.g. $C \in (0.001, 0.01, 0.1, 1, 10, 100, 1000)$. So I chose 0.01, 0.1, 1, 10, 100 as C values.

 ## I used "sag' and 'liblinear' solvers for modeling since our dataset allows us to classify binarily.Other solvers are used for multiclass datasets.
 
 ### As the ROC curve checks the trade off between FP and TP, I chose ROC area under the curve as the scoring metric checks true positive, false positive rate in the graph and adjusts accordingly.
 
 ### For liblinear and sag, the best model is at regularization strength of 0.1 but the area under curve is higher for liblinear, i.e 83.9 compared to 83.8 for sag's roc.
 ### Liblinear solver automatically selects the parameters taking its predecessor predicting output in our conidtion with the combination of AUC_Roc curve it checks the postive rate of the graph and then proceeds further using the Liblinear solver and got the maximum output.
 
### Stocastic Average gradient solver is mainly used on large dataset which takes the loss function to proceed for its further prediction. This being small dataset when performed sag with 'roc_auc' as metric has got improvement over the base pipeline,but not as good as the liblinear solver.
