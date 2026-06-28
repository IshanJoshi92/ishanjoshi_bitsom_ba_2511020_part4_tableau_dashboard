# Part 4 — Tableau Executive Dashboard & Data Storytelling

## 1. Business problem summary
A retail leadership team needs an **executive dashboard** to monitor sales, profitability, customer segments, category performance, shipping, discount impact, and returns — and to identify opportunities and risks. The dashboard tells one connected business story rather than presenting unrelated charts.

## 2. Dataset description
`data/dashboard_sales_data.xlsx` — 4,200 orders, 20 columns (sheet `dashboard_sales_data`; a `data_dictionary` sheet is included), covering Jan 2024–Dec 2025. Fields: order/ship dates, customer & segment, region/state/city, category/sub-category/product, ship mode, sales, quantity, discount, profit, return_flag, delivery_days, customer_rating, campaign_channel. Minor missing values: customer_rating (32), campaign_channel (24); no duplicates.

## 3. Tableau workbook description
`tableau/executive_dashboard.twbx` contains 7 worksheets (sales trend, regional performance, category profitability, customer segment, shipping performance, discount vs profit, return analysis) assembled into one executive dashboard with KPI cards, filters, and a filter action.

## 4. Calculated fields created
- **Profit Margin** = SUM([Profit]) / SUM([Sales])
- **Cost** = [Sales] − [Profit]
- **Average Order Value** = SUM([Sales]) / COUNTD([Order Id])
- **Return Rate** = SUM([Return Flag]) / COUNTD([Order Id])
- **Shipping Delay Bucket** = bins delivery_days into Fast (0–1) / Normal (2–3) / Slow (4–5) / Very Slow (6+)

## 5. Dashboard components
Title; KPI cards (Total Sales ₹217M, Total Profit ₹33M, Profit Margin 15.3%, AOV ₹51,671, Return Rate 4.5%); 7 chart views; layout ordered from summary → trend → category/region → diagnostics.

## 6. Filters and interactions used
Interactive filters for **Region, Category, and Customer Segment** (plus Date and Ship Mode as optional), shown as dashboard quick filters. A **filter action** lets clicking a region on the Regional Performance map filter every other view.

## 7. Key business insights
Technology delivers ~84% of profit; Furniture is low-margin (6.9%) and highest-return (7.7%); discounts above 30% are loss-making; South leads volume; Home Office returns most; Standard Class is the slowest mode. Full set in `outputs/business_insights.md`.

## 8. Dashboard story summary
The business is growing but **profit is concentrated in Technology**, while **Furniture and deep discounts erode value**. Priorities: defend Technology, fix Furniture economics, cap discounts. Full narrative in `outputs/dashboard_story.md`.

## 9. Assumptions and limitations
Dashboard shows **association, not causation**; minor missing values left as-is; no cost-to-serve/inventory/LTV data (returns proxied by rate); covers 2024–2025 only. Chart rationale in `outputs/chart_selection_justification.md`.

## 10. Screenshots

In `tableau/screenshots/`:
- `Full Dashboard.png` — complete executive dashboard (KPI row + all 7 chart views)
- `KPI Cards.png` — the 5 KPI cards (Sales, Profit, Margin, AOV, Return Rate)
- `Map Filter action.png` — clicking a region on the map filters every view
- `Category Filter.png` — category quick-filter interaction applied
- `Discount vs Profit.png` — discount-vs-profit scatter with trend + break-even line
