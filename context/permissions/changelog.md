# Permissions change log

Append-only, newest at the bottom. Add one row for every change to `permissions.yaml`, `context/rules/` or `context/connections/registry.md`.

| Date (UTC) | What changed | From | To | Asked for by | Reason |
|---|---|---|---|---|---|
| 2026-09-14 | Project created | nothing | mode `research`, rules `draft`, no connections | Owner | Initial setup |
| 2026-09-16 | Added registry row for TradingView MCP server | no row | status `proposed` | Owner | Owner asked to start setting up connections, shared the TradingView MCP link |
| 2026-09-16 | Approved TradingView MCP server | status `proposed` | status `approved` | Owner | Owner confirmed approval; TradingView's retention terms remain unstated in their docs, noted in registry |
| 2026-09-16 | Added registry row for MetaTrader 5 (Swissquote) API connection | no row | status `proposed` | Owner | Owner asked to connect to MT5; confirmed Swissquote terminal installed with a demo account |
| 2026-09-16 | Approved MetaTrader 5 (Swissquote) API connection | status `proposed` | status `approved` | Owner | Owner confirmed approval, understanding that the connection uses the account password (no scoped key available) and that paper-mode use of this package can place real orders on the demo account |
