# AdventureWorks2017-
AdventureWorks2017 Quick Analysis

Select *
from Sales.SalesOrderDetail

Select *
from Sales.SalesOrderHeader

Select *
from Production.Product

Select *
from Sales.SalesTerritory

-- Full combination of all tables 
Use AdventureWorks2017
Select ssd.SalesOrderID,PP.Name, ssd.OrderQty, ssd.UnitPrice, (OrderQty*UnitPrice) as LineTotal,SST.Name as 'Region Name',left(ssd.ModifiedDate, 11) as Date,day(SSD.ModifiedDate) as Day, left(DATENAME(MM, SSD.ModifiedDate), 3) as  MonthName, Year(SSD.ModifiedDate) as Year, SSH.CustomerID
from Sales.SalesOrderDetail SSD
	Left join Production.Product PP on SSD.ProductID = PP.ProductID
	Left join Sales.SalesOrderHeader SSH on SSD.SalesOrderID = SSH.SalesOrderID 
	Left join Sales.SalesTerritory SST on SST.TerritoryID = SSH.TerritoryID
--Where year(ssd.ModifiedDate) = 2011 
order by ssd.SalesOrderID asc


