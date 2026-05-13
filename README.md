# loan-risk-predictions

## 📌 Project Overview

This project focuses on building a machine learning-based loan eligibility prediction system to identify whether a customer is likely to repay or default on a loan. The objective is to help financial institutions improve loan approval decisions by detecting high-risk applicants using historical financial and behavioral data.
#### The goal of this project
- Predict whether a customer is eligible for loan approval
- Identify high-risk customers likely to default
- Improve decision-making using machine learning

## 📂 Dataset Description
The dataset contains customer-related financial and demographic information collected from multiple sources:
1. Application Data
2. Bureau data
3. bureau_balance data
4. Credit Card Balance data
5. Installment Payments data
6.  POS Cash Balance data
7. Previous Loan Records data

After aggregation and feature engineering, the dataset contained 200+ engineered features.

## ⚙️ Project Workflow

### 1. Data Aggregation & Merging:
Multiple relational datasets were aggregated and merged into the main application dataset using customer IDs.

- Aggregation techniques:
1. Mean
2. Max
3. Min
4. Sum
5. Count
6. Unique counts

### 2. Data Preprocessing:
#### 1. Missing Value Handling

Different strategies were used based on missing percentage:
|Missing%	|Strategy|
----------|----------
|> 80%	|Dropped columns|
|60–80%	|Created binary missing indicators|
< 50%	|Median/Mode imputation|

#### 2. Outlier Handling
Outliers were handled using:
1. Capping
2. Log Transformation
3. Yeo-Johnson Transformation

This improved model stability and reduced skewness

#### 3. Encoding Techniques
Different encoding methods were applied:
1. One-Hot Encoding
2. Ordinal Encoding
3. Target Encoding

#### 4. Feature Scaling
Scaling was applied only for non-tree-based models: Logistic Regression

Tree-based models:
1. Random Forest
2. XGBoost
3. LightGBM
do not require scaling

#### 5. Class Imbalance Handling
The dataset was highly imbalanced:
1. ~92% Non-default
2. ~8% Default

Techniques used:
1. class_weight="balanced"
2. scale_pos_weight

## 🧠 Feature Engineering & Selection
Model-Based Feature Importance

Fature importance was extracted from:
1. Random Forest
2. XGBoost
3. LightGBM

Importance scores were:
1. Normalized
2. Averaged across models

#### Feature Count Optimization
Different feature subset sizes were evaluated:20,30,40,50,70,100,120,150,200. ROC-AUC was used to identify the optimal feature count.

Final selected features:
200 most important features

## 🤖 Models Training
different machine learning models were trained and evaluated without cv and hyperparameter tuning and with cv and hyperparameter tunnig
1. Logistic 
2. Random forest
3. XGBoost	
4. LightGBM

## 📊 Model Performance
evaluated using Evaluation Metrics:
Accuracy, ROC-AUC (primary metric), Precision, Recall, F1-score

without cv and hyperparameter tunnig
	|Model|	Accuracy|	ROC_AUC	|Precision	|Recall	|F1|
  |------|---------|---------|-----------|-------|--|
|XGBoost|	0.737021	|0.778212|	0.186637	|0.672306|	0.292166|
|LightGBM	|0.747476|	0.776644|	0.190980	|0.657603|	0.295997|
|Logistic| Regression	|0.700372|	0.764067	|0.168317|	0.688016	|0.270467|
|Random Forest	|0.862950	|0.757363|	0.255781	|0.365358|	0.300904

<img width="450" height="250" alt="download" src="https://github.com/user-attachments/assets/47bf4fc7-0d2c-4853-99ca-69bad29ec916" />

<img width="450" height="250" alt="download" src="https://github.com/user-attachments/assets/4c46bfff-a974-4c39-88b5-a5e0f6f676d2" />

with cv and hyperparameter tunnig

 | Model |  ROC_AUC|
 |-------|---------|
 | XGBoost | 0.777639|
 |LightGBM | 0.775810|
 |Logistic | 0.764052|
 |RandomForest | 0.748257|

 - classification report

|class  |precision  |  recall|  f1-score  | support|
|------|-----|---------|-----------|---------|
|0     |  0.95  |    0.90|      0.92 |    56538|
|1      | 0.27    |  0.43      |0.33     | 4965|
|accuracy     |   |         |        0.86 |    61503|
|macro avg      | 0.61    |  0.66    |  0.63    | 61503|
|weighted avg |      0.89     | 0.86  |    0.87 |    61503|

<img width="450" height="250" alt="download" src="https://github.com/user-attachments/assets/629b5cad-4e49-440b-9897-ac137c4519b1" />

## ✅ Final Model Selection
Selected Model: XGBoost

Why XGBoost?
1. Highest ROC-AUC
2. Better handling of imbalanced data
3. Captures non-linear relationships
4. Strong generalization capability

model achieves good performance for non defaulters with 95% precision means almost all approved loans are safe means it finds non defaulters with best accuractly.43% recall for defaulters.model identifies 43% of potential defaulters.


## 🛠️ Tech Stack
Python,Pandas,NumPy,Scikit-learn,Logistic,Randomforest,XGBoost,LightGBM,Matplotlib,Jupyter Notebook

## 🚀 How to Run
### 1. Clone Repository
https://github.com/RushikeshMaske03/loan-risk-predictions.git

### 2. Install Dependencies
pip install -r requirements.txt

### 3. Run Jupyter Notebook

## 🔮 Future Improvements
1. use advanced methods and techniques for better performance
2. deployment

## 👨‍💻 Author
Rushikesh Maske

Data Scientist | Machine Learning
