# 🚀 MLOps-Based Credit Card Fraud Detection System on AWS

## 📌 Problem Statement

Credit card fraud is a critical challenge faced by the fintech industry, resulting in billions of dollars in annual losses. Traditional methods struggle to adapt to the evolving tactics of fraudsters. This project focuses on developing a **Cloud-Native, Scalable, and Automated Credit Card Fraud Detection System** using **MLOps principles** and **AWS services**.

✅ **Goal:** Leverage Machine Learning and Cloud Infrastructure to build a **real-time fraud detection pipeline** capable of handling large volumes of transactions with **high accuracy** and **minimal latency**.

---

## 🏗️ End-to-End Architecture

```
[Transactions Data (CSV/JSON)] --> [S3 (Raw Data)]
      |
  [EventBridge (Trigger)]
      |
[Step Functions (Orchestration)]
      |
[AWS Glue (ETL & Preprocessing)] --> [S3 (Processed Data in Parquet Format)]
      |
[Lambda (Fraud Detection Inference) / SageMaker Endpoint]
      |
[DynamoDB (Fraud Results) / S3]
      |
[SNS (Alerts)] --> [Email / Slack Notifications]
```

---

## 🔧 Tools & Services Used

| Category            | Tool/Service              | Description                                                    |
|---------------------|---------------------------|----------------------------------------------------------------|
| **Cloud Storage**   | AWS S3                    | Stores raw, processed, and fraudulent transaction data.        |
| **ETL & Preprocess**| AWS Glue (ETL, Catalog)   | Cleans, transforms, and catalogs data. Supports Athena.        |
| **Data Processing** | AWS Glue Jobs             | Converts raw CSV/JSON to optimized Parquet format.             |
| **Orchestration**   | AWS Step Functions        | Manages the ETL pipeline and fraud detection flow.             |
| **Event Triggers**  | AWS EventBridge           | Triggers Step Function workflows on new data uploads.          |
| **ML Inference**    | AWS Lambda / SageMaker    | Runs fraud predictions on new transactions.                   |
| **Data Storage**    | DynamoDB                  | Stores flagged fraudulent transactions for analysis.           |
| **Alerting**        | SNS (Simple Notification Service) | Sends alerts on detected fraud transactions.            |
| **Security**        | IAM / KMS / Secrets Manager | Secures data and access policies.                         |
| **Monitoring**      | CloudWatch                | Monitors logs and metrics from Glue, Lambda, and S3.           |

---

## ⚙️ Project Workflow (MLOps Pipeline)

1. **Data Ingestion**
   - Raw transaction files (CSV/JSON) uploaded to S3 (`fraud-raw-transactions`).

2. **Event Trigger**
   - AWS EventBridge detects new files and triggers Step Functions.

3. **ETL & Feature Engineering**
   - Step Functions orchestrate AWS Glue Job execution.
   - Glue Job reads raw data, performs cleaning, feature engineering, and writes Parquet data to S3 (`fraud-processed-transactions`).

4. **Fraud Detection Inference**
   - Step Functions invoke AWS Lambda (or SageMaker Endpoint) for fraud prediction on the processed data.

5. **Result Storage**
   - Fraudulent transactions are stored in DynamoDB and flagged data is stored in S3 (`fraud-fraudulent-transactions`).

6. **Alerts & Notifications**
   - SNS sends real-time alerts (Email/Slack) for detected frauds.

---

## 🛠️ Key Components & AWS Services Configuration

### 1. S3 Buckets
- `fraud-raw-transactions`
- `fraud-processed-transactions`
- `fraud-fraudulent-transactions`

### 2. AWS Glue
- **Glue Crawler**: Auto-detects schema and populates Glue Catalog.
- **Glue Job (PySpark)**: Cleans and transforms data, outputs Parquet files.

### 3. AWS EventBridge
- Event Rule triggers when files are added to `fraud-raw-transactions`.

### 4. AWS Step Functions
- Orchestrates the flow: ETL -> Fraud Prediction -> Storage -> Alerts.

### 5. AWS Lambda (or SageMaker)
- Runs the ML model to predict fraud.
- Lambda processes small batches, SageMaker handles large-scale inference.

### 6. DynamoDB
- Stores fraud predictions with transaction details.

### 7. SNS (Simple Notification Service)
- Sends email/SMS alerts to security teams.

---

## 🔐 Security Implementation

| Service             | Implementation                                              |
|---------------------|-------------------------------------------------------------|
| IAM Roles/Policies  | Fine-grained access control for services.                   |
| KMS                 | Encrypts S3 data and DynamoDB items.                        |
| Secrets Manager     | Manages API keys/DB credentials (for Lambda, etc.).         |

---

## 📊 Dataset Used

- **Kaggle Credit Card Fraud Detection Dataset**  
  [Dataset Link](https://www.kaggle.com/mlg-ulb/creditcardfraud)

### Features:
- **V1-V28**: PCA-transformed features
- **Amount**: Transaction amount
- **Class**: 0 (Non-Fraud), 1 (Fraud)

---

## ✅ Model & Results

### ML Models Used
- Logistic Regression
- Random Forest
- XGBoost

### Model Evaluation (on X_test):

```
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

ROC AUC Score: 0.9998
```

---

## 🧰 Tools & Frameworks

| Tool/Library        | Purpose                                     |
|---------------------|---------------------------------------------|
| Scikit-learn        | ML model development                        |
| XGBoost             | Boosted model accuracy                      |
| Pandas / NumPy      | Data manipulation and preprocessing         |
| Matplotlib / Seaborn| Visualization of EDA and results            |
| Jupyter / Colab     | Development and EDA notebooks               |

---

## 🚀 Future Enhancements

- Implement real-time streaming using Kinesis.
- Deploy microservices on ECS for better scalability.
- Implement CI/CD pipelines using CodePipeline & CodeBuild.
- Integrate AWS GuardDuty & Security Hub for advanced security monitoring.

---

## ✨ Project Highlights

- ✅ Real-time Fraud Detection on AWS  
- ✅ Scalable ETL Pipelines with AWS Glue  
- ✅ Secure and Automated Orchestration via Step Functions & EventBridge  
- ✅ End-to-End MLOps Implementation  

---

## 🙌 Contributors

- Musaddik Vasaikar (Project Lead)
- Ayesha Gaikwad
- Santosh Bangera

---

## 📄 License

This project is licensed under the MIT License.
