# Collab Drop Analytics

Analyzing influencer collection launches ("drops") for a fictional online fashion brand.

**Status:** in progress. Dataset ready, analysis being built Nov to Dec 2026.

## Business problem

Fashion brands launch limited collections designed with influencers. Each drop has a fixed buy, a short launch window, and marketing driven largely by the talent's own posts. The questions that matter: which drops and styles sell through fastest, what drives the difference, and where stock is at risk while there's still time to act.

## Questions this project answers

1. How did each drop perform at Day 1, Day 7, Day 30 and Day 60 on sell-through (STR) and revenue?
2. Which styles and categories lead and lag within a drop?
3. How do talent tier, repeat partnerships, season and launch events relate to sell-through?
4. What happens to styles delivered after launch day?
5. Do talent posts line up with sales spikes, and does that differ by post format? (Correlation, not causation.)
6. When is discounting used, and what does it do to sales pace and revenue?
7. If a drop were live today, what should marketing focus on in Week 2?

## Data

Synthetic data for a fictional brand: invented talents, styles and numbers. No real company data is used.

| Table | Rows | What it holds |
| --- | --- | --- |
| `drops.csv` | 12 | One row per collab drop: talent tier, followers, repeat partner, season, launch date, launch event |
| `styles.csv` | 158 | One row per style: category, color, price, units received, delivery date |
| `daily_sales.csv` | ~9,500 | One row per style per day for 60 days after launch: units sold, price, discount, revenue, returns |
| `talent_posts.csv` | 135 | One row per talent post: date, format, reach |

Period: Feb 2025 to Mar 2026. The data contains **deliberate data quality issues** to find and clean. See [data_dictionary.md](data_dictionary.md).

## Method (planned)

- **Cleaning and analysis:** SQL in Google BigQuery
- **Metrics:** sell-through rate (STR), daily sales pace, revenue, discount depth, return rate (from Day 30, when returns arrive)
- **Dashboard:** Tableau Public (link coming)
- **Summary:** a one-page findings report with limitations

## Structure

```
collab-drop-analytics/
├── README.md
├── data_dictionary.md
├── data/        raw CSVs
├── sql/         exploration, cleaning and analysis queries
└── reports/     findings and executive summary
```

## About

Built by Natalie Giorgalletou as part of a data analytics portfolio. The project mirrors the kind of launch analysis I do in e-commerce, rebuilt on synthetic data. The dataset was generated with Python with AI assistance. The SQL, analysis and conclusions are my own.
