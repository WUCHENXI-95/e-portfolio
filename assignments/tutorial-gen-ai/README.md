# Assignment 5 — Tutorial: Generative AI (Nexla AI-Assisted ETL)

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Lab Tutorial Report |
| **Topic** | Gen AI — AI-Assisted Data Engineering with Nexla |
| **Team** | Nur Firzana, Nuraisyah, Wu Chenxi |
| **Lecturer** | Dr. Aryati Binti Bakri |
| **Tools** | Nexla Express (AI Agent), WeatherAPI.com, Snowflake |

[📄 View Full Report (PDF)](./tutorial-gen-ai-report.pdf)

---

## Project Summary

**Goal:** Demonstrate how AI-assisted data engineering can simplify ETL pipeline development using natural language prompts instead of manual coding.

**Key Concept:** AI-assisted data engineering uses Large Language Models (LLMs) as a co-pilot for data engineers — automating tasks like commenting code, explaining pipelines, enriching metadata, and generating documentation. Engineers focus on design and business requirements while AI handles repetitive configuration.

### What is Nexla AI Agent?

An AI Agent built into the Nexla platform that operates directly within the workspace. Its capabilities include:

- **Pipeline generation from natural language prompts** — describe the data flow, AI generates the ETL components
- **Pipeline explanation and documentation** — summarises data flow logic, transformations, and source-to-target mappings
- **Code and transformation assistance** — generates and explains transformation logic and expressions
- **Metadata enrichment** — automatically updates documentation as pipeline configurations change

### Pipeline Built

| Step | Action |
|------|--------|
| 1 | Submit initial prompt: weather data to Snowflake, every 2 minutes |
| 2 | Create WeatherAPI.com credential |
| 3 | Create Snowflake credential |
| 4 | Create Snowflake sink (WEATHER_DATA table) |
| 5 | Wait for Nexset creation and verify source |
| 6 | Add Celsius to Fahrenheit transformation via prompt |
| 7 | Configure Snowflake destination sink for transformed data |
| 8 | Complete ETL pipeline |
| 9 | Run and verify in Snowflake |

### Transformation Example

| Prompt | Result |
|--------|--------|
| "Add a transformation that converts temperature from Celsius to Fahrenheit using (C x 9/5) + 32 and save it as temp_f. Set temp_f to null if current_temp_c is missing." | AI generated conversion formula, handled null cases, created new Nexset automatically |

### Actors (Use Case Diagram)

- **Data Engineer** — provides prompts, validates output, reviews configurations
- **AI Agent** — generates pipeline components, transformations, documentation

### Key Takeaway

AI tools significantly reduce manual effort in pipeline development, but human oversight remains essential. Issues like field mapping inconsistencies and data quality concerns still require manual review and correction.

---

## Reflection

### What I Learned

This tutorial gave me a practical understanding of how AI-assisted data engineering can streamline ETL development. Using Nexla Express, I built a complete pipeline through natural language prompts — extracting live weather data, transforming temperature from Celsius to Fahrenheit, and loading the results into Snowflake on a 2-minute schedule. The AI handled most of the heavy lifting, including creating connectors, mapping data fields, and generating transformation logic. This experience showed me that AI can serve as a powerful productivity co-pilot, allowing data engineers to focus on architecture and business requirements rather than repetitive configuration tasks. I also learned the importance of validating AI-generated output, since mapping inconsistencies and data quality issues still required manual review.

### Areas for Improvement

- I should craft **more precise and detailed prompts** to reduce ambiguous outputs and minimise the need for manual correction.
- I need to understand **what happens behind the scenes** when the AI generates pipeline components, so I can troubleshoot issues more effectively when they arise.
- The pipeline could be enhanced with **deduplication logic and stronger error-handling mechanisms** to make it production-ready.

### Personal Takeaway

AI is a valuable accelerator for data engineers, but it does not replace domain knowledge or critical thinking. The engineer still needs to validate every output, understand the data flow, and ensure quality at every stage. In the future, I would like to explore integrating this type of AI-assisted workflow with tools like Apache Airflow for fully automated scheduling and Snowflake Tasks for production-grade pipelines.

---

[⬅ Back to Home](../../index.md)
