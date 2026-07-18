# CFO Executive Summary: Financial Performance & Variance

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Modeling-blue?style=for-the-badge)

## 📌 Project Overview
This project is an enterprise-grade **Financial Performance Dashboard** built in **Power BI**. It is designed for C-level executives (CFOs, Finance Directors) to monitor the financial health of the business at a glance. 

Instead of basic descriptive analytics, this dashboard focuses on **financial variance, margin efficiency, and revenue concentration risk**. It relies on robust data modeling and advanced DAX time-intelligence functions to ensure mathematical accuracy across fiscal periods.

---

## 📊 Key Features & Visuals
The dashboard is split into actionable financial views:

1. **The P&L Summary**: Features a dynamic **Waterfall Chart** demonstrating the month-over-month revenue walk, alongside a detailed Segment & Product Matrix highlighting Year-over-Year (YoY) variances with conditional formatting.
2. **Margin Efficiency Analysis**: A dual-axis combo chart tracking Revenue Volume against Gross Margin %. This immediately answers the critical business question: *"Are we sacrificing margin for volume?"*
3. **Pricing Power Quadrant**: A scatter plot analyzing Gross Profit vs. Total Revenue by product. This allows management to easily identify "Cash Cows" (high revenue/high profit) and "Cost Traps" (high revenue/low profit).
4. **Predictive Forecasting**: Utilizes Power BI's built-in AI analytics to project a 90-day forward-looking revenue forecast based on historical exponential smoothing.

---

## ⚙️ Technical Highlights (DAX & Data Modeling)
This project adheres to Power BI developer best practices, avoiding implicit measures and auto-date/time functions.

*   **Custom Date Dimension**: A dynamically generated Calendar table built via DAX (`CALENDAR()`) to handle all time-intelligence routing and custom sorting.
*   **Time-Intelligence DAX**: Calculating historical comparisons to measure true business growth:
    ```dax
    Revenue Last Year (PY) = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Calendar'[Date]))
    Revenue YoY Variance % = DIVIDE([Total Revenue] - [Revenue Last Year (PY)], [Revenue Last Year (PY)], 0)
    ```
*   **Advanced Logic (Concentration Risk)**: Measuring the percentage of total company revenue that relies strictly on the top 3 products:
    ```dax
    Revenue Concentration Top 3 = 
    VAR Top3Sales = SUMX(TOPN(3, ALL(Financials[Product]), [Total Revenue], DESC), [Total Revenue])
    RETURN DIVIDE(Top3Sales, [Total Revenue], 0)
    ```

---

## 📁 Dataset
*   **Source**: Microsoft Financial Sample Dataset
*   **Details**: Enterprise sales data containing Segments, Countries, Products, Units Sold, Gross Sales, COGS, and Profit data over a multi-year period.

---

## 🚀 How to View
1. Download the `.pbix` file included in this repository.
2. Open it using **Power BI Desktop** (Free to download from the Microsoft Store).
3. The dashboard is fully interactive—try clicking on any Product Category in the Matrix or the Scatter Plot to cross-filter the financial timeline and forecast!

---
*Built by Thathsara Rajapaksha*
