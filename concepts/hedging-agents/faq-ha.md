---
description: Common questions about HAs and perpetual futures
---

# FAQ - Hedging Agents

## How come perpetual futures insure the protocol?

Let's take a simple example where initially users brought an amount `y` of collateral to get `y` of stablecoins and Hedging Agents back up exactly this amount `y` of collateral (after putting `x` of collateral in the protocol, `x`is their margin).

If the initial price was `p`, and the current price is now `q`, now to be able to sustain the convertibility, an amount `y.p/q` of collateral is needed to reimburse users.

According to the formula of the position of the HA written, besides the `x` of collateral initially brought, the amount of collateral due to (or taken from) the HA is now `y(1-p/q)`.

Hence while there was initially `x+y` in the protocol, what is now due to HAs and users is:

$$
x+ y\cdot \frac{p}{q} +  y\cdot (1-\frac{p}{q}) = x+y
$$

Since the protocol is fully covered by Hedging Agents with perpetual futures, the protocol will manage to sustain convertibility and keep the stablecoins stable.

## Is there a cost for holding perpetual futures as a HA?

No, there is no funding rate like in centralized exchanges proposing perpetual futures! When someone opens a perpetual, the fees paid for holding that perpetual are independent of the time spent having that perpetual. The only fees paid are computed when a perpetual is opened, or when a perpetual is closed by a Hedging Agent. HAs have the opportunity to increase or decrease the leverage of their perpetuals by removing or adding collateral to it: no fees are taken by the protocol for these transactions.

## Can HAs always enter the protocol?

With Angle, Hedging Agents are here to cover the volatility of the collateral that was brought by users. If the amount of collateral from users is worth `x` of stablecoins and if HAs already cover this amoun, then new HAs will not be able to enter the protocol.

To put it in simpler words, Angle can be seen as a marketplace between stability and volatility seekers. If the offer of volatility is fully taken by HAs, then the protocol cannot propose more leveraged positions (and thus more volatility) than what it has already offered.

## How is the amount to cover by HAs computed?

The amount to cover refers to the amount of collateral expressed in stablecoin value on which HAs can take leveraged positions.

It is obtained by multiplying the amount of collateral in stablecoin value you'd need if every user burnt back the stablecoins they minted to a proportion that represents the target amount of collateral that should be covered.

The amount of collateral in stablecoin value you'd need if every user brought back the stablecoins they minted is simply computed by taking into account each mint and burn of stablecoins using this collateral.

For instance, if a user brought 10 wETH to issue 20000 agUSD, then this amount is 20000 USD of wETH. Now if a user burns 15000 agUSD for 5 wETH, this quantity becomes 5000 USD of wETH. Note that if those 15000 agUSD had been burnt for 7 wETH, this quantity would still be 5000 USD.

If the target proportion that HAs are allowed to cover is 90%, then after the burn the amount to cover by HAs is 5000 \* 0.9 = 4500 agUSD stablecoins. This means that the sum of the committed amount (in collateral) times the entry oracle rates for each HA should be no more than 4500.

**Why is that quantity in stablecoins?**
Let's say that there is one HA in the protocol that entered at a time where the price of collateral with respect to the stablecoin was `p_e` and commits to an amount of collateral of `c`. HAs are not allowed to hedge more collateral that is in the protocol. To this extent, `c` must be collateral in the protocol's reserves, brought by a user minting stablecoins.

If the HA cashes out at a moment in which the collateral is worth `p`, if we imagine that there was only `c` of collateral in the protocol before the HA came in, then the protocol ends up with:

$$
c - \texttt{PnL} =  c \cdot \frac{p_e}{p}
$$

This means that the protocol has enough in reserves to burn:

$$
c \cdot \frac{p_e}{p} \cdot p = c \cdot p_e \texttt{ stablecoins}
$$

## How is the amount covered by HAs computed?

For a given stablecoin-collateral pair, it is the sum of the product between the amount covered by each HA perpetual and the entry rate when this perpetual was created. It is hence expressed in stablecoin value.

This amount is updated whenever a new HA comes in and opens a position or a HA comes out and either cashes out or gets liquidated.

