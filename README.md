# Toronto-Crime-Neighbourhood-Dashboard
## 📊 Project Overview
This project analyzes crime incidents in Toronto using open data sourced from Kaggle.  
The goal is to clean, transform & visualize crime data to uncover insights about:
- Crime distribution across neighbourhoods,
- Common crime categories
- Reporting delays (days)
- Temporal patterns of incidents.

## Project Description
A two-page Power BI dashboard analyzing real Toronto crime data from Kaggle. This project demonstrates data cleaning, DAX measure creation, and advanced visualization techniques to highlight crime patterns, reporting delays, and location-based insights across the city.

## 🧩 Dataset Information
**Source:** [Kaggle – Major Crime Indicators] Link:  
**File Type:** CSV  
**Rows:** ~ 3,00,000+
**Columns Used:**
- Total Crime Incidents
- Report & Occurrence Dates (Year, Month, Day, Hour, Day of Week)  
- Location Type  
- Premises Type    
- Offence  
- Crime Category  
- Neighbourhood + (140)
- UCR CODE

**Data Cleaning Steps:**
- Removed redundant or duplicate columns.  
- Standardized neighborhood names and extracted relevant parts (e.g., “Apartment” from “Apartment (rooming, condo)”).  
- Created new columns (customized) for reporting delay (days) & average reporting delay (days)
- Converted all date columns to proper `datetime` format for time-based visuals.  

---

## 🧮 Key DAX Measures
| Measure | Description |
|----------|--------------|
| **Total Crime Incidents** | =`COUNT(‘major-crime-indicators’)
| **Reporting Delay (Days)** | = [(‘OCC_DATE’) - (‘REPORT_DATE’)]
| **Average Reporting Delay (Days)** | = AVERAGE('major-crime-indicators'[Reporting Delays (Days)])
| **Most Common Crime (MCI Category)** | = VAR TopMCI = TOPN(1,VALUES('major-crime-indicators'[Crime_Category]),CALCULATE(COUNTROWS('major-crime-indicators')),DESC)RETURN CONCATENATEX(TopMCI, 'major-crime-indicators'[Crime_Category], ",")
| **Peak Hour of Crime** | = VAR TopHour = TOPN(1,VALUES('major-crime-indicators'[OCC_HOUR]), CALCULATE(COUNTROWS('major-crime-indicators')),DESC) RETURN CONCATENATEX(TopHour, 'major-crime-indicators'[OCC_HOUR], ",")

---

## 📈 Dashboard Pages

📈 Dashboard Pages
🧭 Page 1 – KPI Dashboard

Purpose: High-level overview of key metrics and citywide crime trends.

Visuals:

Slicers: Occurrence Year | Report Year | Neighbourhood | Crime Category

Cards (KPIs):
- Total Crime Incidents
- Average Reporting Delay (Days)
- Most Common Crime
- Peak Hour
Clustered Bar Chart: Average Reporting Delay (Days) by Neighbourhood 
Map Visual: Total Crimes by Neighbourhood & Crime Category

This page provides a macro-level view of trends and overall performance indicators — helping quickly identify high-crime areas, time periods, and delays in reporting.

🏘️ Page 2 – Category Analysis

Purpose: Deep dive into crime categories, timing, and locations.

Slicers: Occurrence Year and Occurrence Hour for time-based interactivity.

Visuals:
- Tree Map: Total Crimes by Premises Type
- Line Chart: Total Crimes by Occurrence Year
- Stacked Bar Chart: Total Crimes by Offence (Top 10)
- Funnel Chart: Total Crimes by Crime Category (linked to slicers)

This page allows the user to interactively explore when crimes occurred (hour, year), where they happened (premises type), and what category they belonged to.
For instance, selecting a specific hour and year dynamically updates all visuals — giving a precise view of patterns and hotspots.

---

💾 Files in Repository
File	Description
Toronto Crime Report.pbix	Power BI report (interactive)
Toronto_Crime_Cleaned.csv	Cleaned dataset used in the dashboard
Toronto Crime Report Dashboard Snapshot of Report Page 1 & 2

README.md	Project documentation
## 🌐 Interactivity
All visuals are fully interactive with slicers and drill-through features.  
You can filter by:
- Year of occurrence vs. report year  
- Specific neighbourhoods  
- Crime category  

—
## 📚 Tools & Skills
- Power BI (Main data visulization platform used for report creation)
- Power Query (Data transformation & cleaning layer for reshaping and preparing the data)
- DAX [Data Analysis Expression] (Used for calculated measures, dynamic visulas and conditional logics)
- File Format (.pbix for developement .pdf for dashboard preview)

---

## 🧑‍💻 Author
**Shah The Analyst**  
Data Analyst | Power BI | Python | SQL  
📍 Based on real Toronto data, cleaned, analyzed, and visualized by Shah.  
📧 Shahimti12@gmail.com



