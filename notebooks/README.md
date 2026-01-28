## Notebooks Overview

This folder contains Microsoft Fabric notebooks implementing a **medallion architecture**
(Bronze → Silver → Gold) for NYC Yellow Taxi data processing.

### Notebook Flow

1. **01_bronze_ingestion.ipynb**
   - Ingests raw NYC Taxi trip data from Azure Data Lake Gen2
   - Stores data in the Fabric Lakehouse Bronze layer
   - No transformations applied (schema preserved)

2. **02_silver_cleaning.ipynb**
   - Cleans and standardizes Bronze data
   - Handles null values, data types, and invalid records
   - Prepares analytics-ready datasets

3. **03_gold_aggregation.ipynb**
   - Aggregates cleaned data into business-level metrics
   - Produces KPIs such as total trips, revenue, average fare, and distance
   - Optimized for Power BI consumption

### Execution
- Notebooks are orchestrated using a Fabric pipeline
- Pipeline execution is triggered by Azure Blob Storage events
