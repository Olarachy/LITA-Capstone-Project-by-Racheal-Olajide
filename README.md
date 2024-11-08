# LITA-Capstone-Project-Oct-2024

## Project 1 ; Sales Performance Analysis for a Retail Store
### Project Objective
Explore sales data to uncover key insights such as;
- Top Selling Products
- Regional Performance
- Monthly Sales Trends
  Using the following data analsis tool;
  1. Excel
  2. SQL
  3. Power BI
##### The goal is to produce an interactive Power BI dashboard that highlights these findings.

### EXCEL

##### Objectives;
1. Initial exploaration of the sales data. Use pivot tables to summarize total sales by product, region, and month.

  Total sales by Product
|Products  |	Sum of Sales |
|----------|---------------|
|Gloves	   |1,500,000 
|Hat	     |1,587,500 
|Jacket	   |1,050,000 
|Shirt	   |2,450,000 
|Shoes	   |3,087,500 
|Socks	   |912,500 
|Total	   |10,587,500 
![image](https://github.com/user-attachments/assets/5daba623-e92d-4a15-a57d-776814f40614)


  Total sales by region
![image](https://github.com/user-attachments/assets/04c2ea9c-30f3-4456-ac73-2dd785ff4442)

  
  Total sales by month; Grouped by month in year 2023/2024
This shows the monthly performance of each month for year 2023 and 2024.
  
![image](https://github.com/user-attachments/assets/27d8c9c6-fe45-44e5-84b0-7557f3b2e791)

### DATA VISUALIZATION IN EXCEL


### SQL

 #### Sales Performance Analysis for a Retail Store

SELECT * FROM dbo.[Capstone Sales Data ]

Total sales Column
```SELECT Quantity,UnitPrice, Quantity * UnitPrice as Total_Sales from dbo.[Capstone Sales Data ]```

ALTER TABLE [dbo].[Capstone Sales Data ] add Total_Sales int
UPDATE  [dbo].[Capstone Sales Data ] set Total_Sales = Quantity * UnitPrice

Total Sales for each product category
SELECT Product, SUM(Total_Sales) as Total_Sales from  [dbo].[Capstone Sales Data ] group by Product

 Number of sales transaction in each region
SELECT Region, COUNT(Total_Sales) as No_Of_Regional_Sales_Transaction from [dbo].[Capstone Sales Data ] group by region

Highest-selling product by total sales value

SELECT Product, MAX(Total_Sales) as Highest_Selling_Product from [dbo].[Capstone Sales Data ] group by Product

Highest-selling product by total sales value

SELECT Product, SUM(Total_Sales) as Highest_Selling_Product from [dbo].[Capstone Sales Data ] group by Product
order by Highest_Selling_Product desc```

Total revenue per product

SELECT Product, SUM(Total_Sales) as Total_Revenue from  [dbo].[Capstone Sales Data ] group by Product

Monthly sales total for the current year

SELECT Month(OrderDate) as Month, SUM(Quantity*UnitPrice) as Monthly_Sales from [dbo].[Capstone Sales Data ]
where YEAR(OrderDate)= YEAR(GETDATE())
group by Month(OrderDate)

-------Top 5 customers by total purchase amount------

SELECT Top 5 Customer_Id, SUM(Total_Sales) as Total_Purchase_Amount from  [dbo].[Capstone Sales Data ] group by Customer_Id
order by Total_Purchase_Amount desc

---------Percentage of total sales contributed by each region-------
SELECT Region, SUM(Quantity*UnitPrice*100) as Regional_Total_Sales_Percent from [dbo].[Capstone Sales Data ]
group by Region

---------Products with no sales in the last quarter-------

SELECT Distinct Product,OrderID,Quantity from [dbo].[Capstone Sales Data ]
where product NOT IN
(select distinct Product from [dbo].[Capstone Sales Data ]
where OrderDate between '2024-07-01' and '2024-09-03'





