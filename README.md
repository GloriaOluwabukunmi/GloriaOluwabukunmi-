# PROJECT 1
# PROJECT TItle: : Sales Performance Analysis for a Retail Store 


## Project Overview
This project analyzes the sales performance of a retail store, exploring sales data to uncover key insights such as top-selling products, regional performance, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings. 
## Data Sources
The primary source of data was sent by the company
## Data Collected
### The dataset includes the following key column;
- OrderID
- Customer ID
- Product
- Region
- OrderDate
- Quantity
- Unit Price

 ## Project Objectives
- This project was designed to address the following analysis goals;
- summarize total sales by product, region, and month with pivot table.
- average sales per product and total revenue by region with excel formula
- retrieve the total sales for each product category using SQL.
- find the number of sales transactions in each region using SQL.
- find the highest-selling product by total sales value using SQL.
- calculate total revenue per product with SQL.
- calculate monthly sales totals for the current year with SQL.
- find the top 5 customers by total purchase amount with SQL.
- calculate the percentage of total sales contributed by each region with SQL.
- identify products with no sales in the last quarter with SQL.
- Create a dashboard that visualizes the insights found in Excel and SQL with Powerbi and it should include a sales overview, top-performing products, and regional breakdowns
 ## key metrics 
- Sales; sum of sales column
- Average: Average of each product sold

 ## How to use the Data
- Total and Average sales: This was calculated using the SUM and AVERAGE function. This gives insight into the total sales for each product and Region
- Total Revenue: This shows the total revenue for each product with SQL
  Percentage of total sales: This gives insight into the percentage of total sales in each region
## FUNCTIONS USED
SUM, AVERAGE, GROUPBY
## Tools and Method Used
- Data Analysis: The data was analysed using Structured Query Langurage ( SQL), utilizing the various functions  to cteate table, summarize and organise the data for easier intrpretation.
- Data Visualization: table created was exported into The Microsoft excel inorder to create charts for easy visualization to represent the key insights
## Tools Used
- Structured Query Language (SQL)
- For running query
- for data manipulation
- Data Cleaning and Preparation

 
### DATA VISUALIZATION WITH PIVOT TABLE
	
![image](https://github.com/user-attachments/assets/50113805-7402-49c7-9556-e8f1e77ddcd7)
	
![image](https://github.com/user-attachments/assets/45893bbf-d05f-41b5-b827-639b2b42a676)

![image](https://github.com/user-attachments/assets/4ce3e2d9-ef21-4489-9998-a88a65aad66f)
	
![image](https://github.com/user-attachments/assets/77af6086-4263-437b-b0c5-9de5b39c41bb)
	
![image](https://github.com/user-attachments/assets/d2adbe1b-0e36-4340-8171-b0a818775115)

![image](https://github.com/user-attachments/assets/e87008c9-547d-40eb-9876-cb6f4a48a13b)


### AVERAGE SALES FOR GLOVES, HAT. SOCKS, SHIRT, JACKET AND SHOES
|Average sales for gloves|Average sales for hat|Average sales for socks|Average sales for shirt|Average sales for jacket|Average sales for shoes|
|-----------|---------|---------|---------|--------|----------|
|200.06|158.81|121.82|326.56|139.93|308.69|


### TOTAL REVENUE FOR NORTH, EAST, WEST AND SOUTH
|total revenue by North|total revenue by East|total revenue by West|total revenue by South|
|-----------|---------|---------|---------|
|387000|485925|300345|927820|


## SQL QUERIES FOR SALES DATA
- QUERY TO RETRIEVE THE TOTAL SALE FOR EACH PRODUCT CATEGORY
 ```SQL
SELECT product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[SalesData$]
GROUP BY [Product]
  ```
- QUERY TO FIND THE NUMBER OF SALES TRANSACTION IN EACH REGION
```SQL
SELECT Region, COUNT(OrderID) AS NumberOfTransactions
FROM SalesData$
GROUP BY Region
```
- QUERY TO FIND THE HIGHEST SELLING PRODUCT BY TOTAL SALES VALUE
 ```SQL
SELECT Top 1 Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM SalesData$
GROUP BY Product
ORDER BY TotalSales DESC
```
- QUERY

``` SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalRevenue
FROM SalesData$
GROUP BY Product
```
- QUERY TO CALCULATE MONTHLY SALES TOTAL FOR THE CURRENT YEAR
``` SQL
SELECT FORMAT(OrderDate, 'yyyy-MM') AS Month, SUM(Quantity * UnitPrice) AS TotalSales
FROM SalesData$
WHERE OrderDate >= DATEFROMPARTS(YEAR(GETDATE()), 1, 1) -- Start of the current year
  AND OrderDate < DATEADD(YEAR, 1, DATEFROMPARTS(YEAR(GETDATE()), 1, 1)) -- Start of the next year
GROUP BY FORMAT(OrderDate, 'yyyy-MM')
ORDER BY Month
```
- QUERY TO FIND THE TOP 5 CUSTOMWERS BY TOTAL PURCHASE AMOUNT

``` SQL
SELECT TOP 5 [Customer Id], SUM(Quantity * UnitPrice) AS TotalPurchase
FROM SalesData$
GROUP BY [Customer Id]
ORDER BY TotalPurchase DESC
```
- QUERY TO CALCULATE % OF TOTAL SALES CONTRIBUTED BY EACH REGION
``` SQL
SELECT Region, 
       SUM(Quantity * UnitPrice) AS TotalSales,
       (SUM(Quantity * UnitPrice) / (SELECT SUM(Quantity * UnitPrice) FROM SalesData$) * 100) AS PercentageContribution
FROM SalesData$
GROUP BY Region
```
- QUERY TO IDENTIFY PRODUCTS WITH NO SALES IN THE LAST QUARTERS
``` SQL
SELECT Product, SUM(Quantity) As Saless
FROM [dbo].[SalesData$]
WHERE MONTH(Orderdate) BETWEEN 10 AND 12  ---Months 10,11 and 12 (october to december)
GROUP BY Product
Having SUM(Quantity)=0
```



### DATA VISUALIZATION WITH POWERBI DASHBOARD
![Screenshot 2024-11-05 062742](https://github.com/user-attachments/assets/985e45cf-21fb-407b-a83d-e7aab8a12690)


![Screenshot 2024-11-05 062812](https://github.com/user-attachments/assets/b6047ea6-bea6-4520-a980-34bb5cf90f00)


![Screenshot 2024-11-05 062848](https://github.com/user-attachments/assets/c5bc376b-b0fc-4937-858e-bd14d7584f2a)


