---
title: Socialized Losses
---

Socialized Losses happen when the Astaria Insurance Fund is bankrupt due to large amounts of unprofitable liquidations.

Astaria is built to minimize the probability of such an event, but it can still happen. In this case, the exchange would have insufficient USDC funds to meet withdrawal requests for all client funds.

During periods of insufficient capitalization, Astaria applies a Socialized Loss charge to all withdrawals.

The **Socialized Loss Factor** represents the percentage charged on each withdrawal at that point in time in order to offset the loss.

Only users who withdraw during those shortfall periods are affected by Socialized Losses.

Once the Insurance Fund is recapitalized, whether through profitable liquidations or fund transfers, Astaria stops applying the Socialized Loss charge to withdrawals.

## Definitions

### Account Bankruptcy Amount

For a given trading account, the USDC Settlement Balance represents the USDC balance that this account would have if all open positions were closed at the current Mark Price:

$$
\begin{align*}
\text{Account USDC Settlement Balance} = \\
\text{Account USDC Balance}
+ \frac{\text{Account Unrealized PnL}}{\text{USDC Oracle Price}}
\end{align*}
$$

The Bankruptcy Amount of an account is equal to:

$$
\text{Bankruptcy Amount}
=
\max(0, -\text{Account USDC Settlement Balance})
$$

The Bankruptcy Amount is positive only if the account would be bankrupt at current Mark Prices. Otherwise, it is zero.

### Exchange Bankruptcy Amount

The Exchange Bankruptcy Amount is equal to:

$$
\begin{align*}
\text{Exchange Bankruptcy Amount}
=
\max(
0,
\text{Total Users Bankruptcy Amount}
-
\text{Insurance Fund USDC Balance}
)
\end{align*}
$$

### Socialized Loss Factor

$$
\text{Socialized Loss Factor}
=
\frac{
\text{Exchange Bankruptcy Amount}
}{
\text{Total Exchange USDC Balance}
+
\text{Exchange Bankruptcy Amount}
}
$$

If the Exchange Bankruptcy Amount is positive, the Socialized Loss Factor is greater than `0`, and all withdrawals are penalized by this factor.

Only withdrawals are subject to the Socialized Loss penalty. Users who do not withdraw are not affected.

## Example

**Insurance Fund initially has a 1,000 USDC balance and no open positions.**

**There are three traders on the exchange: Alice, Bob, and Charlie. Each has a 1,000 USDC balance. The oracle price of USDC is 1 USD.**

Therefore, the Total Exchange USDC Balance is:

$$
4{,}000
$$

**Alice buys 50 XYZ-USD-PERP against Bob at 100 USD.**

**The Mark Price of XYZ-USD-PERP suddenly crashes to 40.**

Alice now has Unrealized PnL of:

$$
50 \times (40 - 100) = -3{,}000 \text{ USD}
$$

and has a negative account value of:

$$
1{,}000 - 3{,}000 = -2{,}000 \text{ USD}
$$

Therefore, Alice’s Bankruptcy Amount is:

$$
2{,}000 \text{ USDC}
$$

and the Exchange Bankruptcy Amount is:

$$
2{,}000 - 1{,}000 = 1{,}000 \text{ USDC}
$$

The Socialized Loss Factor is then:

$$
\frac{1{,}000}{4{,}000} = 25\%
$$

Charlie withdraws 500 USDC:

- The Insurance Fund receives:

$$
25\% \times 500 = 125 \text{ USDC}
$$

- Charlie’s withdrawal address receives:

$$
75\% \times 500 = 375 \text{ USDC}
$$

**The Insurance Fund takes over Alice’s account.**

**The Mark Price of XYZ-USD-PERP quickly moves up to 70.**

Now the Insurance Fund position has:

$$
50 \times (70 - 100) = -1{,}500 \text{ USD}
$$

of Unrealized PnL.

This means the Insurance Fund is no longer bankrupt and has:

$$
2{,}000 - 1{,}500 = 500 \text{ USD}
$$

This brings the Exchange Bankruptcy Amount to `0` and the Socialized Loss Factor to `0%`.

Withdrawals are no longer subject to any loss.

## Last Resort Mechanism

A time-based **Last Resort Mechanism** operates independently of Socialized Loss.

Its job is to manage the Insurance Fund’s exposure in extreme illiquidity scenarios when the fund is unable to unwind or hedge a large position for an extended period.

In such cases, it can settle counterparty positions under time-based rules.

The difference versus ADL is that users have clear visibility and an ability to anticipate any intervention before it takes place.

The introduction of time allows both solvency and liquidity to recover, which in turn reduces the burden on both mechanisms.
