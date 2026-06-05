# Model Card

## D2C Customer Churn Intelligence & Retention Analytics

---

## 1. Model Overview

### Project Name

D2C Customer Churn Intelligence & Retention Analytics

### Model Name

Gradient Boosting Classifier

### Model Version

1.0

### Developer

Mayank Sharma

### Program

IIT Patna – Applied AI & Machine Learning

### Prediction Objective

Predict whether a customer is likely to churn within the next 60 days.

### Target Variable

```text
churn_next_60d
```

Where:

```text
0 = Customer Retained
1 = Customer Churned
```

The model generates:

* Binary churn prediction
* Churn probability score
* Customer risk classification

The primary objective is to help businesses proactively identify customers at risk of churn and initiate retention interventions before customer loss occurs.

---

# 2. Intended Use

## Primary Use Cases

This model is intended for:

* Customer churn prediction
* Retention campaign planning
* Customer success prioritization
* CRM decision support
* Loyalty program optimization
* Marketing budget allocation
* Customer health monitoring

---

## Intended Users

The model is designed to be used by:

* Customer Success Teams
* CRM Teams
* Marketing Teams
* Business Analysts
* Retention Specialists
* Data Science Teams

---

## Business Goal

The model helps organizations:

* Reduce customer attrition
* Improve customer lifetime value
* Increase retention rates
* Improve marketing efficiency
* Prioritize intervention efforts

---

# 3. Data Used

## Dataset Summary

The model was trained using historical customer behavioral, transactional, support, engagement, and profile data.

### Total Records

| Dataset    | Records |
| ---------- | ------- |
| Training   | 1728    |
| Validation | 336     |
| Testing    | 336     |
| Total      | 2400    |

---

## Features Used

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
* Average Product Rating
* Category Diversity

---

### Support Features

* Ticket Count (90 Days)
* Negative Ticket Rate (90 Days)
* Resolution Time (Hours)

---

### Customer Engagement Features

* Sessions (30 Days)
* Product Views (30 Days)
* Cart Adds (30 Days)
* Wishlist Adds (30 Days)
* Abandoned Carts (30 Days)
* Email Opens (30 Days)
* Campaign Clicks (30 Days)
* Last Visit Days Ago

---

## Data Processing

### Numerical Variables

* Missing value imputation using median
* Standard scaling

### Categorical Variables

* Missing value imputation using most frequent value
* One-hot encoding

---

# 4. Model Approach

## Problem Type

Binary Classification

The objective is to classify whether a customer will churn within the next 60 days.

---

## Machine Learning Models Evaluated

Five candidate models were trained and evaluated:

1. Random Forest
2. Gradient Boosting
3. XGBoost
4. LightGBM
5. Extra Trees

---

## Model Selection Strategy

Models were compared using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC Score

The model with the strongest overall balance across all evaluation metrics was selected.

---

## Selected Model

### Gradient Boosting Classifier

The model demonstrated:

* Strong predictive performance
* High churn detection capability
* Balanced precision and recall
* Excellent ROC-AUC score

---

# 5. Model Performance

## Evaluation Metrics

| Metric    | Score  |
| --------- | ------ |
| Accuracy  | 0.8065 |
| Precision | 0.7847 |
| Recall    | 0.7687 |
| F1 Score  | 0.7766 |
| ROC-AUC   | 0.8756 |

---

## Test Set Performance

### Confusion Matrix

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

## Performance Interpretation

The model successfully identifies the majority of customers who are likely to churn.

Key strengths include:

* High churn detection capability
* Strong discrimination between churners and non-churners
* Low number of missed churn customers
* Strong ranking capability reflected by ROC-AUC

The model intentionally prioritizes churn detection, which is desirable for retention-focused business applications.

---

# 6. Limitations

Although the model performs well, several limitations should be acknowledged.

---

## Data Limitations

### Limited Dataset Size

The model was trained on 2400 customer records, which may not capture all customer behaviors.

