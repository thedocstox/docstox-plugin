---
name: market-brief
description: Summarise the Indian stock market with DocStoX data. Use when the user asks how the market did today, what moved, what FIIs and DIIs are doing, what to watch tomorrow, or for a morning or evening market brief covering Nifty, Sensex, sectors, flows, commodities and news.
---

# Indian market brief

Give a short, dated summary of the Indian market from DocStoX data.

## 1. Gather

Call these in parallel where your client allows:

- `get_market_brief` for DocStoX's own brief of the session and the current market-regime read
- `get_fii_dii_detail` for foreign and domestic institutional flows, with streaks
- `get_global_markets` for GIFT Nifty, global indices, crude, gold, silver and the rupee
- `get_trending_stocks` for the top gainers and losers
- `get_news_movers` for high-impact news joined to the stocks' actual price reaction
- `get_earnings_calendar` for results due in the next few days

`get_market_pulse` adds breadth and index valuations; it can take longer to respond than the others, so call it only when the user asks about breadth or valuation.

## 2. Write the brief

Keep it scannable, in this order:

1. **The session in one line**: how Nifty 50 and Sensex closed, with the date.
2. **Breadth and sectors**: what led and what lagged.
3. **Flows**: FII and DII net buying or selling in ₹ crore, and any streak.
4. **Movers**: the biggest gainers and losers, with the news behind them where DocStoX links one.
5. **Global and commodities**: GIFT Nifty's signal for the next open, crude, gold and the rupee, each with its unit.
6. **Coming up**: notable results and events.

Every figure carries its unit and date. Commodity prices from MCX are futures prices in rupees (gold per 10 g, silver per kg, crude per barrel) and differ from global prices in US dollars per ounce or barrel; do not compare them without converting.

Describe what happened; do not forecast prices or suggest trades. End with:

> This is for informational purposes only and not investment advice. Please consult a SEBI-registered advisor before investing.
