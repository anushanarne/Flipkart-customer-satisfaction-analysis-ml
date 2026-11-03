# Flipkart-customer-satisfaction-analysis-ML
Machine Learning Classification project to predict Flipkart customer satisfaction (Satisfied vs At-Risk) using customer support data, EDA, statistical validation, feature engineering, and Logistic Regression, Random Forest, and XGBoost models.
# Customer Satisfaction Analysis and Prediction Using Machine Learning

## Project Overview

This project focuses on analysing Flipkart customer support interactions and developing machine learning classification models to predict customer satisfaction.

The objective is to identify customers who are likely to be **Satisfied** or **At-Risk** based on customer support data. The project uses Exploratory Data Analysis (EDA), feature engineering, statistical validation, and classification algorithms to understand the factors influencing customer satisfaction.

## Business Problem

Customer satisfaction is an important indicator of customer-service quality.

The project aims to:
- Analyse customer support interactions.
- Identify patterns associated with customer dissatisfaction.
- Predict whether a customer is Satisfied or At-Risk.
- Identify important factors influencing customer satisfaction.
- Support data-driven customer-service decisions.

## Dataset Description

The dataset contains:
- 85,907 customer support records.
- 20 original columns.
- Support channel and issue category.
- Customer remarks.
- Order information.
- Response timestamps.
- Agent details, shift and tenure.
- Customer Satisfaction (CSAT) scores.

### Target Variable

The original CSAT score was converted into two classification categories:

| CSAT Score | Classification |
|---|---|
| 4–5 | Satisfied |
| 1–3 | At-Risk |

The target distribution is approximately:
- 85% Satisfied
- 15% At-Risk

## Project Workflow

1. Data Understanding
2. Data Cleaning and Preprocessing
3. Exploratory Data Analysis (EDA)
4. Feature Engineering
5. Sentiment Analysis
6. Statistical Validation
7. Model Building
8. Model Evaluation
9. Model Selection
10. Model Deployment and Prediction

## Exploratory Data Analysis (EDA)

The following insights were identified:

- The target variable is imbalanced, with approximately 85% Satisfied and 15% At-Risk tickets.
- Response time shows a strong right-skew and differs between satisfaction groups.
- Customer-remark sentiment differs between the two satisfaction groups.
- Satisfaction varies across support channels and issue categories.
- Response time and customer-remark sentiment were identified as important prediction signals.

## Data Preprocessing and Feature Engineering

The following preprocessing steps were performed:

- Handled missing values.
- Removed the highly incomplete `connected_handling_time` column.
- Created features such as:
  - `response_time_min`
  - `response_time_log`
  - `has_remark`
  - `has_order_context`
  - `report_hour`
  - `report_dow`
- Cleaned customer remarks.
- Generated VADER sentiment scores and remark length.
- Applied One-Hot Encoding to selected categorical variables.
- Applied StandardScaler to selected numerical features.
- Used an 80/20 stratified train-test split.
- Handled class imbalance using class weighting / `scale_pos_weight`.

PCA was not used because the final feature set was relatively small and interpretability was preferred.

## Machine Learning Models

Three classification algorithms were compared:

1. Logistic Regression
2. Random Forest
3. XGBoost

Hyperparameter tuning was performed using cross-validation/search methods.

## Model Evaluation Results

| Model | Accuracy | At-Risk Precision | At-Risk Recall | At-Risk F1 | Macro F1 |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 72.27% | 34.37% | 63.90% | 0.4470 | 0.6310 |
| Random Forest | 81.92% | 47.84% | 33.78% | 0.3960 | 0.6448 |
| Tuned XGBoost | 74.04% | 35.30% | 57.63% | 0.4379 | 0.6346 |

### Final Model Selection

Although Random Forest achieved the highest accuracy, Tuned XGBoost provided a better balance for identifying At-Risk customers and was selected as the final model.

At-Risk recall and F1-score were given particular importance because the business objective is to identify customers who may be dissatisfied.

## Statistical Validation

Hypothesis testing supported the main EDA findings.

Statistically significant differences were identified in:
- Response time between satisfaction groups.
- Remark sentiment between satisfaction groups.
- Association between support channel and satisfaction.

The reported p-values were below 0.00001 for all three tests.

## Model Deployment

The final XGBoost model, scaler, and model-column list were saved using Joblib.

Prediction checks were performed on manually created unseen-ticket examples to evaluate the model's prediction behaviour.

## Conclusion

The project demonstrates an end-to-end machine learning classification workflow for predicting customer satisfaction.

Response time and customer-remark sentiment emerged as important signals.

Among the three evaluated models, Tuned XGBoost was selected as the final model because it provided a useful balance for identifying At-Risk customers.

## Technologies and Tools

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- NLTK / VADER Sentiment Analysis
- Joblib
- Google Colab

---

**Project:** Customer Satisfaction Analysis and Prediction Using Machine Learning  
**Project Type:** Classification  
**Dataset:** Flipkart Customer Support Data  
**Target:** Satisfied vs At-Risk  
**Prepared by:** Anusha N
