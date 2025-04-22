# EV MARKET ANALYSIS: UNLOCKING INSIGHTS ACROSS CARS, TRUCKS, VANS, AND BUSES

![File_Thumbnail (1)](https://github.com/user-attachments/assets/1592091b-f67f-4b57-b26b-ae9943e8e5d9)

- **Ideal for policy makers and business executives to understand the EV Global Market dynamics in the 4+ Wheelers vehicle segment.**
-  [Global EV Market Analysis: Unlocking Insights Across Cars, Trucks, Vans, and Buses](https://app.powerbi.com/view?r=eyJrIjoiOTRlOWNlNzktNTk0Ni00YmEwLTk4MDAtOWJjYTI5YzZkNTg5IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9)  


## Table of Contents
- [Business Objective](#business-objective)
- [Dataset](#dataset)
- [Dashboard](#dashboard)
- [Data Model](#data-model)
- [KPIs Evaluated](#kpis-evaluated)
- [Key DAX Measures](#key-dax-measures)
- [Languages and Technologies](#languages-and-technologies)
- [Business Impact](#business-impact)

## Business Objective
This project delivers actionable insights into global EV adoption trends by analyzing vehicle powertrain data, CO₂ displacement, charging infrastructure, and future projections. The dashboard enables policy makers, automotive industry executives, and data analysts to explore:

  📈 Historical Trends (2010–2023): EV sales & stock growth across multiple regions
  
  🔮 Future Projections (2025–2035): APS vs. STEPS policy scenarios & market penetration metrics
  
  ⚡ India’s Emerging Leadership: Post-FAME II & PLI schemes driving BEV dominance
  
  🔍 Key Business Metrics: Oil displacement, charging infrastructure optimization & policy-driven sales

          APS: Ambitious approach which assumes the introduction of innovative policies
          STEPS: Conservative approach assuming the continuation of present policy

## Dataset 
IEA’s Global 4 Wheeler EV Outlook [Dataset](https://docs.google.com/spreadsheets/d/1Tnu0iayO5ln3iYOBU6ksexbFnY3hJNB9/edit?usp=drive_link&ouid=104075893283661227619&rtpof=true&sd=true), a valuable data source offering comprehensive insights into the global EV market.

## Dashboard

#### Global EV Market Overview
<img width="616" alt="EV Overview" src="https://github.com/user-attachments/assets/429d5417-1577-465d-b73e-0b38b1e3d87e" />

#### EV Market Trends (2010-2023)
<img width="617" alt="Historical EV Market 2010-23" src="https://github.com/user-attachments/assets/3b248f34-c138-4242-9938-6407d87e49fd" />

#### EV Transition Performance Metrics
<img width="616" alt="EV Transition Metrics" src="https://github.com/user-attachments/assets/0d83fa2e-234d-4d46-8cab-99ccf6f1be01" />

#### EV Market Projections (2025-35)
<img width="616" alt="EV Projections 2025-35" src="https://github.com/user-attachments/assets/e7e881b9-c456-49fb-baff-4ca83cb1566f" />

#### The Indian EV Leadsrship Blueprint
<img width="616" alt="Indian EV Story" src="https://github.com/user-attachments/assets/b344eadb-44f8-43cd-b1d6-7f2daa7b060f" />





## Data Model 
<img width="886" alt="Image" src="https://github.com/user-attachments/assets/1713a0b0-5b6a-441c-b17e-00d08d3c2cad" />



## KPIs Evaluated
1. % Electricity Demand_L5Y
2. Total_Electricity Demand
3. YoY_Electricity Demand%
4. Total_Energy transition
5. % EV charging_gwth L5Y
5. %Fast Charging_Infra
6. EVs on Road/Charging point
7. New EVs/Charging point
8. Total_Fast Charging
9. Total_Slow Charging
10. YoY_Charging Infra%
11. % Sales Growth_L5Y
12. CAGR_Sales
13. PHEV/BEV Sales
14. Sales_Powertrain
15. Total_Charging points
16. Total_Sales
17. YoY_Sales Growth% etc
    
## Key DAX Measures
### Year On Year Increase in Electricity Demand (4-Wheeler EV)
```DAX
% EV charging_gwth L5Y = 
VAR SelectedRegion = SELECTEDVALUE ( Dim_Region[Region] )
VAR CurrentYear = 2023 // or whatever the current end year is
VAR StartYear = 2019 // calculate from 3 years ago 
VAR CurrentYeardata =
    CALCULATE (
        SUM ( Main[Value] ),
        Dim_Category[Category] = "Historical",
        Dim_Parameter[Parameter] = "EV charging points",
       Dim_date[Year]= CurrentYear,
        Dim_Region[Region] = SelectedRegion
    )
VAR PreviousYeardata =
    CALCULATE (
        SUM ( Main[Value] ),
        Dim_Category[Category] = "Historical",
        Dim_Parameter[Parameter] = "EV charging points",
        Dim_date[Year]= StartYear,
        Dim_Region[Region] = SelectedRegion
    )
RETURN
    IF (
        NOT ISBLANK ( CurrentYeardata )
            && NOT ISBLANK ( PreviousYeardata )
            && PreviousYeardata <> 0,
        DIVIDE ( CurrentYeardata - PreviousYeardata, PreviousYeardata ),
        BLANK ()
    )
```    
### % Change in the EV Charging infrastructure (Last 5 years)
```DAX

% EV charging_gwth L5Y = 
    VAR SelectedRegion = SELECTEDVALUE ( Dim_Region[Region] )
    VAR CurrentYear = 2023 // or whatever the current end year is
    VAR StartYear = 2019 // calculate from 3 years ago 
    VAR CurrentYeardata =
    CALCULATE (
        SUM ( Main[Value] ),
        Dim_Category[Category] = "Historical",
        Dim_Parameter[Parameter] = "EV charging points",
       Dim_date[Year]= CurrentYear,
        Dim_Region[Region] = SelectedRegion
    )
    VAR PreviousYeardata =
    CALCULATE (
        SUM ( Main[Value] ),
        Dim_Category[Category] = "Historical",
        Dim_Parameter[Parameter] = "EV charging points",
        Dim_date[Year]= StartYear,
        Dim_Region[Region] = SelectedRegion
    )
    RETURN
    IF (
        NOT ISBLANK ( CurrentYeardata )
            && NOT ISBLANK ( PreviousYeardata )
            && PreviousYeardata <> 0,
        DIVIDE ( CurrentYeardata - PreviousYeardata, PreviousYeardata ),
        BLANK ()
    ) 
```

## Languages and Technologies
1. **MS Excel** for preliminary analysis.
2. **DAX** for backend operations i.e. to build calculative measures and columns.
3. **Power Query (M language)** for data preparation and reshaping of data.
4. **Power BI** for visualization. Charts and graphs will be employed to reveal trends and patterns in the EV market data.
5. **FIGMA** for building the Wireframe.

## Business Impact
- Actionable recommendations for stakeholders in the EV market, based on data-driven insights. This could include suggestions for government policy, infrastructure development, or industry innovation.


