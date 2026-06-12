# 📊 DrinkNova CRM Sales Analytics Dashboard | Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C94C?style=for-the-badge\&logo=powerbi\&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge\&logo=microsoft\&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge\&logo=microsoft-excel\&logoColor=white)

## 📌 Overview

This project showcases an end-to-end CRM Sales Analytics Dashboard built in Power BI for **DrinkNova**, a fictional beverage distribution company operating across six countries:

* Australia
* France
* Germany
* India
* United Kingdom
* United States

The dashboard provides business stakeholders with a centralized view of sales performance, profitability, shipment trends, and sales representative effectiveness.

---

## 🎯 Business Objective

The goal was to create a self-service analytics solution that enables decision-makers to:

* Monitor sales, costs, and profitability
* Track sales representative performance
* Analyze product-level performance
* Identify low-performing shipments (LBS)
* Monitor month-over-month business trends
* Support data-driven decision making

---

## 📊 Key Performance Indicators

| KPI              | Value |
| ---------------- | ----: |
| Total Sales      |  €34M |
| Total Cost       |  €14M |
| Total Profit     |  €21M |
| Profit Margin    | 60.3% |
| Total Shipments  |    6K |
| Total Boxes Sold |    2M |

---

## 🚀 Dashboard Features

### Interactive Filters

* Product Category Slicer
* Geography Slicer
* Date Range Slicer

### Bookmark Navigation

A bookmark-based toggle allows users to switch between:

* Sales Representative Analysis
* Product Performance Analysis

without navigating to another report page.

### Visualizations

* Monthly Sales Trend Analysis
* Shipment Distribution Histogram
* Sales Representative Performance Table
* Product Profitability Table
* Profit Margin Gauge
* Low Box Sales (LBS) Gauge

---

## 🧮 Sample DAX Measures

### Month-over-Month Boxes Growth %

```dax
MoM Boxes Change % =
VAR CurrentMonth =
    SUM(shipments[Boxes])

VAR PreviousMonth =
    CALCULATE(
        SUM(shipments[Boxes]),
        DATEADD(calendar[Date], -1, MONTH)
    )

RETURN
DIVIDE(CurrentMonth - PreviousMonth, PreviousMonth) * 100
```

### Month-over-Month Cost Growth %

```dax
MoM Cost Change % =
VAR CurrentCost =
    SUM(shipments[cost])

VAR PreviousCost =
    CALCULATE(
        SUM(shipments[cost]),
        DATEADD(calendar[Date], -1, MONTH)
    )

RETURN
DIVIDE(CurrentCost - PreviousCost, PreviousCost) * 100
```

### Low Box Sales Percentage

```dax
LBS Percentage =
DIVIDE(
    [LBS Count],
    COUNTROWS(shipments)
) * 100
```

### Profit Margin %

```dax
Profit % =
DIVIDE(
    SUM(shipments[Boxes]) * AVERAGE(products[Cost per box]) -
    SUM(shipments[cost]),
    SUM(shipments[Boxes]) * AVERAGE(products[Cost per box])
) * 100
```

---

## 🗂️ Data Model

The solution follows a **Star Schema** design to improve report performance and simplify analytical calculations.

### Fact Table

**shipments**

* Shipment Date
* Product
* Geography
* Cost
* Boxes Sold

### Dimension Tables

**products**

* Product Name
* Category
* Cost Per Box

**people**

* Sales Representative
* Team

**locations**

* Country
* Region

**calendar**

* Date
* Month
* Quarter
* Year

---

## 🛠️ Tools & Technologies

| Technology             | Purpose                  |
| ---------------------- | ------------------------ |
| Power BI Desktop       | Dashboard Development    |
| DAX                    | Business Calculations    |
| Power Query            | Data Transformation      |
| Excel                  | Data Preparation         |
| Star Schema Modeling   | Data Modeling            |
| Bookmarks              | Dynamic Navigation       |
| Conditional Formatting | Performance Highlighting |

---

## 📸 Dashboard Screenshots

### Sales Representative View
<img width="656" height="373" alt="image" src="https://github.com/user-attachments/assets/aeeefcd3-bf22-465c-b187-2e6881b35564" />


### Product Performance View
<img width="655" height="374" alt="image" src="https://github.com/user-attachments/assets/544170ee-1356-4f84-9718-0fd0dec519a0" />


### Data Model

<img width="613" height="236" alt="image" src="https://github.com/user-attachments/assets/d7a54815-68da-4d2c-853f-8cda4be71e7b" />

---

## 💡 Business Insights

### Key Findings

* Overall profit margin reached **60.3%**, indicating strong operational efficiency.
* Low Box Sales (LBS) accounted for **10.2% of shipments**, highlighting opportunities for shipment optimization.
* **November 2023** recorded the highest sales volume of the year.
* **Husein Augar** emerged as the top-performing sales representative with €1.47M in sales.
* **Apple Cider** delivered the highest product profitability at 74%.
* **Mango Juice** and **Orange Mojito** showed comparatively weaker margins and may require pricing or marketing review.

---

## 📁 Repository Structure

```text
DrinkNova-CRM-Sales-Analytics/
│
├── Dashboard.pbix
├── Dataset/
│   └── sales_data.xlsx
│
├── Images/
│   ├── dashboard_salesperson.png
│   ├── dashboard_product.png
│   └── data_model.png
│
└── README.md
```

---

## 🎓 Skills Demonstrated

* Power BI Development
* Data Modeling
* DAX Calculations
* KPI Design
* Dashboard Storytelling
* Business Analytics
* CRM Reporting
* Data Visualization

---

## 👤 Author

### Shashank Raman

Senior Data Analyst

📍 Erlangen, Germany

🔗 LinkedIn: https://linkedin.com/in/shashankraman-da

💻 GitHub: https://github.com/shashankRaman12
