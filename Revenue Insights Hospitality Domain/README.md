# 🏨 Hospitality Domain Revenue Analysis Dashboard (Power BI)

An interactive and data-driven Power BI Dashboard designed to analyze revenue performance, room bookings, and operational efficiency for a premier hotel chain in the hospitality industry. This project translates raw data into actionable insights using advanced DAX styling and business metrics.

---

## 📊 Dashboard Visuals & Reports
You can see the visuals and KPI given below.

### 1. Revenue Dashboard Overview
Overview of core metrics including total Revenue (1.69bn), RevPAR (7.34K), ADR, and occupancy insights across weekends and weekdays.
![Revenue Dashboard Hospitality Domain](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/Home.jpeg)  


### 2. Weekly Revenue Performance
Tracks total revenue generation broken down week-by-week and split between Business and Luxury hotel tiers.
![Revenue by week no and category](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/Revenue%20by%20week%20and%20Category.jpeg)  


### 3. Revenue Per Available Room (RevPAR) Analysis
A deep dive into weekly RevPAR fluctuations to understand capacity utilization value across different property categories.
![RevPAR by week no and category](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/RevPAR%20by%20week%20and%20category.jpeg)  


### 4. Average Daily Rate (ADR) Trends
Monitors the average price paid for rooms sold over consecutive weeks, showcasing pricing power.
![ADR by week and Category](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/ADR%20by%20week%20and%20category.jpeg?raw=true)


### 5. Operational WoW Change % Metrics
These detailed charts capture week-over-week growth or decline percentages across key hospitality performance metrics.
![Realization WoW % change Week and Category](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/Realization%20WoW.jpeg?raw=true)

![Occupancy % by Week and Category](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/Occupancy%20WoW.jpeg)

[![DSRN WoW change % by week no and category](path/to/your/image8.png)  ](https://github.com/sadaatalsyed/Power-BI-Projects/blob/main/Revenue%20Insights%20Hospitality%20Domain/DSRN%20WoW.jpeg)


---

## 🛠️ Data Modeling & DAX Formulas



### 📅 Calculated Columns (`dim_date` Table)

1. **Week Number (`wn`)**
   * *Purpose:* Date se standard week number extract karne ke liye.
   ```dax
   wn = WEEKNUM(dim_date[date])


2. **Day Type (day type)**
   Purpose:To divide the days between weekdays and working days according to feedback by stakeholders.
   ```dax
    day type = 
    Var wkd = WEEKDAY(dim_date[date],1)
    return
    IF(wkd > 5, "Weekend", "Weekday")
### 🚀 Week-over-Week (WoW) Time Intelligence Calculations
 **1. Revenue WoW Change %**
  ```dax
  Revenue WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([Revenue],dim_date[wn]= selv)
    var revpw =  CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
    return
    DIVIDE(revcw,revpw,0)-1

  **2. Occupancy WoW Change %**
 ```dax
  Occupancy WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([Occupancy %],dim_date[wn]= selv)
    var revpw =  CALCULATE([Occupancy %],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
    return
    DIVIDE(revcw,revpw,0)-1

  **3. ADR WoW change %**
 ```dax
    ADR WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([ADR],dim_date[wn]= selv)
    var revpw =  CALCULATE([ADR],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
    return
    DIVIDE(revcw,revpw,0)-1
  **4. Revpar WoW change %**
 ```dax
    Revpar WoW change % = 
    Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
    var revcw = CALCULATE([RevPAR],dim_date[wn]= selv)
    var revpw =  CALCULATE([RevPAR],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
    return
    DIVIDE(revcw,revpw,0)-1
  **5. Realisation WoW change %**
 ```dax
  Realisation WoW change % = 
  Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
  var revcw = CALCULATE([Realisation %],dim_date[wn]= selv)
  var revpw =  CALCULATE([Realisation %],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
  return
  DIVIDE(revcw,revpw,0)-1


  
  
