# Trade plan: SYMBOL, setup name

- Ticket id: T-YYYYMMDD-NN
- Created (UTC):
- Account id and type:
- Mode when created:
- Status: idea | planned | submitted | open | closed | cancelled

## Plan

- Instrument and contract:
- Direction:
- Setup, from `rules/strategy.md`:
- Thesis, why this trade and why now:
- Entry price and order type:
- Stop loss:
- Targets:
- Position size:
- Loss if the stop is hit, in base currency and as % of equity:
- Reward to risk:
- Expected holding period:
- Exit early if:
- Scheduled events inside the holding window:

## Risk checks

| Check | Pass or fail | Notes |
|---|---|---|
| Kill switch, mode and rules status allow the trade | | |
| Loss at stop within the per-trade limit | | |
| Position size within the limit | | |
| Daily, weekly and losing-streak limits not reached | | |
| Open positions and combined risk within limits | | |
| Instrument rules met | | |
| No blocked event in the holding window | | |

## Order ticket

For a live order, the owner replies `CONFIRM T-YYYYMMDD-NN`.

- Account:
- Action, quantity, symbol and contract:
- Order type, price and time in force:
- Attached stop and target orders:
- Maximum loss:

## Execution

Copy of the rows added to `trades/trade-log.csv`.

## Review after close

- Result in base currency and in R multiples:
- Did the trade follow the plan? What was different?
- Keep doing:
- Change:
