---
name: compare-stocks
description: Compare two or more Indian stocks side by side with DocStoX data. Use when the user asks to compare companies (for example "TCS vs Infosys"), pick between stocks in a sector, or see how several NSE or BSE companies stack up on growth, profitability, valuation or ownership.
---

# Compare Indian stocks

Put two to ten companies side by side on the same measures, from the same data, as of the same date.

## 1. Resolve the symbols

Use NSE tickers. Resolve any company names with `search_stocks`. If the user named a sector instead of companies ("compare the big IT companies"), call `get_peer_comparison` on the best-known company in that sector and take the largest peers from its result, then confirm the list with the user if it is ambiguous.

## 2. Pull the numbers in batches

Batch tools take many symbols in one call. Use them instead of one call per company:

- `get_batch_fundamentals` with all the symbols: valuation, quality, growth and trend metrics
- `get_batch_financials` with all the symbols: revenue and profit trend, with `include_shareholding` set to true when ownership matters
- `get_batch_quotes` for prices and day change, when the user cares about recent price moves

For each company, `get_peer_comparison` adds the sector median, which tells you whether a figure is high or low for that industry.

## 3. Present a table, then the story

Start with one compact table, one row per company, with the measures that matter for the question. A sensible default set:

| Measure | Why it matters |
|---|---|
| Market cap (₹ crore) | Size |
| Revenue growth (YoY or 3-year) | Momentum of the business |
| Net profit margin | Profitability |
| ROE or ROCE | Return on capital |
| Debt to equity | Balance-sheet risk |
| P/E (and the sector median) | What the market pays |
| Promoter holding | Ownership |

Then explain, in a few sentences, where each company leads and lags, and what explains the differences (business mix, scale, cyclicality). Point out when a cheaper valuation comes with weaker growth or higher debt, so the comparison is fair.

Conventions: ₹ with Indian digit grouping, figures with their period (for example "FY26" or "June 2026 quarter"), and "not available" for missing values rather than estimates. Compare like with like: do not compare a bank's ratios with an IT company's.

Describe; never rank the stocks as buys or sells. End investment-related answers with:

> This is for informational purposes only and not investment advice. Please consult a SEBI-registered advisor before investing.
