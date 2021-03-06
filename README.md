# Model_Comparison_Spine

This project aims to evaluate different types of classification machine learning techniques on spine data to better understand which methods yield more desirable results. Important to this project is to minimize false positives and obtain high precision. 

This .CSV spreadsheet can be located on Kaggle.com and contains 310 rows of 13 columns plus a column for classification of normality. The columns report various areas of the spine like pelvic and cervical areas in two ways, angle and radius. They  are reported in degrees and millimeters respectively. The classification column is reported in binary, 0 being normal and 1 denoting abnormal. After reading the .CSV into a pandas dataframe, LabelEncoder was applied to the classification column. Features were pulled out as all 13 columns of data except for the classification column. All features were forced into numeric integers. 

![alt text](https://github.com/jayghez/Model_Comparison_Spine/blob/master/MC_spine_features.png)

Two copies of the features were made. One copy untouched and one with that was standardized using StandardScaler, both were split for training and testing with a random state of 42 and a testing size of 30%. Next, two functions were created to facilitate the testing of models, one for each copy of the features. These functions reported the same thing for each model, the name, the accuracy score, the confusion matrix, and the classification report.

![alt text](https://github.com/jayghez/Model_Comparison_Spine/blob/master/model_evaluation_f(x).png)

Lastly the various models were ran through these functions and grouped by name into a dictionary. The models were, KNN, GridSearch KNN, Bagged KN, logistic regression, GridSearch logistic regressions, GridSearch and Bagged logistic regression, Decision Trees, and GridSearch Decision Trees. 

The KNN model with neighbors set to 5, on both the GridSearch and typical KNN had model accuracy scores of 83%. Whereas bagging of the GS-KNN, performed at model accuracy of 82%. The scaled features set of the data scored model accuracy of 80% for typical and for 81 % for the GridSearch KNN. The logistic regressions had noticeably higher model accuracy scores with, the typical logistic regressions scoring 86% and the GridSearch with parameters K-Fold equal to the length of y (310), L1, and a penalty of 10 with a model accuracy score of 87%. The scaled version of typical logistic regression scored 90% and the scaled version of GridSearch logistic regression scored 89% with best parameters denoting L2, and a penalty of 10. Bagged GridSearch logistic regression had a model accuracy score 87%. 

![alt text](https://github.com/jayghez/Model_Comparison_Spine/blob/master/score_shot.png)

![alt text](https://github.com/jayghez/Model_Comparison_Spine/blob/master/score_graph_shot.png)

The various models' accuracy scores are important, but recalling that this is medical data means that precision plays a huge importance to the patient. A doctor does not want to rely on the algorithm if it has any false positives i.e telling a patient they have an abnormal spine when in fact they do not. The model that had the highest accuracy is the logistic regression both for the scaled and not scaled feature sets. Fortunately, looking into the confusion matrix, the high score is more of a result from the average of how well the model performed classifying the abnormal than the normal. 
