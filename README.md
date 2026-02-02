# 🍔 QuickBite Crisis Impact Analytics & ML Platform

## 📌 Project Overview

The **QuickBite Crisis Impact Analytics & ML Platform** is an end-to-end **Data Engineering + Analytics + Machine Learning** project built entirely on **Databricks**. The goal of this project is to analyze the impact of a crisis period on a food delivery business and provide **data-driven insights** and **predictive intelligence** to support business recovery.

This project was developed as a **self-directed capstone** and demonstrates production-grade practices across data ingestion, transformation, optimization, analytics, ML experimentation, and orchestration.

---

## 🎯 Business Problem Statement

During crisis periods (e.g., economic downturns, pandemics), food delivery platforms experience:

* Decline in order volumes
* Increase in cancellations
* SLA breaches due to delivery delays
* Drop in customer ratings
* Customer churn

**Objective:**

* Quantify the business impact of the crisis
* Identify cities and restaurants most affected
* Understand customer behavior changes
* Predict customer churn using ML
* Enable data-backed recovery strategies

---

## 🏗️ Architecture Overview

**Platform:** Databricks (Serverless Compute)

**Architecture Pattern:** Medallion Architecture

```
Source Data
   │
   ▼
Bronze Layer (Raw Ingestion)
   │
   ▼
Silver Layer (Cleaned & Enriched Data)
   │
   ▼
Gold Layer (Business Aggregates)
   │
   ▼
Analytics Dashboards & ML Models
```

---

## 🧱 Data Architecture (Medallion)

### 🟤 Bronze Layer

**Purpose:** Raw data ingestion without transformation

* Source: Public/Synthetic dataset
* Stored as Delta tables
* Minimal schema enforcement

Example tables:

* `fact_orders`
* `fact_ratings`
* `fact_orderitems`
* `fact_deliveryperformance`
* `dim_customers`
* `dim_deliverypartner`
* `dim_menuitem`
* `dim_restaurants`

---

### ⚪ Silver Layer

**Purpose:** Data cleaning, enrichment, and business logic

Key transformations:

* Timestamp standardization (`to_timestamp`)
* City & restaurant enrichment
* Cancellation flags
* Delivery delay calculations
* SLA breach indicators
* Crisis phase classification (Pre-Crisis / Crisis / Recovery)
* Sentiment scoring from customer reviews

Example tables:

* `orders_enriched`
* `ratings_enriched`
* `customer_behavior`

**Data Quality Checks:**

* Null handling
* Schema validation
* Duplicate removal

---

### 🟡 Gold Layer

**Purpose:** Analytics-ready business aggregates

Key Gold tables:

* `monthly_orders_trend`
* `city_order_decline`
* `restaurant_order_decline`
* `cancellation_trends`
* `delivery_sla_summary`
* `monthly_ratings_trend`
* `revenue_impact`
* `loyalty_churn`
* `high_value_customer_decline`

**Performance Optimizations:**

* Delta Lake storage
* `OPTIMIZE`
* `Z-ORDER` on frequently filtered columns

---

## 📊 Analytics & Insights

The Gold layer enables rich analytics such as:

* Order & revenue trends across crisis phases
* City-wise and restaurant-wise impact analysis
* Cancellation rate comparison
* Delivery SLA degradation
* Rating & sentiment shifts
* Customer loyalty and churn patterns

These tables are directly consumed by **Databricks SQL Dashboards**.

---

## 🧠 Machine Learning Component

### 🔍 ML Use Case: Customer Churn Prediction

**Problem Framing:**
Predict whether a customer will churn during a crisis period based on pre-crisis behavior.

**Features Used:**

* Pre-crisis order count
* Average order value
* Average delivery delay
* Average rating
* Average sentiment score

**Model:**

* Logistic Regression (chosen for explainability)

**Evaluation Metric:**

* AUC (Area Under ROC Curve)

**Result:**

* Achieved AUC ≈ **0.72**

**MLflow:**

* Experiments tracked with parameters & metrics
* Runs organized by project and use case

> Note: Due to Databricks Serverless + Unity Catalog constraints, model artifact logging was skipped. Metrics and experiment lineage were fully tracked using MLflow.

---

## 🔄 Orchestration (Databricks Jobs)

The entire pipeline is automated using **Databricks Workflows (Jobs)**.

### Job Flow:

1. Bronze Ingestion
2. Silver Transformations
3. Gold Aggregations
4. Delta Optimization (`OPTIMIZE`, `Z-ORDER`)
5. ML Training & Scoring

**Key Features:**

* Task dependencies
* Retry policies
* Serverless compute
* Repeatable & production-ready execution

---

## 🔐 Governance & Best Practices

* Unity Catalog for data organization
* Schema separation (Bronze / Silver / Gold)
* Read/write access separation
* Delta Lake ACID guarantees
* Scalable, cloud-native design

---

## 📁 Project Structure

```
QuickBite/
├── 01_Bronze_Ingestion
├── 02_Silver_Transformations
├── 03_Gold_Aggregations
├── 04_Optimize_Tables
├── 05_ML_Modeling
├── dashboards/
├── README.md
```

---

## 📌 Key Business Outcomes

* Identified top cities and restaurants impacted during crisis
* Quantified revenue and order volume decline
* Measured delivery SLA degradation
* Detected loyal customer churn patterns
* Built predictive model to target high-risk customers

---

## 🧪 Technologies Used

* Databricks (Serverless)
* Apache Spark (PySpark & SQL)
* Delta Lake
* MLflow
* Unity Catalog
* Databricks SQL Dashboards

---

## 📽️ Demo & Presentation

* Architecture walkthrough
* Data pipeline execution
* Dashboard insights
* ML model explanation

(Linked in the LinkedIn post submission)

---

## 🔗 Submission & Credits

**Platform:** Databricks

**Community Tags:**

* Databricks
* Codebasics
* Indian Data Club

---

## 🏁 Conclusion

This project demonstrates how Databricks can be used to build a **scalable, governed, and intelligent analytics platform** that combines data engineering, analytics, and machine learning to solve real-world business problems.

---

⭐ *If you found this project insightful, feel free to connect and discuss data engineering & analytics!*





