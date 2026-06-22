# Industry Visit — PPG Industries Site Visit

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Industrial Site Visit |
| **Company** | PPG Industries (Paint & Coatings Manufacturer) |
| **Theme** | Data Engineering & SAP ERP Internship Practice |
| **Type** | Group site visit + Individual deep-dive sharing session |

---

## Visit Evidence

| Photo 1 | Photo 2 |
|---------|---------|
| ![Visit Photo 1](./industry-visit-photo1.jpg) | ![Visit Photo 2](./industry-visit-photo2.jpg) |

---

## What We Did at PPG

PPG's core problem is **excess and slow-moving inventory** — materials sitting too long, expiring, and causing financial write-downs. We visited their site to understand how they use data engineering to detect and manage these risks.

Their inventory classification rules:
- **Recoverable Assets (RA):** Stock exceeds 12-month consumption
- **Magna Carta Dead Stock:** No consumption for 9+ months
- **Magna Carta Expired:** Past expiry date, requires full write-down

---

## What I Saw and Learned

### The Data Pipeline

PPG built a **4-layer Medallion Architecture** on Azure Databricks:

| Layer | What It Does |
|-------|-------------|
| **Bronze** | Loads raw CSV files as-is, no changes |
| **Silver** | Removes duplicates, fixes nulls, standardises formats |
| **Gold** | Applies business logic — RA flags, MC classification, provision calculation, stockout risk |
| **Curated** | Builds Star Schema (fact + dimension tables) for Power BI |

The data flows from **Oracle, SAP S/4 HANA, Salesforce** → **Azure Data Factory** → **Databricks** → **Power BI**.

### The Tools They Actually Use

| Tool | Purpose |
|------|---------|
| Azure Databricks + Delta Lake | Compute and storage |
| Azure Data Factory | Pipeline orchestration |
| Power BI | Dashboard and reporting |
| Azure Key Vault | Security |
| Atlan Data Catalog | Data governance |

### What Data Engineers Do There

- Build pipelines to pull data from SAP, Oracle, REST APIs
- Migrate data between platforms (e.g. Snowflake to Databricks)
- Debug data inconsistency and integration errors
- Build Power BI dashboards with DAX modelling

### SAP ERP Sharing Session

A separate session covered SAP S/4 HANA functional consulting — how consultants act as a bridge between business users and technical systems. The key message: understanding business processes matters as much as technical skills.

### Internship Structure

PPG runs a 25-week internship with clear progression:
- Weeks 1–4: Orientation and training
- Weeks 5–12: Practical tasks, basic hands-on work
- Weeks 13–20: Pipeline and dashboard development
- Weeks 20–25: Full involvement in real projects

They offer hybrid work (3 days on-site), Microsoft certification programs, and cross-department collaboration.

### Other Projects We Saw

**PPG HullNav Alert** — a vessel monitoring system that predicts hull fouling risks using ship location, speed, and ocean data. A good example of data engineering applied outside manufacturing.

---

## Reflection

### What I Learned

This visit gave me a concrete understanding of what a real data engineering team does day to day. Before this, I only knew the tools from tutorials — Azure, Databricks, Power BI. Seeing how PPG uses them to solve actual inventory problems made everything click. I understood for the first time how a business rule like "stock exceeds 12 months of consumption" gets translated into SQL transformation code in the Gold layer. That connection between business logic and technical implementation was something I had not experienced before.

I also got a clearer picture of what employers expect from fresh graduates. PPG does not just look for people who can write SQL — they want people who can understand why a pipeline exists, communicate with non-technical teams, and keep improving when business needs change. The internship structure they showed us gave me a realistic idea of what to expect in my first year working.

The SAP session was a bonus. I had never thought about ERP consulting as a career path, but seeing how SAP connects to the data side (from transactional ERP to analytical BI dashboards) opened my eyes to more possibilities.

### What Could Be Better

- The visit was mostly presentation-based. I would have liked to see a live demo of their Databricks workspace or Power BI dashboards in action.
- Time was limited — I did not get to ask about their data quality monitoring process in detail.

### What I Plan to Do

- Build a mini version of the PPG inventory pipeline on GitHub using the same Medallion structure, so I have a practical demo for my portfolio.
- Prepare better questions before future visits by researching the company's public technical content first.

---

[⬅ Back to Home](../../index.md)
