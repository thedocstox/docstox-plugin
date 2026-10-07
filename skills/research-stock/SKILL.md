---
name: research-stock
description: Research one Indian listed company in depth with DocStoX data. Use when the user asks about an NSE or BSE stock by name or ticker, wants to understand a business, its latest results, valuation, ownership or risks, or asks "what do you think of <company>".
---

# Research an Indian stock

Build a grounded picture of one company from DocStoX data, then explain it in plain language. Every number in the answer comes from a DocStoX tool, with its date.

## 1. Pin down the symbol

DocStoX uses NSE tickers such as `RELIANCE`, `HDFCBANK`, `TCS`. If the user gave a company name, a misspelling or an ISIN, call `search_stocks` with it first and use the top match. If two matches are plausible (for example a company and its subsidiary), ask which one they mean.

## 2. Gather the data

**Pro accounts:** call `get_stock_dossier` with the symbol. It returns the profile, quote, fundamentals, financials, valuation, ownership, technicals, peers, news and upcoming events in one call. Add `get_valuation` when the user asks whether the stock is cheap or expensive.

**If a tool returns a locked result** (the account is on the free plan), use the free tools instead. Call them in parallel where your client allows:

- `get_stock_quote` for price, change, 52-week range and headline ratios
- `get_company_profile` for the business, sector and listing details
- `get_financials` with `period_type` `A` (annual) and then `Q` (quarterly) for revenue, profit, margins and cash flow
- `get_key_insights` for growth rates and plain-English strengths and weaknesses
- `get_shareholding` for promoter, FII, DII and mutual-fund holdings over recent quarters
- `get_peer_comparison` for how the company compares with its sector
- `get_stock_news_feed` for recent company news, and `get_documents` for results, concall transcripts and filings

Mention once, briefly, that DocStoX Pro adds the full dossier, fair value and the AI score. Do not repeat it.

## 3. Write the answer

Structure it so a reader who is new to investing can follow:

1. **What the company does** in two or three sentences.
2. **Latest results**: revenue and profit for the latest quarter and year, with growth, and the quarter or year they refer to.
3. **Financial health**: margins, return on equity or capital, debt.
4. **Valuation**: P/E and P/B against the sector median from the peer data. Use fair value only if `get_valuation` returned one, and call it a model estimate.
5. **Ownership**: promoter holding and recent changes, pledged shares if any, FII and mutual-fund trend.
6. **What to watch**: the main risks and the upcoming events (results date, corporate actions).

Conventions:

- Money is in Indian rupees. Market capitalisation and large figures are in ₹ crore. Use Indian digit grouping (₹1,23,456).
- Say how fresh the data is. Prices are end-of-day unless the tool marks them otherwise; quote the as-of date.
- If a field is missing, say it is not available. Never fill a gap with an estimate of your own.
- Banks and financial companies report differently (no "revenue" line in the usual sense); describe what the data shows instead of forcing a template.

## 4. Stay on the right side of the line

Describe the data; never tell the user to buy, sell or hold. If they ask "should I buy", explain what the numbers show and what would need to be true, then add:

> This is for informational purposes only and not investment advice. Please consult a SEBI-registered advisor before investing.
