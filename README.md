# 🚚 Route Delay & ETA Risk Analytics for a Logistics Operation

An end-to-end Data Analytics project analyzing logistics delivery performance to identify route delays, evaluate ETA (Estimated Time of Arrival) risk, and improve operational efficiency through SQL, DAX, and Power BI dashboards.

## 📖 Project Overview

Timely deliveries are critical for logistics operations and customer satisfaction. Delays caused by traffic, weather, workforce performance, and geographic factors can negatively impact delivery efficiency.

This project analyzes 43,739 delivery records to identify the major drivers of delay, monitor ETA risk, evaluate delivery agent performance, and provide actionable, evidence-backed business recommendations through interactive Power BI dashboards.

The project follows a complete analytics workflow — from SQL-based data validation and cleaning to KPI design, DAX measure creation, dashboard development, and business insight generation.

## 🎯 Business Objectives

- Identify the major causes of delivery delays
- Quantify ETA risk using a statistically grounded delay definition
- Evaluate delivery agent performance
- Measure the impact of traffic and weather on delivery time
- Compare delivery performance across geographic areas, accounting for sample size
- Monitor logistics KPIs using interactive dashboards
- Provide business recommendations backed by measurable evidence, not assumption

## 🛠️ Technologies Used

- **MySQL** – Data import, validation, and cleaning
- **Microsoft Power BI** – Dashboard development and visualization
- **DAX** – Calculated columns and KPI measures
- **CSV Dataset** – Source data (Amazon Delivery dataset, 43,739 records, 16 columns)

## 📐 Key Definitions

These two definitions anchor every KPI and chart in this project. They are stated explicitly here because the underlying dataset has no published SLA to reference.

**Delayed vs. On-Time** — A delivery is classified as **Delayed** if `Delivery_Time > 125 minutes`, the dataset's own mean and median delivery time, and **On-Time** otherwise. This threshold was chosen deliberately over an arbitrary round number because it reflects the operation's actual baseline performance. In a production setting with a real SLA, this threshold would be replaced by the contracted delivery window.

**High Performer vs. Average Performer** — Delivery agents with an average rating ≥ 4.5 are classified as **High Performers**; all others are **Average Performers**. This threshold sits at the top of the rating distribution and isolates a genuinely differentiated group rather than splitting the dataset roughly in half.

---

## 📂 Project Workflow
## 🗄️ SQL Data Validation & Cleaning

The dataset was validated and cleaned using MySQL before visualization.

- Imported dataset into MySQL (`logistics_analytics.amazon_delivery`)
- Verified table structure and column types (`DESCRIBE`)
- Checked and resolved 54 missing `Agent_Rating` values (imputed with dataset mean, 4.63)
- Checked and resolved 91 missing `Weather`/`Traffic` values (excluded from weather/traffic-specific aggregations rather than imputed, since no defensible substitute value exists for a categorical condition)
- Verified 0 duplicate Order IDs
- Capped 53 invalid `Agent_Rating` values (>5) to the valid 1–5 scale
- Validated `Delivery_Time` — confirmed 0 rows with values ≤ 0
- **Flagged but not silently altered:** `Agent_Age` contains values as low as 15, which falls outside a plausible licensed-delivery-driver range. This is disclosed here as a data integrity issue for the source system owner to investigate rather than corrected, since the right resolution (drop, cap, or verify against source) depends on information not available in this dataset.
- Prepared clean, analysis-ready dataset for Power BI
- 
- ---

## 📊 Dashboard Overview
### 📈 Dashboard 1 – Executive Overview
**KPIs:** Total Orders · Delay % · On-Time % · Avg Delivery Time · Avg Agent Rating
**Visuals:** Traffic Impact on Delivery Time · Weather Impact on Delivery Time · Vehicle Performance · Area-wise Delivery Performance

### 🚦 Dashboard 2 – Route Delay & ETA Risk Analysis
**Visuals:** Delayed vs On-Time Deliveries · Delayed Orders by Traffic · Delay Time Lost (total minutes across all delayed orders) · Average Delay Time by Vehicle · Weather Impact on Delays · Area-wise Delay Rate

