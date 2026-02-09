# 🚕 Mobility Operations Performance Dashboard

> A city is growing fast. Revenue is up. But behind the numbers, cancellations are quietly rising — and nobody's looking at the right dashboard yet.

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)

---

## 👤 About This Project

I'm **Antoine Moineaux**, Data Analyst. This is the **1st project in my portfolio**, focused on core data analyst fundamentals: building a SQL pipeline from scratch, designing operational KPIs, and translating data into a decision-oriented dashboard.

Each of my projects showcases a different facet of the data analyst role:

| # | Project | Skills Demonstrated |
|---|---------|-------------------|
| **1** | **This project — Mobility Operations** | **SQL pipeline, Power BI, operational KPIs, priority framework** |
| 2 | [Fitness Retention Analysis](https://github.com/AntoineMoineaux/fitness-retention-analysis) | Product analytics, user retention, behavioral analysis |
| 3 | [TFC Recruitment Analysis](https://github.com/AntoineMoineaux/tfc-recruitment-analysis) | Custom scoring framework, advanced DAX, decision support, domain expertise |

📫 **Contact me**: [LinkedIn](https://www.linkedin.com/in/antoine-moineaux-37a0b6189) · [Email](mailto:antoine.moineaux@gmail.com)

---

## TL;DR

A mobility marketplace is growing fast — but **growth is masking operational risk**. Trip volume is up, revenue is up, but cancellation rates are quietly climbing in the highest-revenue cities. This project builds a SQL pipeline and a 3-page Power BI dashboard that surfaces those hidden risks and translates them into a **P0 / P1 / P2 priority framework** for operations teams.

**Key finding**: The cities generating the most revenue are also the most fragile operationally. Volume alone is a misleading health signal.

---

## Table of Contents

- [The Problem](#the-problem)
- [The Core Insight](#the-core-insight)
- [The Method: SQL Pipeline in 4 Steps](#the-method-sql-pipeline-in-4-steps)
- [The 3 Dashboards](#the-3-dashboards)
- [The Recommendations: P0 / P1 / P2](#the-recommendations-p0--p1--p2)
- [Dataset](#dataset)
- [Limitations & Trade-offs](#limitations--trade-offs)
- [What's Next](#whats-next)
- [Repo Structure](#repo-structure)
- [How to Run](#how-to-run)
- [Skills Demonstrated](#skills-demonstrated)

---

## The Problem

**Situation**: A mobility platform is scaling across multiple cities. Trip volume is growing, revenue is increasing, leadership is happy.

**The hidden issue**: Growth metrics can mask operational decay. A city can show +30% revenue while cancellation rates silently climb from 8% to 15%. By the time leadership notices, the damage is done — driver churn, customer complaints, reputation loss.

**The question**: How do we build a monitoring system that catches operational risk *before* it becomes a crisis — and tells operations exactly where to focus?

---

## The Core Insight

> Revenue growth hides operational fragility. The cities making the most money are often the ones closest to breaking.

After analyzing trip-level data across multiple cities, the pattern is clear:

- **High-revenue cities can carry the highest cancellation risk** — volume growth alone doesn't signal operational health
- **Cancellations are behavioral, not technical** — primarily driven by customer and driver decisions, which points to UX and incentive design as levers, not infrastructure fixes
- **Risk is concentrated** — a small number of cities account for a disproportionate share of both revenue and cancellation volume, creating operational fragility

→ The dashboard doesn't just track performance. It **flags where growth is fragile** and tells operations where to intervene first.

---

## The Method: SQL Pipeline in 4 Steps

The data goes from raw trip records to dashboard-ready KPIs through a 4-step SQL pipeline:

| Step | Script | What it does |
|------|--------|-------------|
| 1 | `01_create_tables.sql` | Schema definition — building the foundation |
| 2 | `02_data_cleaning.sql` | Cleaning & standardization — removing noise |
| 3 | `03_transformations.sql` | Enrichment — creating KPI-ready fields (cancellation flags, revenue rules, city-level aggregations) |
| 4 | `04_kpi_queries.sql` | Business KPIs — the queries that feed the dashboard |

**Key business rule**: Revenue is generated only for completed trips. Cancelled and no-show trips generate zero revenue. This rule is enforced explicitly in the SQL layer for KPI consistency.

---

## The 3 Dashboards

The dashboard tells a story in 3 acts: first the big picture, then the diagnosis, then the action plan.

### Dashboard 1 — Executive Overview
*"Everything looks great... or does it?"*

High-level view of revenue, trip volume, and cancellation trends. Designed for leadership — the kind of view that makes you feel good about growth until you notice the cancellation trendline going the wrong way.

**The insight**: Revenue is up because volume is up. But the *rate* of cancellations is climbing too. Growth is masking risk.

![Executive Overview](powerbi/screenshots/executive_overview.png)

---

### Dashboard 2 — Operational Performance
*"Which cities are actually healthy, and which ones are running on borrowed time?"*

City-level breakdown of volume, revenue, efficiency, and cancellation risk. This is where the aggregated view breaks down into actionable territory — some cities are clean, others are red flags.

**The insight**: The top-revenue cities aren't necessarily the healthiest. Some are generating revenue through sheer volume while their operational efficiency is declining. Without this view, operations would keep treating all growing cities the same way.

![Operational Performance](powerbi/screenshots/operational_performance.png)

---

### Dashboard 3 — Strategic Recommendations
*"Now that we know where the problems are — what do we do about it?"*

Action-oriented view translating performance metrics into operational priorities. Each city gets a status (healthy / at risk / critical) and a priority level (P0 / P1 / P2).

**The insight**: Not every problem needs the same urgency. A high-revenue city with rising cancellations (P0) needs immediate intervention. A stable, lower-risk city (P2) needs efficiency optimization, not a war room. The priority framework prevents the operations team from treating everything as equally urgent.

![Strategic Recommendations](powerbi/screenshots/strategic_recommendations.png)

---

## The Recommendations: P0 / P1 / P2

The analysis produces a 3-tier priority framework that operations can act on immediately:

| Priority | What it means | Action |
|----------|--------------|--------|
| **P0** | High-revenue city with rising cancellation rates | Immediate intervention — diagnose root cause, adjust driver incentives, review customer UX |
| **P1** | Growth market needing stabilization | Monitor closely, secure driver supply, prevent P0 escalation |
| **P2** | Stable, lower-risk city | Optimize efficiency incrementally, no urgent action needed |

**Why this matters**: Without a priority framework, operations teams either treat everything as urgent (burnout, wasted resources) or nothing as urgent (risks go unnoticed). P0/P1/P2 forces prioritization.

---

## Dataset

| Parameter | Value |
|-----------|-------|
| **Type** | Synthetic dataset inspired by real-world mobility operations |
| **Granularity** | One row per trip |
| **Main entity** | Trips |
| **Key dimensions** | Time, city, driver |
| **Status values** | Completed, cancelled by customer, cancelled by driver, no-show |
| **Data model** | Single fact table (`fact_trips`) |

---

## Limitations & Trade-offs

- **Synthetic data** — no real user behavior or financial constraints; results are illustrative but patterns are realistic
- **Single fact table** — city and driver dimensions not normalized into separate tables, to keep the model simple and readable
- **Descriptive analysis only** — diagnosis and prioritization, no predictive modeling
- **Illustrative thresholds** — P0/P1/P2 cutoffs would normally be refined with domain experts
- **No city metadata** — population, driver supply, and market maturity are not included, which limits contextual analysis

These trade-offs were made deliberately. The goal is a clear, actionable project — not an exhaustive data model.

---

## What's Next

If this were a real operations team, next steps would include:

- Add predictive indicators for cancellation risk (trend-based alerts before P0 escalation)
- Integrate city metadata (population, driver supply) for contextual benchmarking
- Segment cancellations by time of day, driver tenure, and distance to surface granular patterns
- Automate data refresh and operational alerting

This project focuses on diagnosis and prioritization, not automation.

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

1. **SQL pipeline**: Execute scripts in `/sql/` in numerical order (01 → 04)
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
| **Data storytelling** | 3-act narrative: big picture → diagnosis → action plan |
| **Business communication** | Adapting the message to the audience (leadership overview vs. operations deep-dive) |

---

> *This project uses synthetic data and is part of a data analytics portfolio. Thresholds and recommendations are illustrative and would be refined with domain expertise in a production context.*
