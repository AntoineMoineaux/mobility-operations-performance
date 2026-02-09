# 🚕 Mobility Operations Performance Dashboard

> End-to-end data analytics project analyzing operational performance, cancellation risk, and efficiency for a mobility marketplace — from SQL pipeline to Power BI dashboard with actionable recommendations.

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)

---

## 👤 About This Project

I'm **Antoine Moineaux**, Data Analyst. This is the **1st project in my portfolio**, focused on core data analyst skills: SQL data pipeline, KPI design, and business-oriented dashboarding.

Each of my projects showcases a different facet of the data analyst role:

| # | Project | Skills Demonstrated |
|---|---------|-------------------|
| **1** | **This project — Mobility Operations** | **SQL pipeline, Power BI, operational KPIs, priority framework** |
| 2 | [Fitness Retention Analysis](https://github.com/AntoineMoineaux/fitness-retention-analysis) | Product analytics, user retention, behavioral analysis |
| 3 | [TFC Recruitment Analysis](https://github.com/AntoineMoineaux/tfc-recruitment-analysis) | Custom scoring framework, advanced DAX, decision support, domain expertise |

📫 **Contact me**: [LinkedIn](https://www.linkedin.com/in/antoine-moineaux-37a0b6189) · [Email](mailto:antoine.moineaux@gmail.com)

---

## TL;DR

A synthetic mobility marketplace dataset analyzed through a **4-step SQL pipeline** and visualized in a **3-page Power BI dashboard**. The analysis surfaces city-level cancellation risks and translates them into a **P0 / P1 / P2 priority framework** for operational teams.

**Key finding**: High-revenue cities can also carry the highest cancellation risk — volume growth alone doesn't signal operational health. The dashboard identifies which cities need immediate intervention vs. monitoring.

---

## Table of Contents

- [Business Context & Questions](#business-context--questions)
- [Dataset](#dataset)
- [Methodology: 4-Step SQL Pipeline](#methodology-4-step-sql-pipeline)
- [Dashboard](#dashboard)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Limitations & Trade-offs](#limitations--trade-offs)
- [Next Steps](#next-steps)
- [Repo Structure](#repo-structure)
- [How to Run](#how-to-run)
- [Skills Demonstrated](#skills-demonstrated)

---

## Business Context & Questions

Rapid growth in trip volume can mask operational inefficiencies — rising cancellation rates, declining driver efficiency, or revenue concentration risk. This project helps decision-makers identify where to focus attention and which actions to prioritize.

**Key questions addressed:**
1. Which cities drive the majority of revenue and trip volume?
2. Where is cancellation risk increasing — and why?
3. What are the main causes of cancellations (customer, driver, no-show)?
4. Which cities require immediate action (P0) versus monitoring (P2)?

---

## Dataset

| Parameter | Value |
|-----------|-------|
| **Type** | Synthetic dataset inspired by real-world mobility operations |
| **Granularity** | One row per trip |
| **Main entity** | Trips |
| **Key dimensions** | Time, city, driver |
| **Status values** | Completed, cancelled by customer, cancelled by driver, no-show |

**Data model**: Single fact table (`fact_trips`). Revenue is generated only for completed trips — cancelled and no-show trips generate zero revenue.

---

## Methodology: 4-Step SQL Pipeline

| Step | Script | Purpose |
|------|--------|---------|
| 1 | `01_create_tables.sql` | Schema definition and table creation |
| 2 | `02_data_cleaning.sql` | Data cleaning and standardization |
| 3 | `03_transformations.sql` | Data enrichment and KPI-ready transformations |
| 4 | `04_kpi_queries.sql` | Business KPI queries for dashboard consumption |

---

## Dashboard

The Power BI dashboard is structured into 3 pages, each serving a specific audience and purpose:

### Page 1 — Executive Overview
High-level view of revenue, trip volume, and cancellation trends. Designed for executive decision-making.

![Executive Overview](powerbi/screenshots/executive_overview.png)

### Page 2 — Operational Performance
City-level analysis of volume, efficiency, and cancellation risk. Identifies operational pressure points.

![Operational Performance](powerbi/screenshots/operational_performance.png)

### Page 3 — Strategic Recommendations
Action-oriented view translating performance metrics into operational status and priority levels.

![Strategic Recommendations](powerbi/screenshots/strategic_recommendations.png)

---

## Key Insights

- **Revenue growth is volume-driven** — but high-revenue cities can also carry the highest cancellation risk, meaning growth alone doesn't signal operational health
- **Cancellations are behavioral, not technical** — primarily driven by customer and driver decisions rather than system failures, which points to UX and incentive design as levers
- **Risk is concentrated** — a small number of cities account for a disproportionate share of both revenue and cancellation volume, creating operational fragility

---

## Recommendations

The analysis produces a **3-tier priority framework**:

| Priority | Action | Scope |
|----------|--------|-------|
| **P0** | Immediate intervention | High-revenue cities with rising cancellation rates |
| **P1** | Monitor and stabilize | Growth markets needing driver supply management |
| **P2** | Optimize efficiency | Stable, lower-risk cities with incremental improvement potential |

---

## Limitations & Trade-offs

These trade-offs were made deliberately to keep the project clear, actionable, and aligned with real-world data analyst responsibilities:

- **Synthetic data** — no real user behavior or financial constraints; results are illustrative
- **Single fact table** — city and driver dimensions not normalized into separate tables to keep the model simple and readable for a portfolio project
- **Descriptive analysis only** — no predictive modeling; the analysis focuses on diagnosis and prioritization
- **Illustrative thresholds** — operational status and priority cutoffs (P0/P1/P2) would normally be refined with domain experts
- **No city metadata** — population, driver supply size, and market maturity are not included, which limits deeper contextual analysis

---

## Next Steps

- Add predictive indicators for cancellation risk (e.g. trend-based alerts)
- Integrate city metadata (population, driver supply) for contextual benchmarking
- Segment cancellations by time of day, driver tenure, and distance to surface granular patterns
- Automate data refresh and operational alerting

---

## Repo Structure

```
📂 mobility-operations-performance/
├── 📄 README.md
├── 📂 assets/
├── 📂 data/
├── 📂 docs/
├── 📂 powerbi/
│   └── 📂 screenshots/
│       ├── executive_overview.png
│       ├── operational_performance.png
│       └── strategic_recommendations.png
└── 📂 sql/
    ├── 01_create_tables.sql
    ├── 02_data_cleaning.sql
    ├── 03_transformations.sql
    └── 04_kpi_queries.sql
```

---

## How to Run

1. **SQL pipeline**: Execute the scripts in `/sql/` in numerical order (01 → 04)
2. **Dashboard**: Open the Power BI file in `/powerbi/` with Power BI Desktop
3. **Refresh**: Update data connections if needed (`Home > Refresh`)

---

## Skills Demonstrated

| Skill | Application in this project |
|-------|---------------------------|
| **SQL (full pipeline)** | 4-step pipeline: schema creation, cleaning, transformation, KPI queries |
| **Power BI** | 3-page dashboard with executive, operational, and strategic views |
| **KPI design** | Revenue, trip volume, cancellation rate, operational efficiency metrics |
| **Priority framework** | P0/P1/P2 classification translating data into actionable priorities |
| **Data storytelling** | Progressive narrative: overview → diagnosis → recommendations |
| **Documentation** | Transparent methodology, explicit limitations, reproducibility instructions |

---

> *This project uses synthetic data and is part of a data analytics portfolio. Thresholds and recommendations are illustrative and would be refined with domain expertise in a production context.*
