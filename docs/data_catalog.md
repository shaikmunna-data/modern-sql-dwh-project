# **Overview**
The Gold Layer is designed to provide **business-ready data** for reporting, dashboards, and analytics. It consists one fact table containing sales transactions and two dimension tables containing customer and product information.

**This structure helps:**

- Understand **who** bought the product (Customer Dimension)

- Understand **what** was bought (Product Dimension)

- Analyze **how much and when** the sales happened (Sales Fact)
##  1. **gold.dim_customers**
- **Purpose:** This table stores detailed information about each customer. 
- **Columns**

| Column Name     | Data Type    | Description                                                                           |
| :-------------- | ------------ | ------------------------------------------------------------------------------------- |
| customer_key    | BIGINT       | Surrogate key uniquely identifying each customer record in the dimension table.       |
| customer_id     | INT          | Unique numerical identifier assigned to each customer.                                |
| customer_number | NVARCHAR(50) | Alphanumeric identifier representing the customer, used for tracking and referencing. |
| first_name      | NVARCHAR(50) | Customer’s first name.                                                                |
| last_name       | NVARCHAR(50) | Customer’s last name.                                                                 |
| country         | NVARCHAR(50) | Country where the customer lives.                                                     |
| maratial_status | NVARCHAR(50) | Customer’s marital status (e.g., Single, Married).                                    |
| gender          | NVARCHAR(50) | Gender information                                                                    |
| birthdate       | DATE         | Customer’s date of birth.                                                             |
| create_date     | DATE         | Date when the customer record was created in the source system.                       |

## 2. **gold_dim_prodicts**
- **Purpose:** Provides information about the products and their attributes.
- **Columns**


| Column Name    | Data Type    | Description                                                                                          |
| -------------- | ------------ | ---------------------------------------------------------------------------------------------------- |
| product_key    | BIGINT       | Surrogate key uniquely identifying each product record in the product dimension table.               |
| product_id     | INT          | A unique identifier assigned to the product for internal tracking and referencing.                   |
| product_number | NVARCHAR(50) | A structured alphanumeric code representing the product, often used for categorization or inventory. |
| product_name   | NVARCHAR(50) | Descriptive name of the product, including key details such as type, color, and size.                |
| category_id    | NVARCHAR(50) | A more detailed classification of the product within the category, such as product type.             |
| category       | NVARCHAR(50) | The broader classification of the product (e.g., Bikes, Components) to group related items.          |
| sub_category   | NVARCHAR(50) |                                                                                                      |
| maintenance    | NVARCHAR(50) | Whether the product requires maintenance (Yes/No or cost amount).                                    |
| cost           | INT          | Product cost.                                                                                        |
| product_line   | NVARCHAR(50) | Business product line grouping.                                                                      |
| start_date     | DATE         | Date from when the product became available.                                                         |
# **3.gold.fact_sakes**
- **Purpose:** Stores transactional sales data for analytical purposes.
- **Columns:**

| Column Name   | Data Type | Descriptions                                                      |
| ------------- | --------- | ----------------------------------------------------------------- |
| order_number  | NVARCHAT(50)      | Unique identifier for each sales order.                           |
| product_key   | BIGINT      | Foreign key referencing product dimension.                        |
| customer_key  | BIGINT      | Foreign key referencing customer dimension.                       |
| order_date    | DATE      | Date when the order was placed.                                   |
| shipping_date | DATE      | Date when the order was shipped.                                  |
| due_date      | DATE      | Expected delivery or payment due date.                            |
| sales_amount  | INT       | Total revenue for the line item (calculated as quantity × price). |
| quality       | INT       | Number of units sold in the transaction.                          |
| price         | INT       | Selling price per unit of the product.                            |
