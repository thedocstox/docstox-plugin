---
name: review-portfolio
description: Review the user's own DocStoX portfolio or watchlist. Use when the user asks how their portfolio or holdings are doing, what moved today, how concentrated they are, what news affects their stocks, or wants a check-up of their watchlist.
---

# Review my portfolio

Read the signed-in user's own holdings from DocStoX and give a clear, factual check-up.

## 1. Load the holdings

Call `get_user_portfolio` (no arguments). It returns the user's real holdings: quantity, average cost, latest price, value and profit or loss. For a watchlist, call `get_user_watchlist`; if the user has several watchlists, the result lists them, so ask which one or pass its `watchlist_id`.

If the result says there is no signed-in user, the connector is not connected to a DocStoX account: ask the user to connect it (sign in at docstox.com) and try again. If the portfolio is empty, say so and point them to docstox.com/portfolio, where they can add holdings or import a broker statement.

## 2. Enrich it

Take the list of symbols and, in parallel:

- `get_batch_quotes` for today's moves
- `get_batch_fundamentals` for valuation, quality and growth of each holding
- `get_batch_news` for recent news on the holdings
- `get_earnings_calendar` (per symbol, or with no symbol for the market-wide list) for results due soon

## 3. Write the check-up

1. **Snapshot**: total value, today's change and total profit or loss, in ₹ with Indian digit grouping, with the price date.
2. **Today's biggest moves** among the holdings, and any news that explains them.
3. **Concentration**: the largest holdings by weight and the sector mix. Point out when one stock or one sector is a large share of the total.
4. **Quality and valuation at a glance**: holdings with weak profitability, high debt or a stretched valuation versus their sector, described factually.
5. **Coming up**: results dates and corporate actions for the holdings.

Never tell the user to buy, sell, add or trim a position. Describe what the data shows and what they may want to look into. End with:

> This is for informational purposes only and not investment advice. Please consult a SEBI-registered advisor before investing.

The portfolio is private to the user. Do not repeat its contents outside this conversation.
