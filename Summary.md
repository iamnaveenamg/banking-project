# Medallion Banking Pipeline

## PROJECT OVERVIEW

**Banking Data Pipeline & Analytics Platform** – End-to-end enterprise data pipeline demonstrating medallion architecture (Bronze → Silver → Gold) for banking domain. Implemented metadata-driven ingestion from SQL Server, Delta Lake transformations, and analytical gold tables for KPIs, customer analytics, and risk assessment.

---

## RESUME BULLET POINTS

**Choose 4-5 for your resume:**

1. **Engineered production-grade data pipeline using Databricks and Delta Lake with medallion architecture, processing banking transactions from SQL Server into gold tables for customer 360 views and KPI dashboards**

2. **Designed metadata-driven ETL framework with configurable load strategies (MERGE/APPEND/FULL) and watermark-based incremental processing from multi-source systems (SQL Server, Azure Blob Storage)**

3. **Developed 15+ PySpark notebooks transforming normalized banking entities into 5 analytical gold tables with complex aggregations, window functions, and customer segmentation logic**

4. **Implemented comprehensive audit framework with Delta Lake partitioning for pipeline execution tracking, error logging, and failure diagnostics enabling production-grade reliability**

5. **Built enterprise security patterns with Databricks secret scopes for encrypted credential management and ACID guarantees ensuring data governance for financial systems**

---

## TECHNOLOGY STACK

Apache Spark • PySpark • Delta Lake • Databricks • SQL Server • Azure Blob Storage • Python • T-SQL

---

## KEY ACHIEVEMENTS

✓ Production-ready pipeline with fault tolerance and error handling
✓ Reusable metadata-driven framework for rapid source additions
✓ Complete lineage tracking and audit trails for compliance
✓ 5 gold layer tables (customer_360, branch_performance, daily_bank_kpi, transaction_channel_summary, risk_customer_summary)

---

## PROJECT STRUCTURE

```
Banking-Project/
├── 0_SourceData/        SQL Server schema & sample data
├── 1_SetupMetaData/     Metadata initialization & validation  
├── 2_Source_to_Silver/  Ingestion & Bronze→Silver transforms
├── 3_Silver_Gold/       Gold layer analytics (5 tables)
├── 4_Email_Notification Email reports & dashboards
└── Dashboards/          Dashboard artifacts
```

---

**Repository:** https://github.com/iamnaveenamg/banking-project
