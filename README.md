# Stationery-Store

### Business Request 
The Sales Manager requested a move from static reports to interactive for better track of sales performance focusing on products sold, payment method, Geographic breakdown,customers retention, and month over month (MOM) growth rate.

### Tool used
SQL Server Express
SQL Server Management Studio (SSMS)


### Skills Applied
Data Cleaning Queries
-Duplicate Records: 
-Inconsistent Formatting:
-Data validation 
-Fix of Invalid Sales Representative References 

### Business Questions & Key Findings

#### What is the Total Profit ?

```
Select sum(Profit) As [total Profit]
From [SalesSQL].[dbo].[Sales Datasql];
