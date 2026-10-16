# Business-Insights-360


## Company Overview

**AtliQ Hardware** is a fictional consumer-electronics company that makes PC accessories, printers, and related hardware. Starting from a smaller base, it has grown into a global business with operations in four major regions: **APAC, North America, Latin America, and the European Union**.

## How AtliQ Sells

AtliQ reaches the market through two kinds of platforms:

| Platform | Examples |
|---|---|
| Physical retail | Croma, Best Buy |
| Online marketplaces | Amazon, Flipkart |

## Product Divisions

| Division | Full Name |
|---|---|
| **N & S** | Networking & Storage |
| **P & A** | Peripherals & Accessories |
| **PC** | Personal Computers |

## Sales Channels

- **Retailers:** independent sellers, online or in-store, who buy AtliQ products and resell them
- **Direct stores:** AtliQ-owned outlets that sell to consumers directly
- **Distributors:** large partners used in markets with restrictions, such as China and South Korea, to keep products in stock

> **Customers vs. consumers:** AtliQ's *customers* are the retailers and distributors that buy from it. The *consumers* are the end users who ultimately purchase the products.

## Problem Statement

AtliQ Hardware has grown quickly and is now one of the fastest-growing names in consumer electronics. That growth, however, has not been smooth. When the company tried to enter **Latin America**, it took heavy losses because its decisions rested on surveys and gut feeling rather than reliable data.

Until now, the company ran its analysis in **Excel**. As the business expanded, the volume of data and the depth of analysis it needed outgrew what spreadsheets could handle.

To avoid repeating that mistake, AtliQ needs a data-driven reporting solution that can:

- Give management one reliable view of **finance, sales, marketing, and forecasting** performance
- Compare results against **last year** and against **benchmark** figures
- Show how individual **markets, regions, product segments, and sales channels** are performing
- Support better decisions on pricing, discounts, inventory, and market expansion

This project builds that solution as an interactive **Power BI** dashboard on a cleaned and well-modelled dataset.

## Methodology

### 1. Data Cleaning & Transformation

**Cleaning and standardisation**
- Trimmed leading and trailing spaces from text fields so values match correctly during analysis
- Standardised naming conventions across fields for consistency and readability

**Structuring and optimisation**
- Built a dedicated `dim_date` table to support time-based analysis and consistent date filtering
- Appended `fact_sales_monthly` and `fact_forecast_monthly` into one table, `fact_actual_estimates`, combining actual sales and forecast data
- Added the fields needed for analysis to `fact_actual_estimates` using information from related tables
- Disabled the load of intermediate tables that were no longer needed in the final model, which removed duplicated data and reduced the Power BI model size

### 2. Power Query Transformations
- Cleaned, transformed, and structured the raw data in Power Query before loading it into the model
- Created calculated columns to derive extra information needed for reporting
- Kept data types, field structures, and transformed values consistent across tables
- Prepared the data so that modelling and DAX calculations later on were simpler

### 3. Data Modelling
- Organised the data into **fact** and **dimension** tables
- Created relationships on appropriate key columns so filtering and aggregation work accurately
- Brought together sales, forecast, product, customer, market, and date data for the different analytical views
- Structured the model to support cross-functional analysis across **Finance, Sales, Marketing, and Supply Chain**

### 4. DAX Implementation
- Used DAX to build the business logic and calculations behind the dashboard
- Wrote expressions for time-based analysis, financial performance tracking, and actual vs. forecast comparisons
- Applied filter context and relationships so calculations respond correctly to slicers, filters, and selected dimensions
- Used conditional logic to show the relevant metrics for the selected analytical view

### 5. DAX Measures
- Built dynamic measures for key KPIs, including **Net Sales**, **Gross Margin**, and **Gross Margin %**, along with other performance indicators
- Added time-intelligence calculations to compare performance across periods
- Designed measures to compare actuals against forecasts and relevant targets
- Ensured measures update with slicers and filters, so users can analyse performance by period, market, product, customer, and other dimensions

### 6. Dashboard Development & Visualisation
- Built an interactive Power BI dashboard with KPIs, charts, tables, and other visuals
- Split the report into views for **Finance, Sales, Marketing, and Supply Chain**, matching what each function needs to see
- Chose visuals that highlight trends, comparisons, contribution analysis, and areas needing management attention
- Added slicers, filters, and interactive elements so users can explore data at different levels of detail
- Presented complex business data in a clear, structured, and user-friendly layout to support monitoring and data-driven decisions

## Challenges Faced

### 1. Missing Date Dimension
The dataset had no date dimension table. A custom one was built in Power Query, with the date-related columns needed for time-based analysis.

### 2. Heavy Data Cleaning
The raw data needed a lot of cleaning before it was usable. Power Query was used to clean it, standardise values, and apply the required transformations, including calculated columns.

