---
description: How the gauge voting system works with Angle
---

# 🗳 Gauges voting

## 🔎 TL;DR

- veANGLE holders are able to decide where weekly ANGLE emissions go through gauge votes
- The fact that veANGLE holders are responsible for such vote aligns incentives within the protocol

## ✍️ Gauge Voting Principle

Besides voting on governance proposals, veANGLE owners can vote for ANGLE gauge weights with their veANGLE balance. The gauge system implemented by Angle is similar to that of Frax and of Curve.

Like what was done weekly on Snapshot by ANGLE holders before the Angle Governance upgrade, veANGLE holders are now be able to distribute their voting power across a single or multiple gauges on-chain.

A gauge corresponds to a staking contract. By voting for a gauge, veANGLE holders increase the amount of ANGLE tokens sent to the related staking contract with respect to the others. veANGLE holders therefore vote for the gauges they think should receive more rewards.

This allows veANGLE holders, who are the most long term users of the protocol, to have complete control over the future ANGLE emissions.

## ↔️ Incentives alinement

Interestingly, the gauge system lowers the influence of LPs selling off their ANGLE rewards since those LPs do not necessarily have veANGLE to continue voting for the gauge they are providing liquidity to.

This system strongly favors LP who continually lock their rewards into veANGLE to increase their pool's gauge weight. Essentially, and like mentioned in [Frax docs](https://docs.frax.finance/vefxs/gauge), Angle gauges align incentives of veANGLE holders so that the most long term oriented holders control where ANGLE emissions are distributed.

## In Practice

Gauge weights are updated weekly, every Thursday at 2am CET. This means that the ANGLE distribution rate for each pool is constant for 1 week and then updates to the new rate at this time.

Users with veANGLE can allocate their voting power to the available gauges to influence the reward distribution. Then, the sum of all the veANGLE assigned to each gauge by all holders determines the quantity of rewards to be distributed. Once this is done, users don't have to vote again every week except if they want to change them. Votes for a given gauge can only be changed **every 10 days**, so that each votes apply for at least two weeks.

A person can also decide not to allocate all their available voting power.

{% hint style="info" %}
When updating gauge weights and putting more weight on one gauge with respect to another, users should be wary of doing decreases first then increases.
{% endhint %}

{% hint style="info" %}
When increasing the veANGLE balance by locking more tokens or extending a lock, this new veANGLE balance is not taken into account in the current vote allocation. Be careful to apply this new voting power. More info on the [Increasing veANGLE balance page](increasing-veANGLE.md).
{% endhint %}

## ANGLE Issuance Rate

The rate of emission of ANGLE tokens remains unchanged. For details about the ANGLE emission rate, please refer to [this page](/governance/staking.md).

Essentially, the weekly decrease factor of 1.007827 of the ANGLE emissions is guaranteed on-chain.

With such a decreasing factor, distribution with this system is bound to continue and to remain significant for a period of over 10 years.

veANGLE stakers can therefore feel confident staking the maximum duration of 4 years knowing that the gauge program is not temporary and won't be deprecated any time soon.

## Gauge Types

The idea with Angle gauges is to incentivize different types of liquidity pools useful to the protocol:

- agEUR liquidity and markets
- sanTokens
- Perpetuals
- Liquidity pools on exchanges (like on Curve, on Uniswap)
- Liquidity pools on other chains (like agEUR/USDC on Quickswap on Polygon for instance)

The gauge system can also be used to incentivize different things than staking contracts. For instance, incentives for Convex voters on Curve can be linked to a gauge (in fact an EOA or a multisig) where veANGLE owners decide to send some rewards, and the multisig would be responsible for placing the incentives on Votium.

Overall, there is no restriction on which pools or pairs can have a gauge other than that they should pass the gauge governance vote. The idea is however that all gauges should have a link with the agEUR or the Angle protocol, as the governance token of the protocol is being distributed as incentive.

Given that a wide range of contracts can be considered Angle protocol gauges, the system distinguishes several gauge types:

- Type 0 Gauges: mainnet staking contracts internal to the Angle Protocol. LPs of these gauges can receive boosted rewards.
- Type 1 Gauges: corresponding to Angle Perpetual staking contracts. Note that there is no boost for veANGLE holders in these contracts.
- Type 2 Gauges: External staking contracts. This gauge type includes all staking contracts **not on Angle on Ethereum Mainnet**, whether they are on other protocols (Curve or Convex) or on other chains (Polygon or Avalanche).

{% hint style="info" %}
It has been planned that gauge of type strictly greater than 2 would be for gauges on other networks. No such gauge exists for the moment, and gauges that are not on Ethereum mainnet are currently all of type 2.
{% endhint %}

### Gauge type weight

Each gauge type has its own weight, which can be set to shift the distribution of rewards in favor of one or another type of gauges. At the moment, the weights are all set equally so it has no impact. Governance can vote to change these gauge type weights.

**Example**
Assuming an inflation rate $$r$$ changing with every epoch (1 week), a gauge weight $$w_g$$ and a gauge type weight $$w_t$$, then the stream of inflation going to a gauge is:

$$
r' = w_g \times w_t \times r
$$

Every week, depending on gauge votes, the weight $$w_g$$ can change. Governance can also vote to update the weight $$w_t$$.
