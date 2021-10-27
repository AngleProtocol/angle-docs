---
description: Common questions about HAs and perpetual futures
---

# FAQ - Hedging Agents

## How come perpetual futures insure the protocol?

Let's take a simple example where users bring an amount `y` of collateral to get `y` worth of stablecoins, and Hedging Agents back up exactly this amount `y` of collateral \(after bringing a margin of `x` in collateral\).

If the initial price was `p` and the current price is `q`, now to be able to sustain the convertibility, an amount `y.p/q` of collateral is needed to reimburse users.

According to the formula of the position of the HA written, besides the `x` of collateral initially brought, the amount of collateral due to \(or taken from\) the HA is now `y(1-p/q)`.

Hence while there was initially `x+y` in the protocol, what is now due to HAs and users is:

$$
x+ y\cdot \frac{p}{q} +  y\cdot (1-\frac{p}{q}) = x+y
$$

Since the protocol is fully hedged by Hedging Agents with perpetual futures, it can sustain convertibility and keep the stablecoins stable.

## Is there a cost for holding perpetual futures as a HA?

No, there is no funding rate like in centralized exchanges proposing perpetual futures. The only fees paid with Angle perpetuals are entry and exit fees.

There are no fees for removing or adding collateral as margin to a position.

## Can HAs always open new positions with the protocol?

With Angle, Hedging Agents are here to cover the volatility of the collateral that was brought by users. If the amount of collateral from users is worth `x` of stablecoins and HAs already cover this amount, then new ones will not be able to enter the protocol.

To put it in other words, Angle can be seen as a marketplace between stability and volatility seekers. If the supply of volatility is fully taken by HAs, then the protocol cannot offer more leveraged positions \(and thus more volatility\) than what it has already offered.

## How is the amount to hedge by HAs computed?

The amount to hedge for a given collateral corresponds to the quantity of stablecoins issued against this collateral, multiplied by a target ratio fixed by the protocol.

It refers to the total position HAs can open with the protocol.

For instance, if a user minted 20000 agUSD with wETH, then the amount to hedge is 20000 USD of wETH. Then, if a user burns 15000 agUSD against wETH, the amount to hedge becomes 5000 USD of wETH.

If the target proportion that HAs are allowed to hedge is 90%, then after the burn the amount to hedge by HAs is 5000 \* 0.9 = 4500 USD worth of stablecoins. This means that the sum of the position size \(in collateral\) multiplied by the entry oracle rates of HAs should less or equal to 4500 USD.

**Why is that quantity expressed in stablecoins?** Let's say that there is one HA in the protocol that entered at a time where the price of collateral with respect to the stablecoin was `p_e` and commits to an amount of collateral of `c`. HAs are not allowed to hedge more collateral that is in the protocol. To this extent, `c` must be collateral in the protocol's reserves, brought by a user minting stablecoins.

If the HA cashes out at a moment in which the collateral is worth `p`, if we imagine that there was only `c` of collateral in the protocol before the HA came in, then the protocol ends up with:

$$
c - \texttt{PnL} =  c \cdot \frac{p_e}{p}
$$

This means that the protocol has enough in reserves to burn:

$$
c \cdot \frac{p_e}{p} \cdot p = c \cdot p_e \texttt{ stablecoins}
$$

## How is the amount hedged by HAs computed?

For a given stablecoin-collateral pair, it is the sum of the product between the amount hedged by each HA perpetual and the entry rate when this perpetual was opened. It is expressed in stablecoin value.

This amount is updated whenever a HA position is opened, closed, or liquidated.

