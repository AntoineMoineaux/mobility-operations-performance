# 🚕 Mobility Operations Performance Dashboard

End-to-end data analytics project analyzing operational performance, cancellation risk, and decision prioritization for a mobility marketplace using SQL and Power BI.

---

## 🎯 Objective
Provide actionable insights to help operations teams identify where to focus efforts based on revenue, trip volume, and cancellation risk.

---

## 🧠 Business Context
Strong revenue growth can hide operational inefficiencies such as increasing cancellation rates or supply-demand imbalances.  
This project aims to surface these risks early and support data-driven prioritization at the city level.

---

## ❓ Key Business Questions
- Which cities generate the most revenue and trip volume?
- Where are cancellation rates increasing?
- Which cities require immediate action versus monitoring?
- How can operational priorities be structured pragmatically?

---

## 📦 Dataset
- Type: Synthetic dataset inspired by real-world mobility operations
- Granularity: One row per trip
- Main entity: trips
- Key dimensions: time, city, driver
- Status values:
  - completed (generates revenue)
  - cancelled_by_customer
  - cancelled_by_driver
  - no_show

---

## 🏗️ Data Model
The project uses a simple and efficient fact-based model:

- **fact_trips**: trip-level operational data

Business rules:
- Revenue is generated only for completed trips
- Cancelled and no-show trips generate zero revenue

---

## ⚙️ Methodology
1. Data schema definition (`01_create_tables.sql`)
2. Data cleaning and standardization (`02_data_cleaning.sql`)
3. Data enrichment and KPI-ready transformations (`03_transformations.sql`)
4. Business KPI queries (`04_kpi_queries.sql`)
5. Visualization and storytelling in Power BI

---

## 📊 Dashboard Overview
The Power BI dashboard is structured into three pages:

- **Executive Overview**  
  High-level view of revenue, trip volume, and cancellation trends.

- **Operational Performance**  
  City-level analysis of volume, revenue, and cancellation risk to identify operational pressure points.

- **Strategic Recommendations**  
  Action-oriented view translating performance metrics into operational status and priority levels (P0 / P1 / P2).

---

## 📊 Dashboard Screenshots

### Executive Overview
![Executive Overview](powerbi/screenshots/executive_overview.png)

### Operational Performance
![Operational Performance](powerbi/screenshots/operational_performance.png)

### Strategic Recommendations
![Strategic Recommendations](powerbi/screenshots/strategic_recommendations.png)

---

## 🔍 Key Insights
- Revenue growth is primarily driven by increased trip volume rather than improved efficiency.
- High-revenue cities can also present elevated cancellation risk.
- Most cancellations are driven by customer or driver behavior rather than technical failures.

---

## 🧭 Recommendations
- **P0**: Immediate action in high-revenue cities with rising cancellation rates.
- **P1**: Monitor performance and stabilize operations in growth markets.
- **P2**: Optimize efficiency in stable, lower-risk cities.

---

## 🔁 Reproducibility
1. Execute SQL scripts located in the `/sql` folder in numerical order.
2. Open the Power BI file located in `/powerbi`.
3. Refresh data connections if needed.

---

## ⚠️ Limitations & Trade-offs
This project was intentionally designed to balance analytical depth, clarity, and portfolio relevance.

### Data Scope
- Synthetic dataset; no real user behavior or financial constraints.
- No customer lifecycle data (retention, churn, LTV).
- Missing city context such as population or driver supply.

### Modeling Choices
- A single fact table (`fact_trips`) was used to keep the model simple and readable.
- City and driver dimensions were not normalized to avoid unnecessary complexity.
- Business rules (e.g. revenue only for completed trips) were explicitly enforced for KPI consistency.

### Analytical Trade-offs
- The analysis focuses on operational risk rather than behavioral causality.
- Priority thresholds are illustrative and would normally be refined with domain experts.
- No predictive modeling is included; the analysis remains descriptive and diagnostic.

### Visualization Scope
- The dashboard prioritizes decision-making and actionability over exhaustive metric coverage.
- Additional segmentation (time of day, driver tenure, distance buckets) could deepen insights.

These trade-offs were made deliberately to ensure the project remains clear, realistic, and aligned with real-world data analyst responsibilities.

---

## 🚀 Next Steps
- Add predictive indicators for cancellation risk.
- Integrate city metadata for deeper operational context.
- Automate alerts for critical performance thresholds.
