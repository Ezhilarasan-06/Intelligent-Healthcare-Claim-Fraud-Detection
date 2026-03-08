
# Insurance Claims Fraud Detection & Analytics Platform

An end-to-end data engineering and AI project built on Databricks to detect fraudulent insurance claims using rule-based logic and enable plain English querying through an AI assistant.

---

## Problem Statement

- Insurance companies process hundreds of claims daily
- Detecting fraudulent and overpriced claims manually is slow
- No unified view across claims, policies and patients
- Business teams cannot query data without technical help

---

##  Solution

- Built a rule-based fraud detection engine to automatically flag overpriced claims
- Unified claims, policy and patient data using a Star Schema data model
- Structured KPIs to monitor fraud trends, overpricing patterns and policy utilization
- Added an AI assistant powered by Cohere LLM to answer any business query in plain English

---

## Architecture

```
Raw Data (CSV)
      ↓
Bronze Layer  →  Ingested as-is
      ↓
Silver Layer  →  Cleaned & Validated
      ↓
Gold Layer    →  Business-ready tables
      ↓
Star Schema   →  Fact + Dimension tables
      ↓
AI Assistant  →  Plain English querying via Cohere LLM
```

---

##  Project Structure

```
├── bronze/
│   └── bronze_ingestion        
├── silver/
│   └── silver_cleaning        
├── gold/
│   ├── gold_fraud_table         
│   ├── gold_claim_table        
│   └── gold_policy_table     
├── data_model/
│   ├── dim_patient            
│   ├── dim_policy
│   ├── dim_date                
│   ├── dim_procedure          
│   └── fact_claims                    
├── ai_assistant/
    └── chatbot               
```
---

## Star Schema Data Model

```
              dim_patient
                   |
dim_date ── fact_claims ── dim_policy
                   |
             dim_procedure
```

| Table | Type | Description |
|-------|------|-------------|
| `fact_claims` | Fact | Central table with all claim metrics |
| `dim_patient` | Dimension | Patient details |
| `dim_policy` | Dimension | Policy coverage details |
| `dim_date` | Dimension | Admission & discharge dates |
| `dim_procedure` | Dimension | Procedure types & average costs |

---

##  Fraud Detection Logic

Claims are flagged as fraudulent when:

```
procedure_cost > 130% of Average_Cost
```

| Flag | Condition |
|------|-----------|
| `NONE` | Cost within acceptable range |
| `LOW` | Cost exceeds 130% of average |

---

##  AI Assistant

Built using **Cohere LLM API (command-a-03-2025)** — enables business users to query live claims data in plain English.

**Example queries:**
```
👤 Which claims are flagged as fraud?
🤖 Claims C013, C015, C017, C019 and C022 are flagged.
   These exceed 130% of the standard average procedure cost.

👤 What is the claim amount for C013?
🤖 Claim C013 has a procedure cost of ₹1,500 for a CT Scan.
   The standard average is ₹900 — making it 66.7% overpriced.

👤 Does Platinum Health Plan cover ICU?
🤖 Yes, Platinum Health Plan covers ICU with a daily limit
   and has no waiting period for critical procedures.
```

---

##  Tech Stack

| Tool | Purpose |
|------|---------|
| Databricks Community Edition | Cloud data platform |
| PySpark | Data processing |
| Spark SQL | Data modeling & querying |
| Delta Lake | Storage format |
| Medallion Architecture | Pipeline design pattern |
| Star Schema | Data modeling |
| Cohere LLM API | AI assistant |
| Python (requests) | API integration |

---

---

##  Results

- ✅ Automated fraud detection replacing manual review
- ✅ Structured Star Schema enabling fast analytics
- ✅ AI assistant enabling plain English querying for non-technical users

---
