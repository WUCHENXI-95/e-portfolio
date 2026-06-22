# Assignment 1 — Academic Writing

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Technical Report (IEEE Style) |
| **Topic** | Data Quality in Data Engineering |
| **Team** | Lau Yee Wen, Poh Lok Yee, Wu Chenxi |
| **Period** | 23 March – 16 April 2026 |

[📄 View Full Report (PDF)](./assignment1-report.pdf)

---

## Report Highlights

**Core Focus:** How data quality is maintained throughout modern data engineering pipelines.

**Key Sections:**
- **Introduction** — Data must be accurate, complete, consistent, and timely; poor quality costs companies millions annually
- **Literature Review** — Wang & Strong (1996) defined 4 foundational dimensions; Ridzuan et al. (2024) expanded to 20 dimensions for big data
- **Pipeline Integration** — Validation at ingestion, transformation, and storage using Great Expectations & Apache Deequ
- **Real-World Applications** — E-commerce (preventing duplicate orders), finance (risk management accuracy)
- **Challenges** — Data heterogeneity, missing data (MCAR/MAR/MNAR), quality decay over time
- **Future Trends** — ML integration, DataOps practices, data observability tools

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Great Expectations | Automated data quality validation |
| Apache Deequ | Validation library on Apache Spark |
| Apache Spark | Distributed data processing |
| Data Observability | Real-time pipeline anomaly monitoring |
| Data Contracts | Producer-consumer quality agreements |

---

## AI Tools Acknowledgment

ChatGPT and Google Gemini were used for concept understanding, real-world examples, and writing refinement. All outputs were verified against academic sources (see full report Appendix).

---

## Reflection

### What I Learned

Through this assignment, I gained a solid understanding of data quality and its critical role in data engineering. Before this, I did not fully realise how a single data error in the pipeline can cascade to all downstream systems such as BI dashboards and ML models. I learned Wang & Strong's (1996) four classic dimensions of data quality and how modern researchers have expanded these for big data environments. This assignment also strengthened my academic writing skills in English, particularly in structuring a technical report with proper sections and citing references correctly. Working as a team taught me how to divide tasks, manage schedules using Clockify, and merge contributions into one cohesive document.

### Areas for Improvement

I would start the research phase earlier to allow more time for revisions. I also want to read more primary research papers instead of relying on AI tools for initial understanding. The logbook tracking could have been more consistent — some entries were recorded late. Additionally, I would practise paraphrasing more to develop my own writing voice and reduce dependency on AI-generated text.

### Personal Takeaway

This assignment helped me understand the importance of data governance in real organisations, which connects to my interest in data engineering as a career. I also learned that while AI tools are helpful for understanding concepts, verification with academic sources is essential — AI responses are not always accurate. Overall, this was a valuable experience in teamwork, research, and technical communication.

---

[⬅ Back to Home](../../index.md)

