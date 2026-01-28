Architecture Overview
Azure Fabric – NYC Taxi Medallion Pipeline

This project follows a modern cloud-native medallion architecture implemented using Microsoft Fabric, Azure Data Lake Storage Gen2, and Power BI.
It is designed to support secure, scalable, and automated data ingestion, transformation, and analytics.
Architecture Components
1. Identity & Access Management

Microsoft Entra ID (Azure AD) is used for authentication and authorization.

Role-Based Access Control (RBAC) ensures least-privilege access across:

Azure Storage

Event Grid

Microsoft Fabric workspace

Secure access is enforced for pipelines, notebooks, and BI consumption.

2. Data Ingestion Layer (Raw Zone)

Source data is stored in Azure Data Lake Storage Gen2.

Raw NYC Yellow Taxi data is ingested into a Raw / Landing container.

This layer preserves source fidelity and is optimized for traceability and auditing.

3. Medallion Architecture in Microsoft Fabric
🥉 Bronze Layer

Initial ingestion into Fabric Lakehouse.

Data is minimally processed and stored in Delta format.

Handles schema alignment and ingestion validation.

🥈 Silver Layer

Data cleaning, enrichment, and standardization.

Null handling, type casting, and business rule application.

Produces analytics-ready, structured datasets.

🥇 Gold Layer

Aggregated and optimized datasets.

Business KPIs (Trips, Revenue, Distance, Fare metrics).

Designed specifically for BI and reporting consumption.

4. Automation & Event-Driven Processing

Azure Blob Storage events are used to detect new data arrivals.

Event Grid is configured to trigger Fabric pipelines automatically.

This enables near real-time ingestion without manual intervention.

Note: Trigger configuration and RBAC permissions are documented in screenshots for transparency.

5. Analytics & Visualization

Power BI connects directly to the Gold layer.

Interactive dashboards provide:

Borough-level demand analysis

Revenue and trip volume trends

Daily and monthly performance insights

Optimized for decision-making and operational analytics.

Architecture Benefits

Scalable: Built on cloud-native, serverless services.

Secure: RBAC + Entra ID ensure controlled access.

Automated: Event-driven pipelines reduce manual processing.

Analytics-ready: Gold layer enables fast BI performance.

Enterprise-aligned: Follows Microsoft-recommended medallion pattern.

Design Considerations

Separation of concerns across Raw, Bronze, Silver, and Gold layers.

Auditability and data lineage maintained throughout the pipeline.

Optimized for both batch ingestion and future streaming extensions.

Future Enhancements

CI/CD for Fabric pipelines.

Data quality checks using Fabric Data Activator.

Incremental load optimization.

Cost monitoring and performance tuning.
