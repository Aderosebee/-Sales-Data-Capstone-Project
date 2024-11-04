# Capstone Project
---
## Project Title: Sales Data

### Project Overview For Sales Data
This project focuses on analyzing sales data to provide insights into customer purchasing behavior, product performance, and regional sales distribution. The data includes key variables such as OrderID, Customer, Product, Region, OrderDate, Quantity, UnitPrice, and Revenue. The goal of this analysis is to identify patterns and trends in customer orders, assess the performance of different products across various regions, and examine factors that contribute to revenue generation. This analysis can help the company make data-driven decisions to optimize sales and maximize revenue.

### Measures
- OrderID: A unique identifier for each order.
- CustomerId: A unique identifier for each customer placing an order.
- Product: The specific product purchased in each transaction.
- Region: The geographical location (e.g., North, South, East, West) where the order was placed.
- OrderDate: The date when the order was made.
- Quantity: The number of units purchased for each product in an order.
- UnitPrice: The price per unit of the product.
- Total Sales: The total sales value for the order, calculated as Quantity * UnitPrice

### Data Source:
The main data sources for this analysis are the "Data Sales.csv" and "Customer.csv" files, which are open-source datasets available for free download from online repositories like Kaggle, FRED, or other similar platforms.

### Tools Used
- Excel: Employed for data cleaning and visualization.
- SQL: Utilized for data cleaning through queries.
- Power BI: Used for both data cleaning and visualization.

### Data Cleaning and Preparation
---
In the intial phase of Data Cleaning and Preparations, we perform the following action;

- Data loading and Inspection
- Handling missing variables
- Data Cleaning and Formatting

### Objectives
---
1. Retrieve the total sales for each product category.
2. Find the number of sales transactions in each region.
3. Find the highest-selling product by total sales value.
4. Calculate total revenue per product.
5. Calculate monthly sales totals for the current year.
6. Find the top 5 customers by total purchase amount.
7. Calculate the percentage of total sales contributed by each region.
8. Identify products with no sales in the last quarter.

###  EDA (Exploratory Data Analysis) 
---
EDA are set of steps used to explore and understand the dataset better, before cleaning and transformation.
Rows: 50000
Columns: 7 Columns

#### On Excel 
- Calculate using pivot table:
-  The total sales by region
-  Total sales
-  Average of  sales
-  Total sales per product
  
![Sales Excel Pivot](https://github.com/user-attachments/assets/6fe22cd4-24e1-465b-8bf7-30bcdeacb711)


