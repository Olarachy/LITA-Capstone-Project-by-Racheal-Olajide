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
|Region	 |Sum of Sales|
|--------|------------|
|East	   |2,450,000   |
|North	 |1,950,000   |
|South	 |4,675,000   |
|West	   |1,512,500   |
|Total	 |10,587,500  |
![image](https://github.com/user-attachments/assets/04c2ea9c-30f3-4456-ac73-2dd785ff4442)

  
  Total sales by month; Grouped by month in year 2023/2024
This shows the monthly performance of each month for year 2023 and 2024.
  
|Month	  |Sum of Sales|
|---------|------------|
|2023	    |5,575,000   |
|Jan	    |250,000     |
|Feb	    |1,250,000   |
|Mar	    |262,500     |
|Apr	    |37,500      |
|May	    |300,000     |
|Jun	    |500,000     |
|Jul	    |1,200,000   |
|Aug	    |150,000     |
|Sep	    |175,000     |
|Oct	    |675,000     |
|Nov	    |525,000     |
|Dec	    |250,000     |
|2024	    |5,012,500   |
|Jan	    |1,000,000   |
|Feb	    |1,500,000   |
|Mar	    |275,000     |
|Apr	    |200,000     |
|May	    |225,000     |
|Jun	    |750,000     |
|Jul	    |187,500     |
|Aug	    |875,000     |
|Total	  |10,587,500  |
![image](https://github.com/user-attachments/assets/27d8c9c6-fe45-44e5-84b0-7557f3b2e791)

Other Report

### SQL

 Sales Performance Analysis for a Retail Store

SELECT * FROM dbo.[Capstone Sales Data ]

Total sales Column
```SELECT Quantity,UnitPrice, Quantity * UnitPrice as Total_Sales from dbo.[Capstone Sales Data ]```

ALTER TABLE [dbo].[Capstone Sales Data ] add Total_Sales int
UPDATE  [dbo].[Capstone Sales Data ] set Total_Sales = Quantity * UnitPrice

Total Sales for each product category
```SELECT Product, SUM(Total_Sales) as Total_Sales from  [dbo].[Capstone Sales Data ] group by Product```

 Number of sales transaction in each region
```SELECT Region, COUNT(Total_Sales) as No_Of_Regional_Sales_Transaction from [dbo].[Capstone Sales Data ] group by region```

Highest-selling product by total sales value
```SELECT Product, MAX(Total_Sales) as Highest_Selling_Product from [dbo].[Capstone Sales Data ] group by Product```

Highest-selling product by total sales value
```SELECT Product, SUM(Total_Sales) as Highest_Selling_Product from [dbo].[Capstone Sales Data ] group by Product
order by Highest_Selling_Product desc```

Total revenue per product
```SELECT Product, SUM(Total_Sales) as Total_Revenue from  [dbo].[Capstone Sales Data ] group by Product```

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



## PROJECT 2; Customer Segmentation for a Subscription Service

### Excel

1. Pivot tables to find subscription patterns.

2. Average subscription duration

2b.Most popular subscription types.

Other interesting reports.

### SQL

 ```SELECT * FROM[dbo].[Capston Customer Data]

--------Total number of customers from each region-----

SELECT Region, COUNT(DISTINCT CustomerID) AS Total_No_customers 
FROM [dbo].[Capston Customer Data] GROUP BY Region

------Most popular subscription type by the number of customers------

SELECT  TOP 1 SubscriptionType, COUNT(DISTINCT customerid) AS Popular_Subscription
FROM[dbo].[Capston Customer Data]
GROUP BY SubscriptionType

-----Customers who canceled their subscription within 6 months-----

SELECT CustomerID FROM [dbo].[Capston Customer Data] WHERE DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6

------Average subscription duration for all customers------

SELECT AVG(Duration) AS Average_Subscription_Duration 
FROM (
SELECT DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) AS Duration 
FROM [dbo].[Capston Customer Data] 
) AS SubQuery


-------Customers with subscriptions longer than 12 months-------

SELECT CustomerID,SubscriptionStart, SubscriptionEnd, DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) 
AS Subscription_Above_12_Months FROM [dbo].[Capston Customer Data] 
WHERE DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd)>12


-----Total revenue by subscription type------

SELECT  SubscriptionType, SUM(Revenue)AS Total_Revenue
FROM[dbo].[Capston Customer Data] GROUP BY SubscriptionType

-----Top 3 regions by subscription cancellations-----

SELECT TOP 3 Region,
COUNT(*) AS SubscriptionEnd_count
FROM [dbo].[Capston Customer Data]
GROUP BY Region
ORDER BY SubscriptionEnd_Count DESC;

--------Total number of active and canceled subscriptions-----

--------CANCELLED SUBSCRIPTION-----

SELECT COUNT(*) AS Cancelled_Subscription FROM [Capston Customer Data] WHERE Canceled = 'FALSE'

--------ACTIVE SUBSCRIPTION------

SELECT COUNT(*) AS Cancelled_Subscription FROM [Capston Customer Data] WHERE Canceled = 'TRUE'```


### Power BI
https://github.com/Olarachy/LITA-Capstone-Project-by-Racheal-Olajide/issues/1#issuecomment-2457038856


 
Visualization of customer segments, cancellations, and subscription trends
  <img width="641" alt="CAPSTONE CUSTOMER DATA" src="https://github.com/user-attachments/assets/ede4904d-e197-4168-8148-9b73eb55cc66">

[LITA Capstone Dataset Cleaned In Excel.xlsx](https://github.com/user-attachments/files/17631794/LITA.Capstone.Dataset.Cleaned.In.Excel.xlsx)



