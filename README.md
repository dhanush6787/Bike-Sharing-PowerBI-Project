# Analyzing Smart City Bike Sharing Data using Power BI

## 1. Project Overview
Public bike-sharing systems generate continuous data from hundreds of stations across many cities. This project analyzes a bike station dataset in Power BI to understand station performance, usage efficiency and operational patterns across cities.

## 2. Dataset
- File: `Raw_Data/bike-stations-sharing-data.xlsx`
- Rows: 2,856 raw rows, 2,850 stations across 25 cities after cleaning
- Columns: number, name, address, position, banking, bonus, status, Contract Name, Bike Stands, Available Bike Stands, Available Bikes, Last Update

## 3. Tools Used
- Power BI Desktop (Power Query, DAX, Data Model, Visuals)
- Microsoft Word (screenshots and report)
- GitHub (version control and submission)

## 4. Data Cleaning and Transformation (Power Query)
1. Imported the Excel file and promoted headers.
2. Renamed columns to remove spaces (City, Total_Stands, Free_Stands, Bikes_Available, Last_Update).
3. Removed duplicates using Station Number + City.
4. Split the `position` column into Latitude and Longitude and set them to Decimal Number.
5. Converted `Last_Update` to Date/Time/Timezone and created a Date column.
6. Removed the unused placeholder `address` column.
7. Capitalized city names for consistent formatting.
8. Removed invalid rows (stands = 0, and available bikes + free stands greater than total stands).
9. Created a unique Station_Key (City + Station Number) because station numbers repeat across cities.

## 5. Data Model (Star Schema)
- Fact table: `Fact_Stations`
- Dimension tables: `Dim_City`, `Dim_Station`, `Dim_Date`
- Relationships (one-to-many, single direction):
  - Dim_City[City] to Fact_Stations[City]
  - Dim_Station[Station_Key] to Fact_Stations[Station_Key]
  - Dim_Date[Date] to Fact_Stations[Date]

## 6. DAX Measures
Total Stations, Total Stands, Bikes Available, Utilization %, Avg Bikes per Station, Open Stations, Closed Stations, Closed %, Empty Stations, Empty Station %, Overall Utilization, Utilization vs Average, Performance Category. Calculated columns: Station Utilization, Stand Size Category.

## 7. Dashboard
- KPI cards: Total Stations, Bikes Available
- Utilization % by city (bar chart)
- Station map (latitude and longitude)
- Open vs Closed stations (donut chart)
- Slicers: City and Status

## 8. Key Insights
- Dataset has no revenue or distance columns, so utilization (bikes available / total stands) is used as the efficiency measure.
- Overall utilization is 34.4%, with 24.6% of stations empty and 7.2% closed.
- Highest utilization: Lund (54%) and Ljubljana (49%).
- Lowest utilization: Vilnius, Rouen, Cergy-Pontoise, Mulhouse, Santander and Marseille (below 3 percent), mainly because 40-97% of their stations are closed.
- Large stations perform best (41% utilization) compared with medium (32%) and small (29%).
- Recommendation: reopen or review closed stations, rebalance bikes in large cities, and favour larger stations when expanding.

## 9. Folder Structure
```
Bike-Sharing-PowerBI-Project/
  Raw_Data/bike-stations-sharing-data.xlsx
  powerbi/Bike_Sharing_Analysis.pbix
  Bike-Sharing-Projects_Screenshots.pdf
  smart_city_bike_sharing_report.pdf
  README.md
```

## 10. How to Open
Install Power BI Desktop, download the repository and open `powerbi/Bike_Sharing_Analysis.pbix`.

## 11. Author
Dhanush - https://github.com/dhanush6787
