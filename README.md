PlantCo Performance Dashboard 🪴

A powerful, interactive Power BI dashboard that tracks the financial and operational health of a global plant retailer. It transforms raw sales data into clean, dynamic insights to help management see exactly where the business is making or losing money.  
+4

🛠️ Data & Cleaning
The project connects three core tables into a clean data model:  


Fact_sales: Contains quantities, price, dates, and Cost of Goods Sold (COGS).  


Dim_Account & Dim_Product: Holds details about customers, locations, and plant types.  

The Prep Work:

Power Query: Cleaned data by removing duplicates and fixing empty null values.  
+1


Custom Calendar (Dim_Date): Built a full calendar table (Jan 2022 – Dec 2024) to handle advanced date calculations.  

🧠 Smart DAX Formulas
1. The Timeline Matchmaker (Inpast)
Code snippet
Inpast = 
VAR Latestsalesdate = MAX(Fact_sales[Date])
VAR LatestSalesdatePY = EDATE(Latestsalesdate, -12)
RETURN
    Dim_Date[Date] <= LatestSalesdatePY

Why we use it: It creates an identical "window" of time for both years. If this year only goes up to April, it cuts last year’s data at exactly the same day in April. This keeps the year-over-year math honest and accurate.  
+2

2. Year-to-Date (YTD) & Prior Year (PYTD)

YTD: Calculated on the sales date so chart lines stop exactly where your actual sales end.  


PYTD: Uses SAMEPERIODLASTYEAR combined with our Inpast filter to stop the previous year's data at the exact matching day.  

3. The 3-in-1 Dynamic Switch
Uses a single slicer table to instantly toggle the entire dashboard between Sales, Quantity, and Gross Profit. This keeps the report incredibly clean instead of building three separate pages.  

📊 Visuals & Business Value

KPI Cards: Show current YTD vs. Last Year at a glance to check if goals are met.  


Waterfall Chart: Explains how profits changed by pinpointing exactly which countries caused the biggest drops or gains.  
+1


Scatter Plot: Maps customer volume against profit margins to find your most valuable clients versus those buying cheap items at heavy discounts.  
+1


TreeMap: Automatically displays the "Bottom 10" underperforming regions so management knows where to focus first.  

📈 Main Business Takeaway

Profit Over Volume: By calculating Gross Profit (Selling Price - Cost Price) instead of just tracking raw sales volume, the business ensures it stays truly profitable even if supply costs rise.
