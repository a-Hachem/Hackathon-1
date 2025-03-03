# STOP Fraud Project

## 1. Introduction

Credit card fraud is a growing concern, leading to significant financial losses and security risks. This project aims to develop a machine learning model capable of detecting fraudulent transactions based on historical transaction data. Given the highly imbalanced nature of fraud detection (where fraudulent transactions are rare), the project involves advanced data preprocessing, feature selection, and model optimization techniques to improve fraud detection performance.

## 2. Data Cleaning & Feature Selection

### 2.1 Data Cleaning
The dataset initially contained multiple features, including demographic data, transaction details, and account behaviors. The preprocessing steps included:
- Handling missing values using imputation techniques.
- Removing duplicate records to avoid bias in model training.
- Detecting and addressing outliers using statistical and visualization techniques.

### 2.2 Feature Selection
To improve model efficiency and interpretability, feature selection was performed using:
- **ANOVA tests**: Features with a p-value < 0.05 were considered relevant to fraud detection.
- **Correlation analysis**: Redundant and highly correlated features were removed.
- **Domain knowledge**: Transaction-related features were prioritized over personal information.

After feature selection, the dataset was reduced to the most relevant variables while maintaining predictive performance.

## 3. Exploratory Data Analysis (EDA)

### 3.1 Data Visualization

#### 3.1.1 Class Imbalance in Target Variable
The dataset exhibited a severe class imbalance, with fraudulent transactions (‘TARGET=1’) making up a very small proportion of the total transactions. This imbalance impacts model training and requires specialized techniques for correction.

#### 3.1.2 Demographic and Behavioral Insights
- **Gender Distribution**: The dataset had a higher proportion of male individuals.
- **Age Distribution**: Fraudulent transactions were more frequent among individuals aged 30-40.
- **Contract Status**: Fraudulent transactions were often associated with declined or canceled contracts.

### 3.2 Key Findings
- **Severe class imbalance**: Traditional models tend to favor the non-fraudulent class.
- **Fraud patterns**: Younger individuals and declined contracts show higher fraud rates.
- **Potential feature importance**: Transaction frequency and anomalies in contract status may be key fraud indicators.

## 4. Model Training & Evaluation

### 4.1 Logistic Regression

A baseline logistic regression model was trained, but due to class imbalance, it failed to predict fraudulent cases effectively.

**Results:**
- Precision (Non-Fraud) = 0.91, Recall = 1.00, F1-score = 0.95
- Precision (Fraud) = 0.00, Recall = 0.00, F1-score = 0.00

### 4.2 XGBoost

An XGBoost model was trained, improving fraud detection precision but still struggling with recall.

**Results:**
- Precision (Non-Fraud) = 0.91, Recall = 1.00, F1-score = 0.96
- Precision (Fraud) = 0.96, Recall = 0.00, F1-score = 0.00

### 4.3 Model Insights & Challenges
Both models suffered from extremely low recall for fraudulent transactions, indicating that fraud cases were largely misclassified as non-fraud.

**Possible improvements:**
- **Resampling Techniques**: Using **SMOTE (Synthetic Minority Over-sampling Technique)** or **undersampling** to balance the dataset.
- **Cost-Sensitive Learning**: Adjusting class weights in the loss function to penalize misclassification of fraud cases.
- **Anomaly Detection**: Implementing autoencoders or isolation forests to capture rare fraud patterns.
- **Ensemble Methods**: Combining multiple models to improve generalization and robustness.

## 5. Real-Time Fraud Detection Strategy

### 5.1 Key Steps
1. **Real-Time Data Collection**: Continuous transaction monitoring with real-time feature updates.
2. **Feature Engineering**: Extracting temporal and behavioral features to enhance fraud detection.
3. **Adaptive Model Updating**: Periodic retraining with new fraud cases to adapt to evolving fraud techniques.
4. **Anomaly Detection**: Flagging suspicious transactions using unsupervised learning methods.
5. **Automated Alerts & Intervention**: Integrating fraud detection models with an alert system for immediate response.

### 5.2 External Data Sources for Enhancement
- **Geolocation Data**: Identifying transactions that occur in unusual locations.
- **Device Fingerprinting**: Analyzing user behavior to detect anomalies.
- **External Fraud Databases**: Leveraging global fraud databases to cross-check transactions.

## 6. Conclusion

This project highlights the challenges of fraud detection in highly imbalanced datasets. While initial models showed strong performance on the majority class, they struggled to detect fraudulent transactions effectively. By integrating **resampling techniques, anomaly detection, and real-time monitoring**, the accuracy and robustness of fraud detection systems can be significantly improved.

Future work will focus on refining these techniques and exploring deep learning models to further enhance fraud detection performance.

