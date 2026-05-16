---
title: Margin Tiers
---

Astaria uses margin tiers to calibrate risk requirements across different event-linked perpetual markets.

Margin requirements may depend on:

- Market depth
- Volatility
- Event class
- Time to resolution
- Distance of the Index Price from `0.5`
- Proximity to the probability boundaries of `0` and `1`

## Dynamic Risk Profiles

As market conditions change, a market’s effective leverage limits and margin requirements may also change.

This is especially relevant:

- Near event resolution
- During periods of thin liquidity
- When jump risk increases
- When the market enters boundary regions

## Purpose

Margin tiers are designed to ensure that capital efficiency remains aligned with market risk rather than being fixed across all event types.
