---

---
# Mexico Toy Sales

Data project from Mexico toy sales dataset from a fictional company from mavenanalytics.io.

Dataset: https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=mexico%20toy

### Data Stack Used:
> MySQL, DBngin, dBeaver, PowerBI


## Problem Statement
Maven Toys, a fictional toy company with 50 stores in Mexico and 35 different products wants to leverage their sales and inventory data to drive data-driven decision making. 

## Objectives
### Business Objectives
- Create a dashboard with the Key Performing Indicators (KPIs) of the company such as revenue and margin, performance comparisson between products and stores.
- Inventory dashboard report with reorder points by store.
- Sales forecast.

### Personal Objectives
- Practice SQL: Data cleaning, querying, Exploratory Data Analysis (EDA).
- Practice dashboard creation, creating clean, understandable and well designed visualizations.
- Learn and apply Time Series Analysis.

## Insight Found


## Steps Followed

### Download a clean data
1. Download data.
2. Create MySQL server using DBngin.
3. Connect to server using dBeaver.
4. Load the products, stores, sales and inventory tables to the database.
5. Explore the raw tables for data cleaning needs: missing values, wrong data types and formats, total records, duplicate values.
6. Create clean tables:
    1. No missing values were found.
    2. Dates and currency values were strings originally, transformed to date and numeric values accordingly

```sql
create table maven_toys_sales.fact_sales as (
    select 
		Sale_ID as sale_id,
		DATE(`Date`) as sale_date,
		Store_ID as store_id,
		Product_ID as product_id,
		Units as units
    from maven_toys_sales.sales 
);

create table maven_toys_sales.dim_stores as (
	select
		store_id,
		store_name,
		store_city,
		store_location,
		DATE(store_open_date) as store_open_date
	from maven_toys_sales.stores
);

create table maven_toys_sales.dim_product as (
	select 
		product_id,
		product_name,
		product_category,
		convert(REPLACE(Product_Cost, '$', ''), float) as product_cost,
		convert(REPLACE(Product_Price, '$', ''), float) as product_price
	from maven_toys_sales.products 
);
```
### Creating a Dashboard using PowerBI
7. Export the clean tables to csv.
8. Create the .pbix file, import the data and create the data model with all four tables.
9. Create the *profit* and *revenue* measures using DAX.

```dax
```

10. Create the executive summary view
[]()