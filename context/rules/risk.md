# Risk rules

status: draft

These are conservative starting values, not limits you have chosen. Replace each one with your own number before approving. While this file is draft, the agent works in research mode only.

"Equity" means the account's net liquidation value at the start of the trading day.

## Per trade

| Rule | Limit |
|---|---|
| Loss if the stop is hit | At most 1% of equity |
| Stop loss or defined maximum loss, set before entry | Required |
| Position size | At most 20% of equity |
| Reward to risk at the planned target | At least 2:1 |
| Adding to a losing position | Not allowed |

## Per day and week

| Rule | Limit | Action when reached |
|---|---|---|
| Daily loss | 3% of equity | No new trades until the next trading day |
| Weekly loss | 6% of equity | No new trades until next week, then review the journal |
| Consecutive losing trades | 3 | Stop and review before the next trade |
| Open positions | 5 | No new positions |

## Portfolio

| Rule | Limit |
|---|---|
| Combined loss at stops across all open positions | At most 5% of equity |
| Exposure to one sector or one currency | At most 30% of equity |
| Margin loans on stocks and ETFs | Not allowed |

## Instruments

**Stocks and ETFs**

- Average daily volume of at least 500,000 shares.
- Leveraged and inverse ETFs are not allowed.

**Options**

- Defined-risk positions only: long calls and puts, debit spreads, credit spreads, covered calls and cash-secured puts.
- No naked short calls or naked short puts.
- The maximum loss of the position stays within the per-trade limit.
- Close or roll before expiry day unless the plan says otherwise.

**Forex**

- Effective leverage across all forex positions of at most 10:1.
- Stop orders are placed with the broker, not kept as mental stops.

## Scheduled events

No new position within one trading day before a scheduled earnings release, central bank decision or major data release that affects the instrument, unless the plan names that event as the reason for the trade.

## Checks for every trade plan

Record pass or fail for each check in the plan.

1. The kill switch, mode and rules status allow the trade.
2. The loss at the stop is within the per-trade limit.
3. The position size is within the limit.
4. The daily, weekly and losing-streak limits have not been reached.
5. Open positions and combined risk stay within limits after this trade.
6. The instrument rules above are met.
7. No blocked event falls inside the holding window.
