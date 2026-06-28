# Chart Selection Justification

For each major view: the question it answers, why the chart type fits, the field used for colour/size/label/filter, the design principle applied, and the mistake avoided.

## 1. Sales Trend view — Line chart
- **Question:** How are sales changing over time?
- **Why this chart:** A line chart is the standard for a continuous time series; it shows direction, momentum, and seasonality at a glance.
- **Colour/size/label/filter:** Single indigo line; MONTH(order_date) on Columns, SUM(Sales) on Rows; labelled at peak/last point; responds to all dashboard filters.
- **Design principle:** Show change over time clearly; continuous axis, no broken scale.
- **Mistake avoided:** Not a pie or bar — those hide trend and seasonality.

## 2. Regional Performance view — Filled map (+ bar fallback)
- **Question:** Which region/state performs best?
- **Why this chart:** Geographic data is read fastest on a map; a sorted bar is the accessible fallback.
- **Colour/size/label/filter:** Colour = Profit Margin (diverging), label = SUM(Sales); state geography drives location. Clicking a region acts as the dashboard filter.
- **Design principle:** Encode the business metric (margin) on colour, not decoration; sort bars by value.
- **Mistake avoided:** Not colouring by raw sales alone (which hides that all regions share ~15% margin).

## 3. Category Profitability view — Bar chart (by category & sub-category)
- **Question:** Which categories drive profit or losses?
- **Why this chart:** Bars compare magnitudes precisely across a small set of categories/sub-categories.
- **Colour/size/label/filter:** Length = Profit; Colour = Profit Margin (diverging) so low-margin Furniture stands out; sorted descending.
- **Design principle:** Sort by value; use colour to separate "high sales" from "high margin".
- **Mistake avoided:** Not a treemap-only view, which makes Furniture's thin margin hard to read against its large area.

## 4. Customer Segment view — Bar chart
- **Question:** How does performance compare across customer segments?
- **Why this chart:** Three segments compared on sales/profit/return rate — bars are clearest.
- **Colour/size/label/filter:** Sales/Profit bars per segment; Return Rate shown alongside to expose Home Office's higher returns.
- **Design principle:** Pair a volume metric with a quality metric to avoid a misleading "biggest = best" read.
- **Mistake avoided:** Not showing sales alone (which would flatter Home Office despite its returns).

## 5. Discount vs Profit view — Scatter plot
- **Question:** How does discount relate to profit?
- **Why this chart:** A scatter reveals the relationship and the loss-making tail directly; a trend line summarises direction.
- **Colour/size/label/filter:** Discount on X, Profit on Y, coloured by category; reference line at profit = 0.
- **Design principle:** Use the right chart for correlation; add a zero line for business meaning.
- **Mistake avoided:** Not a bar of average profit by discount band only — the scatter shows spread and the negative tail.

## 6. Shipping Performance view — Bar/dual-axis
- **Question:** Which shipping mode is slow and does it affect returns?
- **Why this chart:** Bars compare delivery days and sales across four modes; return rate overlaid.
- **Colour/size/label/filter:** Ship mode on rows; avg Delivery Days and SUM(Sales); Return Rate as label/colour.
- **Design principle:** Consistent colour; sort by the metric in focus.
- **Mistake avoided:** Not implying delivery delay causes returns — shown as association.

## 7. Return Analysis view — Bar (highlight table)
- **Question:** Which categories/segments/regions have higher return risk?
- **Why this chart:** A sorted bar or highlight table makes the Furniture / Home Office hotspots obvious.
- **Colour/size/label/filter:** Return Rate by category & segment; colour intensity = return rate.
- **Design principle:** Sequential colour for a rate; sort to surface the worst.
- **Mistake avoided:** Not using counts (which track volume); a **rate** isolates true return risk.

## Global design choices
- **Consistent palette:** deep indigo `#1C2E5B` for primary marks, sun-gold `#F4D58D` for highlights/KPIs, terracotta `#C0603A` for negative/loss and high-return. Used identically across every view.
- **Hierarchy:** title → KPI cards → trend → category/region → diagnostics (discount, shipping, returns).
- **Minimal clutter:** no 3-D, no redundant gridlines, labels only where they aid reading.
