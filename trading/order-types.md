---
title: Order Types and Matching
---

Astaria supports order types designed for efficient trading of event-linked perpetuals.

## Order Types

- **Market Order**: Executes immediately against available liquidity.
- **Limit Order**: Executes at the selected limit price or better.
- **Stop Market Order**: Becomes a market order once the trigger condition is met.
- **Stop Limit Order**: Becomes a limit order once the trigger condition is met.

## Execution Options

- **Reduce Only**: Can only reduce or close an existing position.
- **Post Only**: Adds liquidity to the order book and will not execute immediately.
- **Immediate or Cancel (IOC)**: Executes immediately for any available size, with the remainder canceled.

## Matching

Astaria uses price-time priority for order matching.

Orders at the best price execute first. If multiple orders share the same price, the earliest order receives priority.

## Resolution-Aware Restrictions

As a market approaches resolution, Astaria may restrict certain actions to reduce settlement risk. Depending on the market state, this can include:

- Reduced maximum leverage
- Restrictions on opening new positions
- Cancellation of resting orders before the final settlement window
