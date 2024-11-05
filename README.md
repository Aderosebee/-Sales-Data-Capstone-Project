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

[Data Visualization](#data-visualization)

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
  
![Sales Excel Pivot](https://github.com/user-attachments/assets/6fe22cd4-24e1-465b-8bf7-30bcdeacb711)

#### SQL Data Analysis
This is where we include some basic lines of code or queries or even some of the DAX expressions used during your analysis;
---
- Show the table
```select * from [dbo].[SalesData]
```
![Selceting tables](https://github.com/user-attachments/assets/503e8400-ec5e-4b66-ba9c-12fc4f8745fb)

- Total Sales for each product category
```SELECT Product, 
SUM(Revenue) AS TotalSales
FROM [dbo].[SalesData]
GROUP By Product;
```
![Total sales by product category](https://github.com/user-attachments/assets/27554940-6646-4819-8fb1-621dd0ff6729)

- Number of transaction by region
```Select Region, count(*) as NumberOfTransactions
From [dbo].[SalesData]
Group by Region;
```
![Number of transactions per Region](https://github.com/user-attachments/assets/147abe2b-0fca-4d03-aeb3-5c0d0b1e35af)

- Top Performing Product
```select top 1 product, sum(quantity*unitprice) as totalsales
From [dbo]. [SalesData]
Group by product
Order by totalsales desc;
```
![Top performing product](https://github.com/user-attachments/assets/25a07345-0979-4767-ba19-4a6cf1396bc9)

- Monthly Sales Total
```Select month(OrderDate) as month, sum(quantity*unitprice) as MonthlySales
From [dbo].[SalesData]
Where year(OrderDate) = year(GetDate())
Group by month(OrderDate)
Order by month;
```
![Monthly sales](https://github.com/user-attachments/assets/ee7e0915-c0a2-4660-8380-ff1f46f76b01)

- Top Performing Customers
```Select top 5 customer_id, sum(quantity*unitprice) as totalpurchaseAmount
From [dbo].[SalesData]
Group by customer_id
Order by TotalPurchaseAmount desc;
```
![Top performing customers](https://github.com/user-attachments/assets/4d9768e4-346c-45cd-b826-a3dfaacb680d)

- Products with no sales
```Select distinct product
From [dbo].[SalesData]
Where product Not In(
Select product
From [dbo].[SalesData]
Where OrderDate >= DateAdd(quarter, -1, GetDate()) and OrderDate < GetDate());
```
![Product with no sales](https://github.com/user-attachments/assets/49bb0fde-df88-4143-a210-6666404e7ac7)

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
- 

---

### Conclusion
---
From the analysis of the sales data, we observed that certain regions and products contributed significantly to the overall revenue. Products with higher quantities sold, or those priced strategically, demonstrated strong sales performance. Customer purchasing behavior varied across regions, with certain customers consistently making larger purchases, which influenced the revenue. Additionally, we noticed fluctuations in sales over different periods, which could indicate seasonal or promotional effects on purchasing patterns.

### Recommendation
---
To enhance revenue and optimize sales performance, we recommend the following actions:

- Targeted Marketing: Focus marketing efforts on regions and customers that show high purchasing behavior. Tailored promotions in these areas could boost revenue.
- Product Optimization: Analyze underperforming products and consider adjusting pricing or bundling with high-performing items.
- Seasonal Promotions: Capitalize on the sales patterns by planning promotions during peak periods to increase order volume and revenue.
- Customer Loyalty Programs: Implement loyalty programs for repeat customers to encourage larger and more frequent purchases, especially in regions with consistent buying patterns.
- Continuous Monitoring: Regularly monitor sales data to identify new trends and adjust strategies as necessary to stay aligned with customer preferences.



