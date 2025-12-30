# Buy Now Superstore Sales Return Rate Analysis Power BI
<img width="899" height="539" alt="Buy Now Superstore Dashboard 1" src="https://github.com/user-attachments/assets/f3dad800-f726-4dfe-a364-f0aadf9ef7fe" />
<img width="835" height="492" alt="Buy now Superstore Dashboard 2" src="https://github.com/user-attachments/assets/c1e724b4-1726-4e91-b253-cd8a5ea0eaab" />

## Table of Contents
- [Project Overview](#-project-overview)
- [Business Objectives](#-business-objectives)
- [Datasets Used](#-datasets-used)
- [Data Preparation](#-data-preparation)
- [Data Modeling](#-data-modeling)
- [DAX Measures](#-dax-measures)
- [Dashboards & Visualizations](#-dashboards--visualizations)
- [Key Insights](#-key-insights)
- [Recommendations](#-recommendations)
- [Data & Decision-Making](#-data--decision-making)
- [Tools Used](#-tools-used)
- [Author](#-author)

## 🔍 Project Overview
This project presents an end-to-end analysis of Sales Performance and Return Impact using Power BI. The goal is to transform raw transactional data into actionable insights that drive decision-making.
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
- <a href="https://github.com/NuelzHeart/Buy-Now-Superstore-Sales-Return-Rate-Analysis-Power-BI-/blob/main/Buy%20Now%20Superstore%20Dataset.xlsx">Dataset</a>

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

## 📐 DAX Measures
- Total Sales = CALCULATE(SUM(factOrder[Sales]), factOrder[Returned] = "No")
- Total Profit = CALCULATE(SUM(factOrder[Profit]), factOrder[Returned] = "No")
- Avg Discount = AVERAGE(factOrder[Discount])
- Profit Margin = DIVIDE([Total Profit], [Total Sales])
- Total Order = DISTINCTCOUNT(factOrder[Order ID])
- Total Returned Order = CALCULATE(DISTINCTCOUNT(factOrder[Order ID]), factOrder[Returned] = "Yes")
- Return Rate = DIVIDE([Total Returned Order], [Total Order], 0)
- Total Customers = DISTINCTCOUNT(factOrder[Customer ID])

## 📊 Dashboards & Visualizations
### 📊 Sales Overview Dashboard
-  <a href="https://github.com/NuelzHeart/Buy-Now-Superstore-Sales-Return-Rate-Analysis-Power-BI-/blob/main/Buy%20Now%20Superstore%20Dashboard%201.png">View Dashboard</a>
### 🟢 Sales Overview Dashboard
#### Key Performance Indicators
| KPI | Value |
| -------------------- | --------------- |
| Total Sales | 2.12M |
| Total Profit | 263.16K |
| Profit Margin | 12.43% |
| Average Discount | 0.16 |
#### Charts Used
- Bar Chart: Total Sales by Region
- Donut Chart: Total Sales by Segment (Consumer, Corporate, Home Office)
- Bar Chart: Total Sales by Product Name
- Line Chart: Monthly Sales Trend
- Column Chart: Total Sales by Category
- Year Slicer (2014–2017)
### 📊 Return Rate Dashboard
-  <a href="https://github.com/NuelzHeart/Buy-Now-Superstore-Sales-Return-Rate-Analysis-Power-BI-/blob/main/Buy%20now%20Superstore%20Dashboard%202.png">View Dashboard</a>
### 🔴 Return Rate Dashboard
#### Key Performance Indicators
| KPI | Value |
| -------------------- | --------------- |
| Total Orders  | 5k |
| Total Returned Orders | 296 |
| Return Rate | 5.91% |
| Total Customers | 793 |
#### Charts Used
- Bar Chart: Return Rate by Region
- Donut Chart: Return Rate by Segment
- Bar Chart: Return Rate by Product Name
- Map Visual: Return Distribution by State
-  Year Slicer (2014–2017)

## 💡 Key Insights
### 📈 Sales Performance Insights (Sales Overview Dashboard)
- The business generated over 2M in total sales, indicating strong market demand across regions and categories.
- The West region leads in total sales, suggesting higher customer concentration or stronger market penetration compared to other regions.
- Technology is the highest revenue-generating category, outperforming Furniture and Office Supplies.
- Consumer segment contributes the largest share of sales, highlighting the importance of retail-focused strategies.
- Sales show a clear seasonal trend, with peaks toward the end of the year (Q4), indicating increased demand during festive or promotional periods.
- A small average discount (0.16) suggests pricing discipline, but may also limit competitiveness in certain segments.
- High sales volume does not always translate to proportional profit, emphasizing the need to monitor profit margin alongside revenue.

### 🔄 Return Behavior Insights (Return Rate Dashboard)
- The overall return rate of ~6% is moderate but represents a significant operational and revenue impact.
- The West region, while leading in sales, also records the highest return rate, signaling potential fulfillment, logistics, or customer expectation issues.
- Certain products show extremely high (up to 100%) return rates, pointing to serious product quality, description mismatch, or delivery problems.
- The Corporate and Consumer segments account for most returned orders, indicating segment-specific expectations or usage patterns.
- States with dense order volumes also show higher return concentrations, suggesting volume-driven operational strain.
- A gap exists between high-order regions and customer satisfaction, as evidenced by return frequency.

## ✅ Recommendations
### 💼 Sales & Profit Optimization
- Focus marketing and inventory investments on high-performing regions (West and East) while improving operational controls to reduce associated returns.
- Expand and promote Technology category offerings, while reviewing pricing and cost structures to protect profit margins.
- Introduce targeted discount strategies for underperforming categories instead of broad discounting.
- Use seasonal sales trends to optimize inventory planning and staffing ahead of peak periods.

### 🔧 Return Reduction & Operational Improvements
- Conduct a root-cause analysis on products with extremely high return rates and consider redesign, delisting, or supplier renegotiation.
- Improve product descriptions, images, and specifications to reduce expectation mismatch, especially for frequently returned items.
- Strengthen quality checks and packaging standards in high-return regions.
- Implement region-specific return policies or logistics audits, particularly in the West region

## 🔮 Data & Decision-Making
- Leverage Power BI forecasting outputs to anticipate future sales and return trends.
- Track return-related KPIs alongside sales metrics in management reviews.
- Continuously enhance the model by adding Return Cost, Delivery Time impact, and Customer Lifetime Value (CLV) for deeper insights.

## 🛠 Tools Used
- **Microsoft Excel:** Used for initial data preparation, including merging tables with VLOOKUP and XLOOKUP, validating data, and performing basic data quality checks before loading into Power BI.
- **Power Query:** Used for data cleaning and transformation such as handling missing values, standardizing column names, assigning correct data types, and creating calculated columns.
- **Power BI:** Used to build the data model, create interactive dashboards, visualize KPIs, analyze sales and return trends, and support data-driven decision-making.
- **DAX (Data Analysis Expressions):** Used to create calculated measures and KPIs including Total Sales, Total Profit, Profit Margin, Return Rate, and time-based analytics.
- **Microsoft PowerPoint:** Used to design the dashboard wireframe and layout planning before implementation in Power BI, ensuring clear visual structure and effective storytelling.

## 👤 Author

### Emmanuel Akaolisa
Data Analyst | Power BI Developer

- 📧 [Email](mailto:akaolisaemmanuel@gmail.com)
- 🔗 [LinkedIn](https://www.linkedin.com/in/emmanuel-akaolisa)
- 💼 [WhatsApp](https://wa.me/2347039250896)
