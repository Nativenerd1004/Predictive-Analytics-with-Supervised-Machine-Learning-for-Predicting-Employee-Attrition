# Predicting Employee's Attrition with Supervised Machine Learning.

![image](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/23871480-e126-40bf-baff-12b578ee98a4)


This project aims to use predictive analytics with supervised machine learning techniques to forecast employee attrition in a company. By analyzing historical data on employee turnover, the goal is to build a model that can accurately predict which employees are at risk of leaving the organization. 

![wired-lineal-153-bar-chart](https://github.com/Nativenerd1004/Ecommerce-Sales-Analysis-Dashbaord/assets/149740069/e3c4b09a-97f0-48ee-aae4-9f8bafd9f848)


## Table of Content
- [Project Overview](#project-overview)
- [Project Objectives](#project-objectives)
- [Data Sources](#data-sources)
- [Data Preprocessing](#data-preprocessing)
- [Evaluation Metrics](#evaluation-metrics)
- [Actionable Insights](#project-overview)
- [Project Overview](#project-overview)
- [Conclusion](#conclusion)




## Project Overview
#### Situation:

```diff 
- Businesses face challenges retaining valuable employees, and predicting potential attrition can aid in mitigating this issue.
```
#### Task: 
```diff 
- To develope a machine learning algorithm to identify employees at high risk of leaving the company.
```
#### Action: 
```diff 
- This project implements a Gradient Boosting Classifier model, trained on employee data, to predict employee attrition.
```
![GradientBoostingClassifier](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/6679bb27-d024-45d9-8264-7474f38e428d)


#### Result: 
```diff 
- The resulting model provides insights into employee risk, enabling proactive measures to improve retention.
```
[Table of Content](#table-of-content)



## Project Objectives
#### Situation: 
```diff 
- The primary objective is to effectively predict employee attrition.
```
#### Task: 
```diff 
- The company aims to achieve high accuracy in identifying employees at risk of leaving.
```
#### Action:
```diff 
- I utilized the Gradient Boosting Classifier, known for its efficiency and handling of complex relationships in data.
```
#### Result: 
```diff 
- The model's effectiveness is measured by its ability to accurately predict potential leavers.
```
[Table of Content](#table-of-content)


## Data Sources

```diff
+ Importing Data into python
```
![Data Import](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/00bed890-e722-4339-9c6c-258fb9f14e7a)


#### Situation: 
```diff 
- Reliable employee data is crucial for model training.
```
#### Task: 
```diff 
- I leveraged a dataset containing employee information, potentially including demographics, job roles, performance metrics, etc.
```
#### Action: 
```diff 
- Collaboration with HR or relevant departments ensures data accuracy and relevance.
```
#### Result: 
```diff 
- Utilizing appropriate data sources is essential for model generalizability and effectiveness.
```
[Table of Content](#table-of-content)



## Data Preprocessing

#### Getting overview about the data 
```diff 
+ td.info()
```
![Data Overview](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/1b25632d-0703-41d6-8cc1-a7bd33017021)

#### Statistical Analysis on Numerical Data
```diff 
+ td.describe().T
```
![Numerical Statistical Analysis](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/5901ff43-c4bd-4953-9075-754ecaac6de8)

##### Missing Values
```diff 
! print (td.isnull().sum())
```

Visualize the missing data
```diff 
+ plt.figure(figsize = (10,3))
+ sns.heatmap(td.isnull(), cbar=True, cmap="magma")
```
![Missing Values](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/e5e0e01d-82e5-40d8-ba9a-540175b50bb5)


#### Statistical Analysis on categorical Data
```diff 
+td.describe(include=['object','bool'])
```
![Categorical Statistics](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/93ffeb2e-3ddf-4cea-bffc-40595e200b54)

#### dropping off some redundant features
```diff 
+td.drop(['Over18','StandardHours','EmployeeCount','EmployeeNumber'],axis=1,inplace=True)
```
![Dropping Off Syntax](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/2b5663a8-3ff9-4f55-a187-f3bc57f13974)

```diff 
!Duplicating the Data
```
![Copy-Of-Data-Set 2024-02-28 at 2 15 11 AM](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/fafa59e4-403c-49b4-b5f7-8f7fde795460)

#### identifying key features from the data set
```diff 
+model = RandomForestClassifier()
```

#### fit the model
```diff 
-model.fit(td_scaled, target)
-importances = model.feature_importances_
-sort_imp = np.argsort(importances)
-names = list(td2.columns)
```

#### plotting a feature importance chart
```diff 
+plt.figure(figsize=(10,7))
+plt.barh(range(len(sort_imp)),importances[sort_imp], color="red")
+plt.yticks(range(len(sort_imp)), [names[x] for x in sort_imp])
+plt.title("Feature Importance")
+plt.xlabel("relative importance measure")
```
![Feature Importance Graph](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/dd4ee443-ada2-4385-ba5f-c17670ed7cf5)

#### split the DataFrame into train and test datasets
```diff
!from sklearn.model_selection import train_test_split
```
```diff
!x_train, x_test, y_train, y_val = train_test_split(td_scaled, target, train_size=0.8, random_state=1)
!x_train # This is the data we will be training from
```
![Split Data Train and Test](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/f08b6a06-4d7e-4442-b046-3192a849349a)

```diff 
+x_test # This is the data we will be predicting from. 
```

#### Import model classifier 
```diff 
+from sklearn.linear_model import LogisticRegression
+from sklearn.tree import DecisionTreeClassifier
+from sklearn.ensemble import GradientBoostingClassifier
+from sklearn.svm import SVC 
```

#### Instantiate model
```diff 
+log_reg = LogisticRegression()
```
#### now let's predict with the x_test 20% dataset which is the testing data
```diff 
@@log_pred = log_reg.predict(x_test)@@
@@log_pred@@
```
![Machine Learning Computation](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/fa43ad37-9d0e-49f0-8536-a75015d62398)


#### import evaluation metrics

from sklearn.metrics import classification_report, confusion_matrix



















#### Situation: 
```diff 
- Raw data often requires cleaning and preparation before training a model.
```
#### Task: 
```diff 
- We address missing values, outliers, and inconsistencies within the employee data.
```
#### Action: 
```diff 
- Techniques like imputation, removal, or scaling may be employed to ensure data quality.
```
#### Result: 
```diff 
- Preprocessed data enhances the model's learning ability and reduces potential biases.
```
```diff 
!scaler = MinMaxScaler()
!td_scaled = pd.DataFrame(scaler.fit_transform(td2), columns = td2.columns)
!td_scaled
```

![Encoding, Segmentation, Scaling ](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/3e68baf8-e9db-42cc-b607-c73d090018f4)
![Scaler](https://github.com/Nativenerd1004/Predictive-Analytics-with-Supervised-Machine-Learning-for-Predicting-Employee-Attrition/assets/149740069/79e02c36-5088-4524-a7f2-3313f60835c9)


[Table of Content](#table-of-content)


## Evaluation Metrics
#### Situation:
```diff 
- Assessing model performance is crucial for understanding its effectiveness.
```
#### Task: 
```diff 
- We utilize metrics like accuracy, precision, recall, and F1-score to evaluate the model's ability to predict attrition.
```
#### Action: 
```diff 
- Analyzing these metrics helps identify areas for improvement and gauge the model's suitability for real-world application. 
```
#### Result: 
```diff 
- Evaluation metrics provide insights into the model's strengths and weaknesses, guiding further development or deployment decisions.
```
[Table of Content](#table-of-content)

## Actionable Insights
#### Situation: 
```diff 
- The model's predictions can inform strategic HR decisions.
```
#### Task: 
```diff 
- Identify employees at high risk and implement targeted interventions to address their concerns and improve retention.
```
#### Action: 
```diff 
- This may involve providing career development opportunities, addressing work-life balance issues, or offering competitive compensation packages.
```
#### Result: 
```diff 
- Actionable insights derived from the model can contribute to improved employee satisfaction and reduced turnover costs.
```
[Table of Content](#table-of-content)

# Conclusion
```diff 
- This machine learning algorithm leveraging a Gradient Boosting Classifier offers valuable insights into employee attrition. By effectively combining data preparation, model training, and evaluation, this project demonstrates the potential of machine learning to address real-world business challenges in the HR domain.
```
```diff 
- Note: This documentation serves as a general framework and might need adjustments based on the specific details and functionalities of your implemented algorithm.
```
[Table of Content](#table-of-content)









