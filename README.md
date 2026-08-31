# Banking Project

This repository contains an end-to-end banking data pipeline implemented as notebooks and SQL scripts. The project demonstrates extracting data from a SQL Server source, landing it in Bronze/Silver/Gold layers, producing analytics (KPIs, customer 360, risk summaries), and sending email notifications / dashboards.

## Repository layout

- .gitignore
- Banking-Project/
  - 0_SourceData/01_sqlserver/
    - 01_createTables.sql — SQL to create sample/source tables
    - 02_InsertScript.sql.dbquery.ipynb — notebook with insert/load scripts
    - 03_IncrementalData.sql — incremental data load script
  - 1_SetupMetaData/
    - 01_setupMetadata.ipynb — create/initialize metadata required by the pipeline
    - 02_Validate_MetaData.ipynb — validation of metadata and table configuration
  - 2_Source_to_Silver/
    - 0_Setup_Secret_Scope.ipynb — instructions to configure secret scopes / connection secrets
    - 1_ReadTables_List.ipynb — discover/read list of source tables
    - 2_Read_Table_Parameters.ipynb — read/construct parameters for table reads
    - 3_Source_Bronze.ipynb — ingest source into Bronze
    - 4_Bronze_Silver.ipynb — transform Bronze to Silver
  - 3_Silver_Gold/
    - Silver_to_Gold_Driver.ipynb — driver notebook orchestrating Silver->Gold transforms
    - gold_transformations/
      - branch_performance.ipynb
      - customer_360.ipynb
      - daily_bank_kpi.ipynb
      - risk_customer_summary.ipynb
      - transaction_channel_summary.ipynb
  - 4_Email_Notification/
    - 01_Send_Email.ipynb — sample notebook to compose/send email reports
  - Dashboards/ — (folder for dashboard artifacts)

## Purpose
This project shows a typical medallion architecture (Bronze → Silver → Gold) for banking data:
- Simulate or ingest transactional and master data from SQL Server
- Build consistent metadata-driven ingestion jobs
- Produce analytical gold tables and reports (KPIs, customer 360, risk summaries)
- Demonstrate notification/reporting via email and dashboards

## Prerequisites
- Jupyter / Databricks environment (these notebooks are written for interactive notebook environments)
- Access to a SQL Server instance (or ability to run the provided SQL scripts locally)
- Python 3.8+ and typical data stack libraries (pandas, pyodbc / sqlalchemy, pyspark if using Spark)
- If using Delta Lake / Databricks: Spark + Delta support
- Secrets manager or secret scope configured for credentials (see 2_Source_to_Silver/0_Setup_Secret_Scope.ipynb)

## Quick start

1. Prepare the source data
   - Run `Banking-Project/0_SourceData/01_sqlserver/01_createTables.sql` against your SQL Server to create sample tables.
   - Use `02_InsertScript.sql.dbquery.ipynb` or `03_IncrementalData.sql` to populate initial and incremental data.

2. Configure secrets and connections
   - Open `Banking-Project/2_Source_to_Silver/0_Setup_Secret_Scope.ipynb` and configure credentials (SQL Server connection string, storage access, email credentials). Do NOT commit secrets to the repo.

3. Initialize metadata
   - Run `Banking-Project/1_SetupMetaData/01_setupMetadata.ipynb` to create any metadata tables/configuration required by the pipeline.
   - Validate metadata with `02_Validate_MetaData.ipynb`.

4. Ingest data (Bronze)
   - Run notebooks in `Banking-Project/2_Source_to_Silver/` in order: `1_ReadTables_List.ipynb`, `2_Read_Table_Parameters.ipynb`, `3_Source_Bronze.ipynb`, then `4_Bronze_Silver.ipynb` to progress to Silver.

5. Transform to Gold and produce analytics
   - Run `Banking-Project/3_Silver_Gold/Silver_to_Gold_Driver.ipynb`.
   - Explore gold_transformations notebooks for specific analytical outputs (customer_360, daily_bank_kpi, risk_customer_summary, etc).

6. Notifications & dashboards
   - Use `Banking-Project/4_Email_Notification/01_Send_Email.ipynb` to generate and send reports.
   - Dashboards folder contains artifacts or pointers for dashboarding tools (e.g., Power BI, Databricks SQL).

## Notes & recommendations
- Notebooks include configuration cells (connection strings, paths, storage mounts). Update those cells before running.
- Use a dedicated service account for DB and storage access; store credentials in a secrets manager.
- For production, convert notebook logic into scheduled jobs (Databricks Jobs, Airflow, etc.) and add monitoring/alerting.
- Large SQL/insert notebooks may contain large payloads; run them in an environment with sufficient resources.

## Contributing
- Open issues or PRs for fixes, improvements, or new transformations.
- Keep secrets out of commits; include only tokenized references to secret scopes/configuration.

## License
Include a license of your choice (e.g., MIT) — add LICENSE file to the repository.

## Contact
Repository owner: iamnaveenamg (see GitHub profile)
