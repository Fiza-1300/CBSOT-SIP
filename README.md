# Customer Churn Prediction, Retention and Segmentation Analysis

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



---

### Approach 2: Hyperparameter Tuning
I experimented with different numbers of trees and tree depths to find the optimal configuration.

**Best Configuration:** n_estimators=350, max_depth=11

**Results:**

| Metric | Score |
|--------|-------|
| Accuracy | 79% |
| Precision (Churn) | 60% |
| Recall (Churn) | 72% |
| F1 Score (Churn) | 66% |



The tuned model significantly improved recall from 52% to 72%.

---

### Approach 3: Feature Importance Analysis
I analyzed which features matter most for predicting churn.

**Top Features:**
1. Tenure Months
2. Monthly Charges
3. Contract Type
4. Total Charges
5. Tech Support
6. Payment Method

I dropped the least important features and retrained the model.

**Results:**

| Metric | Score |
|--------|-------|
| Accuracy | 78% |
| Precision (Churn) | 60% |
| Recall (Churn) | 72% |
| F1 Score (Churn) | 66% |

---

### Approach 4: Finding Best Combination
I systematically tested different combinations of trees and depth values.

**Top 5 Results:**

| Trees | Depth | Accuracy | Recall | Precision | F1 Score |
|-------|-------|----------|--------|-----------|----------|
| 200 | 5 | 80% | 66% | 56% | 61% |
| 200 | 10 | 80% | 66% | 56% | 61% |
| 200 | 15 | 80% | 66% | 56% | 61% |
| 200 | 20 | 80% | 65% | 56% | 60% |
| 100 | 5 | 80% | 65% | 56% | 60% |

---

### Final Model Performance
After all approaches, I selected **RandomForestClassifier with n_estimators=300, max_depth=10, and balanced weights**.

**Cross-Validation Scores (5-fold):**

| Metric | Score |
|--------|-------|
| Mean Accuracy | 78% |
| Mean Recall | 73% |
| ROC-AUC | 0.86 |

**Confusion Matrix:**

Predicted
No Yes
Actual No 907 102
Actual Yes 191 209


---

### Model Comparison Summary

| Approach | Accuracy | Precision | Recall | F1 Score |
|----------|----------|-----------|--------|----------|
| Baseline | 80% | 68% | 52% | 59% |
| Balanced Weights | 79% | 67% | 52% | 59% |
| Hyperparameter Tuned | 79% | 60% | 72% | 66% |
| Feature Selection | 78% | 60% | 72% | 66% |
| Final Model (CV) | 78% | - | 73% | - |

---

## Customer Segmentation

I used **K-Means clustering** to group customers based on their behavior.

**The Three Customer Segments:**

### Segment 0: Budget Loyal Customers
- **Average Tenure:** 35 months
- **Average Monthly Charges:** $50
- **Churn Probability:** 20%
- **Characteristics:** Stable, value-driven customers
- **Strategy:** Maintain pricing, reward loyalty

### Segment 1: High Risk New Customers
- **Average Tenure:** 8 months
- **Average Monthly Charges:** $75
- **Churn Probability:** 65%
- **Characteristics:** Recent customers at high risk
- **Strategy:** Welcome programs, early check-ins

### Segment 2: Loyal Premium Customers
- **Average Tenure:** 40 months
- **Average Monthly Charges:** $95
- **Churn Probability:** 35%
- **Characteristics:** Long-term, high spenders
- **Strategy:** Rewards program, premium features

---

## Business Recommendations

### For High Risk New Customers:
- Offer welcome discounts for first 6 months
- Set up early check-in calls at 1 month and 3 months
- Provide free tech support trial
- Offer incentives to sign yearly contracts

### For Loyal Premium Customers:
- Create loyalty rewards program
- Offer premium features at reduced rates
- Send personalized service updates
- Provide dedicated support line

### For Budget Loyal Customers:
- Maintain competitive pricing
- Upsell additional services carefully
- Reward tenure with small perks
- Focus on value communication

### Overall Strategy:
- Convert month-to-month customers to yearly contracts
- Proactive support for high-risk customers
- Monitor early tenure period closely
- Use churn probability scores for targeted retention

---

## Technical Details

**Tools Used:**
- Python with Pandas and NumPy for data handling
- Matplotlib and Seaborn for visualizations
- Scikit-learn for machine learning
- Google Colab for development

---

## Files in This Project

- `CBSOT_SIP_1.ipynb` - Complete analysis and modeling notebook
- `Telco_customer_churn.xlsx` - The dataset used
- `README.md` - Project documentation

---

## How to Run This Project

1. Open the notebook in Google Colab
2. Upload the Excel file to the Colab environment
3. Run all cells sequentially
4. View the visualizations and results

---

## Future Improvements

- Build a web app for real-time churn prediction
- Add SHAP explanations for model interpretability
- Try XGBoost or LightGBM for better performance
- Create automated reports for business teams

---

## Contributors

- **Fiza-1300** - Project Creator

---

## License

This project is licensed under the MIT License.
