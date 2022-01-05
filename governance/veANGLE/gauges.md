---
description: How the gauge system works with Angle
---

# 🗳 Gauges

## 🔎 TL;DR

- veANGLE holders are able to decide where weekly ANGLE emissions go through gauge votes
- The fact that veANGLE holders are responsible for such vote alines incentives within the protocol

## ✍️Gauge Vote Principle

Besides voting on governance proposals, veANGLE owners can vote for ANGLE gauge weights with their veANGLE balance. The gauge system implemented by Angle is similar to that of Frax and of Curve.

Like what was done weekly on Snapshot by ANGLE holders before the Angle Governance upgrade, veANGLE holders will now be able to distribute their voting power across a single or multiple gauges on-chain.

A gauge corresponds in fact to a staking contract and by voting for a gauge a veANGLE owner increases the amount of ANGLE tokens sent to the related staking contract with respect to other staking contracts. veANGLE owners will therefore vote for the gauges they think should receive more weight.

This allows veANGLE holders, who are the most long term users of the protocol, to have complete control over the future ANGLE emissions.

## ↔️Incentives alinement

Interestingly, the gauge system lowers the influence of ANGLE pairs and pools where the majority of rewards are sold off since those LPs will not have veANGLE to continue voting for their pair.

This system strongly favors LP providers who continually lock their rewards into veANGLE to increase their pool's gauge weight. Essentially, and like mentionned in [Frax docs](https://docs.frax.finance/vefxs/gauge), Angle gauges align incentives of veANGLE holders so that the most long term oriented ANGLE holders control where ANGLE emissions.

## In Practice

Gauge weights are updated once every week every Thursday at 2am CET. This means that the ANGLE emission rate for each pair is constant for 1 week then updates to the new rate on each Thursday morning. Any user can change their weight allocation for a given gauge every 10 days.

When updating their weights, users will dedicate a share of their total veANGLE balances towards each gauge. Then, the sum of all the veANGLE assigned to each gauge by all holders will determine the quantity of rewards to be distributed.

{% hint style="info" %}
When updating gauge weights and putting more weight on one gauge with respect to another, users should be wary of doing decreases first then increases.
{% endhint %}

## ANGLE Issuance Rate

The rate of emission of ANGLE tokens will remain unchanged after the upgrade. For details about the ANGLE emission rate, please refer to [this page](../concepts/staking.md).

Essentially, the weekly decrease factor of 1.007827 of the ANGLE emissions will be guaranteed on-chain.

With such a decreasing factor, distribution with this system is bound to continue and to remain significant for a period of over 10 years.

veANGLE stakers can therefore feel confident staking the maximum duration of 4 years knowing that the gauge program is not temporary and won't be deprecated any time soon.

## Gauge Types

Curve introduced the gauge system for their CRV token emissions. Users lock their veCRV to vote on "weights" of different Curve liquidity pools. The idea with Angle gauges is to incentivize different types of liquidity pools useful to the protocol:

- sanTokens owners
- Perpetual owners
- Liquidity pools on exchanges (like on Curve, on Uniswap)
- Liquidity pools on other chains (like agEUR/USDC on Quickswap on Polygon for instance)

The gauge system could also be used to incentivize different things than staking contracts. For instance, incentives for Convex voters on Curve could be linked to a gauge (in fact an EOA or a multisig) where veANGLE owners decide to send some rewards, and the multisig would be responsible for placing the incentives on Votium.

Overall, there is no restriction on which protocols or pairs can have a gauge weight other than that they should pass the gauge governance vote. The idea is however that all gauges should have a link with the agEUR or the Angle protocol, as the governance token of the protocol is being distributed as incentive.

Given that a wide range of contracts could be considered Angle protocol gauges, the system distinguishes several gauge types:

- Type 0 Gauges: mainnet staking contracts
- Type 1 Gauges: corresponding to Angle Perpetual staking contracts. Note that there will be no boosts for veANGLE holders in these contracts.
- Type 2 Gauges: External staking contracts. This gauge type includes everything that is not being staked on Angle (Curve LP tokens staked on Convex for example)
- Gauges with type > 2: this corresponds to gauges for staking contracts that are not on Ethereum mainnet. The addresses of these gauges is that of a contract that will bridge the rewards to the desired chain and then to the staking contract. This gauge type is not used for the moment.

### Gauge type weight

Each gauge type has its own weight, which can be set to shift the distribution of rewards in favor of one or another type of gauges. At the beginning, the weights will all be set equally so it has no impact. Governance can vote to change these gauge type weights.

**Example**
Assuming an inflation rate $$r$$ changing with every epoch (1 week), a gauge weight $$w_g$$ and a gauge type weight $$w_t$$, then the stream of inflation going to a gauge is:

$$
r' = w_g \times w_t \times r
$$

Every week, depending on gauge votes, the weight $$w_g$$ can change. Governance can also vote to update the weight $$w_t$$.
