# US Job Market Analysis - LinkedIn 2023-2024

What does the US job market look like across 123,000+ LinkedIn postings?
This project analyzes skill demand, salary distribution, geographic patterns,
and remote work premiums using SQL, Python, and Tableau.

---

## Key Findings

| Finding | Value |
|---|---|
| Total postings analyzed | 123,849 |
| Most in-demand skill | Information Technology (12.2% of all jobs) |
| Highest-paying skill | Product Management (avg 145,857/yr) |
| Remote premium at Entry level | +43% vs market average |
| Highest-salary state | CA (avg 106,448/yr) |
| Most competitive level | Entry level (78.3% apply rate) |

---

## Project Structure

    linkedin-job-market/
    ├── linkedin_job_market_analysis.ipynb
    ├── jobs.db
    ├── outputs/
    │   ├── 01_skill_demand.png
    │   ├── 02_salary_by_experience.png
    │   ├── 03_remote_premium.png
    │   ├── 04_state_analysis.png
    │   └── 05_salary_by_skill.png
    └── README.md

---

## Data Source

LinkedIn Job Postings 2023-2024
https://www.kaggle.com/datasets/arshkon/linkedin-job-postings

6 CSV files merged into SQLite with 5 tables:
postings (123k rows), job_skills (213k rows),
skills, companies, industries.

---

## Methodology

### 1. Extract and Clean

- Fixed salary normalization errors: HOURLY values incorrectly
  annualized in source data, reversed and re-converted
  (hourly x 2080, monthly x 12, weekly x 52)
- Applied Winsorization: hourly capped at 200/h,
  annual capped at 500k/yr to remove data entry errors
- Valid salary records after cleaning: 35,538 (28.7%)

### 2. SQL Analysis (SQLite)

Advanced queries using CTEs and window functions:

- Skill demand ranking with market share percentage
- Salary by skill using CTE + RANK window function
- State supply-demand with dual salary and volume ranking
- Experience level progression using LAG function
- Remote vs market average salary comparison

SQL features demonstrated: CTEs, RANK(), LAG(), SUM() OVER(),
CASE WHEN, HAVING, NULLIF, multi-table JOINs

### 3. Visualize

5 Python charts (Matplotlib) + Tableau Public dashboard

#### Dashboard
Tableau Public: https://public.tableau.com/app/profile/zifei.luo/viz/USJobMarketAnalysis-LinkedIn2023-2024/Dashboard2

---

## Key Insights

Skill demand: Top 8 skills cover 67.8% of the market.
IT alone appears in 12.2% of all postings.

Remote premium: Remote roles pay 7-43% more than market
average across all experience levels. Entry level shows
the largest gap at +43%.

Geographic: CA leads in volume (11,484 jobs, avg 106k/yr).
WA offers the best salary-to-volume ratio among top states
(avg 103k/yr, 2,708 jobs).

Competition: Entry level has the highest apply rate (78.3%)
despite the lowest salary - most crowded tier to break into.
Executive roles have only 32.6% apply rate.

---

## Limitations

- Salary data available for only 28.7% of postings
- remote_allowed field only flags confirmed remote roles;
  absence does not confirm on-site
- Skills taxonomy uses 35 broad categories; granular skills
  such as Python or SQL are not captured separately
- Data covers 2023-2024; current market conditions may differ

---

## Skills Demonstrated

Python - Pandas - SQLite - SQL - ETL Pipeline -
Data Cleaning - Winsorization - Matplotlib - Tableau
