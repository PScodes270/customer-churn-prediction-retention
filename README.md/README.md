# Customer Churn Prediction & Retention Analytics

## About the Project

Customer churn means customers stop using a company's services. For a business, losing customers can affect both revenue and growth. So, it is useful to understand why customers leave and which customers might leave in the future.

In this project, I worked with telecom customer data to study churn patterns and build machine learning models that can predict the likelihood of a customer leaving. I also looked at how the results could help a business decide which customers need more attention.

## Dataset

I used the IBM Telco Customer Churn dataset, which contains **7,043 customer records**.

It includes information about customer tenure, contract type, internet services, monthly charges, payment methods, and churn status.

## Tools Used

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- XGBoost
- SHAP
- Jupyter Notebook

## What I Did

### 1. Data Cleaning and Preparation

I first checked the dataset for missing values, duplicate records, and incorrect data types. I converted the relevant columns into suitable formats and prepared the data for analysis.

I also created a few additional features, including average monthly spend, tenure groups, and the total number of services used by each customer.

### 2. Exploratory Data Analysis

I created plots to understand the relationship between customer details and churn. I looked at contract types, tenure, monthly charges, internet services, payment methods, and other service-related information.

Some patterns stood out during the analysis:

- Customers with month-to-month contracts had higher churn.
- Customers who had been with the company for less time were more likely to leave.
- Customers with higher monthly charges showed more churn.
- Fiber optic customers had higher churn than DSL customers in this dataset.
- Electronic check users showed higher churn than customers using other payment methods.

These patterns helped me understand which customer groups might need more attention.

### 3. Machine Learning Models

I trained and compared four classification models:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost

I also tuned the Random Forest and XGBoost models using GridSearchCV. To compare the models, I checked accuracy, precision, recall, F1-score, and ROC-AUC.

### Model Comparison

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 74.88% | 51.75% | 78.88% | 62.50% | 84.91% |
| Decision Tree | 73.95% | 50.60% | 79.14% | 61.73% | 84.11% |
| Random Forest | 76.79% | 54.49% | 76.20% | 63.55% | 85.32% |
| XGBoost | 80.84% | 66.77% | 55.35% | 60.53% | 85.62% |
| Tuned Random Forest | 75.87% | 53.02% | 79.68% | 63.68% | 85.20% |
| Tuned XGBoost | 80.20% | 65.37% | 54.01% | 59.15% | 85.55% |

I selected the tuned Random Forest as the final model because it had the highest F1-score and recall among the models compared after tuning. XGBoost had higher accuracy, but it missed more customers who actually churned.

### 4. Understanding the Results

I used feature importance and SHAP to look at which factors influenced the model's predictions.

Some of the important factors included contract type, internet service, customer tenure, technical support, online security, and monthly charges.

These results show patterns in the dataset. They do not necessarily mean that any single factor directly causes a customer to leave.

### 5. Customer Risk Groups

I divided customers into three groups using their predicted churn probabilities.

| Risk group | Predicted churn probability | Number of customers |
|---|---|---:|
| High risk | 70% or above | 1,557 |
| Medium risk | 40% to below 70% | 1,845 |
| Low risk | Below 40% | 3,641 |

This grouping can help a business prioritize customers for follow-up. The groups represent estimated risk, not a guarantee that a customer will churn.

## Business Recommendations

Based on the analysis, a business could:

- Contact high-risk customers and understand their concerns.
- Review pricing and service issues for customers paying higher monthly charges.
- Give new customers better onboarding and support.
- Look at ways to improve the experience of month-to-month customers.
- Make technical support and online security options easier to understand and access.
- Track whether retention offers actually reduce churn.

## Project Files

- `data/` — Dataset used in the project
- `notebooks/` — Jupyter notebook containing the analysis
- `plots/` — Graphs created during EDA, model evaluation, and interpretation
- `ppt/` — Business presentation
- `report/` — Business analysis report
- `requirements.txt` — Python packages needed to run the notebook

## How to Run the Project

1. Download or clone this repository.
2. Open a terminal in the project folder.
3. Install the required packages:

```bash
pip install -r requirements.txt
```

4. Open `notebooks/customer_churn_analysis.ipynb` in Jupyter Notebook or JupyterLab.
5. Run the notebook cells in order.

## Final Thoughts

This project helped me work through the main steps of a data science problem: cleaning data, exploring patterns, training models, comparing their results, and using the findings to suggest possible business actions.

The final model and risk groups provide a starting point for identifying customers who may need attention. Before using such predictions in a real business, the model would need further validation on new customer data.