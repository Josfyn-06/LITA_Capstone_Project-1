## LITA_Capstone_Project
My first practical application of data analysis concepts learned during my studies with Incubator Hub covering data cleaning, data querying, visualization and insights extraction using Excel, SQL and Power BI.

## Project Title: Sales Data

### Table of Contents
[Project Overview](#project-overview)

[Dataset](#dataset)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualisation](#data-visualisation)

[Insights](#insights)


### Project Overview
This project aims to analyse the sales data of a retail store to gain insights into customer purchasing behaviour, product performance, regional and monthly sales trends in order to make informed business decisions. 

### Dataset
The dataset contains the following columns:
- *OrderID*: A unique identifier for each order
- *CustomerID*: A unique identifier for each customer
- *Product*: The specific product purchased in each order 
- *Region*: The geographical location of where the order was placed
- *Order Date*: The date the order was placed
- *Quantity*: The number of units purchased for each product in an order
- *Unit Price*: The price per unit of a product
- *Sales*: The sales value for an order, calculated as Quantity * Unit Price

### Data Sources
The primary source of data used here is Sales Data.csv and this is an open source data that can be freely downloaded from an open source online such as Kaggle or FRED, though this dataset was given by the Incubator Hub.

### Tools Used
- Microsoft Excel for data cleaning, analysis and visualisation
- SQL (Structured Query Language) foe data querying
- Power BI for visualisation

### Data Cleaning and Preparation
In this phase of my analysis, i performed the following actions:
- *Data loading*: Loaded the data
- *Blank Value Check*: Verified the dataset for blank values
- *Data Type Conversion*: Converted specified columns to text format for consistency
- *Data Standardization*: Reformatted date columns to YYYY-MM-DD for uniformity
- *Duplicate Removal*: Removed duplicate rows to ensure unique records. 40,079  duplicates were found and removed left with 9,921 unique values out of 50,000 records that was given in the dataset.
  
### Exploratory Data Analysis
In this phase of my analysis, i explored the dataset to answer important questions such as:

- Which product are best sellers?
- What is the regional sales performance?
- What is the monthly sales trend?

### Data Analysis
- Excel Analysis
  - *Average Sales per Products*
    ```Excel
    =AVERAGEIF(C:C,"shirt",H:H)
    =AVERAGEIF(C:C,"Shoes",H:H)
    =AVERAGEIF(C:C,"Gloves",H:H)
    =AVERAGEIF(C:C,"Hat",H:H)
    =AVERAGEIF(C:C,"Jacket",H:H)
    =AVERAGEIF(C:C,"Socks",H:H)
    ```

  - *Total Revenue by Region*
    ```Excel
    =SUMIF(D:D,"South",H:H)
    =SUMIF(D:D,"East",H:H)
    =SUMIF(D:D,"North",H:H)
    =SUMIF(D:D,"West",H:H)
    ```

- SQL Queries
  - *Highest Selling Product*
    ```SQL
    select top 1 Product as Highest_Selling_Product,
    sum(sales) as Total_Sales from Sales_Data
    group by product
    ```

  - *Monthly Sales Total for the Current Year*
    ```SQL
    select case month(orderdate)
    when 1 then 'January'
    when 2 then 'February'
    when 3 then 'March'
    when 4 then 'April'
    when 5 then 'May'
    when 6 then 'June'
    when 7 then 'July'
    when 8 then 'August'
    when 9 then 'September'
    when 10 then 'October'
    when 11 then 'November'
    when 12 then 'December'
    end as Month, sum(sales) as Monthly_Sales from Sales_Data
    where year(OrderDate) = year(getdate())
    group by month (OrderDate)
    order by month (OrderDate)
    ```

    



