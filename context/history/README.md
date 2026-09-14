# History

Append-only records. Never edit or delete an entry. Add a correcting entry instead. Git ignores this folder's contents, so records stay on this computer.

| Path | What goes in it |
|---|---|
| `sessions/YYYY-MM-DD-topic.md` | One summary per working session: what was done, decisions made and open items |
| `journal/YYYY-MM-DD-SYMBOL-short-name.md` | One trade plan and review per trade idea, copied from `journal/_template.md` |
| `trades/trade-log.csv` | One row per order event |
| `decisions.md` | Project decisions, such as choosing a broker or a tech stack |
| `plans/` | Plan files written by Claude Code |

## trade-log.csv columns

| Column | Meaning |
|---|---|
| `timestamp_utc` | ISO 8601 UTC time of the event |
| `ticket_id` | Ticket id from the trade plan, for example `T-20260914-01` |
| `account_id` | Account id from `permissions.yaml` |
| `account_type` | `paper` or `live` |
| `event` | `submitted`, `modified`, `cancelled`, `rejected`, `partial_fill` or `filled` |
| `instrument_type` | `stock`, `etf`, `option`, `forex` or another enabled type |
| `symbol` | Ticker or currency pair, for example `AAPL` or `AUD/USD` |
| `contract` | For options, expiry, strike and right, for example `2026-10-16 150 C`. Empty otherwise. |
| `side` | `buy`, `sell`, `sell_short` or `buy_to_cover` |
| `quantity` | Shares, contracts or units |
| `order_type` | `market`, `limit`, `stop` or `stop_limit` |
| `limit_price` | Limit price, empty if not used |
| `stop_price` | Stop price, empty if not used |
| `fill_price` | Average fill price, empty until filled |
| `fees` | Commissions and fees |
| `currency` | Currency of the prices and fees |
| `broker_order_id` | Order id returned by the broker |
| `journal_ref` | File name of the trade plan |
| `confirmed_by_owner` | The `CONFIRM` text received for a live order, or `n/a` for paper |
| `notes` | Anything else |
