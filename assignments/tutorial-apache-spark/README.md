# Assignment 3 — Tutorial: Apache Spark

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Lab Tutorial Report |
| **Topic** | Apache Spark — ETL Pipeline for Brazilian Education Census |
| **Team** | Nur Firzana, Nuraisyah, Wu Chenxi |
| **Lecturer** | Dr. Aryati Binti Bakri |

[📄 View Full Report (PDF)](./tutorial-apache-spark-report.pdf)

---

## Project Summary

**Problem:** The Brazilian National Basic Education Census (Censo Escolar) collects data from every basic education school across Brazil. Each year produces one CSV file with approximately 370 columns and ~180MB. Combined, 11 years of data (2010–2021) reaches ~2.2GB. The flat CSV format makes aggregation queries slow and inefficient, and tools like Pandas crash when handling this volume.

**Goal:** Build an end-to-end ETL pipeline using Apache Spark to transform raw CSV data into a structured Star Schema, load it into PostgreSQL, and visualise insights through Metabase dashboards.

### Architecture Flow

```
Brazilian Open Data Portal (CSV)
→ Python (download)
→ Apache Spark (CSV → Parquet, Star Schema transformation)
→ PostgreSQL (data warehouse via JDBC)
→ Metabase (interactive BI dashboards)
```


### Key Design Decisions

| Decision | Reason |
|----------|--------|
| **Apache Spark over Pandas** | Pandas loads entire dataset into memory and crashes; Spark uses lazy evaluation to handle 2.2GB without memory issues |
| **Parquet over CSV** | ~5x smaller file size, much faster columnar query performance |
| **Star Schema** | Denormalised model optimised for aggregation queries (e.g. "How many students in 2021?") |
| **Docker containerisation** | Ensures portable, reproducible environment for Spark, PostgreSQL, and Metabase |

### Star Schema Design

- **Fact Table (fact_censo):** Primary quantitative measures (enrollment count, teacher count) with foreign keys to dimensions
- **Dimension Tables:** Geographic location (state, city), school type, education level, time period

### Evaluation Results

| Metric | Result |
|--------|--------|
| ETL Pipeline Latency | Average 4.4 seconds for full historical load |
| Storage | Significant reduction via Star Schema + bigint mappings |
| Query Response Time | Under 500ms for dashboard visuals |
| Data Accuracy | 100% replication accuracy, 46,448,401 total enrollments in 2021 |

### Limitations & Future Improvements

- **Current:** Batch processing only — no real-time updates
- **Future:** Spark Streaming + Apache Kafka for real-time pipeline; dbt for automated data testing; Apache Airflow DAGs for workflow automation

---

## Reflection

### What I Learned

This tutorial gave me a deeper understanding of why data understanding matters at the start of any project. I took charge of exploring the raw data structure and quickly discovered that the Brazilian education census contains around 370 columns per year, many of which overlap. Deciding which fields belong in dimension tables versus the fact table was challenging at first, but doing it myself helped me truly grasp the logic behind Star Schema design — fact tables hold measurable indicators, while dimension tables hold descriptive attributes. I also saw firsthand how slow CSV reads can be, even with Spark, which made the conversion to Parquet feel like an obvious and rewarding step. After completing this tutorial, I understand that the quality of a data engineering project depends heavily on how thoroughly we understand the data before building anything.

### Areas for Improvement

- I should have spent more time **planning the schema mapping** before jumping into code — some rework happened because I assigned fields to the wrong tables initially.
- I need to get more comfortable with **PySpark DataFrame operations**, especially joins and aggregations, since I still relied on trial and error in several places.
- The team could have **divided the testing tasks** more clearly — we sometimes duplicated effort when debugging pipeline errors.

### Personal Takeaway

Working with a real, large-scale government dataset taught me that data engineering is not just about writing code. Understanding the data, choosing the right storage format, and designing a schema that serves actual business questions are equally important. This experience also showed me that Docker and containerisation are essential skills for building reliable, reproducible data pipelines.

---

[⬅ Back to Home](../../index.md)
