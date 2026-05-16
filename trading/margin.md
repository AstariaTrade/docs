---
title: Margining
---

Astaria’s margin system is designed specifically for event-linked perpetuals.

Unlike crypto perpetuals, event markets have:

- Prices bounded between `0` and `1`
- Thin liquidity near the extremes
- Discrete resolution into a terminal outcome
- Jump risk that increases near settlement

For that reason, Astaria uses a resolution-aware margin framework.

## Initial Margin

Initial Margin determines how much collateral is required to open a position.

It may include:

- A continuous volatility component
- A jump-risk component
- A size-versus-depth adjustment for large positions

## Maintenance Margin

Maintenance Margin is the minimum account equity required to keep a position open.

If account equity falls below Maintenance Margin, the account becomes eligible for liquidation.

## Leverage

Maximum leverage is dynamic rather than static.

Astaria may reduce available leverage as:

- Resolution approaches
- Market liquidity deteriorates
- Jump risk increases
- The underlying probability moves toward the boundaries of `0` or `1`

## Resolution-Aware Compression

As an event approaches resolution, Astaria can compress maximum leverage toward `1x`.

This is designed to reduce terminal-jump risk and prevent positions from remaining highly levered into final settlement.