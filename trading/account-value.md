---
title: PnL and Account Value
---

Astaria tracks both realized and unrealized profit and loss for every account.

## Position Value

For a position of size `Q` at current Mark Price `M`:

```text
current_notional = |Q| × M
```

## Unrealized PnL

For a long position:

```text
unrealized_pnl = position_size × (mark_price - entry_price)
```

For a short position:

```text
unrealized_pnl = position_size × (entry_price - mark_price)
```

## Realized PnL

Realized PnL is created when a position is partially or fully closed. It is settled into the account’s collateral balance.

## Account Value

Account Value reflects the total value of the account after incorporating open risk:

```text
account_value = collateral_balance + realized_pnl + unrealized_pnl + funding_payments - trading_fees
```

## Account Equity

Account Equity is the value used to determine whether an account satisfies margin requirements.

```text
account_equity = account_value
```

Account Equity is used in:

- Initial margin checks when opening positions
- Maintenance margin checks for existing positions
- Liquidation eligibility
- Withdrawal limits
