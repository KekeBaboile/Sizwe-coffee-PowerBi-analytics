
# Sizwe Coffee | Power BI Commercial & Receivables Analytics

An enterprise-grade commercial performance and accounts receivable analytics solution built in Power BI Desktop for Sizwe Coffee, a South African B2B coffee supplier.

This project transforms fragmented operational datasets into a unified, interactive 4-page executive report supported by a star schema data model and 20 DAX measures reconciling directly to the official R921,000,020.82 commercial control total.



## Business Context & Objective

Prior to this solution, executive leadership (Financial Director and National Sales Manager) relied on manual, disconnected spreadsheet reporting. This project establishes an automated decision-support system to monitor:
* Commercial Performance: Revenue, Gross Margin %, Order Volumes, and Average Order Value (AOV).
* Territory and Rep Output: Target attainment, regional market share, and field sales performance across 18 account reps.
* Cash Flow and Receivables: Invoiced sales, cash settlements, debtor aging balances, and collection friction (Days to Settle).
* Product and Trade Promotions: SKU-level margin contributions and promotional discount effectiveness.


## Data Model Architecture (Star Schema)

The underlying semantic model is built in Import Mode (VertiPaq in-memory storage) using single-direction 1-to-Many (1:*) relationships to ensure predictable evaluation contexts.

### Model Entities
* Fact Tables:
  * sizwe_sales_orders & sizwe_sales_lines — Commercial transactions at order and line-item grain.
  * sizwe_ar_ledger — Invoicing, cash receipts, and debtor balances.
  * sizwe_rep_visits — Field representative activity logs.
* Conformed Dimensions:
  * sizwe_customers — 1,400 B2B trading accounts across South African provinces.
  * sizwe_products — 23 coffee SKUs, categories, unit costs, and retail prices.
  * sizwe_reps — 18 sales representatives and monthly quotas.
  * sizwe_trade_promotions — Active promotional mechanics and discount structures.
  * Dim_Date — Contiguous calendar dimension with South African financial year logic (July–June).

### Grain Mismatch Resolution (Invoice-to-Order)
To avoid circular relationships and many-to-many join distortion between sales lines and AR ledger invoices, the direct join was intentionally disconnected. Both fact tables link independently to shared conformed dimensions (sizwe_customers via Customer_ID and Dim_Date via transaction dates), allowing full cross-filtering while preserving exact financial reconciliation.



## Key Commercial Results & Control Totals

* Total Invoiced Sales Revenue: R921,000,020.82
* Gross Margin: 33.81% (R311,387,907.30)
* Total Cash Settled: R832,400,000.00
* Open Accounts Receivable: R88,600,020.82
* Order Conversion: 3,000 total orders across 1,400 customer accounts.



## Dashboard Structure (4 Interactive Pages)

1. Page 1 — Commercial Overview: High-level financial executive summary, annual revenue trajectories, product line contributions, and regional filters.
2. Page 2 — Regional & Rep Performance: Sales representative target attainment, territory revenue distribution, and rep ranking tables.
3. Page 3 — Receivables & Debtors: Cash collection monitoring, top debtor account rankings, payment terms analysis, and open ledger balances.
4. Page 4 — Product & Promotions: SKU profitability analysis, brand performance, and promotional discount tracking.



