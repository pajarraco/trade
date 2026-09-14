# Connections registry

The agent may contact only services with status `approved`, and send them only the data listed. Statuses are `proposed`, `approved`, `suspended` and `removed`. Never delete a row. Change its status instead.

## APIs

| Name | Purpose | Base URL | Account type | Data sent | Secrets in .env | Retention terms | Status | Since |
|---|---|---|---|---|---|---|---|---|

None yet.

## MCP servers

| Name | Purpose | Runs where | Data sent | Secrets in .env | Status | Since |
|---|---|---|---|---|---|---|

None yet.

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
