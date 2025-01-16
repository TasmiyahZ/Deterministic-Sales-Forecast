# Deterministic-Sales-Forecast
**Overview**
Create a deterministic sales forecast using historical sales growth and seasonal indices


**Approach**
Calculated KPIs to review past sales and derive next year forecasts like Compound Avg Growth rate, Contribution Margin, Seasonal Indices.
Used compound average growth method to normalize the sudden sales increase in 2023 while sales in 2022 and 2024 looked more in line. This smoothed out the growth rate and made more sense. The historical monthly sales were predictable and so a determnistic approach was used.


**Tools**
Excel, PowerQuery, DAX


**DAX Measures**


CAGR
POWER(DIVIDE(CALCULATE(sum([Actual Sales]),Table1[Order Date (Year)]="2024"),CALCULATE(SUM([Actual Sales]),Table1[Order Date (Year)]="2022"),0),1/2)-1
Contribution Margin
DIVIDE([Total Sales],CALCULATE([Total Sales],ALLEXCEPT('Calendar','Calendar'[Year])),0)

Avg Monthly (per Year)
AVERAGEX(ALL('Calendar'[Month]), [Monthly Avg Sales])

Seasonal Index
DIVIDE([Monthly Avg Sales],AVERAGEX(ALL('Calendar'[Month]), [Monthly Avg Sales]),0)

Monthly Forecast 2025
CALCULATE(SUM([Actual Sales]),'Calendar'[Year]=2024)*(1+[CAGR])

