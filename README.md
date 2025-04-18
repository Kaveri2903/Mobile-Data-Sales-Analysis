# Mobile-Data-Sales-Analysis
![mobile sales main dashboard](https://github.com/user-attachments/assets/818cbfe6-8dab-40a1-8c2d-f3bdc9146532)


This repository contains the process and steps to analyze mobile sales data using ETL, data modeling, and DAX measures.

## Table of Contents:
- [Problem Statement](#problem-statement)
- [Datasource](#datasource)
- [Data Transformation (ETL)](#data-transformation-etl)
- [Data Modeling](#data-modeling)
- [DAX](#data-analysis-dax)
- [Dashboard](#Dashboard)


## Problem Statement:

The purpose of this task is to:
- Transform mobile sales data into a usable format.
- Model the data for analysis.
- Create DAX measures to perform key calculations.
- Generate insights from the data to drive business decisions.
- Offer recommendations based on the analysis.

## Datasource :

The dataset used in this task is mobile sales data that contains information on:
- Units sold
- Price per unit
- Product details
- Date and time of sale

The dataset is provided for the purpose of performing ETL processes, data analysis, and generating insights.

## Data Transformation (ETL):

### Merging Date, Month, and Year Columns to Create a Merged Date Column 
The following code merges the Day, Month, and Year columns into a single "Date" column in Power Query:

```m
= Table.AddColumn(#"Removed Columns", "Date", each Text.Combine({Text.From([Day], "en-US"), Text.From([Month], "en-US"), Text.From([Year], "en-US")}, "-"), type date)

```

### Correcting Day Name Column
These transformations replace the abbreviated day names with their full names:

```m
= Table.ReplaceValue(#"Filtered Rows","Mon","Monday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value","Tue","Tuesday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value1","Wed","Wednesday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value2","Thu","Thursday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value3","Fri","Friday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value4","Sat","Saturday",Replacer.ReplaceValue,{"Day Name"})
= Table.ReplaceValue(#"Replaced Value5","Sun","Sunday",Replacer.ReplaceValue,{"Day Name"})

```
### Creating A Custom Calendar

```m
= List.Dates(#date(2021,1,1),1461,#duration(1,0,0,0))
```


## Data Modeling:

And then dataset was cleaned and transformed, it was ready to the data modeled.

The sales insights data tables as show below:
![Screenshot 2025-04-17 105847](https://github.com/user-attachments/assets/3f1c160d-c942-4475-9c21-d7df589a6896)

## DAX :
```m

### Total Sales

Total_sales = SUMX(Mobile_Sales_Data,Mobile_Sales_Data[Units Sold]*Mobile_Sales_Data[Price Per Unit])

### Transactions

Transactions = COUNTROWS(Mobile_Sales_Data)

### Average Price

Average_Price = AVERAGE(Mobile_Sales_Data[Price Per Unit])

```
## Dashboard :
![mobile sales main dashboard](https://github.com/user-attachments/assets/5a9569c0-0844-4b8e-9344-5eb5fdd87e4f)

![mobile Sales photo](https://github.com/user-attachments/assets/5d5fe158-501f-4cbf-9784-91e43098f722)

![mobile sales data photo 2](https://github.com/user-attachments/assets/0b34a978-0358-4a19-ba0a-6a36d809cf8f)

## References :
https://www.sqlbi.com/learn/introducing-dax-video-course/0/

---
