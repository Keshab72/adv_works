# Querying a Large Relational Database
## AdventureWorks2022

## Problem Statement:
How to get details about customers by querying a database?

## Topics:
In this project, you will work on downloading a database and restoring it on the server. You will then query the database to get customer details like name, phone number, email ID, sales made in a particular month, increase in month-on-month sales and even the total sales made to a particular customer.

## Highlights:
Table basics and data types
Various SQL operators
Various SQL functions

## Tasks To Be Performed:
### 1. Download the AdventureWorks database from the following location and restore it in your server:
Location: https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms

File Name: AdventureWorks2022.bak

AdventureWorks is a sample database shipped with SQL Server and it can be downloaded from the GitHub site. AdventureWorks has replaced Northwind and Pubs sample databases that were available in SQL Server in 2005. Microsoft keeps updating the sample database as it releases new versions.

### 2. Restore Backup:
Follow the below steps to restore a backup of your database using SQL Server Management Studio:
-  Open SQL Server Management Studio and connect to the target SQL Server instance
-  Right-click on the Databases Node and select Restore Database
-  Select Device and click on the ellipsis (...)
-  In the dialog box, select Backup devices, click on Add, navigate to the database backup in the file system of the server, select the backup, and click on OK.
- If needed, change the target location for the data and log files in the Files pane
Note: It is a best practice to place the data and log files on different  drives.
- Now, click on OK

This will initiate the database restore. After it completes, you will have the AdventureWorks database installed on your SQL Server instance.

### 3. Perform the following with help of the above database:
- Get all the details from the person table including email ID, phone number and phone number type
- Get the details of the sales header order made in May 2011
- Get the details of the sales details order made in the month of May 2011
- Get the total sales made in May 2011
- Get the total sales made in the year 2011 by month order by increasing sales
- Get the total sales made to the customer with FirstName='Gustavo' and LastName ='Achong'


## Data Analysis:- 
- Get the details of the sales details order made in the month of May 2011
```sql
select * from sales.SalesOrderDetail
select * from sales.SalesOrderHeader
SELECT * FROM
sales.SalesOrderHeader soh
INNER JOIN sales.SalesOrderDetail sod
ON soh.salesorderid = sod.salesorderid
WHERE orderdate BETWEEN '2011-05-01' AND '2011-05-31'
```
- Get the total sales made in the year 2011 by month order by increasing sales
```sql
SELECT DATEPART(MONTH, soh.orderdate) AS order_month, SUM(sod.orderqty * sod.unitprice) AS total_sales
FROM sales.SalesOrderDetail sod
INNER JOIN sales.SalesOrderHeader soh
ON sod.salesorderid = soh.salesorderid
WHERE YEAR(soh.orderdate) = 2011
GROUP BY DATEPART(MONTH, soh.orderdate)
ORDER BY total_sales ASC;
```
All the remaining queries is available in "adventureworks 2022" pdf file

THANK YOU 
