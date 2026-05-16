---
title: Funding
---

Funding is the mechanism that keeps Astaria perpetuals aligned with their underlying event-market reference price.

When the perpetual trades above the Index Price, longs may pay shorts. When it trades below the Index Price, shorts may pay longs.

## Premium Signal

Astaria measures the difference between:

- The perpetual Mark Price
- The event-market Index Price

This difference is the funding premium.

## Boundary-Aware Funding

Event markets behave differently near the boundaries of `0` and `1`.

A small absolute deviation near `0.02` or `0.98` can represent a large relative distortion. For that reason, Astaria’s funding model may apply additional correction in boundary regions.

This makes funding more responsive when:

- The market is close to resolution
- The probability is near `0` or `1`
- Relative deviations become economically larger than the raw basis suggests

## Funding Payments

Funding transfers occur between long and short traders and do not represent a protocol fee.

The exact funding schedule and calculation parameters may vary by market and will be published in the relevant market specification.
