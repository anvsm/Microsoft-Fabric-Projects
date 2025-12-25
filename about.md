# Trek Bike Sales Analysis – End-to-End Project (Microsoft Fabric)
This project demonstrates an end-to-end data engineering and analytics pipeline built using Microsoft Fabric. The workflow covers data ingestion, transformation, modeling, and reporting for Trek Bike Sales data.

---

## Project Overview
The objective of this project is to design and implement a data pipeline that ingests raw sales data, transforms it into meaningful insights, and builds a semantic model to enable interactive reporting in Power BI.

---
## Fabric Components Used:

1)	Lakehouse
2)	Data Pipeline
3)	Notebook
4)	Dataflow Gen2
5)	Data Warehouse
6)	Semantic Model
7)	Power BI

---

## Steps Followed

**1). Workspace & Storage Setup**

- Created a workspace: **Trek-BikeSales-WS**
- Created a warehouse: **TrekBikeSales-DWH**
- Created a lakehouse: **DataStagingLakehouse**
  
**2). Data Ingestion (Pipeline)**

- Created a pipeline: Rawdataingest
- Added Copy Data Activity to pull sales data from GitHub using API.
- Configured HTTP connector with GitHub source URL.
- Destination: Lakehouse → Sub-folder sourcefiles.
- Verified pipeline execution → Sales_Data.csv successfully loaded into Lakehouse.
  
**3). Data Transformation (Notebook)**

- Created a notebook: Bike Sales Analytics Notebook.
- Performed transformations and loaded output as Delta Table into Lakehouse.
- Configured pipeline with:
- Delete Activity (to clean old data).
- Notebook Activity (to execute transformations).
- Verified → new_sales Delta Table successfully created in Lakehouse.
  
**4). Dataflow Gen2 Transformations**

- Created DataflowTransformations.
- Connected to DataStagingLakehouse → selected new_salesdata table.
- Applied transformations.
- Destination: Lakehouse → Replace existing new_salesdata table.
- Pipeline executed successfully with transformed data available.

**5). Data Warehouse Schema**

- Created Sales Schema with Fact and Dimension tables.
- Created Staging View in DWH from Lakehouse (new_salesdata).
- Developed Stored Procedure to insert data into Fact & Dim tables.
- Executed procedure → Data successfully populated.

**6). Semantic Model & Reporting**

- Built Semantic Model on top of Data Warehouse.
- Defined relationships between Fact & Dimension tables.
- Created a Calendar Table and linked with Fact data.
- Enabled Power BI auto-report generation from Semantic Model.

---

For Detailed Technical Docs, Refer to this Link: [Trek Bike Sales Documentation](https://docs.google.com/document/d/1QrKhsWo6287eHkklFaUAm-tVXzGfVX1G/edit?usp=sharing&ouid=117502349783094744613&rtpof=true&sd=true)
