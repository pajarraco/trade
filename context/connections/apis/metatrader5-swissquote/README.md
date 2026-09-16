# MetaTrader 5 (Swissquote)

Registry entry: `context/connections/registry.md`, APIs table (status `approved`, since 2026-09-16).
Credential names in `context/connections/.env.example`; real values go only in
`context/connections/.env` (git-ignored) — fill them in directly in that file,
never in chat.

## What it is

MetaQuotes' official `MetaTrader5` Python package. It talks to a MetaTrader 5
terminal running on this machine over local IPC — there is no network API and
no hosted service. The terminal installed here is Swissquote's, at
`C:\Program Files\Swissquote Bank MT5 Client Terminal\terminal64.exe`
(resolved from the Start Menu shortcut, which points here rather than to an
executable directly).

## Setup

1. Install the package (Windows-only):
   ```
   pip install MetaTrader5
   ```
2. Copy `context/connections/.env.example` to `context/connections/.env` if you
   have not already, and fill in:
   - `MT5_SWISSQUOTE_LOGIN` — your MT5 account number
   - `MT5_SWISSQUOTE_PASSWORD` — your MT5 account password
   - `MT5_SWISSQUOTE_SERVER` — the broker server name shown in the terminal
     (e.g. `Swissquote-Server` or similar — check Terminal > Login dialog)
   - `MT5_SWISSQUOTE_TERMINAL_PATH` — full path to `terminal64.exe` (already
     filled into `.env.example` for this install)
3. Make sure the MT5 terminal is closed or logged out of any conflicting session
   before the package calls `initialize()` — it can also launch the terminal itself.

## Use in this project

- **Read-only first.** Until `permissions.yaml` mode is `paper` and `rules_status`
  is `approved`, the agent only reads account info (`account_info()`,
  `positions_get()`, `orders_get()`, `copy_rates_*` for market data). No orders.
- **Paper mode.** Once mode allows it, orders go through `order_send()` against
  the demo account only, following the trade workflow in `AGENTS.md` (risk
  checks, journal entry, trade-log row).
- **Live mode.** Not applicable until the owner adds a live account to
  `permissions.yaml` `accounts:` and switches mode — and even then, every order
  needs `CONFIRM <ticket id>`.

## Status

Tested 2026-09-16: connected read-only, `account_info()` confirms DEMO mode on
Swissquote-Server. See the registry for the full result.

**Important quirk found during testing:** calling `mt5.initialize(login=..., password=..., server=...)`
or `mt5.login(...)` directly — i.e. an automated login over the IPC API — fails
with `[-6] Terminal: Authorization failed`, even though the same credentials
work fine through the terminal's own GUI login. What does work: leave the
terminal open and manually logged in (via the GUI), then call
`mt5.initialize(path=...)` with **no** login/password/server — the package
attaches to that already-authenticated session instead of starting a new IPC
login. `context/data/tmp/test_mt5_connection.py` implements this attach-first,
explicit-login-as-fallback pattern.

Practical implication: any script using this connection needs the MT5 terminal
already running and logged into the account beforehand. Don't retry automated
`login()` calls repeatedly with the same credentials — repeated failures could
look like credential stuffing to the broker and risk an account lockout.
