# Customer Churn Prediction & Segmentation

## Project Overview
Customer churn is one of the biggest challenges faced by telecom companies. Losing existing customers directly impacts revenue and business growth. This project uses Machine Learning techniques to predict whether a customer is likely to leave the company and applies customer segmentation to identify different groups of customers for targeted business strategies.

The project combines:
- Exploratory Data Analysis (EDA)
- Data Cleaning and Preprocessing
- Customer Churn Prediction using Random Forest
- Customer Segmentation using K-Means Clustering
- Business Recommendations for Retention

---

## What I Built
The project has three main parts:

- **Data Analysis** - Understanding what drives customer churn through visualizations
- **Churn Prediction** - Building and improving machine learning models
- **Customer Segmentation** - Grouping customers into meaningful clusters

---

## Data Exploration

### Key Findings:

**Tenure vs Churn**
Customers with shorter tenure (less than 12 months) are much more likely to churn. The average tenure for customers who left is significantly lower than those who stayed.

**Monthly Charges**
Customers who churn tend to have higher monthly charges. The median monthly charge for churned customers is around $80, compared to $65 for loyal customers.

**Contract Type**
Month-to-month contracts have the highest churn rate. Over 40% of customers on month-to-month contracts end up leaving, while customers on yearly contracts rarely churn.

**Payment Method**
Electronic check users churn the most, while credit card and bank transfer users are more loyal.

**Tech Support**
Customers without tech support are more likely to churn, showing the importance of support services.

---

## Data Preparation
Before building models, I cleaned the data:

- Converted Total Charges to numeric format
- Filled missing Total Charges values with 0
- Removed unnecessary columns like CustomerID, location data
- Created dummy variables for categorical columns using one-hot encoding

---

## Machine Learning Models

### Baseline Model
First, I trained a basic Random Forest with 100 trees.

**Results:**

| Metric | Score |
|--------|-------|
| Accuracy | 80% |
| Precision (Churn) | 68% |
| Recall (Churn) | 52% |
| F1 Score (Churn) | 59% |

---

### Approach 1: Handling Class Imbalance
The dataset has fewer churn cases than non-churn cases. I used `class_weight='balanced'` to give more importance to the minority class.

**Results:**

| Metric | Score |
|--------|-------|
| Accuracy | 79% |
| Precision (Churn) | 67% |
| Recall (Churn) | 52% |
| F1 Score (Churn) | 59% |

**Classification Report:**
