# SQL-exercises-Week-3
/*1. Display the total amount collected from the orders for each order date. */

USE AdventureWorks2012
SelecT orderdate, SUm(totaldue)
from sales.SalesOrderHeader
group by orderdate 
　
/*2. Display the total amount collected after selling the products, 774 and 777. */
USE AdventureWorks2012
select productID, OrderQty, UnitPrice
from sales.SalesOrderDetail
where productid in (774,777)

　
/*3. Write a query to display the sales person ID of all the sales persons and the name of the territory to which they belong.*/
USE AdventureWorks2012
select businessentityid
from sales.SalesPerson
join sales.salesterritory
on sales.SalesPerson.TerritoryID=Sales.SalesTerritory.Name

/*4. Write a query to display the Business Entities of the customers that have the 'Vista' credit card.*/

USE AdventureWorks2012
select customerid, cardtype
from sales.customer, sales.creditcard
where cardtype in (vista)
　
/*5, Write a query to display all the country region codes along with their corresponding territory IDs*/

use AdventureWorks2012
select name,TerritoryID
from sales.SalesTerritory
　
/*6. Find out the average of the total dues of all the orders.*/
USE AdventureWorks2012
select avg(totaldue)
from sales.SalesOrderHeader
/*7. Write a query to report the sales order ID of those orders where the total value is greater than the average of the total value of all the orders.*/
USE AdventureWorks2012
select PurchaseOrderNumber,TotalDue
from sales.SalesOrderHeader
having avg(totaldue) > avg(TotalDue)
