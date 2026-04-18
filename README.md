# End-to-End Data Pipeline Using Azure Data Factory
## Overview

This project showcases the design and implementation of an end-to-end automated data pipeline using Azure Data Factory (ADF). The solution is built to handle data ingestion, validation, transformation, and storage, making data readily available for analytics and reporting.

It simulates a real-world data engineering workflow, where incoming files are automatically processed from a landing zone, validated, transformed, and loaded into a structured database for downstream consumption in Power BI.

## Architecture Overview

The pipeline follows a modular, scalable, and event-driven architecture:

Landing folder (Azure Blob Storage) – Entry point for all incoming files

ADF Event Trigger – Automatically initiates the pipeline upon file upload

Metadata Validation Layer – Ensures file structure and schema integrity

Processing Layer – Handles transformation, conversion, and routing logic

Storage Layer (Azure SQL Database) – Stores cleaned and structured data

Reporting Layer (Power BI) – Enables data visualization and insights

Archive & Rejected folder – Maintains processed and invalid files for traceability

## Pipeline Workflow

1️⃣ File Ingestion

Files are uploaded into the Landing folder, triggering the pipeline using an event-based trigger for real-time processing.

2️⃣ Metadata Extraction

A Get Metadata (GetFileList) activity retrieves incoming files.

Each file is processed individually using a ForEach activity to ensure scalability.


3️⃣ Schema Validation

A second metadata check (GetFileStructure) validates:

Required columns

File format (CSV or Excel)

Schema consistency

4️⃣ File Routing (Switch Activity)

Based on validation results, files are routed as follows:

✅ Valid CSV Files

Sent directly to Data Flow

Transformed and loaded into Azure SQL Database

Original file archived

✅ Valid Excel Files

Passed to an Azure Function App for conversion (Excel → CSV)

Transformed using Data Flow

Loaded into Azure SQL Database

Original file archived

❌ Invalid Files

Moved to Rejected Folder

Removed from Landing Zone

5️⃣ Data Transformation

Azure Data Flows are used to:

Clean and standardize data

Handle data type conversions

Remove invalid or null records

Map data to the target SQL schema

6️⃣ Storage & Reporting

Cleaned and structured data is stored in Azure SQL Database

Power BI connects directly to the database to create dashboards and generate insights

7️⃣ Archiving

All original files from the landing folder are archived to ensure:

Data lineage

Auditability

Historical tracking

## Azure Services Used
Azure Data Factory (ADF)

Azure Blob Storage

Azure Functions

Azure SQL Database

Visual Studio Code

Power BI

## Key Features

Fully automated event-driven pipeline

Supports both CSV and Excel ingestion

Dynamic schema validation and file routing

Scalable ETL architecture

Integrated Azure Function for file conversion

Built-in error handling and rejection mechanism

End-to-end data lineage and archiving system

## Challenges & Learnings
Implemented dynamic pipeline logic using Switch, ForEach, and Parameters

Integrated Azure Functions with ADF for file conversion workflows

Designed validation layers to ensure data quality and consistency

Gained hands-on experience troubleshooting pipeline failures and debugging errors

Strengthened understanding of real-world ETL pipeline architecture

## Outcome

Developed a robust, automated, and scalable data pipeline capable of:

Handling multiple file formats

Validating and processing data efficiently

Delivering clean, structured data for analytics

This project demonstrates practical experience in cloud-based data engineering, pipeline orchestration, and data workflow automation.

### Author

Asmau Abdulkarim

Aspiring Data Engineer | Data Analyst
