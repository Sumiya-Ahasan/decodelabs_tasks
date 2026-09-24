# **Project 2 - Credit Card Fraud Detection**

A supervised machine learning project for detecting fraudulent credit card transactions using an imbalanced synthetic transaction dataset.

## **Project Overview**

The objective of this project is to build and evaluate classification models capable of identifying fraudulent transactions.

Because fraud represents a small minority of transactions, accuracy alone can be misleading. Therefore, this project focuses primarily on:

* Precision  
* Recall  
* F1-score  
* ROC-AUC

The project also demonstrates the use of SMOTE to address class imbalance.

## **Dataset**

The dataset contains 10,000 synthetic credit card transactions.

### **Dataset characteristics**

* Records: 10,000  
* Features: 10  
* Target variable: `is_fraud`  
* Target classes:  
  * `0` \= Legitimate transaction  
  * `1` \= Fraudulent transaction  
* Fraudulent transactions: 151  
* Legitimate transactions: 9,849  
* Fraud rate: approximately 1.51%

The dataset is synthetic and contains no real customer information.

### **Features**

| Feature | Description |
| :---- | :---- |
| `transaction_id` | Unique transaction identifier |
| `amount` | Transaction amount |
| `transaction_hour` | Hour of the transaction |
| `merchant_category` | Merchant category |
| `foreign_transaction` | Whether the transaction is international |
| `location_mismatch` | Whether billing and transaction locations mismatch |
| `device_trust_score` | Device trust score from 0–100 |
| `velocity_last_24h` | Number of transactions in the previous 24 hours |
| `cardholder_age` | Age of the cardholder |
| `is_fraud` | Target variable: 0 \= legitimate, 1 \= fraud |

## **Machine Learning Workflow**

The project follows this pipeline:

1. Load and inspect the dataset  
2. Perform data quality checks  
3. Analyze the fraud class distribution  
4. Perform exploratory data analysis  
5. Separate features and target  
6. Remove the transaction identifier  
7. Split data into training and testing sets  
8. Preprocess numerical and categorical features  
9. Apply SMOTE to the training data  
10. Train Logistic Regression  
11. Train Random Forest  
12. Evaluate both models  
13. Compare model performance  
14. Perform Random Forest hyperparameter tuning  
15. Evaluate the tuned model  
16. Analyze feature importance  
17. Draw final conclusions

## **Models**

### **Logistic Regression**

Logistic Regression is used as a baseline classification model for predicting whether a transaction is fraudulent.

### **Random Forest**

Random Forest is used as a tree-based ensemble classifier and is compared against Logistic Regression.

### **Hyperparameter Tuning**

GridSearchCV is used to search for improved Random Forest hyperparameters using ROC-AUC as the optimization metric.

## **Handling Class Imbalance**

The dataset contains significantly fewer fraudulent transactions than legitimate transactions.

SMOTE (Synthetic Minority Over-sampling Technique) is applied to the training data to increase representation of the minority fraud class.

The test set is kept separate from SMOTE so that model evaluation is performed on unseen data.

## **Evaluation**

The models are evaluated using:

### **Precision**

Measures how many transactions predicted as fraudulent were actually fraudulent.

### **Recall**

Measures how many of the actual fraudulent transactions were successfully detected.

### **F1-score**

Provides a balance between precision and recall.

### **ROC-AUC**

Measures the model's ability to distinguish between fraudulent and legitimate transactions across classification thresholds.

Accuracy is not used as the primary evaluation metric because the dataset is highly imbalanced.

## **Results**

The final model results are presented in the project notebook and the `results/model_results.csv` file.

|  | Model | Precision | Recall | F1-Score | ROC-AUC |
| :---: | ----- | ----- | ----- | ----- | ----- |
| **0** | Logistic Regression | 0.287129 | 0.966667 | 0.442748 | 0.993299 |
| **1** | Random Forest | 1.000000 | 0.633333 | 0.775510 | 0.999255 |
| **2** | Tuned Random Forest | 1.000000 | 0.633333 | 0.775510 | 0.999205 |

## **Visualizations**

The project includes:

* Fraud vs legitimate transaction distribution  
* Exploratory data analysis  
* Confusion matrices  
* ROC curve comparison  
* Model performance comparison  
* Random Forest feature importance

## 

## **Technologies**

* Python  
* Pandas  
* NumPy  
* Matplotlib  
* Scikit-learn  
* Imbalanced-learn  
* Jupyter Notebook / Google Colab

## **Key Learning Outcomes**

This project demonstrates practical understanding of:

* Binary classification  
* Imbalanced classification  
* SMOTE  
* Data preprocessing  
* Categorical encoding  
* Feature scaling  
* Logistic Regression  
* Random Forest  
* Precision and Recall  
* F1-score  
* ROC-AUC  
* Confusion matrices  
* Hyperparameter tuning  
* Feature importance  
* Machine learning pipelines

## **Limitations**

This project uses a synthetic dataset intended for educational and experimentation purposes. Therefore, the results should not be interpreted as evidence of performance on real financial transaction systems.

A real-world fraud detection system would require larger and more representative transaction data, temporal validation, stronger fraud-prevention considerations, and additional domain-specific features.
