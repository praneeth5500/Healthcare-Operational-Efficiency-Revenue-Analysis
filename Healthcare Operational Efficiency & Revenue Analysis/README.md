# Healthcare Operational Efficiency & Revenue Analysis 🏥

## 📌 Project Overview
**Goal:** To analyze hospital admission data to identify revenue drivers and operational bottlenecks.
**The Problem:** High readmission rates and extended Length of Stay (LOS) reduce bed availability and increase operational costs.
**The Solution:** An end-to-end analytics pipeline using **Snowflake** for data warehousing and **Power BI** for visualization.

## 🛠️ Tech Stack
* **Database:** Snowflake (Data Warehousing), SQL (Data Transformation)
* **ETL:** Python (Pandas) for initial cleaning
* **Visualization:** Power BI (DAX, Interactive Dashboards)
* **Domain:** Healthcare Analytics, Revenue Cycle Management (RCM)

## 📊 Key Insights & Results
1.  **Revenue Impact:** Analyzed **$1.4B** in total revenue across 10,000+ patient records.
2.  **Operational Bottleneck:** Identified that **'Urgent Asthma'** admissions have the highest Average Length of Stay (**15.8 days**), which is 5% higher than the baseline.
3.  **Strategic Recommendation:** Review discharge protocols for Urgent Care Asthma patients to improve bed turnover rates.

## 📷 Dashboard Preview
![Dashboard Screenshot](04_Screenshots/dashboard_main.png)
*(Note: Upload your screenshot to the 04_Screenshots folder and rename it to dashboard_main.png)*

## 🧠 SQL Logic (Sample)
```sql
-- Calculating Length of Stay and Revenue Per Day
SELECT 
    Medical_Condition, 
    ROUND(AVG(DATEDIFF(day, Admission_Date, Discharge_Date)), 1) AS Avg_LOS,
    SUM(Billing_Amount) AS Total_Revenue
FROM healthcare_data
GROUP BY Medical_Condition
ORDER BY Avg_LOS DESC;
