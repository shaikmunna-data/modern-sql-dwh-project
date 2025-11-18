# **Naming Conventions**

This document explains how to name schemas, tables, views, columns, and other objects in the data warehouse. The aim is to make everything simple, consistent, and easy to understand.

## **Table of Contents**

1. [General Principles](#general-principles)
2. [Table Naming Conventions](#table-naming-conventions)
   - [Bronze Rules](#bronze-rules)
   - [Silver Rules](#silver-rules)
   - [Gold Rules](#gold-rules)
3. [Column Naming Conventions](#column-naming-conventions)
   - [Surrogate Keys](#surrogate-keys)
   - [Technical Columns](#technical-columns)
4. [Stored Procedure Naming](#stored-procedure-naming)

---

## **General Principles**

- Use **snake_case** for all object names (lowercase with underscores).
- Use **English** for all names.
- Avoid SQL **reserved keywords**.
- Keep names clean, meaningful, and easy to understand.

---

## **Table Naming Conventions**

### **Bronze Rules**

- Bronze layer stores raw data exactly as received from the source.
- Table names must start with the **source system name** and match the original table name.
- **Format:**  
  `sourcesystem_entity`
- **Examples:**  
  - `crm_customer_info`  
  - `erp_sales_order`

---

### **Silver Rules**

- Silver layer contains cleaned and transformed data but still follows the source structure.
- Naming rules are the **same as Bronze**.
- **Format:**  
  `sourcesystem_entity`
- **Example:**  
  - `crm_customer_info`

---

### **Gold Rules**

- Gold layer contains business-ready, meaningful, and well-structured tables.
- Table names must use business-friendly names.
- **Format:**  
  `category_entity`
- **Category Prefix Examples:**  
  - `dim_` → Dimension table  
  - `fact_` → Fact table  
  - `report_` → Reporting table

**Examples:**  
- `dim_customers`  
- `fact_sales`  
- `report_sales_monthly`

#### **Category Glossary**

| Pattern   | Meaning                | Examples                              |
|-----------|-------------------------|----------------------------------------|
| `dim_`    | Dimension table         | `dim_customer`, `dim_product`          |
| `fact_`   | Fact table              | `fact_sales`                           |
| `report_` | Report or summary table | `report_customers`, `report_sales_monthly` |

---

## **Column Naming Conventions**

### **Surrogate Keys**

- Dimension tables must use surrogate keys ending with `_key`.
- **Format:**  
  `table_name_key`
- **Example:**  
  - `customer_key` (Primary key for `dim_customers`)

---

### **Technical Columns**

- Technical or metadata columns must start with **`dwh_`**.
- These track metadata such as load dates, update timestamps, batch IDs, etc.
- **Format:**  
  `dwh_column_name`

**Examples:**  
- `dwh_load_date`  
- `dwh_update_timestamp`

---

## **Stored Procedure Naming**

- All stored procedures for data loading must follow this pattern:
- **Format:**  
  `load_layer`

Where `<layer>` is:  
- `bronze`  
- `silver`  
- `gold`

**Examples:**  
- `load_bronze`  
- `load_silver`  
- `load_gold`

---