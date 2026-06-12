📊 DrinkNova — CRM Sales Analytics Dashboard (Power BI)
   
📌 Project Overview
An end-to-end CRM Sales Analytics Dashboard built in Power BI for DrinkNova — a fictional beverage distribution company operating across 6 countries (Australia, France, Germany, India, UK, USA).

The dashboard enables sales leadership and management to monitor revenue performance, sales rep efficiency, product profitability, and shipment trends — replicating the kind of analytics typically built on top of CRM platforms like Microsoft Dynamics 365, HubSpot, or Salesforce.
________________________________________
🎯 Business Problem
DrinkNova's sales team needed a single source of truth to:
•	Track sales, cost, and profit across products and geographies
•	Monitor individual sales rep performance against targets
•	Identify low-performing products (LBS — Low Box Sales)
•	Analyse month-over-month trends to drive data-driven decisions
•	Enable self-service analytics for non-technical stakeholders
________________________________________
📊 Dashboard Features
KPI Summary Bar
Metric	Value
Total Sales	€ 34M
Total Cost	€ 14M
Total Shipments	6K
Total Boxes	2M
Total Profit	€ 21M
Profit %	60.3%

    Interactive Features
•	📌 Bookmark Toggle — Switch between Sales Person view and Product view on the same dashboard page — no page navigation needed
•	🔍 Category Slicer — Filter by Coffee, Fizzy, Healthy, Juice, Milkshake, Mocktail, Tea
•	🌍 Geography Slicer — Filter by Australia, France, Germany, India, UK, USA
•	📅 Time Slicer — Drill into any date range (Mar 2023 – Jan 2024)
Visualisations
•	📈 Sales Trend Line Chart — Monthly revenue trend with MoM comparison
•	📊 Shipments Histogram — Distribution of shipment volumes (LBS analysis)
•	🏆 Sales Rep Performance Table — Sales, Profit, Profit % with conditional formatting
•	🛒 Product Performance Table — Product-level revenue and profitability
•	🎯 Profit % Gauge — Company-wide profit margin at a glance
•	⚠️ LBS % Gauge — Low Box Sales percentage to monitor underperformance
________________________________________
🧮 DAX Measures Written
-- Month-over-Month Boxes Change %
MoM Boxes change% = 
VAR CurrentMonth = SUM(shipments[Boxes])
VAR PrevMonth = CALCULATE(SUM(shipments[Boxes]), DATEADD(calendar[Date], -1, MONTH))
RETURN DIVIDE(CurrentMonth - PrevMonth, PrevMonth) * 100

-- Month-over-Month Cost Change %
MoM cost change % = 
VAR CurrentCost = SUM(shipments[cost])
VAR PrevCost = CALCULATE(SUM(shipments[cost]), DATEADD(calendar[Date], -1, MONTH))
RETURN DIVIDE(CurrentCost - PrevCost, PrevCost) * 100

-- LBS Percentage (Low Box Sales)
LBS Percentage = 
DIVIDE([LBS Count], COUNTROWS(shipments)) * 100

-- Profit %
Profit % = 
DIVIDE(SUM(shipments[Boxes]) * AVERAGE(products[Cost per box]) - SUM(shipments[cost]),
       SUM(shipments[Boxes]) * AVERAGE(products[Cost per box])) * 100
________________________________________
🗂️ Data Model — Star Schema
                    ┌─────────────┐
                    │  shipments  │  ← Fact Table
                    │  (central)  │
                    └──────┬──────┘
           ┌───────────────┼───────────────┐
           │               │               │
    ┌──────▼──────┐ ┌──────▼──────┐ ┌─────▼───────┐
    │  products   │ │   people    │ │  locations  │
    │  Category   │ │ Sales person│ │    Geo      │
    │  Cost/box   │ │    Team     │ │   Region    │
    └─────────────┘ └─────────────┘ └─────────────┘
                           │
                    ┌──────▼──────┐
                    │  calendar   │
                    │    Date     │
                    └─────────────┘
Tables:
•	shipments — Fact table: Boxes, Cost, Date, Geography, Product
•	products — Dimension: Category, Cost per box, Product name
•	people — Dimension: Sales person, Team, Picture
•	locations — Dimension: Geo, Region
•	calendar — Date dimension for time intelligence
________________________________________
🛠️ Tools & Techniques Used
Tool / Feature	Usage
Power BI Desktop	Dashboard development
DAX	MoM measures, LBS %, Profit % calculations
Star Schema	Data modelling — fact + dimension tables
Bookmarks	Toggle between Sales Person and Product views
Conditional Formatting	Profit % visual indicators (green/red)
Gauge Charts	Profit % and LBS % at-a-glance KPIs
Slicers	Category and Geography filtering
Advanced Excel	Data preparation and cleaning
________________________________________
📸 Dashboard Screenshots
Sales Person View
 
Product View
 
Data Model
 
________________________________________
💡 Key Business Insights
1.	Overall profit margin is strong at 60.3% — company is operating efficiently
2.	LBS rate of 10.2% — 1 in 10 shipments is below minimum box threshold, worth investigating
3.	November 2023 peak — highest sales month, likely seasonal demand spike
4.	Top sales rep: Husein Augar — €1,473K sales with 62.9% profit margin
5.	Apple Cider leads product profitability at 74.0% profit margin
6.	Mango Juice and Orange Mojito are underperformers — below 30% profit margin, candidates for review
________________________________________
🔗 Related Projects
•	🧪 A/B Testing — Hotel Booking Conversion
•	📊 Sales Insights Dashboard — Tableau
________________________________________
👤 Author
Shashank Raman — Senior Data Analyst
📍 Erlangen, Germany | 🔗 LinkedIn | 💻 GitHub

