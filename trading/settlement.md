---
title: Resolution Zones
---

Astaria markets enter a dedicated **Resolution Zone** as the underlying event approaches final settlement.

This mechanism exists because event-linked perpetuals do not behave like ordinary crypto perps near maturity. Prediction markets can collapse discretely to a terminal outcome of `0` or `1`.

## Stage 1: Leverage Compression

Before resolution, Astaria may reduce maximum leverage and require positions to become safer over time.

This can include:

- Lower maximum leverage
- Additional margin requirements
- Restrictions on opening new highly levered positions

## Stage 2: Trading Halt

During the final pre-resolution window, Astaria may halt trading in the perpetual market.

This can include:

- No new orders accepted
- Resting orders canceled
- Open interest recorded for settlement

## Stage 3: Cash Settlement

Once the event resolves, positions settle in cash based on the terminal outcome.

If the underlying market resolves to:

- `1`, the event settles as true
- `0`, the event settles as false

Settlement may remain subject to a dispute window or oracle finality process where applicable.

## Purpose

Resolution Zones are designed to reduce:

- Terminal-jump liquidation risk
- Disorderly execution in the final moments before resolution
- Market instability caused by discrete event settlement
