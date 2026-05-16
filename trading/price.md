---
title: Mark and Index Price
---

Astaria separates the **Mark Price** of the perpetual contract from the **Index Price** of the underlying event market.

## Index Price

The Index Price is Astaria’s reference value for the underlying event probability.

It is constructed from observable market data and is designed to be robust against thin liquidity and short-lived price distortions. The index may combine:

- A simple midpoint from the underlying prediction market
- A depth-protected midpoint
- A recent volume-weighted reference price

Astaria may also apply a conservative adjustment when market depth becomes unusually thin.

## Mark Price

The Mark Price is the trading price of the perpetual contract on Astaria.

It is used for:

- Unrealized PnL
- Liquidation checks
- Account health calculations
- Settlement-related risk controls

## Why They Differ

The Index Price tracks the external event-market reference. The Mark Price reflects the value of Astaria’s perpetual contract.

Funding payments are designed to pull the Mark Price toward the Index Price over time.