## CUSTOMER CHURN PREDICTION: A MACHINE LEARNING APPROACH FOR SYRIATEL
# PART ONE: BUSINESS UNDERSTANDING

Telecommunications companies like SyriaTel face a major challenge: customer churn — the phenomenon where customers stop using their services after a certain period. Every customer that leaves represents a loss in potential revenue and increases the cost of customer acquisition.
The question SyriaTel faces is: can we predict which customers are likely to leave, before they actually do? This project seeks to address that exact challenge.

The goal of this project is to build a machine learning classifier that can predict whether a customer is likely to churn (i.e., stop doing business with SyriaTel "soon"). If successful, such a system could be used to proactively identify at-risk customers and take steps to retain them — through promotions, targeted outreach, or improved customer service.
if SyriaTel can accurately predict customer churn, they can act before it happens. Preventing even a small percentage of customers from leaving can translate into significant revenue savings. By helping SyriaTel understand the patterns that lead to churn, this model becomes a tool for business intelligence and proactive customer engagement.

Stakeholders;
1)SyriaTel's customer retention team — who can use this model to flag and engage customers likely to churn.

2)Marketing teams — who may use these predictions to create personalized offers.

3)Executives and business analysts — who need data-driven insights to inform strategic decisions about product and service improvements.

## PART TWO: DATA UNDERSTANDING
## 2.1 Data Source
The dataset consists of customer records from SyriaTel, a telecommunications company. Each entry represents an individual customer and includes features that capture various aspects of their interaction with the company. These features span service usage patterns (such as minutes and charges for calls during different times of day), service plan types (such as whether the customer is on an international or voicemail plan), and customer service interactions (like the number of support calls made).
The primary target variable is a field indicating whether or not a customer has churned.

## Reasons why this data is sufficient
This data is structured to capture patterns that may correlate with customer churn, making it highly useful for our goal of predicting which customers are likely to leave the company.it contains behavioral, demographic, and account features that are plausibly related to churn decisions.
## The following steps were taken to prepare the data for modelling:

Missing Values: Checked and confirmed that no missing values were present in the dataset.

Duplicates: Verified that there were no duplicate rows based on a unique identifier.

Data Types & Unique Values: Reviewed the data types and unique values for all columns to understand the structure and detect potential issues.

Outliers: Identified and handled outliers using boxplots to ensure numeric features were within reasonable ranges.

Categorical Data Encoding: Applied one-hot encoding to transform categorical variables into numeric format, increasing the feature set from 21 to 69 columns.

Unnecessary Columns: Removed the 'phone number' column, which was a unique identifier not useful for modeling.

Data Type Conversion: Converted all boolean columns from True/False to 0/1 integers to ensure consistency with numeric features.

Final Dataset Shape: The cleaned dataset now contains 3333 rows and 69 columns, ready for modeling.

Finally, the prepared dataset was saved as cleaned_data.csv for reproducibility.
## Model Comparison Summary

| Model                  | R² Score | MAE     | MSE     | RMSE   | Notes |
|------------------------|----------|---------|---------|--------|-------|
| Linear Regression | 1.0000   | 0.0026  | 0.0000  | 0.0029 | Perfect fit (likely due to a direct formula relationship) |
| Multiple Linear Regression | 1.0000 | 0.0026  | 0.0000  | 0.0029 | Also perfect — confirms strong deterministic relationship |
| Polynomial Regression  | 1.0000   | 0.0026  | 0.0000  | 0.0029 | No improvement over linear models (expected) |
| Ridge Regression       | 1.0000   | 0.0037  | 0.0000  | 0.0045 | Excellent accuracy with slight regularization |
| Lasso Regression       | 0.9999   | 0.0807  | 0.0101  | 0.1005 | Slight drop in accuracy; useful for feature selection |

---

### What’s Next?
We now move on to **Ensemble Modeling**, which combines multiple models to improve prediction performance, especially useful in **classification tasks like churn prediction**.



## 5.1  Evaluation of Final Model

###  Final Model Selected
After building and comparing multiple classification models — including Logistic Regression, Ridge Classifier, Lasso Classifier, and Random Forest — the **Random Forest Classifier** was selected as the final model. It showed the best combination of predictive performance and practical usefulness in identifying customer churn risk.

###  Justification for Model Choice and Metrics
The goal of this project is to predict whether a customer will churn. In a real-world context, the cost of **false negatives** (i.e., failing to identify a churning customer) is higher than false positives. Therefore, metrics like **ROC AUC**, **recall**, and **precision** are particularly important.

Among all models:
- **Random Forest** had a strong ROC AUC score of **0.94**, indicating excellent class separability.
- Its **accuracy** was also high at **94%**.
- It achieved **very high precision (0.97)** for classifying churners (class 1), meaning most flagged churners were truly at risk.
- While recall (0.59 for churners) wasn’t perfect, it still outperformed simpler models and offered a good balance.

This makes Random Forest the most **business-relevant** choice: it detects churners reliably while minimizing unnecessary alerts.

###  Final Evaluation on Holdout Test Set
The final Random Forest model was trained using training data, validated using a validation split, and finally tested on a **completely separate holdout test set**, preventing data leakage.

**Final Test Results:**
- **Accuracy**: 94%
- **ROC AUC Score**: 0.94
- **Confusion Matrix**:
## Tableau Dashboard

The Tableau dashboard explores the relationship between customer churn and call behavior:

- *Sheet 1* shows churn status (True or False) compared to *Total Day Calls*. This helps identify if customers who make more or fewer calls during the day are more likely to churn.
- *Sheet 2* compares churn with *Total Night Calls*, providing insights into how night-time call activity might influence customer retention.
- Both sheets use visualizations that make it easy to spot trends and differences between customers who stayed and those who left.

🔗 [View the dashboard on Tableau Public https://public.tableau.com/authoring/SyriaTelTableauDashboard/Sheet1#1


These visuals support the analysis in the Jupyter notebook by offering a clearer view of behavioral patterns among churned and non-churned 
