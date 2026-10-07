# DocStoX for Claude and ChatGPT

Research Indian stocks with your AI assistant, using real NSE and BSE data instead of the model's memory.

DocStoX is an equity research platform covering every actively traded company on the National Stock Exchange and the Bombay Stock Exchange. This plugin connects your assistant to the DocStoX connector (a remote MCP server) and adds skills that teach it how to research Indian stocks well: which data to pull, in what order, and how to present it with units, dates and plain-English explanations.

![DocStoX stock card in a conversation](assets/screenshot-1-stock-card.png)

## What you can do

- **Research a company**: business, latest quarterly and annual results, margins, debt, valuation against its sector, promoter and institutional ownership, risks and upcoming events.
- **Compare stocks**: put TCS, Infosys and HCL Tech (or any set of companies) side by side on growth, profitability, valuation and ownership.
- **Screen the market**: find companies that match your conditions, such as mid-caps with ROE above 20% and low debt, and see why each one qualified.
- **Review your portfolio**: a check-up of your own DocStoX holdings or watchlist: today's moves, concentration, news and results due.
- **Get a market brief**: Nifty and Sensex, sectors, FII and DII flows, top movers with the news behind them, GIFT Nifty, crude, gold and the rupee.

In apps that support interactive views, stock quotes, screens and your portfolio also appear as charts and tables inside the conversation.

## Example prompts

- "Research HDFC Bank: what it does, latest results, valuation and key risks."
- "Compare TCS, Infosys and HCL Tech on revenue growth, margins, ROE and valuation."
- "Find Indian mid-caps with ROE above 20%, debt to equity below 0.5 and P/E under 30."
- "How is my DocStoX portfolio doing today?"
- "Give me today's Indian market brief."

## Install

The DocStoX server is `https://mcp.docstox.com/mcp` (streamable HTTP). Any app or tool that supports remote MCP servers can use it. When you connect, you are sent to docstox.com to sign in with Google or with your DocStoX email and password, then asked to allow read-only access. A free account is created if you do not have one. Apps that cannot open a browser sign-in can use a personal API key from https://docstox.com/mcp/keys, sent as `Authorization: Bearer dox-...`.

### AI assistants

- **Claude (claude.ai, Claude Desktop, Cowork):** add DocStoX from the Claude directory, or upload this plugin under **Customize > Plugins > Add**, then connect DocStoX on the plugin's **Connectors** tab.
- **ChatGPT:** add DocStoX from the ChatGPT apps directory, or follow the steps at https://docstox.com/mcp.
- **Perplexity** (Pro, Max, Enterprise): **Settings > Connectors > Custom connector > Remote**, URL `https://mcp.docstox.com/mcp`, sign in with OAuth.
- **Mistral Le Chat:** **Connectors > Add connector > Custom MCP**, URL `https://mcp.docstox.com/mcp`, authentication with an API key (`Authorization: Bearer dox-...`).
- **Manus:** **Settings > Connectors > Custom MCP**, URL `https://mcp.docstox.com/mcp`, header `Authorization: Bearer dox-...`.

### Coding tools and agents

**Claude Code:**

```bash
/plugin marketplace add thedocstox/docstox-plugin
/plugin install docstox@docstox
```

**Codex:** **Customize > Plugins > Add > Add plugin marketplace**, source `thedocstox/docstox-plugin`, ref `main`.

**VS Code / GitHub Copilot:** [Install in VS Code](https://vscode.dev/redirect/mcp/install?name=docstox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//mcp.docstox.com/mcp%22%7D) · [Install in VS Code Insiders](https://insiders.vscode.dev/redirect/mcp/install?name=docstox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//mcp.docstox.com/mcp%22%7D&quality=insiders)

**Kiro:** [Add to Kiro](https://kiro.dev/launch/mcp/add?name=docstox&config=%7B%22url%22%3A%22https%3A//mcp.docstox.com/mcp%22%2C%22disabled%22%3Afalse%2C%22autoApprove%22%3A%5B%5D%7D)

**Gemini CLI:**

```bash
gemini extensions install https://github.com/thedocstox/docstox-plugin
```

**Cursor:** open this link in your browser, or add the JSON below to `~/.cursor/mcp.json`:

```text
cursor://anysphere.cursor-deeplink/mcp/install?name=docstox&config=eyJ1cmwiOiJodHRwczovL21jcC5kb2NzdG94LmNvbS9tY3AifQ%3D%3D
```

**Cline, Windsurf, Goose, LM Studio, Zed, OpenCode and other clients:** add this to the client's MCP settings (field names vary slightly: `url`, `serverUrl` or `httpUrl`):

```json
{
  "mcpServers": {
    "docstox": { "url": "https://mcp.docstox.com/mcp" }
  }
}
```

Step-by-step guides for every client: https://docstox.com/docs/connect-your-ai/connect-coding-tools

## Plans and limits

A free DocStoX account includes 50 tool calls a day (1,000 per rolling 30 days) and covers prices, financials, ownership, news, market data and your own portfolio. DocStoX Pro raises the limit to 5,000 calls a day and adds research tools such as the full stock dossier, fair value, the AI score, market-wide screens and options analytics. The skills fall back to free tools when a Pro tool is not available on your plan. See https://docstox.com/pricing.

## Data and privacy

- **What the plugin contains:** skills (Markdown instructions) and a reference to one remote server, `https://mcp.docstox.com/mcp`. It runs no code on your computer and stores nothing itself.
- **What is sent:** when your assistant uses DocStoX, it sends the tool name and its inputs (for example a stock symbol or screening conditions) to `mcp.docstox.com`, authenticated with your DocStoX sign-in. Your conversation, other chats, files and memory are not sent.
- **What DocStoX records:** usage per account (which tool, when, and whether it succeeded) to apply your plan's limits and show you your usage at https://docstox.com/mcp/keys. You can revoke a connected app there at any time.
- **Read-only:** every DocStoX tool reads data. The plugin cannot place trades, move money, or change your portfolio, watchlist or account.

Full policy: https://docstox.com/privacy. Terms: https://docstox.com/terms.

## Disclaimer

DocStoX provides market data and research tools for information only. Nothing produced with this plugin is investment advice. Please consult a SEBI-registered advisor before investing.

## Support

Documentation: https://docstox.com/docs/connect-your-ai/mcp-overview
Email: support@docstox.com

## License

The contents of this repository (skills, manifests and documentation) are released under the MIT License. Use of the DocStoX service is governed by the DocStoX terms at https://docstox.com/terms.
