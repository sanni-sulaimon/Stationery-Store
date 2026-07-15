# Stationery-Store

### Business Request 
The Sales Manager requested a move from static reports to interactive for better track of sales performance focusing on products sold, payment method, Geographic breakdown, Customers retention, and month over month (MOM) growth rate.

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

#### 📌 Q1 What is the Total Profit ?

```
Select sum(Profit) As [total Profit]
From [SalesSQL].[dbo].[Sales Datasql];
```
|Profit|1086191|
|------|-------|

### 📌 Q2 What is the total amount of sales by category ?

```
Select Category, Sum(Amount) As [Total Sales]
From [SalesSQL].[dbo].[Sales Datasql]
Group by Category
Order by [Total Sales] Desc;
```
|Category |Total Sales|
|------|-------|
|Office Supplies|	1446574 |
|Electronics|	1371448|
|Furniture |	1329158|

### 📌 Q3 What is the total amount of Profit by category ?
```
Select Category, Sum(Profit) As [Total Profit]
From [SalesSQL].[dbo].[Sales Datasql]
Group by Category
Order by [Total Profit] Desc;
```

|Category |Total Sales|
|------|-------|
|Office Supplies|	381587 |
|Electronics|	354907|
|Furniture |	349697|

###  📌 Q4 What is the high level of performance ?
```
Select 
Sum(Amount) As [Toatal Revenue],
Sum(Profit) As [Total Profit],
Sum(Quantity) As [Total item Sold]
From [SalesSQL].[dbo].[Sales Datasql];
```
|Total Revenue| 4147180|
|------|-------|
|Total Profit|	1086191 |
|Total Item Sold|	8424 |


### 📌 Q5 Top Performing Sub-Categories
```Select 
Category,
Sub_Category,
Sum(Amount) As [Total Sales],
Sum(Profit) As [Total Profit]
From [SalesSQL].[dbo].[Sales Datasql]
Group by Category,Sub_Category
Order by [Total Profit] Desc;
```

|Category | Sub_Category | Total Sales | Total Profit|
|------|-------|-------|------|
|Office Supplies | Markers |	480073 |	133388|
|Furniture|	Sofas|	416490|	110079|
|Electronics|	Electronic | Games |	362728 |	99533|
|Office Supplies|	Paper|	344150|	97908|
|Office Supplies|	Pens|	405179|	95701|
|Furniture |	Tables |	361350 | 91771|
|Electronics |	Printers |	343142 |	91668|
|Electronics |	Laptops |	302971 |	84284|
|Furniture |	Bookcases |	298769 |	81965|
|Electronics |	Phones |	362607 |	79422|
|Furniture |	Chairs |	252549 |	65882|
|Office Supplies |	Binders |	217172 |	54590|

### 📌 Q6 Calculate the Monthly Sales & Profit Trend ?

```
Select 
FORMAT(Order_Date,'yyyy-MM') As [Year_Month],
Sum(Amount) As [Monthly_Sales],
Sum(Profit) As [Nonthly_Profit]
From [SalesSQL].[dbo].[Sales Datasql]
Group by FORMAT(Order_Date,'yyyy-MM')
Order by Year_Month ASC;
```

