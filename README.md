# TextEmAll
SQL Challenge for Text Em All

Challenge 1:(15 - 20 minutes) 

  select * from wideworldimporters.sales.customertransactions

  select transactiondate, amountexcludingtax, tax amount, transactionamount, finalizationdate from    
  wideworldimporters.sales.customtertransactions group by transactiondate

  select TransactionDate, sum(TransactionAmount) as total_earned
  from wideworldimporters.sales.CustomerTransactions
  group by TransactionDate
  order by TransactionDate;


Challenge 2: (20 - 25 minutes)

  select * from wideworldimporters.sales.customercategories

  select * from wideworldimporters.sales.customers

  select * from wideworldimporters.sales.customerstransactions

  select WideWorldImporters.sales.CustomerCategories.CustomerCategoryID, 
     WideWorldImporters.sales.CustomerCategories.CustomerCategoryName, 
     WideWorldImporters.sales.Customers.AccountOpenedDate
  from WideWorldImporters.sales.CustomerCategories, 
     WideWorldImporters.sales.Customers
  where WideWorldImporters.sales.CustomerCategories.CustomerCategoryID = 
     WideWorldImporters.sales.Customers.CustomerCategoryID;
    
  (Answer) The fasted growing customer category from Q1 of Fiscal Year 2015 to Fiscal Year 2016 was category 5 (Computer Store).  
  It appears that category 5 grew about 50% from the previous year. 
  
  
Challenge 3: (45 minutes)
  
  This challenge was difficult for me. I was able to query the table I needed very quickly, however, I was not able to sort the table how I wanted. The resulting table was extremely long. Everytime I tried to write a different query to order or group the table in a way that was easier to read, it resulted in a table that could not be correct. The numbers that would appear just didn't make any sense. So here is the orignal query I used to get the table. The table is long, but with practice, I would learn how to get the result I need. 
  
select WideWorldImporters.Purchasing.Suppliers.SupplierName,
    WideWorldImporters.Purchasing.SupplierTransactions.IsFinalized
from WideWorldImporters.Purchasing.Suppliers, 
    WideWorldImporters.Purchasing.SupplierTransactions
    
select avg(WideWorldImporters.Purchasing.SupplierTransactions.TransactionAmount) 
    as average_invoice
from WideWorldImporters.Purchasing.SupplierTransactions;


Challenge 4: (15 minutes)

select StockItemName, UnitPrice, RecommendedRetailPrice
from WideWorldImporters.Warehouse.StockItems
where RecommendedRetailPrice - UnitPrice <1;

(Answer) The item with the lowest gross profit is the 3 kg Courier post bag (White) 300x190x95mm with a profit of $0.33.

select StockItemName, UnitPrice, RecommendedRetailPrice
from WideWorldImporters.Warehouse.StockItems
where RecommendedRetailPrice - UnitPrice > 200;

(Answer) The item with the highest gross profit is the Air cushion machine (Blue) with a profit of $940.01.

alter table WideWorldImporters.warehouse.stockitems
add column gross int;

alter table WideWorldImporters.warehouse.stockitems
alter column gross decimal(5,2);

update WideWorldImporters.Warehouse.StockItems
set gross = RecommendedRetailPrice - UnitPrice;

select stockitemname, unitprice, recommendedretailprice, gross 
from WideWorldImporters.Warehouse.StockItems
order by gross

(Answer) The median gross income from all items is $8.91;
