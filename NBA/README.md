# NBA Statistical Analysis

Analysis of NBA data across 11 seasons (2015-16 to 2025-26), covering web scraping, database design, exploratory data analysis and hypothesis testing.

---

## What this project does

- Scrapes player, team and award data from [basketball-reference.com](https://www.basketball-reference.com)
- Stores everything in a normalized MySQL database
- Answers four analytical questions about player performance, team composition and the direction of the league

---
## Collaboration

The EDA and analysis notebook was built in collaboration with [bahramzarean](https://github.com/bahramzarean) as part of the same bootcamp project group.

Full group repository: [QBC-Group3-EDA-NBA-Analysis](https://github.com/bahramzarean/QBC-Group3-EDA-NBA-Analysis)

---

## Project structure

```
├── NBA_Scraping.ipynb        web scraping (basketball-reference.com)
├── Data_Cleaning.ipynb       cleaning and transforming the raw CSVs
├── Build_Database.ipynb      loading cleaned data into MySQL
├── NBA_EDA_Analysis.ipynb    EDA, hypothesis tests, regression and recommendation
├── schema.sql                database structure
├── queries.sql               analytical SQL queries
└── cleaned/                  output of the cleaning notebook
```

---

## Analysis

### Hypotheses tested

| # | Question | Test | Result |
|---|---|---|---|
| 1 | Has the BMI of the top 20 players increased? | Mann-Whitney U (one-tailed) | Not rejected · p = 0.565 |
| 2 | Has the innate ability index of champion teams increased? | Mann-Whitney U (one-tailed) | Not rejected · p = 0.366 |
| 3 | Are champion team players older than the rest of the league? | Mann-Whitney U (one-tailed) | **Rejected · p = 0.0002** |
| 4 | Does position affect MVP list appearances? | Chi-square | **Rejected · p < 0.05** |

### Other findings
- Three-point attempt share grew from ~28% in 2016 to ~40% in 2026
- Linear regression predicts PER from box score stats with R² = 0.926
- Point guard recommendation: **Luka Dončić**, Stephen Curry, Shai Gilgeous-Alexander

---

## Database

11 tables across three layers:

- **Base:** `players` · `teams` · `seasons` · `coaches`
- **Seasonal:** `player_season_stats` · `team_stats` · `team_coaches`
- **Analytical:** `player_playoff_stats` · `player_advanced_stats` · `league_stats`

---

## How to run

```bash
pip install requests beautifulsoup4 pandas sqlalchemy pymysql
```

Run the notebooks in order:

1. `NBA_Scraping.ipynb` — scrapes all data (~40 min)
2. `Data_Cleaning.ipynb` — cleans and standardizes the CSVs
3. `Build_Database.ipynb` — creates and fills the MySQL database
4. `NBA_EDA_Analysis.ipynb` — the full analysis

---



---

## Tools

Python · BeautifulSoup · Pandas · MySQL · SQLAlchemy · SciPy · Scikit-learn · Plotly · Seaborn
