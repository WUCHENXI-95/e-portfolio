# Project Industry (PPG) — Recoverable Assets & Inventory Risk Management

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Industry Project (Group) |
| **Topic** | Recoverable Assets (RA) & Inventory Risk Management (IRM) |
| **Industry Partner** | PPG (Paint & Coatings Manufacturer) |
| **Team Size** | 7 members |
| **Wu Chenxi's Role** | Data pipeline development (Silver & Gold layer transformations) |

[📄 View Full Report (PDF)](./project-industry-ppg-report.pdf)

---

## Project Summary

**Problem:** PPG manages 20 raw materials across different production lines without an automated system to detect inventory risks such as surplus stock, expired materials, and critical shortages. The company relied on periodic manual spreadsheet reviews, which were error-prone, inconsistent, and lacked an audit trail.

**Goal:** Build an automated, end-to-end data engineering pipeline integrated with a Power BI dashboard to support Recoverable Assets (RA) and Inventory Risk Management (IRM) for PPG.

### Architecture — Four-Layer Medallion

| Layer | Purpose | Tool |
|-------|---------|------|
| **Bronze** | Raw CSV ingestion, no transformation | Azure Data Lake Gen2 |
| **Silver** | Data cleaning, standardisation, business rule application | Azure Databricks |
| **Gold** | Business-ready outputs (RA, MC, stockout risk, provision) | Azure Databricks |
| **Curated** | Star Schema for reporting | Azure Synapse Analytics |

### Data Pipeline Flow

```
6 CSV Files (Materials, Inventory, PO, Suppliers, SO, Production)
→ Azure Data Lake Gen2 (Bronze)
→ Azure Databricks (Silver — cleaning + business rules)
→ Azure Databricks (Gold — risk classification)
→ Azure Synapse Analytics (Curated — Star Schema)
→ Microsoft Power BI (Dashboard)
```

### Key Business Classifications Applied

| Classification | Rule | Finding |
|---------------|------|---------|
| **Recoverable Assets (RA)** | Stock on hand > 12 months of consumption | 11 materials, excess stock value RM92,770 |
| **Magna Carta Dead Stock** | No consumption for 9+ months | Identified materials with no recent usage |
| **Magna Carta Expired** | Past expiry date | 3 materials, total provision RM29,720 |
| **Stockout Risk** | Stock below reorder level | 9 materials, causing 183 unfulfilled production orders |
| **Customer Order Impact** | Sales orders affected by shortages | 192 affected customer sales orders |

### Database Design — Star Schema

| Table | Content |
|-------|---------|
| **fact_inventory_status** | Monthly inventory risk status per material (RA flag, MC flags, provision, stockout risk) |
| **dim_material** | Material master data (name, category, unit cost, expiry date) |
| **dim_supplier** | Supplier details (name, country, reliability rating) |
| **dim_time** | Date attributes (year, quarter, month) |
| **dim_purchase_order** | Purchase order records |
| **dim_production_order** | Production consumption records |
| **dim_sales_order** | Customer sales order records |

### Power BI Dashboard — 7 Business Questions

| Q | Dashboard View | Business Question |
|---|---------------|-------------------|
| Q1 | Materials Below Reorder Level | Which materials have stock below the reorder point? |
| Q2 | Recoverable Assets | Which materials exceed 12 months of consumption? |
| Q3 | MC Dead Stock | Which materials show no consumption for 9+ months? |
| Q4 | MC Expired Materials | Which materials have passed their expiry date? |
| Q5 | Total MC Provision | What is the total write-down amount under IAS 2? |
| Q6 | Unfulfilled Production Orders | Which production orders could not be fulfilled? |
| Q7 | Affected Customer Sales Orders | Which customer orders face delays? |

### Technology Stack

| Technology | Role |
|-----------|------|
| Azure Data Lake Storage Gen2 | Central storage (Bronze, Silver, Gold, Curated) |
| Azure Data Factory | Ingestion and orchestration |
| Azure Databricks | Data cleansing and business rule transformation |
| Azure Synapse Analytics | Data warehouse (Star Schema, SQL views) |
| Microsoft Power BI | Interactive dashboard |
| Azure Key Vault | Credential management |
| Azure Active Directory | Authentication and access control |

### Methodology

Waterfall SDLC — requirements were predefined with PPG before development, making a sequential phase-by-phase approach appropriate.

---

## Reflection

### What I Learned

Working on this industry project with PPG gave me hands-on experience building a real, production-scale data engineering pipeline from start to finish. I contributed to developing the Silver and Gold layer transformations in Azure Databricks, where I learned how to implement complex business rules such as Recoverable Assets classification, Magna Carta Dead Stock and Expired detection, financial provision calculation, and stockout risk tracing. Understanding how these rules connect to IAS 2 inventory valuation standards taught me that data engineering is not just a technical task — it directly impacts financial reporting and compliance. I also gained practical experience with the Medallion Architecture and Star Schema design, which I had only studied theoretically before. Coordinating across seven team members required clear communication and well-defined responsibilities, and I learned how to manage dependencies between pipeline layers so that errors in one stage do not propagate downstream.

### Areas for Improvement

- I should have documented the business rule logic more thoroughly during development, as some transformation code was difficult to trace back to the original PPG requirements during testing.
- The pipeline currently relies on batch processing with manual CSV uploads. In a real production environment, I would implement automated data ingestion and incremental loading to support more frequent reporting.
- I need to deepen my understanding of PySpark optimisation techniques, as some Gold layer transformations took longer than expected when processing the full dataset.

### Personal Takeaway

This project showed me that building a data pipeline for a real company involves much more than writing code. Understanding the business context — why materials expire, how surplus stock affects the balance sheet, and what a stockout means for production — is essential for designing transformations that deliver genuinely useful insights. The experience of working end-to-end from raw CSV files to a functioning Power BI dashboard gave me confidence that I can contribute to enterprise-level data engineering projects in the future.

---

[⬅ Back to Home](../../index.md)
