# Buy Now Superstore Sales Return Rate Analysis Power BI

## 🔍 Project Overview
This project presents an end-to-end Sales Performance and Return Impact Analysis using Power BI. The goal is to transform raw transactional data into actionable insights that drive decision-making.
The dashboards provide a clear view of:
- Overall sales and profitability
- Customer purchasing behavior
- Product and regional performance
- Return patterns and their business impact
  
This project demonstrates strong skills in data cleaning, data modeling, DAX, visualization design, and business insight generation.

## 🎯 Business Objectives
- Measure overall sales and profit performance
- Identify high-performing and underperforming regions, products, and segments
- Analyze customer behavior and return patterns
- Quantify the impact of product returns on revenue and operations
- Support data-driven decision-making with interactive dashboards

## 📂 Datasets Used
- <a href="">Dataset</a>

### 1️. Orders Table
Contains transactional data, including:
- Order ID, Order Date, Ship Date
- Customer details
- Product details
- Sales, Profit, Quantity, Discount
### 2️. Returns Table
- Flags returned orders using Order ID
### 3️. People Table
- Maps Managers to Regions for accountability analysis

## 🧹 Data Preparation
### Step 1: Initial Data Preparation in Excel
Before loading the data into Power BI, preliminary data preparation was performed in Microsoft Excel to simplify integration and improve data quality:
- Used VLOOKUP and XLOOKUP to merge related tables where applicable
  - Matched Orders with Returns using Order ID to identify returned orders
  - Mapped Regions to Managers using the People table
- Performed basic checks for missing or inconsistent values
This step ensured the datasets were logically aligned before advanced transformations.
### Step 2: Power Query Cleaning & Transformation
- Loaded the prepared datasets into Power Query
- Validated merged fields and standardized column names
- Filled missing values in the Returned field with "No"
- Removed duplicates and corrected data types (Date, Numeric, Text)
- Created a calculated column for Order Processing Time (Ship Date – Order Date)

## 🧱 Data Modeling
### Star Schema Design
#### Fact Table
- FactOrders (Sales, Profit, Quantity, Discount, Returned)
#### Dimension Tables
- Customers
- Products
- Regions
- Returns
### Date Table
#### Date Table (DAX)
- A comprehensive Date Table was created using DAX and linked to the Orders table via Order Date.
