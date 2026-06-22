# Assignment 2 — Tutorial: Microsoft Azure

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Lab Tutorial Report |
| **Topic** | Microsoft Azure — End-to-End Cloud Data Platform |
| **Team** | Nur Firzana, Nuraisyah, Wu Chenxi |
| **Lecturer** | Dr. Aryati Binti Bakri |

[📄 View Full Report (PDF)](./tutorial-azure-report.pdf)

---

## Project Summary

**Goal:** Migrate data from on-premises SQL Server to Azure cloud, build an automated data pipeline, and create a Power BI dashboard for business intelligence.

**Problem:** Many companies suffer from "data silos" — important data stuck in old on-premise systems, making analysis difficult.

### Solution — Medallion Architecture

| Layer | Purpose | Tool |
|-------|---------|------|
| **Bronze** | Raw data, preserved as-is | Azure Data Lake Gen2 |
| **Silver** | Cleaned, filtered, standardised | Azure Databricks (PySpark) |
| **Gold** | Aggregated, business-ready | Azure Databricks → Synapse |

### Data Pipeline Flow
```
SQL Server (on-premise)
→ Azure Data Factory (orchestration, Self-Hosted Integration Runtime)
→ Azure Data Lake Gen2 (Bronze → Silver → Gold)
→ Azure Synapse Analytics (serving layer)
→ Microsoft Power BI (dashboard)
```

### Key Features

- **Metadata-Driven Approach** — Uses "Get Metadata" + "ForEach" to automatically discover and process tables
- **Security** — Azure Key Vault manages all secrets; no hard-coded passwords
- **Role-Based Access Control** — Configured Managed Identities for proper permissions

### Azure Services Used

| Service | Role |
|---------|------|
| Azure Data Factory | Pipeline orchestration |
| Azure Data Lake Gen2 | Scalable storage |
| Azure Databricks | Spark-based transformation |
| Azure SQL Database | Source & destination |
| Azure Key Vault | Security & secrets management |
| Microsoft Power BI | Visualisation & dashboard |

### Power BI Dashboards

- **Strategic Sales Insights** — Total Products (295), Total Revenue (708.69K), gender distribution analysis, interactive slicers by title and product category
- **Global Revenue Analytics** — Geospatial performance, product popularity, customer demographics with dynamic cross-filtering

---

## Reflection

### What I Learned

Building this end-to-end cloud data platform was a challenging journey that taught me much more than just technical skills. I started from scratch and faced several significant hurdles. Initially, I struggled with my local environment, dealing with SQL Server installation errors and Java configuration issues that prevented the Self-Hosted Integration Runtime from working. I also hit a wall with cloud security; I realized that simply being an "Owner" was not enough to access secrets, so I had to learn how to configure Role-Based Access Control and Managed Identities properly. I even faced data corruption issues by mixing file formats and lost pipeline logic because I forgot to publish my work. These failures forced me to become a better troubleshooter.

Overcoming these obstacles gave me deep practical knowledge. I successfully built a Medallion Architecture, moving data from Bronze to Gold layers. I moved beyond manual work by using Azure Data Factory's "Lookup" and "ForEach" loops with dynamic expressions like `@item()` to automate the ingestion of multiple tables. I learned to secure my pipelines by using Azure Key Vault instead of hard-coding passwords. In Databricks, I used PySpark to clean data and rename columns efficiently. Finally, I utilized Synapse Serverless SQL to query data directly from the lake.

### Areas for Improvement

- I should have **published my pipeline changes more frequently** — I lost work because I forgot to publish after editing.
- I need to **document configuration steps** as I go, rather than trying to remember them later.
- My **troubleshooting skills** still need improvement — some errors took too long to resolve because I did not know where to look.

### Personal Takeaway

This project proved to me that while coding is important, the ability to **debug errors and manage details** is what truly makes a data engineer successful. The experience of building a complete cloud data pipeline from scratch, with real obstacles along the way, gave me confidence that I can work with enterprise-level data infrastructure in the future.

---

[⬅ Back to Home](../../index.md)

