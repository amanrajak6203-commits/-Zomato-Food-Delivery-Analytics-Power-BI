# 🍽️ Zomato Food Delivery Analytics | Power BI

### End-to-End Food Delivery Operations & Restaurant Performance Analysis

A comprehensive **Power BI analytics project** designed to analyze food delivery operations, order trends, restaurant performance, delivery efficiency, and cancellation patterns using a dataset containing approximately **1 million orders**.

The project transforms transactional data into interactive business intelligence dashboards, enabling stakeholders to monitor operational KPIs, identify delivery bottlenecks, and make data-driven decisions.

> **Disclaimer:** This is an independent portfolio project using sample/simulated food delivery data. It is not affiliated with or endorsed by Zomato.

---

## 📊 Dashboard Overview

The project consists of **3 interactive Power BI dashboard pages**.

### 1. Executive Overview

![Executive Overview](screenshots/01-executive-overview.png)

Provides a high-level overview of food delivery operations and overall business performance.

**Key KPIs:**
- Total Orders
- Completed Orders
- Order Completion Rate
- Cancelled Orders
- Cancellation Rate

**Business Focus:**
- Monitoring order volumes and fulfillment performance
- Identifying cancellation trends
- Tracking operational performance over time

### 2. Delivery Performance Analytics

![Delivery Performance](screenshots/02-delivery-performance.png)

Analyzes delivery efficiency, preparation time, delays, and on-time delivery performance.

| KPI | Value |
|---|---:|
| Average Delivery Time | 12.38 min |
| Average Preparation Time | 17.47 min |
| Average Fulfillment Time | 41.56 min |
| Delayed Orders | 77,969 |
| Delivery Delay Rate | 8.16% |
| On-Time Delivery Rate | 91.84% |

**Key Visualizations:**
- Monthly Average Delivery Time Trend
- Monthly Delivery Delay Rate
- Delivery Time Variation
- Delivery Reliability Insights

### 3. Restaurant Performance Analytics

![Restaurant Performance](screenshots/03-restaurant-performance.png)

Evaluates restaurant contribution, cuisine popularity, preparation efficiency, and cancellation behavior.

| KPI | Value |
|---|---:|
| Total Restaurants | ~3,000 |
| Total Restaurant Orders | 1,000,000 |
| Average Preparation Time | 17.47 min |
| Restaurant Cancelled Orders | ~15,000 |
| Restaurant Cancellation Rate | 1.54% |
| Average Order Value | ₹380.08 |

**Key Visualizations:**
- Order Volume by Cuisine
- Orders by Outlet Area
- Average Order Value by Price Tier
- Order Distribution by Cuisine

---

## 🎯 Business Objectives

- Analyze order completion and cancellation performance.
- Evaluate delivery efficiency and identify operational delays.
- Compare restaurant performance across cuisines and outlet areas.
- Analyze average order values across restaurant price tiers.
- Identify unusual patterns and potential data-quality issues.
- Build interactive dashboards to support operational decision-making.

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| Power BI Desktop | Dashboard development and visualization |
| DAX | KPI calculations and analytical measures |
| Power Query | Data cleaning and transformation |
| Data Modeling | Fact-dimension relationships |
| Excel / CSV | Source-data storage and import |

---

## 🗂️ Data Model

The project uses a relational data model consisting of fact and dimension tables.

**Fact Tables**
- `fact_orders` — Order transactions, order values, preparation times, delivery durations, and cancellation details.
- `fact_payments` — Payment transaction and attempt details.

**Dimension Tables**
- `dim_customers` — Customer information.
- `dim_restaurants` — Restaurant attributes, cuisine, outlet area, price tier, and ratings.
- `dim_delivery_partners` — Delivery partner information.
- `Dim_Date` — Calendar attributes for time-based reporting.

![Power BI Data Model](docs/data_model.png)

The model uses relationships between fact and dimension tables to support filtering, aggregation, and KPI calculations.

---

