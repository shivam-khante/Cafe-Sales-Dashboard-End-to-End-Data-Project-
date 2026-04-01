1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
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
