# Data dictionary

All data is synthetic. Currency is SEK. Dates are ISO format (YYYY-MM-DD).

## drops.csv (one row per drop)

| Column | Type | Description |
| --- | --- | --- |
| drop_id | string | Unique drop ID (primary key), e.g. D01 |
| talent_id | string | Unique talent ID |
| talent_name | string | Fictional talent name |
| talent_tier | string | micro, mid or macro, by follower count |
| followers | integer | Talent's follower count at launch |
| is_repeat_partner | integer | 1 if the talent had a previous collab with the brand, else 0 |
| season | string | SS (spring/summer) or AW (autumn/winter) |
| launch_date | date | Launch day (Day 1) |
| has_launch_event | integer | 1 if there was a launch event, else 0 |

## styles.csv (one row per style)

| Column | Type | Description |
| --- | --- | --- |
| style_id | string | Unique style ID (primary key), e.g. S0001 |
| drop_id | string | Drop the style belongs to (foreign key to drops) |
| style_name | string | Product name |
| category | string | Dresses, Tops, Knitwear, Tailoring, Outerwear, Denim or Accessories |
| color | string | Color name |
| retail_price_sek | integer | Full retail price |
| units_received | integer | Units bought and delivered for the drop |
| delivery_date | date | When the stock arrived. Can be after launch_date (late delivery) |

## daily_sales.csv (one row per style per day, Days 1 to 60)

| Column | Type | Description |
| --- | --- | --- |
| date | date | Calendar date |
| drop_id | string | Foreign key to drops |
| style_id | string | Foreign key to styles |
| day_since_launch | integer | 1 = launch day |
| units_sold | integer | Units sold that day (gross, before returns) |
| discount_pct | integer | Discount applied that day, 0 if full price |
| unit_price_sek | decimal | Price paid per unit after discount |
| revenue_sek | decimal | units_sold x unit_price_sek |
| units_returned | integer | Units returned that day. Returns arrive from Day 30 onward |

## talent_posts.csv (one row per post)

| Column | Type | Description |
| --- | --- | --- |
| post_id | string | Unique post ID (primary key) |
| drop_id | string | Foreign key to drops |
| post_date | date | Date of the post |
| format | string | story, reel, feed or tiktok |
| reach | integer | Accounts reached |

## Known issues

This dataset intentionally contains data quality problems (duplicates, gaps, formatting and value errors) to practice cleaning. Findings and fixes are documented in `sql/02_cleaning.sql` as the project progresses.
