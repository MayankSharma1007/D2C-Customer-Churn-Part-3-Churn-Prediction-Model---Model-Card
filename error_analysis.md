# Error Analysis Report

## Project Information

| Field               | Value                                                 |
| ------------------- | ----------------------------------------------------- |
| Project             | D2C Customer Churn Intelligence & Retention Analytics |
| Model               | Gradient Boosting Classifier                          |
| Test Samples        | 336                                                   |
| Correct Predictions | 262                                                   |
| False Positives     | 56                                                    |
| False Negatives     | 18                                                    |

---

# 1. Objective

The purpose of this report is to investigate model prediction errors and understand why certain customers were incorrectly classified.

Error analysis is essential because overall evaluation metrics alone do not reveal the nature of model mistakes or their business implications.

This report focuses on:

* False Positive analysis
* False Negative analysis
* Customer-level examples
* Business impact assessment
* Recommendations for improvement

---

# 2. Error Summary

| Error Type          | Count |
| ------------------- | ----- |
| Correct Predictions | 262   |
| False Positives     | 56    |
| False Negatives     | 18    |

---

# 3. False Positive Analysis

## Definition

False Positives are customers predicted as churners by the model but who actually remained active.

Mathematically:

```text
Actual Churn = 0
Predicted Churn = 1
```

Total False Positives:

```text
56 Customers
```

---

## Business Risk

False Positives may lead to:

* Unnecessary retention offers
* Additional discount expenditure
* Increased marketing costs
* Inefficient CRM resource allocation

However, the business impact is generally moderate because the customer remains active.

---

## Customer Examples (False Positives)

### Example 1

| Feature               | Value         |
| --------------------- | ------------- |
| City Tier             | Tier 2        |
| Age Group             | 35-44         |
| Acquisition Channel   | Google Search |
| Recency Days          | 72            |
| Frequency             | 1             |
| Monetary Value        | 899.51        |
| Predicted Probability | 0.665         |

Observation:

Customer showed moderate inactivity and low purchase frequency, causing the model to classify the customer as churn-risk despite remaining active.

---

### Example 2

| Feature               | Value         |
| --------------------- | ------------- |
| City Tier             | Tier 1        |
| Age Group             | 25-34         |
| Acquisition Channel   | Google Search |
| Recency Days          | 42            |
| Frequency             | 1             |
| Monetary Value        | 644.61        |
| Predicted Probability | 0.510         |

Observation:

Low purchase frequency and limited engagement contributed to churn prediction.

---

### Example 3

| Feature             | Value     |
| ------------------- | --------- |
| City Tier           | Tier 1    |
| Acquisition Channel | Instagram |
| Loyalty Tier        | Silver    |
| Recency Days        | 92        |
| Frequency           | 2         |
| Monetary Value      | 1622.28   |

Observation:

Long inactivity period outweighed strong spending history.

---

### Example 4

Customer with:

* Recency = 28 days
* Frequency = 2
* High monetary value
* Influencer acquisition channel

Observation:

Customer behavior resembled historical churners despite remaining active.

---

### Example 5

Customer with:

* Recency = 55 days
* Frequency = 3
* Loyalty Tier unavailable
* Moderate engagement

Observation:

Temporary inactivity triggered churn prediction.

---

# Common False Positive Pattern

Most False Positive customers exhibited:

* Higher recency values
* Lower purchase frequency
* Missing loyalty information
* Reduced campaign engagement

These characteristics are historically associated with churn behavior.

---

# 4. False Negative Analysis

## Definition

False Negatives are customers predicted as retained customers who actually churned.

Mathematically:

```text
Actual Churn = 1
Predicted Churn = 0
```

Total False Negatives:

```text
18 Customers
```

---

## Business Risk

False Negatives represent the most expensive error type.

Potential consequences include:

* Loss of customer revenue
* Missed retention opportunities
* Reduced customer lifetime value
* Increased future acquisition costs

These customers receive no intervention because the model incorrectly assumes they will remain active.

---

## Customer Examples (False Negatives)

### Example 1

| Feature               | Value    |
| --------------------- | -------- |
| City Tier             | Tier 1   |
| Age Group             | 18-24    |
| Loyalty Tier          | Platinum |
| Recency Days          | 14       |
| Frequency             | 3        |
| Monetary Value        | 2456.91  |
| Predicted Probability | 0.015    |

Observation:

Customer appeared highly engaged and valuable but unexpectedly churned.

---

### Example 2

| Feature               | Value  |
| --------------------- | ------ |
| City Tier             | Tier 2 |
| Age Group             | 25-34  |
| Recency Days          | 57     |
| Frequency             | 2      |
| Monetary Value        | 937.32 |
| Predicted Probability | 0.124  |

Observation:

Behavior appeared healthy despite eventual churn.

---

### Example 3

| Feature        | Value  |
| -------------- | ------ |
| City Tier      | Tier 2 |
| Age Group      | 18-24  |
| Recency Days   | 20     |
| Frequency      | 1      |
| Monetary Value | 627.36 |

Observation:

Recent activity misled the model into predicting retention.

---

### Example 4

Customer with:

* Recency = 50 days
* Gold loyalty tier
* Active email engagement
* Multiple wishlist additions

Observation:

Positive engagement indicators masked future churn intent.

---

### Example 5

Customer with:

* Recency = 9 days
* Frequency = 1
* Recent website visit
* Active browsing behavior

Observation:

Short-term activity caused the model to underestimate churn risk.

---

# Common False Negative Pattern

Most False Negative customers demonstrated:

* Recent website activity
* Strong monetary value
* Email engagement
* Cart additions
* Loyalty membership

These positive signals reduced predicted churn probability despite actual churn.

---

# 5. Comparative Error Assessment

| Error Type     | Count | Business Severity |
| -------------- | ----- | ----------------- |
| False Positive | 56    | Medium            |
| False Negative | 18    | High              |

Although False Positives occur more frequently, False Negatives are significantly more damaging because they directly result in customer loss.

---

# 6. Key Findings

1. The model prioritizes churn detection and therefore produces more False Positives than False Negatives.

2. Only 18 churn customers were missed.

3. Most False Positives exhibited inactivity patterns similar to actual churners.

4. Most False Negatives appeared highly engaged shortly before churning.

5. Recency Days remains the strongest factor influencing prediction decisions.

---

# 7. Recommendations

To reduce future errors:

* Incorporate customer sentiment analysis.
* Track purchase sequences over time.
* Include product-level interaction features.
* Monitor customer engagement trends.
* Retrain the model quarterly.
* Add behavioral trend features instead of relying solely on snapshots.

---

# 8. Conclusion

The Gradient Boosting model achieved strong predictive performance with relatively few False Negatives. While 56 False Positives were generated, only 18 actual churn customers were missed.

From a business perspective, this error profile is acceptable because retaining potentially at-risk customers is generally preferable to failing to identify genuine churners. The model is therefore suitable for deployment in customer retention and churn prevention workflows.
