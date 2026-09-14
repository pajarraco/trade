# Data

Git ignores this folder's contents, so data stays on this computer.

| Folder | What goes in it |
|---|---|
| `market/` | Prices, quotes, option chains and economic data from approved connections |
| `account/` | Balance, position and statement snapshots. Sensitive. |
| `research/` | Watchlists, screens, analysis and backtest results |
| `tmp/` | Temporary files. Safe to delete at any time. |

## File naming

Name files `source_dataset_YYYY-MM-DD.ext`, for example `broker_AAPL-daily_2026-09-14.csv`.

- Use CSV or Parquet for tables, JSON for raw API responses and Markdown for notes.
- Keep the source and download date in the file name.
- Never store credentials in data files.