|Year_Month |	Monthly_Sales |	Monthly_Profit |
|------|-------|-------|
|2020-03 |	20141 |	5288|
|2020-04 |	92371 |	23900|
|2020-05|	72184	|14125|
|2020-06|	46183|	9331|
|2020-07|	34809|	11598|
|2020-08|	76933|	25207|
|2020-09|	73073|	25129|
|2020-10|	66286|13872|
|2020-11|	74992|	20568|
|2020-12| 75148|	20809|
|2021-01|15430|	3660|
|2021-02|	47781|	8681|
|2021-03|	73944	|27088|
|2021-04|	55250|	11468|
|2021-05|	81638|	19613|
|2021-06|	72993|	19538|
|2021-07|	56449|	11097|
|2021-08|	61431|	12200|
|2021-09|	29000|	4900|
|2021-10|	130579|	27793|
|2021-11|	82329|	19254|
|2021-12|	82701|	20050|
|2022-01|	111368	|29641|
|2022-02|	54494|	15182|
|2022-03|	60439|	16636|
|2022-04	|71942|	17560|
|2022-05|	104769|	20838|
|2022-06|	80088|	25569|
|2022-07|	54489|	15282|
|2022-08|	132849|	37579|
|2022-09|	38768|	12756|
|2022-10|	108296|	28823|
|2022-11|	29803|	6805|
|2022-12|	117642|	30597|
|2023-01|	46129|	11528|
|2023-02|	21262|	3850|
|2023-03|	76124|	22698|
|2023-04|	59966|	15214|
|2023-05|	70418	|15166|
|2023-06|	67074|	19399|
|2023-07|	110687|	30816|
|2023-08|	63401|	16540|
|2023-09|	51924|	11775|
|2023-10|	78406|	19858|
|2023-11|	73695|	22555|
|2023-12|	83511|	21148|
|2024-01|	24171|	6834|
|2024-02|	84946|	18757|
|2024-03|	76900|	24256|
|2024-04|	83441|	20910|
|2024-05|	82912|	20085|
|2024-06|	70314|	18390|
|2024-07|	85337|	27447|
|2024-08|	47204|	12100|
|2024-09|	54149|	15557|
|2024-10|	57497|	14057|
|2024-11|	47905|	13695|
|2024-12|	52969|	13064|
|2025-01|	85117|	27011|
|2025-02	|73887	|23613|
|2025-03|	31242|	7431|

### 📌 Q7 Rank the Top 10 Customers by Total Amount Spent
```
Select Top 10 CustomerName,
COUNT(DISTINCT Order_ID) As [Total ORDER],
Sum(Amount) As [Total_Spent]
From [SalesSQL].[dbo].[Sales Datasql]
Group by CustomerName
Order by Total_Spent Desc;
```

| CustomerName |	Total Order |	Total_Spent |
|------------|----------------|-----------|
|Brent Hernandez|	1	| 9992|
|Susan Burke|	1|	9992|
|Cassandra Farley|	1	|9989|
|Tammy Anthony	|1	|9989|
|Frank Garcia|	1|	9965|
|Jennifer Marshall|	1|	9965|
|Tanya Thomas MD|	1|	9952|
|Christopher Rogers|	1 |	9921|
|Andrew Krueger|	1	|9914 |
|Jeffrey Weber |	1 |	9914|

### 📌 Q8 Calculate the Total Amount & Transaction Count of each PaymentMode
```
Select 
PaymentMode, 
COUNT(Order_ID) As [Transaction_count],
Sum(Amount) As [Total_Amount]
From [SalesSQL].[dbo].[Sales Datasql]
Group by PaymentMode
Order by Transaction_count DESC;
```
|PaymentMode |	Transaction_count |	Total_Amount
|------------|----------------|-----------|
|Debit Card	 | 179 |	989289 |
|UPI |	165  |	817630| 
| Credit Card |	165 |	788241|
|COD |	149 |	798994|
|EMI |	144 |	753026|

### 📌 Q9 What is the Geographical Breakdown

```
Select State,City,
Sum(Amount) As Regional_Sales
From [SalesSQL].[dbo].[Sales Datasql]
Group by State,City
Order by Regional_Sales Desc
```

|State |	City |	Regional_Sales|
|	-------|------|------------|
|	New York|		Buffalo|		282282|	
|	California|		San Francisco|		277599|	
|	Texas	|	Dallas|		266531|	
|	California|		San Diego	|	265781|	
|	Florida|		Orlando	|	258770|	
|	Illinois|		Springfield	|	246323|	
|	Florida|		Miami|		244885|	
|	New York|		New York City|		231535|	
|	Texas|		Austin|		231295|	
|	Ohio|		Cleveland	|	216258|	
|	Illinois|		Chicago|		209840|	
|	Ohio|		Cincinnati|		208630|	
|	Illinois|		Peoria|		206404|	
|	Texas|		Houston|		200159|	
|	Florida|		Tampa|		193750|	
|	Ohio|		Columbus|		181156|	
|	California|		Los Angeles|		172926|	




