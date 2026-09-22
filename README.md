# 🚲 Bike Sales Analysis & Customer Intelligence Dashboard

[![Excel](https://img.shields.io/badge/Microsoft_Excel-Advanced_Analysis-2D6A4F?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyByb2xlPSJpbWciIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiBmaWxsPSJ3aGl0ZSI+PHBhdGggZD0iTTIzIDEuNXEuNDEgMCAuNy4zLjMuMjkuMy43djE5cTAgLjQxLS4zLjctLjI5LjMtLjcuM0g3cS0uNDEgMC0uNy0uMy0uMy0uMjktLjMtLjdWMThIMXEtLjQxIDAtLjctLjMtLjMtLjI5LS4zLS43VjdxMC0uNDEuMy0uN1EuNTggNiAxIDZoNVYyLjVxMC0uNDEuMy0uNy4yOS0uMy43LS4zek02IDEzLjI4bDEuNDIgMi42NmgyLjE0bC0yLjM4LTMuODcgMi4zNC0zLjhINy40NmwtMS4zIDIuNC0uMDUuMDgtLjA0LjA5LS42NC0xLjI4LS42Ni0xLjI5SDIuNTlsMi4yNyAzLjgyLTIuNDggMy44NWgyLjE2ek0xNC4yNSAyMXYtM0g3LjV2M3ptMC00LjV2LTMuNzVIMTJ2My43NXptMC01LjI1VjcuNUgxMnYzLjc1em0wLTUuMjVWM0g3LjV2M3ptOC4yNSAxNXYtM2gtNi43NXYzem0wLTQuNXYtMy43NWgtNi43NXYzLjc1em0wLTUuMjVWNy41aC02Ljc1djMuNzV6bTAtNS4yNVYzaC02Ljc1djNaIi8+PC9zdmc+)](https://github.com/HussainRiaz-sudo/Bike-Sales-Analysis)
[![Pivot Tables](https://img.shields.io/badge/Pivot_Tables-Data_Modeling-3A5A40?style=for-the-badge)](https://github.com/HussainRiaz-sudo/Bike-Sales-Analysis)
[![Feature Engineering](https://img.shields.io/badge/Feature_Engineering-IFS_Logic-52796F?style=for-the-badge)](https://github.com/HussainRiaz-sudo/Bike-Sales-Analysis)
[![Business Intelligence](https://img.shields.io/badge/Business_Intelligence-Interactive_Dashboard-2A9D8F?style=for-the-badge)](https://github.com/HussainRiaz-sudo/Bike-Sales-Analysis)
[![License: MIT](https://img.shields.io/badge/License-MIT-2D6A4F?style=for-the-badge)](./LICENSE)

---

## 📌 Executive Summary

This end-to-end data analytics project explores a retail dataset of **1,000 prospective customer profiles** across three continents (*North America, Europe, and the Pacific*) to uncover the demographic, economic, and geographic determinants that drive bicycle purchases.

The project demonstrates full-cycle data lifecycle management in **Microsoft Excel**: from establishing immutable raw-data safeguards and systematic data wrangling, to feature engineering using advanced logical functions (`IFS`), multi-dimensional Pivot Table modeling, and dynamic executive dashboard visualization with interactive Slicers.

```
┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│     bike_buyers         │ ──> │     Working Sheet       │ ──> │  Pivot Table & Slicers  │
│  (Raw Immutable Backup) │     │  (Cleaned & Engineered) │     │  (Interactive Dashboard)│
└─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘
```

---

## 🛡️ Data Architecture & Safety Protocols

A foundational principle of dependable data analytics is **preserving data integrity before applying irreversible transformations**:

1. **Immutable Raw Data Store (`bike_buyers`):** The original raw dataset was preserved in an isolated, read-only backup sheet. This guarantees full auditability and provides a zero-risk rollback path in the event of pipeline anomalies or corrupted calculations.
2. **Active Analytics Layer (`Working Sheet`):** All subsequent cleaning operations, deduplication routines, and feature-engineered columns were implemented in a dedicated working worksheet, leaving the original raw data completely uncompromised.

---

## 🧹 Data Cleaning & Preprocessing

The raw customer callout underwent structured auditing to resolve inconsistencies, formatting anomalies, and categorical ambiguities:

| Cleaning Task | Methodology & Transformation | Rationale |
| :--- | :--- | :--- |
| **Duplicate Resolution** | Evaluated 1,000+ entries across primary keys and demographic attributes; removed redundant customer rows. | Eliminates double-counting in pivot metrics and prevents skewed averages. |
| **Categorical Standardization** | Replaced abbreviated codes (`M` / `S` → `Married` / `Single`; `M` / `F` → `Male` / `Female`). | Enhances chart label legibility and prevents user confusion on stakeholder dashboards. |
| **Currency Formatting** | Formatted the `Income` field to standard USD currency format (`$#,##0`). | Ensures monetary figures are immediately readable and consistent across summaries. |
| **Data Type Enforcement** | Validated numeric fields (`Age`, `Children`, `Cars`) and verified text integrity across `Education`, `Occupation`, and `Region`. | Prevents aggregation errors and formula failures in downstream Pivot calculations. |

---

## ⚙️ Feature Engineering: Age Brackets via `=IFS()`

Continuous numerical age values introduce visual noise when mapped across charts. To transform continuous ages into actionable business segments, a new calculated attribute **`Age Brackets`** was engineered using the Excel `=IFS()` function:

```excel
=IFS(L2 < 31, "Young", L2 <= 49, "Middle Age", L2 >= 50, "Old Age")
```

### Segmentation Rationale:
- **`Young` (<31):** Early career entrants, students, and young adults with developing disposable income.
- **`Middle Age` (31–49):** Established workforce with stable income, family commitments, and peak commuting needs.
- **`Old Age` (50+):** Mature professionals and retirees with distinct recreation and leisure considerations.

---

## 🔍 Key Analytical Findings & Core Insights

### 1. Income Differential: Buyers Consistently Earn More
Across both genders, customers who purchased a bicycle demonstrated a systematically higher average income than non-buyers:

| Gender | Non-Buyers (Avg Income) | Buyers (Avg Income) | Percentage Lift |
| :--- | :---: | :---: | :---: |
| **Female** | \$53,440 | **\$55,774** | **+4.37%** |
| **Male** | \$56,208 | **\$60,124** | **+6.97%** |
| **Combined Total** | \$54,875 | **\$57,963** | **+5.63%** |

> 💡 **Takeaway:** Bicycle purchases correlate with higher purchasing power. Promotional campaigns should emphasize premium engineering, lifestyle convenience, and longevity over pure price discounting.

---

### 2. The Middle-Age Dominance (31–49)
The middle-age bracket represents the undisputed primary driver of the retail bicycle market:

```
Customer Distribution by Age Bracket:
Middle Age (31-49)  ██████████████████████████████  617 (61.7%)  ──>  324 Purchases (67.4% of total sales)
Old Age (50+)       ███████████████                 300 (30.0%)  ──>  122 Purchases (25.4% of total sales)
Young (<31)         ████                            83  (8.3%)   ──>   35 Purchases (7.2% of total sales)
```

- **Middle Age Customers:** Represent **61.7% of the total customer base** and generate **67.4% of all bicycle purchases** (52.51% within-bracket conversion rate).
- **Market Sizing:** Middle-age shoppers represent the primary volume and revenue foundation, making them the priority persona for marketing spend.

---

### 3. Commute Distance Threshold & Utility Curve
The likelihood of bicycle acquisition correlates strongly with daily commute distance:

| Commute Distance | Total Customers | Purchased: No | Purchased: Yes | Conversion Rate |
| :--- | :---: | :---: | :---: | :---: |
| **0–1 Miles** | 366 | 166 | 200 | **54.64%** |
| **1–2 Miles** | 169 | 92 | 77 | **45.56%** |
| **2–5 Miles** | 162 | 67 | 95 | **58.64%** *(Peak)* |
| **5–10 Miles** | 192 | 116 | 76 | **39.58%** |
| **More than 10 Miles** | 111 | 78 | 33 | **29.73%** *(Steep Drop)* |

> 🚲 **Utility Sweet Spot:** Conversion peaks between **2 and 5 miles (58.64%)** and **0 to 1 miles (54.64%)**. Beyond 10 miles, cycling utility drops sharply to under 30%, where automotive transit becomes the dominant modality.

---

### 4. Regional Variations
- **Pacific:** Led all regions with a **58.85%** purchase conversion rate.
- **Europe:** Balanced split with **49.33%** conversion.
- **North America:** Largest total addressable volume (508 customers) but the lowest conversion rate (**43.31%**), representing a major expansion opportunity.

---

## 📊 Interactive Excel Dashboard Architecture

The workbook contains an executive dashboard powered by synchronized Pivot Tables and dynamic chart components:

1. **KPI Visualizations:**
   - **Average Income by Gender & Purchase Status:** Clustered column chart illustrating the direct income gap between buyers and non-buyers.
   - **Customer Age Bracket Breakdown:** Visual bar comparison illustrating the overwhelming contribution of the 31–49 demographic.
   - **Customer Commute Distance Curve:** Trend line showing the steep conversion falloff beyond 5 miles.
2. **Interactive Multi-Filter Slicers:**
   - `Marital Status` (Married vs Single)
   - `Region` (Europe, North America, Pacific)
   - `Education` (Bachelors, Graduate Degree, High School, Partial College, Partial High School)
   - `Home Owner` (Homeowners vs Renters)

All slicers are cross-connected across all three pivot caches, enabling instant scenario analysis across specific demographic cuts.

---

## 💼 Actionable Business Recommendations

1. **Target the Middle-Age Segment (Ages 31–49):** Allocate the primary marketing budget toward 31–49 year-old working professionals. Highlight weekend family recreation, fitness benefits, and mid-range commute utility.
2. **Commuter Starter Bundles for 0–5 Mile Commuters:** Package commuter bicycles with essential urban accessories (helmets, bike locks, pannier bags, and lights) targeting individuals living within 5 miles of their workplace.
3. **E-Bike / Hybrid Strategy for Long Commutes (>10 Miles):** Traditional pedal bicycles experience severe adoption resistance past 10 miles (70.3% non-buyers). Introducing electric bicycles (e-bikes) with pedal assist can unlock this underserved commuter segment.
4. **North American Conversion Acceleration:** Because North America contains over 50% of prospective leads but lags in conversion (43.3%), implement targeted localized incentives, corporate wellness programs, and financing options.

---

## 📂 Repository Structure

```
Bike-Sales-Analysis/
├── 📄 Bike Sales Dashboard.xlsx   # Full Excel workbook (Raw data, Cleaned data, Pivot models, Dashboard)
├── 📄 LICENSE                     # MIT License
└── 📄 README.md                   # In-depth project documentation & analysis
```

---

## 🚀 How to View and Interact with the Dashboard

1. **Download the Workbook:** Download [`Bike Sales Dashboard.xlsx`](./Bike%20Sales%20Dashboard.xlsx) from this repository.
2. **Open in Microsoft Excel:** Launch the file in Excel 2016 or newer (or Microsoft 365) to ensure full Slicer and Pivot Chart functionality.
3. **Navigate to the `Dashboard` Tab:** Interact with the Slicers on the side to filter metrics by **Region**, **Marital Status**, and **Education Level** in real time.

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE) — free to use and reference for analytical and educational purposes.