# Insight Memo — Northwind Sales Analysis

## TL;DR
- Concentration: Top‑10 customers drive ≈91% of revenue in the sample.
- Seasonality: revenue spikes in Mar–Apr, dips in May; AOV peaks in March (~$4,076).
- Action: prioritize Top‑10 retention and pre‑peak Coffee stock/promo to stabilize peaks and prevent lost sales.

## Business question
In one sentence: Where and when should we focus customers, inventory, and timing to maximize revenue and stability during seasonal peaks?

## KPIs & definitions
- Total Revenue = sum of `line_total` over the selected period.
- AOV (Average Order Value) = sum(`line_total`) ÷ count(distinct `OrderID`).
- Top‑N Share = revenue from Top‑N customers (or products) ÷ total revenue.

## Data & caveats
- Source: Northwind MySQL or the included processed CSVs (`data/processed/`); visual outputs in `figures/`.
- Date range: Jan–Jun 2006 (order‑line grain). Results will vary with different Northwind variants, but patterns are consistent.

## Method
- Tools: MySQL (views/queries), Python (Pandas/Matplotlib), Excel and Power BI for presentation.
- Steps: robust extract → tidy `order_lines.csv` → compute KPIs (monthly revenue, AOV, Top‑N customers/products) → charts and dashboard views.

## Findings
- Seasonality: revenue spikes in Mar–Apr, dips in May, partial recovery in June.  
  **So what:** staff and stock ahead of peaks; avoid over‑correction after the May dip.
- AOV: March is highest at ~$4,076.  
  **So what:** identify drivers (assortment/discounting) and replicate with bundles where viable.
- Concentration: Top‑10 customers ≈ 91% of revenue.  
  **So what:** focus retention/cross‑sell and proactive outreach to reduce volatility risk.
- Product mix: “Northwind Traders Coffee” leads at ~$29.9k.  
  **So what:** ensure availability and promo timing; pair with complementary products during peaks.

## Recommendation (owner, when, expected impact)
- Sales Ops + Merch to run Top‑10 outreach and pre‑peak Coffee stock/promo in the next cycle. Expected effect: stabilize peak‑month revenue and reduce lost sales.
- Add a light discount discipline review (vs. realized line value) this cycle. Expected effect: protect margin while maintaining volume.

## Risks / assumptions
- Six‑month window; analysis assumes seasonality persists over a full year.
- Snapshot excludes COGS/margin; discount review used as a proxy guardrail.
- Outcomes depend on execution (supply, staffing) and may vary by instance.

## Next steps
- Extend to 12–24 months; validate seasonality and refine peaks.
- Add COGS/margin to quantify profit impact and guardrails.
- Segment customers (e.g., RFM) and pilot targeted offers near peaks.

**Appendix**
- Power BI: `PowerBI/NorthWind PowerBI.pbix` (PDF: `PowerBI/NorthWind PowerBI.pdf`).
- Excel: `Excel/Excel northwind analysis.xlsx` (PDF: `Excel/Excel northwind analysis.pdf`).
- Notebook/Script: `northwind_analysis.ipynb`, `northwind_analysis.py`.
- SQL: `sql/` (e.g., `01_kpi_monthly_revenue.sql`, `02_kpi_aov_by_month.sql`).
- Data dictionary: `README.md` → Data Dictionary; sample CSVs in `data/processed/`.

*Note on numbers*: Metrics reflect the Jan–Jun 2006 snapshot included in this repo; running against a different instance will change figures but not the workflow.

