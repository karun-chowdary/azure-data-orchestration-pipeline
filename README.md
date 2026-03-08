# azure-data-orchestration-pipeline
Enterprise-grade data pipeline orchestrating PySpark transformations via Azure Data Factory, secured with Azure Key Vault and ADLS Gen2.
# Enterprise Data Orchestration & ETL Pipeline (COVID-19 Dataset)

## 📌 Project Overview
This repository contains an end-to-end, metadata-driven data engineering solution built on Microsoft Azure. The project demonstrates the ingestion, transformation, and orchestration of global COVID-19 reporting data using **Azure Data Factory (ADF)** as the primary orchestrator and **Azure Databricks (PySpark)** for heavy compute.

The architecture is designed to industry standards, focusing on security, dynamic parameterization, and scalability.

##Architecture Architecture & Data Flow
*(Note: Create a simple diagram in draw.io showing API -> ADLS Gen2 -> ADF -> Databricks -> SQL and add the image link below)*

![Architecture Diagram](Link-to-your-diagram-image-here)

1. **Bronze Layer (Ingestion):** Azure Data Factory dynamically ingests raw data from external HTTP APIs (ECDC) and lands it in Azure Data Lake Storage Gen2 (ADLS).
2. **Silver Layer (Transformation):** ADF triggers Azure Databricks notebooks. PySpark is used to clean, filter, and structure the raw data.
3. **Gold Layer (Serving):** Transformed data is loaded into Azure SQL Database (or Synapse Analytics) for downstream reporting and BI dashboards.

## 🛠️ Technology Stack
* **Orchestration:** Azure Data Factory (ADF)
* **Compute / Transformation:** Azure Databricks, PySpark
* **Storage:** Azure Data Lake Storage Gen2 (ADLS Gen2)
* **Security & Governance:** Azure Key Vault, Managed Identities
* **Version Control / CI/CD:** GitHub Integration

## 🚀 Key Engineering Implementations

Instead of hardcoding basic pipelines, this project implements the following enterprise-level design patterns:

### 1. Security-First Design (Azure Key Vault)
* **Zero Hardcoded Secrets:** All credentials, connection strings, and database passwords are securely stored in Azure Key Vault.
* **Managed Identities:** ADF is authenticated to ADLS Gen2 and Key Vault using System Assigned Managed Identities, eliminating the need for explicit credentials.

### 2. Metadata-Driven Dynamic Pipelines
* Implemented parameterization across all Linked Services and Datasets.
* Utilized **Get Metadata**, **Lookup**, and **ForEach** activities to create a single, reusable pipeline capable of processing multiple source files dynamically, reducing code duplication by over 80%.

### 3. Compute Delegation
* ADF is strictly used for orchestration and lightweight data movement (Copy Data).
* Heavy, complex data transformations are delegated to Databricks (PySpark), demonstrating cost-effective compute management.

### 4. Event-Triggered Automation
* Pipelines are scheduled using **Storage Event Triggers**, initiating the ETL process automatically the moment new files arrive in the Data Lake.

## 📁 Repository Structure
*(Note: Azure Data Factory will automatically populate this section with JSON files when connected to Git).*
* `/pipeline`: Contains the JSON definitions for all orchestration logic.
* `/dataset`: Dynamic dataset definitions for ADLS and Azure SQL.
* `/linkedService`: Connection configurations secured via Key Vault.
* `/notebooks`: Contains the PySpark code executed on Databricks clusters.

## 👨‍💻 Author
* N. Karun Sai
* Data Engineer specializing in scalable cloud architectures.
* []
* [karunsai619@gmail.com]
