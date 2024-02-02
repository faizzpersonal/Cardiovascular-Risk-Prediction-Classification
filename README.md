# Classification Cardio Risk ML Model
# OBJECTIVE
The dataset contains information about cardiovascular health of residents of Framingham, Massachusetts, with 3390 rows and 17 features. The dataset has no duplicate values, but some features have null values, which can be adjusted. The features include age, education, sex, smoking status, BP medication, cholesterol level, diabetes status, BP, BMI, glucose level, and heart rate. The goal is to build a model that predicts the risk of developing Coronary Heart Disease in the next 10 years.
The data cleaning process involved treating null values with median/mode/mean, distinguishing features into categorical, discrete, and continuous, and not treating outliers as they might contain useful information. Exploratory data analysis (EDA) was performed to extract insights, followed by feature engineering and data preprocessing, including label encoding for categorical features and creating new features like pulse pressure, smoking status, and diabetic status. Variance Inflation Factor (VIF) was calculated to find multicollinearity between features, and important features were selected for further analysis.
Since the data is imbalanced, SMOTE (over-sampling) was used to deal with it. The data was split into train and test sets, and the data was transformed using standard scaler. The data was oversampled to balance it, and different models like Logistic Regression, KNN, Random Forest, Naive Bayes, and XGBoost were implemented with accuracy, precision, recall, F1-score, and AUC as evaluation metrics. Among all the models, XGBoost performed well with GridSearch CV as hyperparameter tuning on both training and test data samples, and it was chosen as the final model.

# Problem Statement
The dataset is from an ongoing cardiovascular study involving residents of Framingham, Massachusetts. The primary objective is to forecast whether a patient is at risk of developing coronary heart disease (CHD) over a 10-year period. The dataset encompasses more than 4000 records, featuring 15 attributes. These attributes encompass a range of factors including demographic details, behavioral patterns, and medical risk factors, all of which serve as potential indicators for predicting the likelihood of coronary heart disease.

# Attribute Information

id: Unique id of each Patient<br>
AGE: Age of Patient<br>
Educarion: Education of Patient<br>
Sex : Gender of Patient<br>
is_smoking : Whether the Patient is Smoker or not<br>
CigsPerDay: If Patient is smoker then how many Cigrattes Patient smokes per day<br>
BPMeds: Whether the Patient is taking BP medicines or not<br>
prevalentStroke: Whether the Patient has prevalant score or not<br>
prevalentHyp : Whether the Patient has Hypertension or not<br>
Diabets : Whether the Patient is diabetic or not<br>
totchol : Cholestrol Level of Patient<br>
sysBP : BP Measure<br>
diaBP : BP Measure<br>
BMI : Boday Mass Index of Patient<br>
Heartrate : HeartRate of Patient<br>
Glucose : Glucose level of Patient<br>
TenYearCHD :Target Variable we need to predict what is the chances of getting CHD for next 10 years<br>




# CONCLUSION
### EDA
EDA helps us to extract useful insights from the data.Following were some of the insights drawn:
In the data set around 57% of the patients's gender was Female and around 49.8% of the patients are smokers.18.5% of the Male patients and 12.4% of Female patients and around 16.3% of the patients who are smokers and 13.8% of the non-smoker patients have chances of getting the disease
only 2.9% of the patient are taking BP medicines and only 0.6% of the patient has prevalent Stroke and around 31.5% of the patients has prevalent Hypertension and only 2.6 % of the patients has Diabetes and Only 15.1% of the patients has a chance of getting cardio-vascular disease in next 10 years
People at Education Level 1 have more chances of getting the disease than other Education Level
Majority of the patient's age were in the range of 40-50 and the chances of suffering with CHD increase with increase in age
Patients suffering with the prevalant stroke have more chances of suffering with the disease
Daibetes patients are having more glucose level and are more prone to CHD
Patients having Cholestrol greater than 300 mg/dl and less than 150 mg/dl are having more chances of getting the disease'
Patients having systolic Bp greater than 150 mmhg and less than 110 mmhg are having more chances of getting the disease
Patients having dia-Bp greater than 100 mmhg and less than 70 mmhg are having more chances of getting the disease
There is not a specific BMI which can lead to CHD but it can seen that patients with overweight and obese conditions i.e BMI >25 are have little more risk of getting CHD in future
Patients having heart rate more than 90 are having little more risk of getting the disease

### ML
Logistic Regression,Random forest,KNN,Naive Bayes and XGBoost model is implemented on the dataset. Based on the performance of all the models, XGBoost model is selcted as the final prediction model. The XGBoost model outperformed the other models in several key aspects, making it the preferred choice for prediction.KNN has also shown good performance on training data with 100% AUC score but only 81% on test sample data that means model has overfitted.
The XGboost model with hyperparamter tunning ,has performed very well with higher accuracy,recall,F1 score and AUC value of 99% on training and 94% on test.The best paramters was found to be 'gamma': 0, 'learning_rate': 0.1, 'max_depth': 5, 'n_estimators': 300. Out of 1152 patients our optimal model is correcly predicting 518 of class 0 and 509 of class 1 patients, other 90 and 35 are FN and FP cases. I have applied Feature importance method to find out what are the features that are important for the prediction of the target feature:
it can be seen that age feature is contributing the most around 22.8% followed by the pulse_pressure 13.8% and then education around 11.85% and so on