### 👨‍💼 Dashboard 3 – Delivery Agent Performance Analytics
**Visuals:** Average Delivery Time by Age Group · Average Delay Time by Agent Performance · Delay Rate by Agent Performance · Agent Rating Distribution
**Purpose:** Evaluate workforce efficiency and identify performance improvement opportunities.

### 💼 Dashboard 4 – Business Recommendations & Impact
Key Findings · Business Recommendations · Expected Business Impact · Executive Summary

## 🔍 Key Business Insights

- **Traffic congestion is the largest single driver of delay.** Average delivery time rises from 101 minutes (Low traffic) to 148 minutes (Jam) — a 47% increase.
- **Weather has a real, secondary effect.** Cloudy and Fog conditions average 136–138 minutes versus 104 minutes for Sunny — a 32% increase.
- **Area-level delay required a sample-size check before being trusted.** An initial cut showed Semi-Urban deliveries averaging 238 minutes, nearly double every other area. Investigating further showed Semi-Urban represents only 152 of 43,739 orders (0.3% of the dataset), versus 32,698 for Metropolitan (75%). Given this imbalance, the Semi-Urban average is not treated as a reliable basis for a resourcing decision. Instead: Metropolitan drives the largest absolute volume of delayed orders due to scale, while Urban and Other perform best on a per-order basis (104–109 minutes). Semi-Urban is flagged for further data collection, not acted on.
- **High-performing agents (rating ≥ 4.5) show measurably lower delay rates** than Average Performers across traffic and weather conditions, indicating the effect isn't just easier routes being assigned to top agents.
- **46.96% of deliveries are classified as delayed** under the dataset-baseline threshold defined above.

## 💡 Business Recommendations

**1. Route Optimization (highest priority)** — Re-route deliveries around high-traffic zones during Jam/High conditions. Traffic shows the largest measured effect on delay, making this the highest-leverage intervention.

**2. Weather-Aware Scheduling (secondary priority)** — Build forecasted-weather buffers into ETA promises during Cloudy/Fog conditions to close the 32% time gap versus clear-weather deliveries.

**3. Workforce Development** — Formalize the rating ≥ 4.5 threshold into a benchmarking and training program for Average Performers, where the upside is already quantified.

**4. Semi-Urban: Investigate Before Acting** — Rather than reallocate resources to Semi-Urban based on 152 orders, extend data collection for one additional reporting cycle to confirm whether the elevated average reflects a genuine operational gap or a small-sample artifact.

## 📈 Expected Business Impact

- Reduce delivery delays, prioritized by traffic-driven interventions first
- Improve ETA accuracy via a clearly defined, reproducible delay threshold
- Enhance customer satisfaction and workforce productivity
- Avoid resourcing decisions based on statistically unreliable segments
- Enable data-driven logistics planning grounded in disclosed, defensible methodology

## 📁 Repository Structure
Route-Delay-ETA-Risk-Analytics/
│
├── Dataset/
├── SQL/
│   ├── Data_Validation.sql
│   └── Data_Cleaning.sql
├── PowerBI/
│   └── Route_Delay_Analytics.pbix
├── Dashboard_Screenshots/
├── Documentation/
│   ├── Project_Report.pdf
│   └── Presentation.pdf
└── README.md

## ⚠️ Limitations

This analysis is based on a single historical dataset snapshot, not a live feed. Geographic coordinates (latitude/longitude) were available but not yet used to compute delivery distance — see Future Enhancements. The Delayed/On-Time threshold is derived from the dataset's own statistical baseline in the absence of a published SLA; if a formal SLA exists, the analysis should be re-run against that value instead.

## 🚀 Future Enhancements

- Distance-normalized delay metric using existing latitude/longitude fields
- Predictive delay-risk classification using ML (current analysis is descriptive/diagnostic)
- Real-time GPS and live traffic API integration
- Weather API integration for dynamic schedule adjustments
- Automated delay-risk alerting system
- Expanded Semi-Urban sample to validate the area effect flagged above
- Cloud-based dashboard deployment

## 👨‍💻 Author

**Pidaparthi Sai Jayadeep**
B.Tech – Computer Science & Engineering (AI & ML), KL University
Aspiring Data Analyst
Skills: SQL | Power BI | DAX | Data Analytics | Business Intelligence

⭐ If you found this project useful, consider giving it a star!