This amount should always remain inferior to the target amount HAs should cover (as specified [above](faq-ha.md#how-is-the-collateral-to-cover-by-has-computed)). Above this amount covered, HAs are no longer allowed to create perpetuals within Angle protocol. What's more, if HAs cover way too much with their perpetuals, then keepers can force the cash out of some positions.

## What is exactly implied by the coverage ratio?

The coverage ratio refers to the portion of the amount that should be covered by Hedging Agents that is actually covered by them.

If 1 user brought 1 wETH to get 2000 agUSD, and if the target coverage proportion is set to 90%, then for the agUSD stablecoin, the amount HAs should cover is 1800 USD of wETH. If one HA enters the protocol when wETH is also worth 1000 USD, brings 2 wETH and decides to commit to the variation of 0.8 wETH (this HA is then leveraged 1.4x), then 800 out of the 1800 wETH in stablecoin value are covered: the coverage ratio is 44.44%.

## What happens if there are too many HAs with respect to the amount to cover from the protocol?

It is possible that at a given moment, more is covered by HAs than what is to cover.

Imagine the case where `x` of collateral has been brought by users to issue `x` of stablecoins, and that the target proportion of it (90%) is fully covered by HAs. If a user burns `y` stablecoins against collateral, then the amount of collateral in stablecoin value to reserve for users becomes `x-y`, but the amount covered by HAs is `0.9x`.

The protocol defines two different proportions for the coverage ratio: one above which they are no longer allowed to create perpetuals and one above which any HA can be forcefully cashed out because too much is covered. In this case, as said above, the proportion above which HAs are no longer allowed to create perpetuals is 90%.

Imagine the limit proportion is defined at 95%, then if `0.9x/(x-y)` becomes superior to `0.95`, then some HAs could be cashed out till the amount covered by HAs is back in the bounds again (below the target proportion).

When a HA position is cashed out like that, the HA gets the value of her position in collateral. Keepers are responsible for cashing out HAs positions in such cases.

## What happens if the protocol does not have enough reserves to close a HA position?

It is possible, because of users bringing one collateral, getting stablecoins and directly burning it against another collateral or because some of the reserves will be lent and thus not immediately available, that when a HA tries to cash out her position there is not enough collateral in the pool to which she contributed.

In this case, the HA will get everything that can be given to her from the collateral pool, and the rest will be given in Standard Liquidity Providers' tokens (which we call sanTokens).

## Can I open multiple perpetuals?

A HA can own multiple perpetuals across a similar pool. For example, for the pool wBTC/agUSD, a HA can choose to have a perpetual leveraged 10x and another position that is leveraged 5x.

Once the amount covered by a HA has been set, it can no longer be modified. For instance if a HA opens a perpetual and brings 1 wETH in this perpetual and commits to 5 wETH, the HA can add or remove collateral from this perpetual to change the leverage, but it can never modify this amount committed (also defined as the position size). The solution would be to cash out this position and to open a new position.

A HA can also own perpetuals across multiple pools for different stablecoins. For instance, a HA could have a perpetual for the pool USDC/agEUR, and another perpetual for the pool wETH/agUSD.

Perpetuals are treated as NFTs by the protocol: they can be transferred from one address to another and are non fungible.

## What's the minimum amount of time I can stay as a HA?

To reduce the risk of front-running with the oracle, after perpetual creation, a HA cannot exit or remove collateral from the position within the hour that follows.

{% hint style="info" %}
This is a parameter that can be modified by protocol governance
{% endhint %}

## Is there a maintenance margin like in centralized exchanges?

Yes! If the cash out amount of a HA is below a certain proportion of the collateral that the HA commits to, a keeper will liquidate your perpetual. The maintenance margin is to depend on the stablecoin/collateral pair concerned. For instance for wETH used for agUSD stablecoins, the maintenance margin may be set to `6.25%`.

## Are there bounds on the leverage I can get with the perpetual futures I own as a HA?

Yes. There is however no minimal bound on the leverage, meaning you can come as a HA in the protocol, bring 2 wETH and choose to cover 0.001 wETH.

This maximum leverage will depend on the pairs considered. For instance, for a perpetual on the pair wETH (collateral) / USD (stablecoin), the maximum leverage allowed may be 10.

For a perpetual on the pair USDC (collateral) / EUR (stablecoin), the maximum leverage allowed may be as big as 100.

## Are there slippage protections for HAs?

Yes. When coming in the protocol and creating a perpetual, HAs can specify the maximum oracle value they are willing to see stored in their perpetual.

The same goes for HAs cashing out their perpetual: they can specify the smallest oracle value below which they do not want their transaction executed.