### 3. Complex DAX Measures
- Used `SWITCH(TRUE())` to return different financial metrics depending on the condition
- Used `MAX()` to pull scalar values where a single value was needed
- Combined `CALCULATE()` with `ALL()` and `ALLEXCEPT()` to change the filter context and get the intended results

### 4. Many-to-Many Relationships
Some tables ended up in a many-to-many relationship. This was fixed by creating a supporting table with the `ALLNOBLANKROW()` function, which gave the model the cardinality it needed.

### 5. File Size Optimisation
The data model was analysed and optimised with **DAX Studio**, cutting the file size by about **25%**.

### 6. Dynamic LY vs. Benchmark Comparison
Built a toggle that lets users switch between **Last Year (LY)** and **Benchmark (BM)** comparisons inside the report. It runs on supporting DAX measures and a dedicated selection table.

## Business Insights

### Growth and Profitability
- Net Sales grew by roughly 280% in FY 2019, 140% in FY 2020, 200% in FY 2021, and 350% in FY 2022. Gross Margin also rose over the years, although GM % slipped slightly in some years.
- Net Profit % has stayed negative since 2020 because of high operating and marketing expenses, which is typical for a company in its growth phase. Management should review these costs to improve net profitability.
- Net Sales are in line with benchmark figures, but GM % is not. Discounts, product costs, and pricing need a closer look to understand the gap.

### Markets and Regions
- APAC was the largest market from FY 2019 to FY 2022, led by India, while Latin America stayed the smallest.
- India is the best market on Net Sales and GM, and the fastest growing, reaching about 13% market share in FY 2022. The USA also sits in the high Net Sales, high GM % quadrant. South Korea and Canada need attention to find room for better sales and profitability.
- North America has the highest GM % and APAC the highest Net Sales, but both regions show low Net Profit %. Canada and India have the lowest Net Profit % within their regions, so improving them would lift regional profitability.
- Among subzones, North America earned the highest revenue in FY 2022, yet AtliQ's market penetration there was only about 5%.

### Customers and Channels
- Amazon was the top global customer in every year. Nova (Austria) has been the smallest since FY 2020.
- Retailers are the biggest channel, bringing in nearly 70% of Net Sales overall and about 72% in FY 2022. Strong retailer relationships matter for sustaining sales, while the profitability of this channel and the scope to grow other channels both need review.

### Products and Segments
- Notebook is the largest contributor to Net Sales and had the highest revenue growth in every fiscal year, yet it has the lowest Net Profit %, turning most negative in FY 2022, likely because of higher marketing spend. Discounts, product costs, and operating expenses should be checked.
- Desktop grew the least in FY 2019 and FY 2020, and Networking became the weakest segment in FY 2022. Suitable strategies could move Peripherals and Desktop into the high Net Sales, high Net Profit % quadrant.
- USB flash drives underperformed in FY 2021 and FY 2022, pointing to product or market challenges.
- AQ 5000 Series Electron 9 5900X, AQ MB Elite, and AQ Wi Power Dx1 had zero sales in FY 2022, likely because of demand shifts or outdated models.

### Discounts and Marketing
- Heavy discounts are being used to generate Net Sales. A flat post-discount rate applied to every product and customer within a market is eroding GM %. A performance-based discount strategy for each product and customer within each market is recommended, along with a check on whether discounts bring enough extra sales to justify them.
- The UK had the highest marketing costs, making it a key area for strategy review. Germany follows, with low revenue but high marketing spend.

### Forecasting and Supply Chain
- Forecast Accuracy (FCA %) fell from about 86% in FY 2019 to about 73% in FY 2020 because of COVID-19 disruptions, then recovered to about 80% in FY 2021 and 81% in FY 2022. March 2020 was the weakest month, which shows why forecasts must account for unexpected market conditions.
- In 2022, Peripherals had the lowest forecast accuracy at 68.17%. Accessories had a higher accuracy of 87.42% but still recorded a high Net Error. The reasons behind these deviations need investigation to improve inventory and sales planning.
- Excess inventory was a major issue in FY 2019 and FY 2020, while stock shortages became the challenge in FY 2021 and FY 2022. A surge in work-from-home demand in FY 2020 caused stockouts of processors, keyboards, and WiFi extenders.

### Competitive Position and Market Share
- AtliQ's market share rose from 0.20% in 2019 to 5.87% in 2022, with PC share moving from about 1% in FY 2021 to about 6% in FY 2022. Dell is the most consistent performer and AtliQ's biggest competitor, followed by Lenovo. The factors behind this growth should be analysed so it can be sustained.

### Seasonality
- Sales peaked from September to December in every year, likely because of festive and year-end promotions.

**Live Dashboard Link :**https://tinyurl.com/5n98nr8u
