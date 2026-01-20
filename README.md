# 🦢 Swansea City FC – Performance Dashboard (Power BI)

An interactive **Power BI dashboard** that analyses Swansea City FC performance across multiple seasons using match logs and player stats.  
This project focuses on **clean data modeling (star schema)**, **Power Query transformations**, and **DAX measures** to deliver clear, filterable insights.

---

## 📌 What This Dashboard Shows
<img width="2190" height="1232" alt="Swansea City Thumbnail" src="https://github.com/user-attachments/assets/68162a5a-b71e-438b-857e-93cb6fecfb94" />

### ✅ High-Level KPIs
- Matches Played
- Win %
- Goals Scored
- Goals Conceded
- Goal Difference
- Seasons Covered

### ✅ Visuals & Analysis
- Win Percentage by Season/Year
- Top 5 Goalscorers (dynamic)
- Attendance by Day of Week
- Player table (minutes, goal contributions, yellow/red cards)
- Season slicer (filters all visuals)

---

## 📁 Data Sources

Data was collected and structured from:
- Match logs (Results, GF/GA, opponent, attendance, possession, formations)
- Player season stats (goals, assists, minutes, cards, xG/xAG where available)

> **Note:** Data is stored in Excel and loaded into Power BI.

---

## 🧱 Data Model (Star Schema)

### Tables
- **DimMatchesSeason** (Fact)
  - Match-level records: `Date`, `Result`, `GF`, `GA`, `Opponent`, `Attendance`, `Possession`, etc.
- **DimPlayersSeason** (Fact-like aggregate by season)
  - Player-season stats: `Player`, `Season`, `Goals`, `Assists`, `Minutes`, `Yellow Cards`, `Red Cards`, etc.
- **DimSeason** (Dimension)
  - One row per season (unique key): `2023/24`, `2024/25`, `2025/26`

### Relationships (Required)
```text
DimSeason[Season] 1 ──── * DimMatchesSeason[Season]
DimSeason[Season] 1 ──── * DimPlayersSeason[Season]
