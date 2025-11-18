# **SQL Datawarehouse Project**
## 📌**Project Overview**
This project is a simple SQL Data Warehouse built using **Bronze, Silver, and Gold Layers**.The main idea is to take raw data from sources (like CRM/ERP CSV files), clean it, and finally create useful tables and views for reporting.

## 🏭**Data Architecture**
The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** Layers:
![Data Architecture](docs/high_level_architecture.png)

### 🥉**Bronze Layer - Raw Data**
- Stores the **raw files** exactly as they come.
- No transformations.
- Mainly used for backup and tracing the original data.
### 🥈**Silver Layer - Cleaned Data**
- Data is cleaned, standardized, and formatted. 
- Missing values, wrong formats, and inconsistent data are fixed here.
- These tables are ready for analysis but still not in business format.
### 🥇**Gold Layer - Business Layer**
- Contains **Views**, not tables.
- Combines different tables, adds logic, and creates final business-ready datasets. 
- Used for reporting, SQL queries, and dashboards.









