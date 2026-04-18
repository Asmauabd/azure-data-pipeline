
# End-to-end Azure Data Factory pipeline project
# Overview

This project demonstrates an end-to-end automated data pipeline built using Azure Data Factory (ADF). The pipeline is designed to handle structured data ingestion, validation, transformation, and storage for analytics and reporting purposes.

It simulates a real-world data engineering workflow where files are automatically processed from a landing zone into a SQL database and made available for visualization through Power BI.

# Key Features

Fully automated event-driven pipeline

Supports both CSV and Excel ingestion

Dynamic schema validation

Scalable ETL architecture

Built-in error handling and file rejection system

End-to-end data lineage and archiving

# Architecture Overview

The pipeline follows a modular and event-driven architecture:

i.Landing Zone (Azure Blob Storage): Entry point for all uploaded files

ii.ADF Event Trigger: Automatically triggers pipeline on file upload

iii.Metadata Validation Layer: Checks file structure and schema

iv.Processing Layer: Handles transformation, conversion, and routing

v.Storage Layer: Loads cleaned data into Azure SQL Database

vi.Reporting Layer: Power BI dashboards for analytics

vii.Archive & Rejected Zones: Stores original processed files and invalid datasets
# Pipeline Workflow
1. File Ingestion

  Files are uploaded to the Landing folder, which triggers the pipeline using an event-based trigger.

2. Metadata Extraction

  A Get Metadata (GetFileList) activity retrieves all incoming files. Each file is processed individually using a ForEach activity.

3. Schema Validation
 
  A second metadata check (GetFileStructure) validates;

  Required columns

  File format (CSV or Excel)

  Schema consistency

4. File Routing (Switch Activity)

 Based on validation:
 
 i.Valid CSV Files Sent directly to Data Flow
 
 Transformed and loaded into SQL Database
 
 Original file archived
 
ii.Valid Excel Files Processed through an Azure Function App to convert Excel → CSV

 Passed to Data Flow for transformation
 
 Loaded into SQL Database
 
 Original file archived
 
iii.Invalid Files
 
 Moved to Rejected Folder
 
 Removed from landing zone
 
5. Data Transformation
   
 Azure Data Flows are used to;

 Clean and standardize data
 
 Handle data type conversions
 
 Remove invalid or null records
 
 Map data to SQL schema
 
6. Storage & Reporting

Cleaned data is stored in Azure SQL Database

Power BI connects directly to SQL for dashboards and insights

7. Archiving

 All successfully processed files are archived to maintain:
 
 Data lineage
 
 Auditability
 
 Historical tracking
 
# Azure Services Used

Azure Data Factory

Azure Blob Storage

Azure Functions

Azure SQL Database

Power BI



# Learning Outcomes

This project strengthened practical skills in:

Cloud-based ETL pipeline design

Data orchestration using Azure Data Factory

Serverless compute with Azure Functions

Data validation and transformation techniques

End-to-end data engineering workflow design



# Author

Asmau Abdulkarim

Data Analyst | Aspiring Data Engineer

