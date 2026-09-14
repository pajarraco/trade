# context

Everything the trading agent knows, is allowed to do, connects to and has done lives in this folder.

| Folder | Holds | Who edits it |
|---|---|---|
| `rules/` | Your profile, risk limits, strategy and privacy rules | You. The agent can propose changes. |
| `permissions/` | Operating mode, allowed actions, kill switch and change log | You. The agent logs the changes you ask for. |
| `connections/` | Registry of APIs and MCP servers, setup notes and secrets | You approve. The agent sets them up. |
| `data/` | Market data, account snapshots, research and temp files | The agent |
| `history/` | Sessions, trade plans, trade log, decisions and plans | The agent, append-only |
| `memory/` | Standing facts and lessons | The agent |

Git ignores the contents of `data/`, `history/` and `memory/`, and every `.env` file. They stay on this computer and are never pushed to GitHub.

## Getting started

1. Fill in `rules/profile.md`.
2. Replace the default limits in `rules/risk.md` with your own.
3. Describe how you trade in `rules/strategy.md`.
4. When all three are right, set `rules_status: approved` in `permissions/permissions.yaml` and add a line to `permissions/changelog.md`.
5. Choose a broker and a market data source, then add them by following `connections/README.md`.

## Stop all trading

Create an empty file named `HALT` in `permissions/`. Delete it to resume.
