# Supply Chain & Inventory Analysis (Excel)

An Excel project that analyses inventory against demand for 1,000 logistics shipments (2024), flags stock-out and overstock risk, generates reorder alerts, and compares truck performance.

## Objective
Optimise stock and demand: find where inventory is too low or too high, decide when to reorder, and see which trucks perform worst.

## Dataset
`smart_logistics_dataset.csv` has 1,000 shipment records across 10 trucks (Jan-Dec 2024). Key columns: `Inventory_Level`, `Demand_Forecast`, `Asset_ID`, `Logistics_Delay`, `Waiting_Time`, `Asset_Utilization`, `Logistics_Delay_Reason`.

## What I built
| Sheet | Purpose |
|---|---|
| supply chain project | Cleaned data plus helper columns: stock gap, coverage ratio, stock status, reorder alert, reorder quantity, month |
| truck_Summary | Per-truck shipments, delay rate, avg wait time, utilization, stock-outs, reorder alerts, rank |
| lookup | Pick a truck from a dropdown and fetch its metrics (VLOOKUP, INDEX-MATCH) |
| forecast | Monthly avg demand and inventory, plus a 3-month linear forecast |
| dashboard | KPI summary |
| pivot table and charts | Stock status pivot and charts |

## Logic used
- **Stock-out:** inventory < demand forecast
- **Overstock:** inventory > 2 x demand forecast
- **Reorder alert:** inventory < 1.2 x demand forecast
- **Reorder quantity:** amount needed to reach 1.5 x demand forecast
- **Forecast:** `FORECAST.LINEAR` over 12 monthly averages, projected for months 13-15

## Key findings
- 26.1% of shipments are stock-out and 28.4% are overstock; only 45.5% are healthy.
- 364 of 1,000 records trigger a reorder alert.
- Truck_10 has the highest delay rate (64.8%); Truck_5 has the lowest (49.5%).
- Average demand stays roughly flat at about 198-200 units a month, so the forecast is flat too.

## Skills demonstrated
Lookup functions (VLOOKUP, INDEX-MATCH), logical formulas (IF, nested IF, MAX), COUNTIFS/AVERAGEIFS, RANK, conditional formatting, pivot tables, forecasting basics, dashboard design.

## Limitations
- The dataset has no supplier or product column, so each truck (`Asset_ID`) is used as a proxy for a supplier.
- The thresholds (2x, 1.2x, 1.5x) are my own assumptions and can be changed in the formulas.
- The forecast is a simple linear trend on one year of data and does not capture seasonality.

## How to use
Download `supply_chain_project.xlsx` and open it in Excel. Formulas recalculate automatically.
