# Econ 3916 PS1 --- The Cost of Living Brief

## Project Overview

This project compares changes in prices from 2019 to 2024 for an
illustrative household and selected official Consumer Price Index (CPI)
series from the Federal Reserve Bank of St. Louis's FRED database.

The household is a single parent working full time at an hourly wage and
raising one school-age child. The parent rents an apartment, commutes by
car, and pays for groceries, utilities, childcare, and healthcare.

## Research Question

How much did the cost of a representative household basket increase
between 2019 and 2024, and how does that change compare with broader
consumer price measures?

## Household Basket

The basket contains seven spending categories:

-   Rent
-   Groceries
-   Transportation
-   Utilities
-   Childcare
-   Healthcare
-   Household and personal care

Each category has a 2019 price, a 2024 price, and a budget weight. The
weights sum to 1.0, so they represent the full household budget in the
model.

**Important limitation:** The household prices and budget weights are
illustrative assumptions. They are not verified records of an actual
household's spending.

## Methods

### 1. Household price index

The analysis calculates a fixed-weight Laspeyres price index using 2019
as the base year (= 100). The budget weights remain fixed, so categories
that account for a larger share of spending have more influence on the
result.

The analysis also calculates the unweighted average of the percentage
price changes across the seven categories for comparison.

### 2. Official CPI comparisons

The notebook downloads selected series from FRED and compares annual
average index levels for 2019 and 2024. The series include:

-   Headline CPI (`CPIAUCSL`)
-   Rent (`CUSR0000SEHA`)
-   Food at home (`CUSR0000SAF11`)
-   Used cars (`CUSR0000SETA02`)
-   Electricity (`CUSR0000SEHF01`)
-   Medical care (`CPIMEDSL`)

These series are proxies for household expenses, not exact measures of
this particular household's costs. In particular, the selected series do
not directly measure this household's childcare expenses or its full
cost of commuting.

### 3. Rebased chart

The official series are rebased so that 2019 = 100. This puts the series
on a common scale. The household index is shown only at 2019 and 2024
because the basket contains prices for those two years only.

### 4. Data checks and seasonal adjustment

The notebook audits each FRED series for its observation dates and
missing months, compares headline CPI and rent over their full and
shared observation periods, and plots seasonally adjusted and unadjusted
headline CPI. Missing observations are not automatically interpolated or
replaced.

## Main Results

  -----------------------------------------------------------------------
  Measure                                                          Result
  ------------------------------ ----------------------------------------
  Unweighted average price                                         24.76%
  increase across categories     

  Household Laspeyres price                                        100.00
  index in 2019                  

  Household Laspeyres price                                        125.55
  index in 2024                  

  Weighted household basket                                        25.55%
  price increase                 

  Difference between weighted                      0.79 percentage points
  and unweighted increases       
  -----------------------------------------------------------------------

For the selected FRED series, the annual-average changes from 2019 to
2024 were:

  Series           Price index change
  -------------- --------------------
  Headline CPI                 22.70%
  Rent                         26.86%
  Food at home                 26.80%
  Used cars                    28.70%
  Electricity                  30.81%
  Medical care                 13.13%

These official series provide context, but they represent broader
consumer groups and should not be treated as a direct measurement of
this household's inflation experience.

## Conclusion

The illustrative household basket's index rises from 100 in 2019 to
125.55 in 2024, implying a 25.55% increase. This is slightly higher than
the unweighted average increase because the index gives greater
importance to categories with larger budget weights, especially rent and
groceries.

Confidence in the household estimate is **moderate**. The arithmetic
follows the stated method, but the conclusion depends on the accuracy
and representativeness of the illustrative prices and weights. The
results are best used to identify possible cost pressures, not as an
exact measure of every household's experience.

## Requirements

The notebook uses Python and the following packages:

-   `numpy`
-   `pandas`
-   `matplotlib`
-   `requests`

## How to Run

1.  Open the notebook in Google Colab or a Jupyter environment.
2.  Install any missing packages listed above.
3.  Run the notebook cells in order.
4.  Ensure that the environment has internet access to download the FRED
    CSV data.
5.  Review the printed tables, charts, data audit, and written
    interpretation.

## Data Source

Federal Reserve Bank of St. Louis, FRED: https://fred.stlouisfed.org/

The notebook retrieves CSV observations from FRED's graph data endpoint.
Results may change if the source series are revised or updated.

## Limitations

-   The household basket is illustrative rather than based on a verified
    household budget.
-   National or broader CPI series may not match the household's
    location, lease, insurance, travel, or spending patterns.
-   Used-car prices do not capture the full cost of commuting by car.
-   Childcare is included in the household basket but does not have a
    dedicated CPI proxy in the selected series.
-   Differences between the household index and official CPI series do
    not mean that one measure is wrong; they measure different baskets
    and populations.
