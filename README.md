# D2C Customer Churn Intelligence & Retention API

## Part 3: Churn Prediction Modeling & Model Card

**Student Name:** Mayank Sharma

---

# Project Overview

Customer churn is one of the most critical business challenges in Direct-to-Consumer (D2C) businesses. Acquiring new customers is often significantly more expensive than retaining existing customers.

This project develops a machine learning-based churn prediction system capable of identifying customers who are likely to churn within the next 60 days.

The objective is to proactively identify high-risk customers and support customer retention initiatives through data-driven decision making.

The solution leverages customer demographics, transaction history, engagement behavior, support interactions, and loyalty information to build predictive models capable of estimating churn probability.

---

# Problem Statement

Predict whether a customer will churn within the next 60 days.

Target Variable:

```text
churn_next_60d
```

Where:

```text
0 = Customer Retained
1 = Customer Churned
```

The prediction system helps businesses:

* Identify churn-risk customers
* Prioritize retention campaigns
* Improve customer lifetime value
* Reduce customer acquisition costs
* Optimize marketing expenditure

---

# Dataset Information

The dataset contains customer-level information collected from multiple business systems.

## Dataset Size

| Dataset Split  | Records |
| -------------- | ------- |
| Training Set   | 1728    |
| Validation Set | 336     |
| Test Set       | 336     |
| Total Records  | 2400    |

---

## Feature Categories

### Customer Profile Features

* City Tier
* Age Group
* Acquisition Channel
* Loyalty Tier
* Preferred Category
* Marketing Consent

---

### Transaction Features

* Recency Days
* Frequency (180 Days)
* Monetary Value (180 Days)
* Return Rate (180 Days)
* Average Discount Percentage
* Product Rating
* Category Diversity

---

### Support Features

* Ticket Count
* Negative Ticket Rate
* Resolution Time

---

### Customer Engagement Features

* Sessions
* Product Views
* Cart Adds
* Wishlist Adds
* Abandoned Carts
* Email Opens
* Campaign Clicks
* Last Visit Days Ago

---

# Project Workflow

The project follows a complete machine learning lifecycle.

## Phase 1: Data Understanding

* Dataset loading
* Shape analysis
* Data type analysis
* Statistical summaries
* Missing value assessment
* Target variable inspection

---

## Phase 2: Data Preprocessing

### Numerical Features

* Median Imputation
* Standard Scaling

### Categorical Features

* Most Frequent Imputation
* One-Hot Encoding

---

## Phase 3: Model Development

Multiple machine learning models were trained and evaluated.

### Models Evaluated

1. Logistic Regression
2. Random Forest
3. Gradient Boosting
4. XGBoost
5. LightGBM
6. Extra Trees

---

## Phase 4: Model Evaluation

Models were compared using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC Score

---

## Phase 5: Threshold Analysis

Different probability thresholds were evaluated to identify the optimal trade-off between:

* Precision
* Recall
* F1 Score

Thresholds tested:

```text
0.3
0.4
0.5
0.6
0.7
```

---

## Phase 6: Error Analysis

Prediction errors were investigated through:

* False Positive Analysis
* False Negative Analysis
* Business Impact Assessment
* Customer-Level Case Studies

---

## Phase 7: Model Documentation

Deliverables include:

* Model Card
* Error Analysis Report
* Metrics JSON
* Saved Models

---

# Best Model Selection

## Selected Model

### Gradient Boosting Classifier

The model demonstrated the strongest overall balance across evaluation metrics and was selected as the final deployment candidate.

---

## Final Model Performance

| Metric    | Score  |
| --------- | ------ |
| Accuracy  | 0.8065 |
| Precision | 0.7847 |
| Recall    | 0.7687 |
| F1 Score  | 0.7766 |
| ROC-AUC   | 0.8756 |

---

# Confusion Matrix Summary

|                 | Predicted Retained | Predicted Churn |
| --------------- | ------------------ | --------------- |
| Actual Retained | 112                | 56              |
| Actual Churn    | 18                 | 150             |

---

## Error Distribution

| Outcome             | Count |
| ------------------- | ----- |
| Correct Predictions | 262   |
| False Positives     | 56    |
| False Negatives     | 18    |

---

# Key Business Insights

Feature importance analysis identified the strongest churn drivers:

1. Recency Days
2. Monetary Value
3. Days Since Signup
4. Last Visit Days Ago
5. Product Views
6. Return Rate
7. Average Discount Percentage
8. Resolution Hours
9. Product Rating
10. Purchase Frequency

The analysis indicates that customer inactivity is the strongest indicator of future churn.

---

# Repository Structure

```text
Part_3_Churn_Prediction_Model_&_Model_Evaluation/

│
├── Models/
│   ├── extra_trees.pkl
│   ├── gradient_boosting.pkl
│   ├── lightgbm.pkl
│   ├── logistic_regression.pkl
│   ├── random_forest.pkl
│   └── xgboost.pkl
│
├── Part_3_outputs/
│   ├── churn_distribution.png
│   ├── combined_model_performance_comparison.png
│   ├── confusion_matrix.png
│   ├── dataset_split.png
│   ├── evaluation_metrics_summary.png
│   ├── final_model_metrics.png
│   ├── missing_value_analysis.png
│   ├── model_comparison.csv
│   ├── prediction_outcome_distribution.png
│   ├── statistical_summary.png
│   ├── target_variable_distribution.png
│   ├── threshold_analysis.png
│   ├── threshold_selection_analysis.png
│   └── top_feature_importance.png
│
├── churn_model.ipynb
├── error_analysis.md
├── metrics.json
├── model_card.md
├── requirements.txt
└── README.md
```

---

# Output Artifacts

## Saved Models

The following trained models are saved in serialized format:

* Logistic Regression
* Random Forest
* Gradient Boosting
* XGBoost
* LightGBM
* Extra Trees

Format:

```text
.pkl
```

---

## Visualizations Generated

The project generates visualizations for:

* Missing Values
* Dataset Distribution
* Target Variable Distribution
* Dataset Split Analysis
* Model Comparison
* Evaluation Metrics
* Threshold Analysis
* Confusion Matrix
* Feature Importance
* Prediction Outcome Analysis

---

## Documentation Files

### model_card.md

Contains:

* Intended Use
* Data Used
* Model Approach
* Performance
* Limitations
* Ethical Risks
* Monitoring Requirements
* Deployment Considerations

---

### error_analysis.md

Contains:

* False Positive Analysis
* False Negative Analysis
* Customer Examples
* Business Risk Assessment
* Improvement Recommendations

---

### metrics.json

Contains structured machine learning evaluation metrics for deployment and monitoring purposes.

---

# Installation

Clone the repository:

```bash
git clone <repository_url>
```

Move to project directory:

```bash
cd Part_3_Churn_Prediction_Model_&_Model_Evaluation
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Running the Notebook

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
churn_model.ipynb
```

Execute cells sequentially.

---

# Future Improvements

Potential future enhancements include:

* Hyperparameter Optimization
* Ensemble Modeling
* Explainable AI (SHAP)
* Real-Time Churn Scoring
* Customer Lifetime Value Prediction
* Automated Retraining Pipelines
* FastAPI Deployment
* Cloud Deployment

---

# Conclusion

This project demonstrates a complete end-to-end churn prediction pipeline from data preprocessing to model evaluation and documentation.

The selected Gradient Boosting model achieved strong predictive performance and provides actionable insights for customer retention strategies. The generated artifacts, reports, and visualizations make the solution suitable for both academic evaluation and practical business applications.