This amount should always remain inferior to the target amount HAs should hedge \(as specified [above](faq-ha.md#how-is-the-collateral-to-cover-by-has-computed)\). Above this amount hedged, HAs are no longer allowed to open perpetual positions on Angle. Additionally, if HAs hedge significantly more than the target hedge amount, then keepers can force-close some positions.

## What is exactly implied by hedging ratio?

The hedging ratio refers to the portion of the amount to hedge by Hedging Agents that is actually hedged.

If one user mints 2000 agUSD for 1 wETH, and the target hedging ratio is set to 90%, then the amount HAs should hedge for agUSD is 1800 USD of wETH. If one HA enters the protocol when wETH is worth 1000 USD, brings 2 wETH and decides to commit to the variation of 0.8 wETH \(this HA has a leverage of x1.4\), then 800 out of the 1800 wETH in stablecoin value are hedged: the hedging ratio is 44.44%.

## What happens if there are too many HAs with respect to the amount to hedge from the protocol?

At any given point in time, HAs could hedge more than the target hedge amount.

In case this happens, the protocol has two parameters: the target hedging ratio, and the limit hedging ratio.

The target heding ratio gives the amount to be hedged by HAs. Above this ratio, HAs can't open positions anymore. The limit hedging ratio is the maximum hedging ratio possible in the protocol. If HAs start hedging more than this ratio because of users burning stablecoins, their positions can be automatically cashed out.

Imagine the limit hedging ratio is defined at 95%, then if `0.9x/(x-y)` becomes superior to `0.95`, then some HAs could be cashed out till the amount covered by HAs is back in the bounds again \(below the target hedging ratio\).

When a HA position is cashed out like that, the HA gets back its margin plus any unrealized PnL. Keepers are responsible for cashing out HAs positions in such cases.

## What happens if the protocol does not have enough reserves to close a HA position?

It is possible, because of users bringing one collateral, getting stablecoins and directly burning it against another collateral or because some of the reserves are lent and thus not immediately available, that when a HA tries to close her position there is not enough collateral in the pool to which she contributed.

In this case, the HA gets everything that can be given to from the collateral pool, and the rest is returned in Standard Liquidity Providers' tokens \(called sanTokens\).

## Can I open multiple perpetuals?

A HA can own multiple perpetuals across a similar pool. For example, a HA can choose to have two positions on the wETH/USD pair, one with a x5 leverage, and the other with a x2 leverage. Each position has its dedicated margin \(isolated margin perpetuals\).

Once the amount hedged by a HA has been set, it can no longer be modified. For instance if a HA opens a position of 5 wETH with 1 wETH of collateral as margin, the HA can add or remove collateral from this perpetual to change the leverage, but it can never modify this amount committed \(also defined as the position size\). The solution would be to close this position and to open a new one.

A HA can also own perpetuals across multiple pairs for different stablecoins. For instance, a HA could have a perpetual on the pair USDC/EUR, and another perpetual on the pair wETH/USD.

In the protocol, positions are represented as NFTs: they can be transferred from one address to another and are non fungible.

## What's the minimum amount of time I can stay as a HA?

To reduce the risk of front-running with the oracle, after perpetual creation, a HA cannot exit or remove collateral from the position within the hour that follows.

{% hint style="info" %}
This is a parameter that can be modified by protocol governance.
{% endhint %}

## Is there a maintenance margin like in centralized exchanges?

Yes. If the [margin ratio](https://docs.angle.money/concepts/hedging-agents#has-liquidations) goes below a certain threshold, your position should get liquidiated by keepers. The maintenance margin depends on the stablecoin/collateral pair concerned. For instance for wETH/USD pair, the maintenance margin should be set at `6.25%`.

## Are there minimum or maximum leverage as a HA on Angle?

There is no minimal leverage, meaning you can come as a HA in the protocol, bring 2 wETH and open a position of only 0.001 wETH \(thus hedging only that amount\).

There is a maximum leverage though. This parameter will depend on the volatility of the pairs.

For perpetuals on forex pairs like USDC/EUR, the maximum leverage is set at x100.

## Are there slippage protections for HAs?

Yes. When coming in the protocol and creating a perpetual, HAs can specify the maximum oracle value they are willing to accept as entry price.

The same goes for HAs cashing out their perpetual: they can specify the smallest oracle value below which they do not want their transaction executed.
