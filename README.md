# Olist Ecommerce Data Project

## Architecture Overview
This project demonstrates a robust, end-to-end data pipeline for ecommerce analytics using Azure Data Factory, ADLS Gen2, Azure Key Vault, Azure Databricks, and Databricks SQL,
following the medallion (Bronze-Silver-Gold) architecture pattern.

<img width="7844" height="2217" alt="olist_data_architecture" src="https://github.com/user-attachments/assets/247bd7ee-435e-4cf8-a7de-dc99f1d34549" />


## Pipeline Steps

### 1. Ingestion from GitHub using Azure Data Factory (ADF)
- Data is sourced directly via HTTP from a public GitHub repository containing raw Olist ecommerce datasets.
- An Azure Data Factory pipeline orchestrates the data transfer. Multiple ADF activities are used to fetch, validate, and stage the raw data in Azure Data Lake Storage (ADLS) Gen2
  for further processing.

### 2. Secure Data Access with Key Vault and Databricks
- Azure Key Vault is set up to securely store the ADLS storage account access key.
- An Azure Databricks workspace is provisioned.
- Databricks Secret Scopes are linked with Key Vault, ensuring credential-free, secure access to storage from notebooks and jobs.

### 3. Data Processing in Azure Databricks
- Databricks notebooks (PySpark) perform advanced data cleaning, transformation, and multi-table join operations.
- The processed, curated data is stored in the “Silver” layer container within ADLS Gen2, which serves as a refined source for analytics and further aggregation.

### 4. Gold Layer Views Creation
- Analytical views are created in the “Gold” layer, representing key business-ready aggregates and denormalized datasets.
- These are defined in Databricks, optimized for reporting and dashboarding needs.

### 5. Analytics & Visualization
- Databricks SQL is utilized to write complex queries that feed business KPIs and insights.
- Databricks Dashboards are built to visualize trends, metrics, and performance indicators sourced from gold-layer analytical datasets, enabling real-time ecommerce insights
  for stakeholders.

  <img width="4000" height="2089" alt="Olist Sales Dashboard 2025-09-18 12_49-1" src="https://github.com/user-attachments/assets/511cb862-fe17-4fad-ba47-e57203b1c78c" />


---

## Key Highlights
- **Modular Orchestration:** Each pipeline stage (ingest, clean, join, aggregate, present) is modular and can be independently extended or reused.
- **Secure By Design:** All credentials are managed via Azure Key Vault and Databricks Secrets, minimizing risk.
- **Scalable Processing:** Data Lake and Databricks together support batch and large-scale, parallel data transformations.
- **Business-Focused Outputs:** Views and dashboards ensure actionable, business-ready reporting from raw ecommerce data.

---

