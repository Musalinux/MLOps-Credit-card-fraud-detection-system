# MLOps based Credit Card Fraud Detection System

## **Problem Statement:**

**Cloud-Based Credit Card Fraud Detection** aims to leverage machine learning algorithms and cloud infrastructure to identify fraudulent credit card transactions in real-time. Credit card fraud remains one of the most significant challenges in the global fintech industry, with billions of dollars lost annually to fraudulent activities. Traditional fraud detection methods often struggle to keep up with the ever-evolving tactics of fraudsters. This project focuses on creating an efficient, scalable, and accurate fraud detection system using data science and cloud-based technologies. By deploying the model on cloud platforms like AWS, the system will be capable of handling large volumes of transactions, providing real-time detection, and scaling seamlessly to meet increasing demands. The project will involve dataset exploration, feature engineering, machine learning model development, and deployment on cloud services such as AWS SageMaker and Lambda.

## 🔧 Tools and resources required
| **Category** | **Tool/Service** | **Description** | **Free Tier** |
| --- | --- | --- | --- |
| **AWS Services** | **AWS S3 (Storage)** | Used to store the dataset for training and testing the model. | 5GB of standard storage. |
|  | **AWS SageMaker (Model Training & Deployment)** | A fully managed service for training and deploying machine learning models. | 250 hours of t2.micro instances (for training), 50 hours of inference (for deployment). |
|  | **AWS Lambda (Model Inference API)** | Serverless compute to deploy and run the trained model as an API for real-time fraud detection. | 1 million requests and 400,000 GB-seconds of compute time per month. |
|  | **AWS API Gateway** | Used to create a RESTful API to interact with Lambda function for real-time fraud detection. | 1 million API calls per month. |
|  | **AWS Glue (ETL and Preprocessing)** | Used for data cleaning, transformation, and preprocessing. | 1 million requests per month. |
|  | **AWS CloudWatch** | For monitoring the deployed model and tracking logs. | 5GB of log data ingestion per month. |
| **Machine Learning Libraries (Open Source)** | **Scikit-learn** | For implementing machine learning algorithms (e.g., Random Forest, Logistic Regression). | Free to use. |
|  | **XGBoost** | For boosting algorithms, improving model accuracy. | Free to use. |
|  | **Pandas & NumPy** | For data manipulation, cleaning, and feature engineering. | Free to use. |
|  | **Matplotlib & Seaborn** | For visualizing the dataset and model results. | Free to use. |
| **Data Science & Development Environment** | **Jupyter Notebooks or Google Colab** | For exploratory data analysis (EDA), preprocessing, and prototyping machine learning models. | Google Colab is free and provides a Python environment with GPUs if needed. |
| **Data Sources** | **Kaggle Credit Card Fraud Detection Dataset** | A publicly available dataset with labeled transaction data for fraud detection. | Free access (requires a Kaggle account). |


### Model Outcome: 
```bash
y_pred = model.predict(X_test)

print("Classification Report:\n", classification_report(y_test, y_pred))
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("ROC AUC Score:", roc_auc_score(y_test, y_pred))
````

### Current Output: 
```` bash
Classification Report:
               precision    recall  f1-score   support

           0       1.00      1.00      1.00     56777
           1       1.00      1.00      1.00     28518

    accuracy                           1.00     85295
   macro avg       1.00      1.00      1.00     85295
weighted avg       1.00      1.00      1.00     85295

Confusion Matrix:
 [[56763    14]
 [    2 28516]]
ROC AUC Score: 0.9998416450672509
````
