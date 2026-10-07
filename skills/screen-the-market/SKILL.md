---
name: screen-the-market
description: Find Indian stocks that match the user's criteria with DocStoX screens. Use when the user asks to find, filter or shortlist NSE or BSE companies (for example "mid-caps with ROE above 20% and low debt", "stocks near their 52-week low", "companies where promoters are buying"), or wants ideas within a theme or sector.
---

# Screen the Indian market

Turn the user's idea into explicit conditions, run them against every listed company, and explain why each result qualified.

## 1. Turn the idea into conditions

Restate the user's request as measurable conditions before running anything, for example: "market cap category Mid, ROE at least 20%, debt to equity at most 0.5, P/E at most 30". If a word is vague ("good", "cheap", "growing"), pick a reasonable threshold, say which one you picked, and invite the user to change it.

## 2. Run the screen

**Common filters:** call `screen_stocks`. It takes named filters such as `min_roe`, `max_debt_equity`, `max_pe`, `min_revenue_yoy_pct`, `min_pat_yoy_pct`, `market_cap_cat` (Large, Mid, Small, Micro), `sector`, `near_52w_low`, `new_52w_high`, `max_promoter_pledged`, plus `sort_by`, `sort_dir` and `limit`.

**Anything else:** call `list_screener_metrics` with a `search` word to find the metric ids, then `screen_advanced` with a `filters` tree that combines conditions with `all`, `any` and `not`, and `sort_by` on one or more metrics. Use this for ideas the named filters cannot express, such as a company that swung from a loss to a profit, or promoters increasing their stake.

**If the screening tools return a locked result** (free plan), say that market-wide screening is part of DocStoX Pro, then offer what the free tools can do:

- `get_themes` and `get_theme_members` to browse thematic baskets (for example defence or EV)
- `get_trending_stocks` and `market_heatmap` for today's movers and an index's constituents
- `get_peer_comparison` to list companies in one sector, then `get_batch_fundamentals` to check them against the user's conditions yourself

## 3. Present the results

- Say how many companies matched and repeat the conditions that were applied, exactly as the tool echoed them.
- Show a table of the top results with the metrics that made each one qualify.
- If nothing matched, say which condition was most restrictive and suggest relaxing that one. Do not loosen conditions silently.
- Mention notable gaps: a company with no data for a condition cannot pass it.

A screen narrows the market; it does not say any result is a good investment. Never present results as recommendations. End with:

> This is for informational purposes only and not investment advice. Please consult a SEBI-registered advisor before investing.
