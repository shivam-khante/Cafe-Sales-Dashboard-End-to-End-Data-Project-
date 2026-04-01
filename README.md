# ☕ Cafe Sales End-to-End Data Project (SQL + Power BI)

## 📌 Project Overview

This project is a complete **end-to-end data analytics solution** that transforms raw cafe sales data into actionable business insights.

It covers:

* Data cleaning & transformation using SQL
* Data modeling with a star schema
* Interactive dashboard creation in Power BI

The project demonstrates how raw transactional data can be converted into **decision-ready insights**.

---

## 🎯 Objectives

* Analyze sales performance and trends
* Identify top and low-performing products
* Understand customer purchasing patterns
* Evaluate payment behavior
* Build a scalable data model for reporting

---

# 🏗️ Data Pipeline Architecture

The project follows a **layered data architecture**:

```
Bronze Layer → Silver Layer → Gold Layer (Star Schema) → Power BI Dashboard
```

---

## 🥉 Bronze Layer (Raw Data)

* Source: `bronze_cafe_sales`
* No transformation applied
* Used as the base ingestion layer

---

## 🥈 Silver Layer (Data Cleaning & Transformation)

* Created view: `silver_cafe_sales`
* Key transformations:

  * Handled null and invalid values
  * Standardized text fields (Item, Location, Payment)
  * Converted data types (numeric & date fields)
  * Recalculated incorrect Total_Spent values
  * Removed inconsistencies

---

## 🥇 Gold Layer (Data Modeling)

### ⭐ Fact Table

* `fact_sales`

  * Transaction_ID
  * Item_ID
  * Payment_ID
  * Location_ID
  * Date_ID
  * Quantity
  * Price_Per_Unit
  * Total_Spent

### 🧩 Dimension Tables

* `dim_item` → Product details
* `dim_payment` → Payment methods
* `dim_location` → Sales channels
* `dim_date` → Date hierarchy

👉 Surrogate keys are generated using **window functions (DENSE_RANK)**

---

## 🔍 Data Quality Checks

* Null value detection
* Duplicate transaction checks
* Negative value validation
* Data consistency validation

These checks ensure **reliable and analysis-ready data**.

---

# 📊 Power BI Dashboard

## 🏠 1. Executive Overview

* Total Revenue: **$84.79K**
* Total Orders: **10K**
* Average Order Value: **$8.89**
* Stable revenue trend with periodic peaks

---

## 📦 2. Product Analysis

* Top Product: **Salad ($18.2K)**
* Revenue concentrated in top 3 products
* Low-performing products identified

---

## 📅 3. Time Analysis

* Peak months: **June & October**
* Strong sales on **Sunday & Monday**
* Weekly demand variation observed

---

## 💳 4. Payment Analysis

* Balanced usage across payment methods
* High “Other” category → data quality issue
* Digital payments trending upward

---

## 📈 Key Metrics (DAX)

```DAX
Total Revenue = SUM(fact_sales[Total_Spent])

Total Orders = DISTINCTCOUNT(fact_sales[Transaction_ID])

AOV = DIVIDE([Total Revenue], [Total Orders])

MoM Growth % = 
DIVIDE(
    [Total Revenue] - [Revenue LM],
    [Revenue LM]
)
```

---

## 🎨 Dashboard Features

* Multi-page interactive dashboard
* KPI cards for quick insights
* Time-based trend analysis
* Product and payment breakdown
* Slicers for dynamic filtering

---

# 📂 Project Structure

```
├── data/
├── images/
├── sql/
│   ├── Data
│   │  ├──dirty_cafe_sales.csv
│   ├── Data Profiling.txt
│   ├── Data Cleaning.txt
│   ├── Dimension_views.sql
│   ├── Fact_view.sql
├── cafe_dashboard.pbix
├── README.md
```

---

# 🗄️ SQL Highlights

* Built a **multi-layer data pipeline**
* Applied strong **data cleaning logic**
* Designed **star schema for analytics**
* Used **joins + window functions**
* Implemented **data validation checks**

---

# 🚀 Business Insights

* Revenue is consistent but dependent on few products
* Opportunity to increase AOV via upselling
* Payment data needs better categorization
* Seasonal trends can guide promotions

---

# 🛠️ Tools & Technologies

* SQL (MySQL)
* Power BI
* DAX
* Data Modeling (Star Schema)

---

# 💡 Future Improvements

* Customer segmentation
* Predictive sales forecasting
* Data quality improvement automation
* Advanced Power BI tooltips & drill-through

---

# 📣 Conclusion

This project showcases:

* End-to-end data analytics workflow
* Strong SQL + Power BI integration
* Data cleaning, modeling, and visualization skills
* Ability to generate meaningful business insights

---

## ⭐ If you like this project

Give it a ⭐ on GitHub and feel free to connect!
