# online-retail-data-engineering
eginner-friendly end-to-end ETL pipeline using PySpark, Databricks, Delta Lake, Spark SQL, and Power BI.
# Online Retail Data Engineering Project

An end-to-end beginner-friendly data engineering project built using **PySpark, Databricks Free Edition, Delta Lake, Spark SQL, and Power BI**.

## Project Overview

This project demonstrates how raw online retail transaction data can be ingested, cleaned, transformed, and summarized into business-ready datasets for analysis and visualization.

The pipeline follows the **Medallion Architecture** with Bronze, Silver, and Gold layers and uses Power BI to create an interactive sales dashboard.

## Architecture

```text
Online Retail CSV Dataset
          |
          v
    Bronze Layer
   Raw Data in Delta
          |
          v
    Silver Layer
 Data Cleaning and
 Transformations
          |
          v
     Gold Layer
 Country-wise and
 Product-wise Summaries
          |
          v
      Spark SQL
  Business Analysis
          |
          v
      Power BI
    Sales Dashboard
```

## Technologies Used

- **Python / PySpark** — Data processing and transformation
- **Databricks Free Edition** — Cloud-based data engineering environment
- **Delta Lake** — Storage for Bronze, Silver, and Gold datasets
- **Spark SQL** — Business queries and data analysis
- **Power BI Desktop** — Data visualization and dashboard development
- **GitHub** — Source code and project documentation

## Dataset

The project uses the Online Retail dataset, containing transaction records from a UK-based online retail business.

Key columns include:

- `InvoiceNo` — Invoice identifier
- `StockCode` — Product identifier
- `Description` — Product description
- `Quantity` — Quantity purchased or returned
- `InvoiceDate` — Transaction date and time
- `UnitPrice` — Price per unit
- `CustomerID` — Customer identifier
- `Country` — Customer's country

The original dataset is not included in this repository. Obtain it from the original dataset provider before reproducing the project.

## Data Engineering Workflow

### 1. Data Ingestion — Bronze Layer

- Loaded the source CSV dataset into Databricks.
- Saved the ingested data in Delta format.
- Preserved the ingested rows separately from subsequent cleaning operations.

### 2. Data Cleaning — Silver Layer

- Identified missing values across columns.
- Checked for exact duplicate records.
- Examined cancelled invoices and negative quantities.
- Removed exact duplicate rows.
- Removed records missing selected essential fields.
- Replaced missing product descriptions with `Unknown Product`.
- Converted transaction dates, quantities, and prices to appropriate data types.
- Created a `SalesAmount` column using quantity multiplied by unit price.

### 3. Data Aggregation — Gold Layer

Created two business-ready datasets:

**Country Sales Summary**
- Country
- Total net transaction value
- Distinct invoice count

**Product Sales Summary**
- Product identifier
- Product description
- Total net transaction value
- Net quantity

Saved both summaries in Delta format and exported them to CSV for Power BI.

### 4. SQL Analysis

Used Spark SQL to:

- Identify countries with the highest net transaction value.
- Calculate each country's percentage of total net transaction value.
- Identify the top 10 products by net transaction value.

### 5. Power BI Dashboard

Built a basic dashboard containing:

- Total Net Sales KPI card
- Sales by Country bar chart
- Top 10 Products by Net Sales bar chart

## Repository Structure

```text
online-retail-data-engineering/
│
├── notebooks/
│   └── Online_Retail_ETL.py
│
├── sql/
│   └── sales_analysis.sql
│
├── powerbi/
│   └── Online_Retail_ETL_Dashboard.pbix
│
├── screenshots/
│   └── dashboard.png
│
├── README.md
└── .gitignore
```

*The filenames above are suggested examples. Include only the files that are actually present in your repository.*

## Key Business Insights

The analysis enables users to:

- Compare net transaction values across countries.
- Identify products with high net transaction values.
- Compare net quantities across products.
- Explore overall retail transaction performance through visualizations.

## Important Data Considerations

- The dataset contains returns and cancelled invoices.
- Negative quantities and transaction values have been retained in the analysis.
- Consequently, sales figures represent **net transaction value**, not necessarily completed sales revenue.
- Missing customer identifiers may limit customer-level analysis.
- The current implementation is a beginner-level batch ETL pipeline and does not include automated orchestration, incremental ingestion, or production monitoring.

## How to Reproduce the Project

1. Obtain the original Online Retail CSV dataset.
2. Upload it to a Databricks volume.
3. Run the PySpark notebook to create the Bronze, Silver, and Gold datasets.
4. Run the Spark SQL analysis queries.
5. Export the Gold summary datasets to CSV.
6. Import the CSV files into Power BI Desktop.
7. Build or open the dashboard.

## Learning Outcomes

Through this project, I practiced:

- ETL pipeline fundamentals
- PySpark DataFrame operations
- Data profiling and cleaning
- Delta Lake storage
- Medallion Architecture
- Spark SQL queries and window functions
- Data aggregation and KPI preparation
- Power BI dashboard development

## Future Improvements

- Implement a fact-and-dimension data model.
- Add automated data-quality checks.
- Introduce incremental data ingestion.
- Add pipeline orchestration and monitoring.
- Expand the dashboard with additional KPIs.

---

**Project Type:** Beginner Data Engineering / ETL  
**Status:** Initial end-to-end pipeline and dashboard completed  
**Purpose:** Hands-on learning and portfolio development

