# Traffic Accident Analysis (1998–2025)

Year-wise traffic accident trends and severity insights, explored in **Python (pandas, Matplotlib)** and presented in **Microsoft Power BI**.

## Overview

This project analyses 28 years of annual traffic accident records. The notebook checks data quality, explores yearly trends, injury categories and year-over-year change, and measures how the variables relate to each other. The findings are then summarised in a Power BI dashboard and a presentation.

**Questions the project answers**

- How does accident volume change over time?
- How do fatalities vary by year?
- Which severity categories have the largest counts?
- Which measures move together?

## Headline numbers

| Metric | Value |
|---|---|
| Years covered | 1998–2025 (28 yearly records) |
| Total accidents | 165,289 |
| Fatalities (people killed) | 23,864 |
| Persons involved | 179,086 |
| Average accidents per year | 5,903 (median 5,184.5) |
| Highest year | 2013, with 9,710 accidents |
| Lowest year | 2022, with 3,453 accidents |
| Highest fatalities | 2012, with 1,401 killed |

## Key findings

- **High plateau, then a sharp drop.** Accidents averaged about 8,258 a year in 2012–2019 and about 4,067 a year in 2020–2025.
- **Biggest swings.** The largest year-over-year rise was 2012 (+47.2%) and the largest fall was 2020 (−36.2%).
- **Fatalities track fatal accidents closely.** Correlation is 0.99, and there are about 1.04 deaths per fatal accident.
- **Fatal share peaked in 2020.** 20.8% of accidents that year, against 14.4% over all years, even though total accidents fell.
- **Minor-injury accidents dominate.** They make up 54.7% of all category counts, followed by grievous injury (22.9%), fatal (13.9%) and non-injury (8.5%).
- **Total accidents track persons involved almost exactly** (correlation 0.97).

## Dataset

One row per year, 28 rows and 11 columns, all integers.

| Column | Meaning |
|---|---|
| `_id` | Record number |
| `YEAR` | Year (1998–2025) |
| `Fatal Accidents` | Accidents involving deaths |
| `Fatal Killed` | People killed in fatal accidents |
| `Grievous Injury - Accidents` | Accidents with grievous injury |
| `Grievous Injurty - Injured` | People grievously injured (the source header contains a typo) |
| `Minor Injury - Accidents` | Accidents with minor injury |
| `Minor Injury - Injured` | People with minor injuries |
| `Non Injury` | Accidents with no injury |
| `Total Accidents` | Overall accident count |
| `Total number of persons involved` | People involved in accidents |

The notebook reads the file under its original download name. A copy of the same 28 rows is included here as `data/traffic_accidents.csv`.

## Data quality

Checks run in the notebook:

- Shape is 28 × 11
- No missing values
- No duplicate rows and no duplicate years
- No negative values

Items to verify with the data source before drawing strong conclusions:

- **2013:** the four category columns add up to 9,705, but `Total Accidents` is 9,710.
- **Grievous-injury counts jump sharply** (87 accidents in 1999, 1,470 in 2010, 4,332 in 2018), which may reflect a recording or definition change. Grievous injuries exceed minor injuries in 2017–2021 and 2023–2024.
- **Persons involved is lower than total accidents** in 2008, 2009, 2010 and 2015.
- **Header typo:** `Grievous Injurty - Injured` should be renamed before building the Power BI model.

## Methodology

1. **Load and inspect:** read the CSV with pandas, check shape, data types and column names.
2. **Validate:** missing values, duplicate rows, duplicate years and negative values.
3. **Describe:** summary statistics, mean, median, maximum and minimum of total accidents.
4. **Visualise:** year-wise accidents, fatal accidents vs people killed, grievous vs minor injuries, category comparison.
5. **Year-over-year change:** absolute and percentage change in total accidents, with the largest rise and fall.
6. **Correlation:** correlation matrix and heatmap across the nine numeric measures.
7. **Report:** KPI cards, trend charts, severity breakdown and a year slicer in Power BI.

## Power BI dashboard layout

- Page title and KPI cards at the top (total accidents, fatalities, persons involved)
- Year-wise accident trend and severity breakdown in the centre
- Year slicer and summary table for filtering
- Consistent severity colours and readable labels

## Repository structure

```
.
├── README.md
├── data/
│   └── traffic_accidents.csv
├── notebooks/
│   └── Trafic_EDA.ipynb
└── presentation/
    └── Traffic_Accident_Analysis_Final.pptx
```

## How to run

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook notebooks/Trafic_EDA.ipynb
```

In the first data-loading cell, point `pd.read_csv` to `data/traffic_accidents.csv`. The notebook was written in Google Colab, so its original paths start with `/content/`.

## Tools

- Python 3, pandas, NumPy, Matplotlib
- Microsoft Power BI Desktop

## Limitations

Year-level data cannot identify hotspots, causes or time-of-day patterns. With only 28 data points, correlations are indicative rather than conclusive, and correlation does not imply causation.

## Future scope

- Add location, road type, time of day and vehicle fields
- Confirm category definitions with the data owner and re-run the analysis
- Refresh the Power BI report when new annual records arrive

## Author

**Kannadasan K**
