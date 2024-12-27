Walmart Sales Data Analysis

Project Overview

This project analyzes Walmart Sales data to gain insights into:

Top-performing branches and products.

Sales trends across different product categories.

Customer behavior and preferences.

The goal is to identify factors influencing sales performance and provide actionable recommendations for optimizing sales strategies. The dataset is sourced from the Kaggle Walmart Sales Forecasting Competition.

Dataset Description

The dataset contains historical sales data for 45 Walmart stores across various regions, including markdown events during holidays that affect sales trends. The analysis focuses on three branches located in Mandalay, Yangon, and Naypyitaw. The dataset includes 17 columns and 1,000 rows:

Column

Description

Data Type

invoice_id

Invoice ID of the sales transaction

VARCHAR(30)

branch

Branch where the sale occurred

VARCHAR(5)

city

City where the branch is located

VARCHAR(30)

customer_type

Type of customer (e.g., Member/Non-member)

VARCHAR(30)

gender

Gender of the customer

VARCHAR(10)

product_line

Product category

VARCHAR(100)

unit_price

Price per unit

DECIMAL(10, 2)

quantity

Number of units sold

INT

VAT

Tax on the purchase

FLOAT(6, 4)

total

Total cost of the transaction

DECIMAL(10, 2)

date

Date of purchase

DATE

time

Time of purchase

TIMESTAMP

payment_method

Payment method used

VARCHAR(15)

cogs

Cost of goods sold

DECIMAL(10, 2)

gross_margin_percentage

Gross margin percentage

FLOAT(11, 9)

gross_income

Gross income

DECIMAL(10, 2)

rating

Customer rating

FLOAT(2, 1)

Analysis Objectives

1. Product Analysis

Identify top-performing product lines.

Analyze product lines requiring improvement.

2. Sales Analysis

Examine sales trends by product category and branch.

Measure the effectiveness of sales strategies.

3. Customer Analysis

Segment customers and analyze purchasing trends.

Assess the profitability of different customer segments.

Approach

Data Wrangling

Handle NULL or missing values by setting NOT NULL constraints during table creation.

Replace missing data where applicable.

Feature Engineering

Add a column time_of_day (Morning, Afternoon, Evening) based on transaction time.

Add a column day_name to extract the day of the week.

Add a column month_name to extract the transaction month.

Exploratory Data Analysis (EDA)

Analyze sales, revenue, and customer trends.

Answer specific business questions to support decision-making.

Business Questions Addressed

Generic Questions

How many unique cities are in the data?

In which city is each branch located?

Product Analysis

How many unique product lines exist?

Which product line has the highest sales and revenue?

Which product line has the highest VAT?

What is the most common product line by gender?

What is the average rating of each product line?

Sales Analysis

Sales trends during different times of the day and week.

Which customer type generates the most revenue?

Which city has the largest VAT percentage?

Customer Analysis

Which customer type makes the most purchases?

Gender distribution of customers across branches.

Time of the day when customers provide the highest ratings.

Revenue and Profit Calculations

Cost of Goods Sold (COGS): COGS = unit_price * quantity

VAT: VAT = 5% * COGS

Total Revenue: total = VAT + COGS

Gross Income: gross_income = total - COGS

Gross Margin Percentage: gross_margin_percentage = gross_income / total

Example Calculations

For a sample row:

unit_price = 45.79

quantity = 7

COGS: 45.79 * 7 = 320.53

VAT: 0.05 * 320.53 = 16.03

Total Revenue: 320.53 + 16.03 = 336.56

Gross Margin Percentage: 16.03 / 336.56 = 4.76%

Code Implementation

For SQL queries and database setup, refer to the file SQL_queries.sql. Example:

-- Create database
CREATE DATABASE IF NOT EXISTS walmartSales;

-- Create table
CREATE TABLE IF NOT EXISTS sales (
    invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10, 2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6, 4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10, 2) NOT NULL,
    gross_margin_pct FLOAT(11, 9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
);

Conclusion

This project provides valuable insights into Walmart's sales data, helping to identify trends, optimize strategies, and improve overall performance. Future work could focus on predictive modeling to forecast sales and identify potential areas for growth.

