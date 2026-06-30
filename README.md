# 🚚 Route Delay & ETA Risk Analytics for a Logistics Operation

An end-to-end Data Analytics project focused on analyzing logistics delivery performance to identify route delays, evaluate ETA (Estimated Time of Arrival) risks, and improve operational efficiency through SQL, DAX, and Power BI dashboards.

---

## 📖 Project Overview

Timely deliveries are critical for logistics operations and customer satisfaction. Delays caused by traffic, weather, workforce performance, and geographical factors can negatively impact delivery efficiency.

This project analyzes logistics delivery data to identify the major drivers of delays, monitor ETA risks, evaluate delivery agent performance, and provide actionable business recommendations through interactive Power BI dashboards.

The project follows a complete analytics workflow—from SQL-based data validation and cleaning to KPI creation, dashboard development, and business insights.

---

## 🎯 Business Objectives

- Identify the major causes of delivery delays.
- Analyze ETA (Estimated Time of Arrival) risk.
- Evaluate delivery agent performance.
- Measure the impact of traffic and weather on delivery time.
- Compare delivery performance across different geographic areas.
- Monitor logistics KPIs using interactive dashboards.
- Provide business recommendations to improve operational efficiency.

---

## 🛠️ Technologies Used

- **MySQL** – Data import, validation, and cleaning
- **Microsoft Power BI** – Dashboard development and visualization
- **DAX (Data Analysis Expressions)** – Calculated columns and KPI measures
- **CSV Dataset** – Source data

---

## 📂 Project Workflow

```text
Business Problem
        │
        ▼
Dataset Collection
        │
        ▼
MySQL Database
        │
        ▼
Data Validation
        │
        ▼
Data Cleaning
        │
        ▼
Power BI
        │
        ▼
Data Modeling
        │
        ▼
DAX Measures
        │
        ▼
Interactive Dashboards
        │
        ▼
Business Insights
        │
        ▼
Business Recommendations
```

---

## 🗄️ SQL Data Validation & Cleaning

The dataset was validated and cleaned using MySQL before visualization.

Tasks performed:

- Imported dataset into MySQL
- Verified table structure
- Checked missing values
- Cleaned missing Agent Ratings
- Verified duplicate Order IDs
- Validated categorical values
- Verified numerical ranges
- Prepared clean dataset for Power BI analysis

---

# 📊 Dashboard Overview

## 📈 Dashboard 1 – Route Delay Analytics

### KPIs

- Total Orders
- Delay Percentage
- On-Time Percentage
- Average Delivery Time
- Average Agent Rating

### Visuals

- Traffic Impact on Delivery Time
- Weather Impact on Delivery Time
- Vehicle Performance
- Area-wise Delivery Performance

---

## 🚦 Dashboard 2 – ETA Risk Analysis

### Visuals

- Delayed vs On-Time Deliveries
- Delayed Orders by Traffic
- Delay Time Lost
- Average Delay Time by Vehicle
- Average Delay Time by Weather
- Area Delay Percentage

---

## 👨‍💼 Dashboard 3 – Workforce Analytics

### Visuals

- Average Delivery Time by Age Group
- Average Delay Time by Agent Performance
- Delay Rate by Agent Performance
- Agent Rating Distribution

Purpose:

Evaluate workforce efficiency and identify performance improvement opportunities.

---

## 💼 Dashboard 4 – Business Recommendations & Impact

Includes:

- Key Findings
- Business Recommendations
- Expected Business Impact
- Executive Summary

---

# 📌 Key Performance Indicators (KPIs)

- Total Orders
- Delay Percentage
- On-Time Percentage
- Average Delivery Time
- Delay Time Lost
- Average Agent Rating

---

# 🔍 Key Business Insights

- Traffic congestion is the largest contributor to delivery delays.
- Semi-Urban regions experience the highest delay rates.
- Weather conditions significantly affect delivery performance.
- High-performing delivery agents achieve lower delay rates.
- Nearly half of the deliveries experience delays.
- Delivery performance varies across vehicles and operational regions.

---
# Semi-Urban areas show the highest average delivery time.

However,

this category contains a much smaller number of orders compared to Urban and Metropolitan regions.

Further operational investigation is recommended before making large-scale resource allocation decisions.

---

# 💡 Business Recommendations

### Route Optimization

- Optimize delivery routes for traffic-heavy locations.
- Introduce alternate routes during congestion.

### Resource Allocation

- Deploy additional delivery resources in Semi-Urban areas.
- Balance delivery workloads across operational regions.

### Weather-Aware Operations

- Adjust delivery schedules during adverse weather.
- Improve ETA planning using weather forecasts.

### Workforce Improvement

- Benchmark high-performing delivery agents.
- Provide targeted training for average-performing agents.

---

# 📈 Expected Business Impact

- Reduce delivery delays
- Improve ETA accuracy
- Enhance customer satisfaction
- Increase workforce productivity
- Improve operational efficiency
- Enable data-driven logistics planning

---

# 📁 Repository Structure

```
Route-Delay-ETA-Risk-Analytics/
│
├── Dataset/
│
├── SQL/
│   ├── Data_Validation.sql
│   ├── Data_Cleaning.sql
│
├── PowerBI/
│   └── Route_Delay_Analytics.pbix
│
├── Dashboard_Screenshots/
│
├── Documentation/
│   ├── Project_Report.pdf
│   └── Presentation.pdf
│
└── README.md
```

---

# 🚀 Future Enhancements

- Real-time ETA monitoring
- Predictive delay forecasting using Machine Learning
- Live traffic API integration
- Automated delay alert system
- Cloud-based dashboard deployment

---

# 👨‍💻 Author

**Sai Reddy**

B.Tech – Computer Science & Engineering (AI & ML)

Aspiring Data Analyst

**Skills:** SQL | Power BI | DAX | Data Analytics | Business Intelligence

---

## ⭐ If you found this project useful, consider giving it a Star!
