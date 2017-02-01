## Key words
- WHERE
- GROUP BY
- ORDER BY (sort)
- JOIN (merge)
- these commands are case insensitive.
- The values are case sensitive.



## Practice Exercises
Which customers are from the UK?

```sql
SELECT * FROM Customers WHERE Country = 'UK'
```

What is the name of the customer who has the most orders?

```sql
SELECT CustomerName, COUNT(*) as count
FROM Customers
JOIN Orders
ON Customers.CustomerID = Orders.CustomerID
GROUP BY CustomerName   
ORDER BY count desc limit 1
```
Which supplier has the highest average product price?

```sql
SELECT SupplierName, AVG(Price) as ave
FROM Suppliers
JOIN Products ON Suppliers.SupplierID = Products.SupplierID
GROUP BY SupplierName
ORDER BY ave desc limit 1
```
How many different countries are all the customers from? (Hint: consider DISTINCT.)
```sql
SELECT COUNT(DISTINCT Country) from Customers
```

What category appears in the most orders?
```sql
SELECT CategoryName, cc
from Categories
JOIN
	(SELECT CategoryID, COUNT(*) as cc from Products
    JOIN OrderDetails ON Products.ProductID = OrderDetails.ProductID
    GROUP BY CategoryID) as A
ON Categories.CategoryID = A.CategoryID
ORDER BY cc desc limit 1
```

What was the total cost for each order?
```sql
SELECT
	OrderID, SUM(Price) as totalPrice
FROM
	Products
JOIN
	OrderDetails on Products.ProductID = OrderDetails.ProductID
GROUP BY
	OrderID
```
Which employee made the most sales (by total cost)?
```sql
SELECT lastName, firstName, totalSales FROM Employees JOIN (SELECT EmployeeID, SUM(totalPrice) as totalSales from Orders JOIN (SELECT
	OrderID, SUM(Price) as totalPrice
FROM
	Products
JOIN
	OrderDetails on Products.ProductID = OrderDetails.ProductID
GROUP BY
	OrderID) as A
ON Orders.OrderID = A.OrderID
GROUP BY
	EmployeeID
ORDER BY totalSales desc limit 1) as B
ON
	Employees.EmployeeID = B.EmployeeID
```
Which employees have BS degrees? (Hint: look at the LIKE operator.)
```sql
SELECT * FROM [Employees] WHERE Notes LIKE '%BS%'
```
Which supplier of three or more products has the highest average product price? (Hint: look at the HAVING operator.)
```sql
SELECT SupplierName FROM Suppliers INNER JOIN (SELECT SupplierID, AVG(Price) as avgPrice
	FROM Products GROUP BY SupplierID HAVING COUNT(SupplierID) > 3 ORDER BY avgPrice desc limit 1) as B
ON Suppliers.SupplierID = B.SupplierID
```
