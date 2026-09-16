# Connections registry

The agent may contact only services with status `approved`, and send them only the data listed. Statuses are `proposed`, `approved`, `suspended` and `removed`. Never delete a row. Change its status instead.

## APIs

| Name | Purpose | Base URL | Account type | Data sent | Secrets in .env | Retention terms | Status | Since |
|---|---|---|---|---|---|---|---|---|
| MetaTrader 5 (Swissquote) | Read account balance, positions, orders and market data from the locally installed MT5 terminal, via MetaQuotes' official `MetaTrader5` Python package. Later, in `paper` mode only: place/modify/cancel orders on the demo account (never live, without a `CONFIRM <ticket id>` per the hard rules). | None — local IPC to the installed terminal (`C:\Program Files\Swissquote Bank MT5 Client Terminal\terminal64.exe`), not a network API. The terminal itself talks to Swissquote's servers as normal MT5 traffic, outside the agent's control. | Demo/paper to start, owner's Swissquote account | Nothing leaves this machine through the agent directly — the Python package calls the local terminal process in-process/IPC. Data read: balance, positions, open orders, historical/live quotes. Data written (paper mode only): order placement/modification/cancellation on the demo account. | MT5 account login (account number), password and server name, needed for the package's `login()` call | N/A — local terminal connection, not a third-party hosted data API. Swissquote's own account terms apply to the broker relationship itself. | approved | 2026-09-16T06:17:41Z |

**Notes:** Tested 2026-09-16 — connected read-only, confirmed DEMO mode, server `Swissquote-Server`, broker Swissquote Bank SA. Automated API login (`mt5.login()` / `mt5.initialize()` with credentials) fails with `[-6] Authorization failed` even with correct credentials; the working path is attaching to an already-running, manually-logged-in terminal (`mt5.initialize(path=...)` with no login args). See `context/connections/apis/metatrader5-swissquote/README.md` for detail. Practical effect: the MT5 terminal must be open and logged in by the owner before the agent can read this account.

## MCP servers

| Name | Purpose | Runs where | Data sent | Secrets in .env | Status | Since |
|---|---|---|---|---|---|---|
| TradingView | Market data (quotes, OHLCV bars, economic indicators), symbol search, screener, news, fundamentals/forecasts, SEC filings/transcripts, calendars (earnings, macro, dividends), watchlist management, price alert creation/management. Read-only for market/reference data; can write watchlists and alerts. Cannot place, modify or cancel trades/orders. | Hosted at mcp.tradingview.com (not local — see note below) | Whatever symbols/queries the agent sends (tickers, screener filters, watchlist/alert edits) go to TradingView's hosted server | None expected — auth is OAuth 2.1 via TradingView account login during connection setup, not an API key. Confirm during setup whether Claude Code stores a token, and if so, that it stays out of this repo. | approved | 2026-09-16T05:42:11Z |

**Notes:** (1) TradingView's docs (tradingview.com/mcp/docs) state no data retention/privacy terms as of the proposal date — this was flagged to the owner, who approved the connection anyway on 2026-09-16. (2) Requires an Essential-or-higher TradingView subscription (trial excluded) and OAuth login to the owner's TradingView account. (3) This is a hosted server, not local — the agent will only send it the queries/edits needed for the task at hand.

## Candidates, not evaluated

Services to look at when choosing. None of them is approved. Check that each one supports your country and account type.

| Service | Covers | Notes |
|---|---|---|
| Interactive Brokers | Stocks, ETFs, options, forex and futures on many exchanges | Paper trading account and trading APIs |
| OANDA | Forex | Demo accounts and REST API |
| Alpaca | US stocks, ETFs and options | Paper trading and REST API |
| tastytrade | Options and stocks | Sandbox and REST API |
| Alpha Vantage, Finnhub | Market data | Free tiers with rate limits |
| FRED | US economic data | Free API key |
