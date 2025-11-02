# 🌍 UK Energy Analytics Dashboard — Power BI Project

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-yellow?logo=powerbi)
![SQL](https://img.shields.io/badge/Query-SQL-blue)
![Data Modeling](https://img.shields.io/badge/Concept-Star%20Schema-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📊 Project Overview
This Power BI project analyzes **UK electricity consumption and revenue patterns** using **synthetic but realistic energy data** modeled on regional and customer-type trends.  
The dashboard provides data-driven insights for **decision-making in the UK energy and utilities sector**, highlighting your skills in **data modeling, DAX, Power Query, and storytelling with data**.

---

## ⚙️ Data Model
Built using a **Star Schema** to support efficient queries and clear relationships between dimensions and fact data.

| Table | Description |
|--------|--------------|
| **Fact_Energy_Clean** | Hourly readings of energy consumption (kWh), temperature, and humidity |
| **Stg_Customers** | Customer information (CustomerID, CustomerName, CustomerType, RegionID) |
| **Stg_Region** | Region details (RegionID, RegionName, Zone) |
| **Stg_Tariff** | Tariff rates by CustomerType |
| **Dim_Date** | Calendar table with date intelligence columns (Year, Month, Weekday, etc.) |

**Relationships:**
- `Fact_Energy_Clean[CustomerID]` → `Stg_Customers[CustomerID]`
- `Fact_Energy_Clean[RegionID]` → `Stg_Region[RegionID]`
- `Fact_Energy_Clean[Date]` → `Dim_Date[Date]`
- `Stg_Customers[CustomerType]` → `Stg_Tariff[CustomerType]`

This structure enables accurate filtering, time-based analysis, and dynamic DAX calculations.

---

## 🧮 Key DAX Measures

```DAX
-- Total Energy Consumption
Total_Consumption =
SUM(Fact_Energy_Clean[Consumption_KWh])

-- Total Revenue (£)
Total Revenue (£) =
SUMX( Fact_Energy_Clean,
VAR CustType = RELATED(Stg_Customers[CustomerType])
VAR PricePerKWh =
 LOOKUPVALUE(
 Stg_Tariff[Price_per_kWh],
 Stg_Tariff[CustomerType],
 CustType,
 -- default if no match:
 BLANK()
)
RETURN Fact_Energy_Clean[Consumption_KWh] * IF( ISBLANK(PricePerKWh), 0, PricePerKWh ) )
```

## 📈 Dashboard Highlights

🔹 **Consumption by Region** — identifies energy usage distribution across the UK  
🔹 **Peak vs Off-Peak Consumption** — compares demand during different hours  
🔹 **Revenue & Consumption Over Time** — dual-axis trend analysis for performance tracking  
🔹 **Revenue by Customer Type** — business segmentation by residential, industrial, and commercial customers  

---

## 🧠 Skills Demonstrated

✅ **Power Query** — data transformation and cleaning  
✅ **SQL Querying** — relational joins & data extraction  
✅ **DAX** — advanced calculated columns and measures  
✅ **Data Modeling** — dimensional design with star schema  
✅ **Power BI Service** — report building & publishing  
✅ **Business Storytelling** — clear visuals that support data-driven decisions  

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|----------|
| **Power BI Desktop** | Data modeling & dashboard design |
| **SQL Server** | Query and manage data |
| **CSV / Excel** | Synthetic data source |
| **DAX & M Language** | Analytics & transformation |
| **GitHub** | Project sharing and version control |

---

## 📸 Dashboard Preview

![Dashboard Preview](./dashboard.png)

---

## 💼 About

👩‍💻 **Developed by:** *Manisha Sharma*  
🎯 * Power BI Developer & Data Analyst*  
📍 *Exeter, UK*

A project built to showcase **business intelligence**, **analytical thinking**, and **dashboard storytelling** skills using **Microsoft Power BI**.

---

## 🚀 How to View

1. Clone this repository or download the `.pbix` file  
2. Open the file in **Power BI Desktop**  
3. Refresh data connections (if prompted)  
4. Explore the data model and interact with visuals  

---

## 🌐 Connect with Me

- 💼 [LinkedIn](https://www.linkedin.com/in/manishasharma0402/)  
- 📧 [Email](manishasharma9503@gmail.com)  
- 🐙 [GitHub](https://github.com/serenityincode)

---

⭐ *If you found this project insightful, don’t forget to star this repository!*
