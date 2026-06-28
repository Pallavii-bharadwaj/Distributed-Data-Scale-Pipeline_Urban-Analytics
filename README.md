# Broken Windows Theory — London Crime Analysis

An end-to-end cloud data pipeline and analytical study investigating the **Broken Windows Theory** across all 32 London boroughs using crime, fly-tipping, and recycling data. Built on **Azure Data Lake Gen2, Databricks, Delta Lake, and Tableau**, processing 1M+ records spanning 2008–2023.

---

## What is the Broken Windows Theory?

The Broken Windows Theory (Wilson & Kelling, 1982) proposes that visible signs of disorder and neglect — such as broken windows, fly-tipping, and poor waste management — signal that an area is uncared for, encouraging further crime. This project investigates whether urban neglect indicators statistically correlate with crime rates across London boroughs.

---

## Project Overview

| Item | Detail |
|---|---|
| **Data sources** | London Datastore — crime records, fly-tipping incidents, recycling rates |
| **Coverage** | All 32 London boroughs + City of London |
| **Time period** | 2008–2023 (15 years) |
| **Records processed** | 1M+ crime records |
| **Architecture** | Medallion (Bronze → Silver → Gold) |
| **Award** | Merit |

---

## Architecture

```
London Datastore (raw data)
        │
        ▼
Azure Data Lake Gen2 (Bronze layer — raw ingestion)
        │
        ▼
Azure Databricks (Silver layer — cleaning, transformation, SQL queries)
        │
        ▼
Delta Lake (Gold layer — analytical datasets)
        │
        ▼
Tableau (dashboards + visualisations)
        │
        ▼
Statistical Analysis + Policy Recommendations
```

---

## Tech Stack

- **Cloud:** Azure Data Lake Storage Gen2, Azure Databricks
- **Storage format:** Delta Lake (ACID transactions, time travel)
- **Processing:** PySpark, SQL on Databricks
- **Architecture:** Medallion (Bronze/Silver/Gold layers)
- **Visualisation:** Tableau
- **Analysis:** Python, Pandas, Statistical Modelling

---

## Key Findings

- Statistically significant positive correlation between fly-tipping rates and crime incidents across London boroughs
- Boroughs with lower recycling rates showed consistently higher crime rates across the study period
- Temporal analysis revealed crime peaks align with periods of increased urban neglect indicators
- Policy-relevant recommendations produced for borough-level intervention strategies

---

## Repository Contents

```
broken-windows-london-analysis/
├── CBDA_code.ipynb              # Databricks pipeline — ingestion, transformation, analysis
├── CBDA_report.pdf              # Full written report with findings and recommendations
├── Crime_Analysis.twb           # Tableau workbook with interactive dashboards
├── architecture_diagram.png     # Pipeline architecture diagram
└── README.md
```

---

## How to Run

### Prerequisites
- Azure account with Databricks workspace
- Azure Data Lake Gen2 storage container
- Tableau Desktop (to open `.twb` file)

### Steps
1. Upload raw datasets from [London Datastore](https://data.london.gov.uk/) to your Data Lake Bronze container
2. Open `CBDA_code.ipynb` in Azure Databricks
3. Update the storage account connection strings in the first cell
4. Run all cells — pipeline handles Bronze → Silver → Gold transformation automatically
5. Connect Tableau to your Gold layer Delta tables and open `Crime_Analysis.twb`

---

## Data Sources

All data sourced from the publicly available [London Datastore](https://data.london.gov.uk/):
- Metropolitan Police recorded crime statistics
- Fly-tipping incident reports by borough
- Household recycling rates by borough

