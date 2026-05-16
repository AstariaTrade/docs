---
title: Liquidations
---

Liquidations occur when an account no longer satisfies its maintenance margin requirement.

## Trigger

An account becomes liquidatable when:

```text
account_equity < maintenance_margin
```

## Liquidation Process

Astaria may liquidate positions progressively rather than all at once.

This can include:

- Partial liquidation in tranches
- Size limits based on available market depth
- Time spacing between liquidation steps
- Throttling during stressed market conditions

## Anti-Cascade Controls

Large forced liquidations can worsen market instability. Astaria may slow liquidation throughput when liquidation demand becomes large relative to available depth.

This is intended to reduce reflexive liquidation cascades during periods of extreme stress.

## Insurance Fund

Losses that exceed the margin available in a liquidated account may be absorbed by the Insurance Fund.

If the Insurance Fund becomes insufficient, Astaria may enter a shortfall state governed by the Socialized Losses and Last Resort Mechanism.

## Resolution-Aware Liquidations

Event-linked perpetuals can experience large discrete moves as markets approach resolution.

To reduce terminal-jump risk, Astaria may:

- Increase margin requirements
- Reduce maximum leverage
- Restrict new position openings
- Halt trading in the final settlement window

These controls are designed to reduce liquidation pressure during the highest-risk period of an event’s lifecycle.