### Snapshot-Based Features

The dataset represents a snapshot in time and may not fully capture long-term customer behavior trends.

### Historical Dependency

Future customer behavior may differ from historical patterns used during training.

---

## Feature Limitations

The model does not currently use:

* Customer sentiment analysis
* Product review text
* Social media interactions
* Competitor information
* Real-time customer activity streams

---

## Model Limitations

Predictions are probabilistic and not guarantees.

Unexpected customer behavior may still occur despite strong predictive performance.

---

# 7. Ethical Risks

Machine learning predictions can influence customer treatment and business decisions.

The following ethical considerations should be addressed.

---

## Misclassification Risk

The model can generate:

### False Positives

Customers predicted to churn but who remain active.

Potential consequence:

* Unnecessary retention incentives
* Increased marketing expenditure

---

### False Negatives

Customers predicted to stay but who actually churn.

Potential consequence:

* Lost revenue
* Missed retention opportunities

---

## Fairness Risk

Some customer groups may receive systematically different predictions because of patterns present in historical data.

Potentially affected groups include:

* Age groups
* City tiers
* Acquisition channels
* Loyalty segments

Regular fairness audits should be performed.

---

## Privacy Risk

Customer behavioral data contains sensitive information.

Organizations should:

* Restrict access to prediction outputs
* Follow applicable privacy regulations
* Protect customer records and model artifacts

---

# 8. Monitoring Requirements

Continuous monitoring is required after deployment.

---

## Model Performance Monitoring

Track:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Churn Capture Rate

---

## Data Drift Monitoring

Monitor changes in:

* Recency behavior
* Purchase frequency
* Monetary value
* Customer engagement patterns
* Support interaction patterns

---

## Prediction Drift Monitoring

Monitor:

* Monthly churn prediction rates
* Average churn probability scores
* Customer risk distribution

Significant changes may indicate degradation in model performance.

---

## Retraining Recommendation

Recommended retraining schedule:

```text
Every 3–6 months
```

Earlier retraining may be required if:

* Data drift is detected
* Business conditions change significantly
* Customer behavior patterns evolve

---

# 9. When the Model Should NOT Be Used

The model is designed as a decision-support system and should not be used in isolation.

---

## High-Stakes Individual Decisions

The model should not be used as the sole basis for:

* Account termination
* Service denial
* Customer exclusion
* Pricing decisions
* Contract decisions

Human review must always be involved.

---

## Different Business Domains

The model was trained on D2C customer behavior and should not be directly applied to:

* Banking customers
* Healthcare customers
* Insurance customers
* Telecom customers

without retraining and validation.

---

## Major Business Changes

The model should not be used without revalidation when:

* New product categories are introduced
* Marketing strategy changes significantly
* Customer acquisition channels change substantially
* Economic conditions change dramatically

---

## Low-Quality Input Data

Predictions should not be trusted if:

* Large numbers of features are missing
* Data collection processes fail
* Significant data quality issues are detected

---

# 10. Key Churn Drivers Identified

Feature importance analysis identified the following major contributors to churn prediction:

1. Recency Days
2. Monetary Value (180 Days)
3. Days Since Signup
4. Last Visit Days Ago
5. Product Views (30 Days)
6. Return Rate (180 Days)
7. Average Discount Percentage
8. Resolution Hours
9. Average Rating
10. Frequency (180 Days)

The strongest predictor was **Recency Days**, indicating that recent customer inactivity is the most influential indicator of future churn.

---

# 11. Conclusion

The Gradient Boosting Churn Prediction Model provides a reliable mechanism for identifying customers at risk of churn and enables proactive retention strategies.

The model achieves strong predictive performance across multiple evaluation metrics while maintaining a low number of missed churn customers.

When combined with regular monitoring, fairness checks, periodic retraining, and human oversight, the model can serve as an effective decision-support tool for customer retention and churn management initiatives.