## 📐 Key DAX Measures

### Total Orders

```dax
Total Orders =
DISTINCTCOUNT(fact_orders[Order_ID])
```

### Completed Orders

```dax
Completed Orders =
CALCULATE(
    [Total Orders],
    fact_orders[Order_Status] = "Completed"
)
```

*Adjust the status value if the dataset uses a different completed-order label.*

### Order Completion Rate

```dax
Completion Rate % =
DIVIDE(
    [Completed Orders],
    [Total Orders],
    0
)
```

### Average Preparation Time

```dax
Avg Preparation Time =
AVERAGE(fact_orders[Prep_Min])
```

### Average Delivery Time

```dax
Avg Delivery Time =
AVERAGE(fact_orders[Delivery_Min])
```

### Restaurant Cancellation Rate

```dax
Restaurant Cancellation Rate % =
DIVIDE(
    [Restaurant Cancelled Orders],
    [Total Restaurant Orders],
    0
)
```

Percentage measures are formatted as percentages in Power BI.

---

## 💡 Key Business Insights

### 1. Delivery Reliability

Approximately **91.84% of delivered orders were on time**, while **8.16% experienced delays**, highlighting opportunities to improve delivery consistency.

### 2. Delivery Time Variation

Monthly average delivery time remained approximately between **12.0 and 12.9 minutes**, with a noticeable increase in January 2026.

### 3. Restaurant Order Concentration

One restaurant, **Sushi Hub (R02389)**, accounts for approximately **529,404 orders**, representing **52.94% of total orders**.

This unusually high concentration requires further validation to determine whether it represents genuine demand, synthetic-data skew, or a data-quality issue.

### 4. Restaurant Price-Tier Analysis

Average order values differ across restaurant price tiers:

| Price Tier | Average Order Value |
|---|---:|
| Premium | ₹586.70 |
| Mid-range | ₹379.63 |
| Budget | ₹274.50 |

Premium restaurants have the highest average order value, indicating differences in customer spending across restaurant segments.

### 5. Cuisine and Outlet Area Performance

The dashboard highlights significant order concentration within particular cuisines and outlet areas. These patterns should be interpreted cautiously until the restaurant-level outlier has been validated.

---

## 🔍 Data Quality & Limitations

- The dataset is intended for portfolio and analytical demonstration purposes.
- Restaurant-level order concentration is unusually high and requires investigation.
- KPI definitions depend on order status, cancellation classification, and delivery-delay rules.
- Payment transactions may contain multiple records per order and should not be directly summed as order counts.
- The dashboard is not a representation of Zomato's official business performance.

---

## 📁 Repository Structure

```text
Zomato-Food-Delivery-Analytics-PowerBI/
│
├── README.md
├── Zomato_Food_Delivery_Analytics.pbix
│
├── screenshots/
│   ├── 01-executive-overview.png
│   ├── 02-delivery-performance.png
│   └── 03-restaurant-performance.png
│
├── dax/
│   └── measures.md
│
└── docs/
    ├── data_model.png
    ├── data_dictionary.md
    └── business_insights.md
```

---

## 🚀 How to Use

1. Clone or download this repository.
2. Install Microsoft Power BI Desktop.
3. Open `Zomato_Food_Delivery_Analytics.pbix`.
4. Explore the three dashboard pages.
5. Review the DAX measures, data model, and documented insights.

**Note:** If the Power BI report requires external source files, update the data-source paths in Power Query before refreshing.

---

## 📌 Project Outcomes

This project demonstrates practical skills in:

- Power BI dashboard development
- Data cleaning and transformation
- DAX measure development
- Relational data modeling
- KPI design and validation
- Operational and restaurant analytics
- Data visualization and storytelling
- Data-quality investigation

---

## 📄 License & Disclaimer

This project is created for educational and portfolio purposes. Zomato is a trademark of its respective owner. The project is not affiliated with the company.

**⭐ If you find this project useful, consider starring the repository!**
