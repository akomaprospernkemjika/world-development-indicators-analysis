# World Development Indicators — Exploratory Data Analysis

![Excel](https://img.shields.io/badge/Microsoft_Excel-Used-217346?logo=microsoft-excel&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-Used-F2C811?logo=powerbi&logoColor=black)

**Author:** Akoma Prosper Nkemjika
**Contact:** akomawole@gmail.com
**Data Source:** World Bank — World Development Indicators (WDI)

---

## Overview

This project explores macroeconomic and development indicators across 268 countries 
and territories using data extracted from the World Bank's World Development 
Indicators database. The goal was to clean, reshape, and analyse the dataset to 
uncover patterns in energy access, inflation, financial depth, and services trade 
across the globe.

This is an ongoing analytical project. Contributions, corrections, and feedback 
are welcome.

---

## Dataset

| Property | Detail |
|---|---|
| Source | World Bank — World Development Indicators |
| Countries | 268 countries and territories |
| Indicators | 5 |
| Years covered | 2000–2008 and 2017–2024 |
| Known gap | 2009–2016 is absent from this export |
| Missing value marker | `..` (replaced with blanks during cleaning) |

### Indicators
- Access to electricity, rural (% of rural population)
- Broad money (% of GDP)
- Inflation, consumer prices (annual %)
- Inflation, GDP deflator (annual %)
- Trade in services (% of GDP)

---

## What Was Done

### 1. Data Cleaning (Microsoft Excel)
- Removed footer and metadata rows appended by the WDI export
- Deleted the 2025 column (100% missing across all countries)
- Replaced all `..` missing value markers with proper blanks
- Cleaned year column headers from `2000 [YR2000]` format to plain integers
- Visually flagged the 2009–2016 data gap with a column border separator
- Converted data to a named Excel Table (`WDI_Raw`)

### 2. Reshaping (Power Query)
- Reshaped dataset from wide format (17 year columns) to long (tidy) format
- Each row now represents one Country × Indicator × Year observation
- Added a `Gap Year` flag column to identify 2009–2016 rows if appended later
- Long format contains **18,253 rows** of actual observations

### 3. Wide Format
- Built a pivot table from the long format
- Each indicator becomes its own column
- One row per Country × Year
- Converted to a static named table (`WDI_Wide`) for analysis

### 4. Correlation Matrix
- Computed pairwise Pearson correlations across all 5 indicators
- Applied conditional colour formatting for visual clarity

### 5. Country Rankings
- Ranked all 268 countries by average Rural Electricity access (2000–2024)
- Ranked all 268 countries by average Trade in Services (2000–2024)
- Classified countries into tiers: High, Medium, Low, Very Low, No Data

---

## Key Findings

### Correlation Matrix
The only meaningful correlation in the dataset is between the two inflation 
measures — **Inflation CPI vs Inflation Deflator at 0.70**. All other indicator 
pairs show near-zero correlation, suggesting these five indicators capture largely 
independent dimensions of development.

### Rural Electricity Access Rankings
| Position | Countries |
|---|---|
| Highest (Rank 1) | Andorra, and most developed nations at 100% |
| Lowest | Congo DRC |

### Trade in Services Rankings
| Position | Country | Avg (% of GDP) |
|---|---|---|
| 1st | Luxembourg | — |
| 2nd | Malta | — |
| 3rd | Ireland | — |
| 4th | Aruba | — |
| 5th | Singapore | — |
| Lowest | Zimbabwe | — |

Small, finance-driven or tourism-dependent economies dominate the top of the 
Trade in Services ranking. Larger, commodity-dependent economies tend to rank lower.

### Nigeria's Position
Nigeria's performance across both ranked indicators is a cause for reflection:

| Indicator | Average Value | Rank | Tier |
|---|---|---|---|
| Rural Electricity Access | 25.52% | 210 / 256 | Low |
| Trade in Services (% of GDP) | 6.56% | 224 / 256 | Very Low |

Nigeria ranks in the bottom quarter globally on both indicators. With over 
210 million people, a rural electricity average of just 25.5% over the analysis 
period highlights a significant infrastructure gap. A Trade in Services average 
of 6.56% of GDP reflects limited integration into global services trade despite 
the country's size and economic potential.

---

## What This Analysis Does Not Cover

In the interest of transparency, the following were not completed in this version 
of the analysis:

- **Trend analysis** — how each indicator changed over time per country or region
- **Regional grouping** — aggregating countries by World Bank income group or 
  geographic region
- **Inflation analysis** — no deep dive into the 2022–2023 global inflation surge 
  visible in the data
- **Broad money analysis** — financial deepening over time not explored
- **Scatter plots** — visual relationships between indicators not charted
- **2009–2016 gap** — this period is missing from the dataset and was not 
  interpolated or sourced from elsewhere
- **2024 data** — approximately 43% missing, treated with caution and not used 
  for ranking

These represent clear opportunities for extension by contributors.

---

## Files

| File | Description |
|---|---|
| `WDI_Analysis.xlsx` | Full cleaned workbook — Raw data, Long Format, Wide Format, Correlation Matrix, Country Rankings |

---

## Contributions & Feedback

This analysis is open for review, extension, and constructive criticism. 
If you spot an error, have a suggestion, or want to build on this work:

- Open an **Issue** on this repository
- Submit a **Pull Request** with your additions
- Or reach out directly at **akomawole@gmail.com**

Areas particularly open for contribution:
- Trend and time series analysis
- Regional and income group comparisons
- Visualisations and dashboards
- Python or R replication of the cleaning and analysis steps

---

## Disclaimer
This analysis was conducted as a learning and portfolio project. 
Findings should not be cited for academic or policy purposes without 
independent verification against the original World Bank source data.
