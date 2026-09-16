# TradingView MCP server

Registry entry: `context/connections/registry.md` (status `approved`, since 2026-09-16).
Configured in the root `.mcp.json` as server `tradingview`.

## What it is

TradingView's official hosted MCP server. Docs: https://www.tradingview.com/mcp/docs.
Runs on TradingView's infrastructure (mcp.tradingview.com), not on this computer.

## What it can do

- Read: quotes, OHLCV bars, economic indicators, symbol search, screener, news,
  fundamentals/forecasts, SEC filings/transcripts, earnings/macro/dividend calendars.
- Write: watchlist management, price alert creation/management.
- Cannot place, modify or cancel trades or orders.

## Auth

OAuth 2.1 through your TradingView account login. No API key, so nothing goes in
`.env` for this connection. The login/authorization step happens interactively —
run `/mcp` (or `claude mcp`) in an interactive Claude Code session and follow the
browser prompt. It could not be completed from a non-interactive session.

Requires an Essential-tier or higher TradingView subscription; trial accounts are
excluded per TradingView's docs.

## Known gaps

TradingView's docs did not state data retention/privacy terms as of the approval
date. The owner approved the connection anyway (see `context/permissions/changelog.md`,
2026-09-16). Worth revisiting if that becomes a concern.

## Status

Configured but not yet authorized/tested. Next step: complete the OAuth login in an
interactive session, then run a read-only query (e.g. a symbol search or quote) and
note the result in the registry per the README's "Test" step.
