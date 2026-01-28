# Customer-Attrition-Early-Warning
This project demonstrates an end-to-end analytics and machine learning pipeline for a brick-and-mortar retail company.

## Dashboard



The objective is to identify customers who are at high risk of becoming inactive within the next 90 days and to quantify the associated revenue at risk. This enables targeted retention actions instead of broad, inefficient campaigns.

The project combines SQL-based analytics engineering, an explainable machine learning model built in Python, and an executive Power BI dashboard.

## Business Problem
Retail companies often recognize declining sales only after customers have already stopped purchasing.

This project addresses the following business questions:
- Which customers are likely to become inactive in the near future?
- How much revenue is at risk in the next 90 days?
- Which customers should retention teams prioritize?

Instead of modeling traditional subscription churn, this project focuses on customer attrition defined as behavioral inactivity.

## Attrition Definition
A customer is labeled as attrited if no purchase occurs in the following 90 days.

This future-oriented definition turns the model into an early warning system rather than a retrospective report.

## Architecture
The pipeline follows a clear, production-oriented structure:

- CSV and POS data
- loaded into PostgreSQL (staging layer)
- cleaned and standardized in raw schema
- business-ready features built in core schema
- SQL-based feature engineering (RFM, rolling windows, attrition label)
- machine learning in Python using scikit-learn
- risk scores written back to PostgreSQL
- Power BI dashboard consuming model outputs

## Data Model
Raw data sources include:

- Point-of-sale transactions covering three years
- Customer master data
- Product data
- Store and regional data

Feature engineering is performed entirely in SQL and includes:
- Customer-by-month time grid
- RFM-style metrics
- Rolling activity windows (30 and 90 days)
- Recency, tenure, and seasonality features
- Future inactivity-based attrition label

This approach ensures transparency, reproducibility, and scalability.

## Machine Learning Model
The model used is logistic regression.

This choice was made deliberately to prioritize:
- Explainability
- Business interpretability
- Stable and reliable risk scoring

Model evaluation results:
- ROC-AUC approximately 0.76
- Attrition recall approximately 0.50 after threshold optimization
- Precision-Recall AUC approximately 0.63

Key drivers of attrition identified by the model include:
- Long customer tenure combined with declining recent activity
- Increasing recency (days since last purchase)
- Seasonal effects
- Loyalty program membership significantly reducing attrition risk

The model favors interpretability over complexity to support real-world business adoption.

## Power BI Dashboard
The Power BI dashboard is designed for both executives and operational teams.

Key KPIs:
- Total customers
- High-risk customers
- Revenue at risk within the next 90 days

Visualizations include:
- Revenue at risk trend over time
- High-risk customers by city
- Top 20 customers ranked by attrition probability

Customer-level tooltips explain key risk drivers such as recency, recent activity, and tenure, enabling explainable and actionable insights.

## Business Impact
This solution enables early identification of customers showing declining behavior before revenue is lost.

It supports:
- Targeted retention campaigns
- Better allocation of marketing budgets
- Clear prioritization of customers based on risk and revenue impact
- A shift from reactive to proactive decision-making

Instead of analyzing lost revenue, the business can act in advance.

# Technology Stack
- Database: PostgreSQL
- Languages: SQL, Python
- Machine Learning: scikit-learn
- Visualization: Power BI

## Next Improvements
Potential future enhancements include:
- Comparison with tree-based models such as Random Forest or Gradient Boosting
- Incremental and scheduled scoring pipelines
- Integration with CRM systems
- A/B testing of retention strategies

## Author
This project was created as part of a professional analytics portfolio to demonstrate end-to-end analytics engineering, machine learning, and business-oriented reporting.
