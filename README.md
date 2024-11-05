# Capstone Project 1
---
## Project Title: Sales Data
---
[Project Overview For Sales Data](#project-overview-for-sales-data)

[Measures](#measures)

[Data Source](#data-source)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Objectives](#objectives)

[Exploratory Data Analysis](#exploratory-data-analysis)

[On Excel](#on-excel) 

[SQL Data Analysis](#sql-data-analysis)

[Dashboard Overview](#dashboard-overview)

[Data Analysis and Insights Generation](data-analysis-and-insights-generation)

[Conclusion](#conclusion)

[Recommendation](#recommendation)

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

### Data Source
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

###  Exploratory Data Analysis
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
![New Excel](https://github.com/user-attachments/assets/8d0def3d-51ca-4204-9e91-a83d2d9c9297)


#### SQL Data Analysis
This is where we include some basic lines of code or queries or even some of the DAX expressions used during your analysis;
---
- Show the table
```select * from [dbo].[SalesData]
```
![Selecting table1](https://github.com/user-attachments/assets/fc41c3b9-532b-4ef6-b462-2304cd0f4ced)


- Total Sales for each product category
```SELECT Product, 
SUM(Revenue) AS TotalSales
FROM [dbo].[SalesData]
GROUP By Product;
```
![Total Sales by pc](https://github.com/user-attachments/assets/3a27139d-30dd-4655-952e-ac85b399933d)


- Number of transaction by region
```Select Region, count(*) as NumberOfTransactions
From [dbo].[SalesData]
Group by Region;
```
![Region by transact](https://github.com/user-attachments/assets/024c2991-d084-409c-9935-91f4b1a65869)

- Top Performing Product
```select top 1 product, sum(quantity*unitprice) as totalsales
From [dbo]. [SalesData]
Group by product
Order by totalsales desc;
```
![Top 1 product](https://github.com/user-attachments/assets/f06b2152-4cb6-40f9-985f-9c4bd0b7aa2d)

- Monthly Sales Total
```Select month(OrderDate) as month, sum(quantity*unitprice) as MonthlySales
From [dbo].[SalesData]
Where year(OrderDate) = year(GetDate())
Group by month(OrderDate)
Order by month;
```
![Order Date](https://github.com/user-attachments/assets/2987064e-ecbc-4c51-ba88-021c08134900)

- Top Performing Customers
```Select top 5 customer_id, sum(quantity*unitprice) as totalpurchaseAmount
From [dbo].[SalesData]
Group by customer_id
Order by TotalPurchaseAmount desc;
```
![Top customer](https://github.com/user-attachments/assets/c6177abe-cc31-4e54-acbe-ae3ebb0ccd56)

- Products with no sales
```Select distinct product
From [dbo].[SalesData]
Where product Not In(
Select product
From [dbo].[SalesData]
Where OrderDate >= DateAdd(quarter, -1, GetDate()) and OrderDate < GetDate());
```
![Distinct prod](https://github.com/user-attachments/assets/2cdd8f05-dbc1-4a43-93ea-4f363c46863a)

### Dashboard Overview
![Dashboard Overview 2](https://github.com/user-attachments/assets/ba6f4276-597e-414a-ace9-d68aa548c901)




### Data Analysis and Insights Generation
1. Top Performing Product: To gain a deeper understanding on the products with highest revenue and highest quantity sold.

![Top Performing Products based on quantity and revenue](https://github.com/user-attachments/assets/5c1431d7-ea49-4413-8061-fc3054c2716f)

Insights:
- Shoes generated the highest revenue at $0.61M despite the fact that only 14000 shoes were sold, indicating that this product is the most popular followed by shirts at $0.49M with a quantity of 12000 and hats at $0.32M with quantity of 16000. Gloves and jackets generated the lowest revenue at $0.30M and $0.21M respectively.
- This suggests that shoes and shirts are possibly appealing to similar customer.

2. Sales Trend by Month and Region: To gain understading about the seasonal trends of the products sales as the month progresses and accepted regionwise.

![Sales Trend](https://github.com/user-attachments/assets/81aaf0d9-31b0-44af-af6b-09ebde01d9f7)

Insights:
- There is an increase in total sales with $0.55M in the month of february in the southern region followed by $0.27M in the month of July in the eastern region followed by $0.25M in the month of January in the northern region followed by $.0.27M in the month of August in the western region.
- This denotes that there is more concentration at the southern region which needs to be circulated to other regions.

3. Product Sales by Region: To gain indepth knowledge about revenue generated in each region.

![Total sales by r](https://github.com/user-attachments/assets/e790d360-d765-41b7-9269-b46727612668)

Insights:
- 
---

### Conclusion
---
From the analysis of the sales data, we observed that certain regions like south and east; and products like shoes and shirts contributed significantly to the overall revenue. Products with higher quantities sold, or those priced strategically, demonstrated strong sales performance.  Additionally, we noticed fluctuations in sales over different periods, which could indicate seasonal or promotional effects on purchasing patterns.

### Recommendation
---
To enhance revenue and optimize sales performance, we recommend the following actions:

- Targeted Marketing: Focus marketing efforts on regions and customers that show high purchasing behavior. Tailored promotions in these areas could boost revenue.
- Product Optimization: Analyze underperforming products and consider adjusting pricing or bundling with high-performing items.
- Seasonal Promotions: Capitalize on the sales patterns by planning promotions during peak periods to increase order volume and revenue.
- Customer Loyalty Programs: Implement loyalty programs for repeat customers to encourage larger and more frequent purchases, especially in regions with consistent buying patterns.
- Continuous Monitoring: Regularly monitor sales data to identify new trends and adjust strategies as necessary to stay aligned with customer preferences.



