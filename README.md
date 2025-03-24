# 4-WHEELER EV MARKET ANALYSIS-2024
- [4 WHEELER EV Global Market Analysis](https://drive.google.com/file/d/1PgO8HBE7IFmpd0m69toSzl3o8lkHtMDh/view?usp=drive_link)
- [Preview Dashboard](https://project.novypro.com/VAmAc0)
- **Use case for policy makers and business executives to understand the EV Global Market dynamics in the 4+ Wheeelers vehicle segment.**
## Table of Contents
- [Business Objective](#business-objective)
- [Dataset](#dataset)
- [Data Model](#data-model)
- [KPIs Evaluated](#kpis-evaluated)
- [Key DAX Measures](#key-dax-measures)
- [Demo Preview](#demo-preview)
- [Languages and Technologies](#languages-and-technologies)
- [Business Impact](#business-impact)

## Business Objective
- An ambitious project based on 2024 IEA Global EV Outlook Report, whose purpose is basically for strategic planning.
Ascertains the current market scenario using data highlighting the performance analysis of the markets across different areas like stock, sales, stock share, sales share, availability 
of charging infrastructure, Energy transition, 4-Wheeler EV Electricity Demand by framing informed actionable recommentations for the EV businesses to work on.
- The region focused in this analysis are: USA, China, Japan, Europe, India and the World (for reference)
- Prediction based on APS (Announced Pledges Scenario) and STEPS (Sustainable Development Scenario) are respectively present in the dataset and is also analyzed to chart the path ahead of the 
 probable factors which could drive the EV Market further for e.g. India currently has only a 2% market penetration, this study could help us understand the probable factors which could drive the further growth in the country.

          APS: Ambitious approach which assumes the introduction of innovative policies
          STEPS: Conservative approach assuming the continuation of present policy

## Dataset 
IEA’s Global 4 Wheeler EV Outlook [Dataset](https://docs.google.com/spreadsheets/d/1Tnu0iayO5ln3iYOBU6ksexbFnY3hJNB9/edit?usp=drive_link&ouid=104075893283661227619&rtpof=true&sd=true), a valuable data source offering comprehensive insights into the global EV market.

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

## Demo Preview
1.
<img width="584" alt="Image" src="https://github.com/user-attachments/assets/89cd9ba9-17e9-41a6-ad74-8c7ef7ea6db9" />

2.
<img width="583" alt="Image" src="https://github.com/user-attachments/assets/5668508a-9add-4883-9fe3-d88cfed4206b" />

3.
<img width="593" alt="Image" src="https://github.com/user-attachments/assets/ef3e886d-5c16-47fe-b134-780878a7aac5" />

## Languages and Technologies
1. **MS Excel** for preliminary analysis.
2. **DAX** for backend operations i.e. to build calculative measures and columns.
3. **Power Query (M language)** for data preparation and reshaping of data.
4. **Power BI** for visualization. Charts and graphs will be employed to reveal trends and patterns in the EV market data.
5. **FIGMA** for building the Wireframe.

## Business Impact
Actionable recommendations for stakeholders in the EV market, based on data-driven insights. This could include suggestions for government policy, infrastructure development, or industry innovation.

