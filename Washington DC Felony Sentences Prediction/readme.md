# Washington DC Felony Sentences
Link to Dataset: [https://opendata.dc.gov/datasets/DCGIS::felony-sentences/explore](https://opendata.dc.gov/datasets/DCGIS::felony-sentences/explore)
### Introduction: 
Felonies have been a major concern in the US in the recent times.Young population are being involved in crime intentionally or unintentionally.Unlike counties,we see many day-to-day crimes in the headlines in the downtowns of major cities.My objective is to let people know what crime they are doing and what sentence they get depending on their age and crime they have committed.
### Objective :To predict and classify the sentence type of offense depending on the offense,age, offense category.
### Dataset Description
#### **This dataset has been retreived from 'Open Data DC'.This dataset contains all felony counts sentenced from 2010 to 2020 and includes offender demographic information such as gender, race, and age, as well as sentencing information such as the offense, offense severity group, and the type and length of sentence imposed. The dataset is updated annually.**
### Features
1. OBJECTID:( type: esriFieldTypeOID, alias: OBJECTID )

- Internal feature number.

2. RID:( type: esriFieldTypeString, alias: RID, length: 255)

- Row number, sequential

3. GENERIC_CASE_ID: ( type: esriFieldTypeString, alias: GENERIC_CASE_ID, length: 255)

- Randomly generated unique identifier for cases

4. GENERIC_OFFENDER_ID:( type: esriFieldTypeString, alias: GENERIC_OFFENDER_ID, length: 255)

- Randomly generated unique identifier for offenders

5. CHARGE_NUMBER:(type: esriFieldTypeDouble, alias: CHARGE_NUMBER)

- Specific charge number within a case

6. SENTENCE_YEAR (type: esriFieldTypeDouble, alias: SENTENCE_YEAR)

- The year the case was sentenced

7. RACE:(type: esriFieldTypeString, alias: RACE, length: 255)

- Race of the accused

8. GENDER: (type: esriFieldTypeString, alias: GENDER, length: 255)

- Gender of accused

9. AGE_GROUP: (type: esriFieldTypeString, alias: AGE_GROUP, length: 255)

- Age group at the time of offense

10. OFFENSE: (type: esriFieldTypeString, alias: OFFENSE, length: 255)

- The offense of conviction within a case

11. OFFENSE_TYPE: (type: esriFieldTypeString, alias: OFFENSE_TYPE, length: 255)

- The category for the offense of conviction

12. HOMICIDE_TYPE:(type: esriFieldTypeString, alias: HOMICIDE_TYPE, length: 255)

- The type of homicide, if the offense was homicide

13. OFFENSE_SEVERITY_GROUP:( type: esriFieldTypeString, alias:OFFENSE_SEVERITY_GROUP, length: 255)

- The sentencing guidelines ranking for the offense of conviction

14. SENTENCE_TYPE: ( type: esriFieldTypeString, alias: SENTENCE_TYPE, length: 255 )

- The type of sentence imposed for the offense of conviction

15. SENTENCE_IMPOSED_MONTHS: ( type: esriFieldTypeDouble, alias: SENTENCE_IMPOSED_MONTHS)

- The prison sentence length imposed in months Not available for indeterminate and life sentences; A value of 1 month may indicate that the defendant may have been sentenced to time served, the actual value of which is not available to the Commission.

16. SENTENCE_SUSPENDED_MONTHS:(type: esriFieldTypeDouble,alias: SENTENCE_SUSPENDED_MONTHS)

- The prison sentence length suspended in months

17. SENTENCE_TO_SERVE_MONTHS:(type: esriFieldTypeDouble, alias: SENTENCE_TO_SERVE_MONTHS)

- The amount of time to serve in prison Not available for indeterminate and life sentences; A value of 1 month may indicate that the defendant may have been sentenced to time served, the actual value of which is not available to the Commission

18. SENTENCE_PROBATION_MONTHS:(type: esriFieldTypeDouble, alias: SENTENCE_PROBATION_MONTHS )
- The probation sentence length imposed in months

19. VVCA_AMT: ( type: esriFieldTypeDouble, alias: VVCA_AMT )

- A court-ordered payment under the Victims of Violent Crime Compensation Act (VVCA) that goes to the Crime Victims Compensation Program

20. FINE_AMT: ( type: esriFieldTypeDouble, alias: FINE_AMT ) -The amount of court fines imposed

21. RESTITUTION_AMT: ( type: esriFieldTypeDouble, alias: RESTITUTION_AMT )

- The amount of restitution (the amount that the offender is ordered to pay the victim for damages that the victim suffered as a result of the crime)

22. FINE_SUSPENDED_AMT: ( type: esriFieldTypeDouble, alias: FINE_SUSPENDED_AMT )

- The amount of court fines imposed that were suspended

23. GIS_ID: ( type: esriFieldTypeString, alias: GIS_ID, length: 50 )

24. GLOBALID: ( type: esriFieldTypeGlobalID, alias: GLOBALID, length: 38 )

25. CREATOR: ( type: esriFieldTypeString, alias: CREATOR, length: 255 )

26. CREATED: ( type: esriFieldTypeDate, alias: CREATED, length: 8 )

27. EDITOR: ( type: esriFieldTypeString, alias: EDITOR, length: 255 )

28. EDITED: ( type: esriFieldTypeDate, alias: EDITED, length: 8 )


### Data Cleanup
1. Though this dataset has 28 columns.I omitted 'GIS_ID','GLOBALID', 'CREATOR', 'CREATED', 'EDITOR', 'EDITED' columns because they dont have significant information for analysis.
2. Columns 'OBJECTID', 'RID', 'GENERIC_CASE_ID','GENERIC_OFFENDER_ID' are dropped because they are not continuous varbiables but random random sequences.
3. Column 'HOMICIDE_TYPE' can be used for analysis but is dropped because it has almost 22000 nulls.Even if we do imputing, its values will be duplicated.
4. 'VVCA_AMT','FINE_AMT', 'RESTITUTION_AMT', 'FINE_SUSPENDED_AMT' are dropped since my objective is to predict the sentence type and not the amount to be imposed.
5. Final dataset has 24324 rows and 10 columns

### EDA Outcomes:
In this project, I did Exploratory data analysis on various dataframe columns to get insights about how the offenders are charged based on their age, gender and offense they have committed.
Some insightful observations:
#### 1. Number of felonies by year:
- From the distirbutions, we can observe that the number of felonies have decreased over time.This might be due to the awareness among people or due to unreported cases.
#### 2. Felonies count for each offense:
- Felonies by type 'violent' are the highest followed by type 'Drug'.Sex felonies are the least in DC from 2010 to 2020.
#### 3. Felonies count by sentence:
- Incarceration is the most serious sentence type among all the felonies.Whereas the number of sentences for probation and short split are on par with each other.Long split is rarely sentenced.
#### 4.Felonies by Gender:
- Male population has committed most number of felonies accounting around 22000 while Females accounted to low value of 3000.
#### 5.Felonies by count by age:
- It is evident from the distribution that young people aged 18-30 are more tended to commit a crime compared to elders.Obviously, old aged people aged 71+ are not accused much.
#### 6.Felonies by Number of felonies by felony charge number:
- This distribution shows the number of felonies by charge number.Charge number is nothing but severity of crime.People are often charged by number '1'.
#### 7.This treemap shows top ten offenses in Washington DC.Assualt is the offense people committed most often followed by robbery.There are instances where people are charged with double offenses e.g., Posseing a firearm during violence.
#### 8.Charge number and imposed sentence are positively correlated but are weakly correlated.This implies charge number(felony severity) has less impact on felony sentence imposition.
#### 9.Offenses related to 'Drug' are mostly due to unlawful possession of liquid PCP,distribution of controlled substance and intentionally possessing a substance.
#### 10.Catgory 'Weapon' offenses, highest being unlawful possession of firearm followed by carrying pistol without license outside home or business.
#### 11.Homicides mostly included Voluntary Manslaughter and Muder-II followed by Muder-I.People are not accused seriously for First,Second degree murders without possessing any firearms.
#### 12.Assualts and Robberies with or without arms are the most common offenses in this category.
#### 13.'Other' is largest category with 52 offenses.Bail reform ,Prison and contempt are the top 3 felonies in this category.
#### 14.First Degree and second degree child abuse are the most serious offenses in Sex category followed by first degree sexual abuse.
#### 15.People aged between 22-30 committed more crimes.Of these, Drug and Violence categories share same number of sentences whereas sex , homicide share equal sentences.Similar trend can be seen for Property and Other categories.This can be observed from the bar chart.
#### 16.Crosstab depicts the proportion of offenses committed by a gender for each cateogory.In all cases, Males commited more offenses than Females.
#### 17.The lineplot explains the change in number of cases over years.People are mostly sentenced with incarceration (imprisonment for one year/more or even death).No of incarcerations are high during the year 2010.But are gradually reduced over time.Probation and Short Split sentences started at around 80 in 2010 and are constant until 2019 but suddenly declined in 2020.Long Split has the least number of sentences among others.It also followed a trend similar to Short Split are very low.

### Feature Engineering
#### 1.My objective is to predict sentence type.But the distribution of classes seams to be imbalanced.There are less samples for Long Split.Short Split Sentence and Long Split means offenders serving some time in prison and some time outside depending on their behaviour.Probation also serves the same purpsose.So,I merged the Short Split and Long Split into Probation and thus making the class distribution balanced and making it a binary classification
#### 2. Most of my features are categorical and as a part of preprocessing, I have to label encode them for training.
#### 3.Most of the features are negatively correlated to target variable "SENTENCE_TYPE".I think it is a good correlation because higher correlation might have masked the prediction.

### Modeling and Classification
1. Since, there is a slight imbalance in the class data, I have done oversampling to negate the imbalance to some extent using SMOTE function
2. This dataset has almost 24324 rows.So, we alteast need 80 % of the data for training.
#### Classification using Logistic Regression
- Hyperparameters Used: Used 0.001, 0.1,1,10 as penalty strengths for grid search.
- This model seems to be best for classification when hyperparameter C is 0.1
- Accuracy of 60% cannot be considered a good discrimination.Since, the target variable is slightly imbalanced, I chose roc_auc_score as a metric to decide the model.
- For this classifier, ROC_AUC score is 68% which has to be improved
#### Classification using Decision Tree Classifier
- Hyperparameters Used: Used 1,2,3,4 as max_depths for grid search.
- This model seems to be best for classification when hyperparameter max depth is 4
- This model has 68% accuracy which is better compared to Logistic Regression.
- Even the area has been increased to 74%,but that's not enough for a good classification.
#### Classification using KNN
- Hyperparameters Used: Used 1,4,6,10 as number of neighbors for grid search.
- This model seems to be best for classification when hyperparameter number of neighbors are 10
- It seems like KNN is has better accuracy compared to Logistic and DTC having 70% accuracy
- Also, the area of curve for KNN has also increased to 76%.

### Conclusion
####After analyzing the three models, I think KNN Classifier can classify better compared to others.We can improve the accuracy by dealing the dataset imbalance through better modeling techniques.

### References:
1. [https://www.alpharithms.com/correlation-matrix-heatmaps-python-152514/](https://www.alpharithms.com/correlation-matrix-heatmaps-python-152514/)
2. [https://medium.com/geekculture/how-to-plot-a-treemap-in-python-48743061cfda](https://medium.com/geekculture/how-to-plot-a-treemap-in-python-48743061cfda)
3. [https://machinelearningmastery.com/multinomial-logistic-regression-with-python/](https://machinelearningmastery.com/multinomial-logistic-regression-with-python/)
4. [https://medium.com/analytics-vidhya/how-to-carry-out-k-fold-cross-validation-on-an-imbalanced-classification-problem-6d3d942a8016](https://medium.com/analytics-vidhya/how-to-carry-out-k-fold-cross-validation-on-an-imbalanced-classification-problem-6d3d942a8016)
5. [https://github.com/appliedecon/data602-lectures](https://github.com/appliedecon/data602-lectures)
