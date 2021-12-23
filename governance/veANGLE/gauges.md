---
description: How the gauge system works with Angle
---

# 🗳 Gauges

## 🔎 TL;DR

* veANGLE holders are able to decide where weekly ANGLE emissions go through gauge votes
* The fact that veANGLE holders are responsible for such vote alines incentives within the protocol

## ✍️Gauge Vote Principle

Besides voting on governance proposals, veANGLE owners can vote for ANGLE gauge weights with their veANGLE balance. The gauge system implemented by Angle is similar to that of Frax and of Curve.

Like what was done weekly on Snapshot by ANGLE holders before the Angle Governance upgrade, veANGLE holders will now be able to distribute their voting power across a single or multiple gauges on-chain.

A gauge corresponds in fact to a staking contract and by voting for a gauge a veANGLE owner increases the amount of ANGLE tokens sent to the related staking contract with respect to other staking contracts. veANGLE owners will therefore vote for the gauges they think should receive more weight.

This allows veANGLE holders who are the most long term users of the protocol to have complete control over the future ANGLE emission rate.

## ↔️Incentives alinement

Interestingly, the gauge system lowers the influence of ANGLE pairs and pools where the majority of rewards are sold off since those LPs will not have veANGLE to continue voting for their pair.

This system strongly favors LP providers who continually stake their rewards for veANGLE to increase their pool's gauge weight. Essentially, and like mentionned in [Frax docs](https://docs.frax.finance/vefxs/gauge), Angle gauges align incentives of veANGLE holders so that the most long term oriented ANGLE holders control where ANGLE emissions.

## In Practice

Gauge weights are updated once every week every Thursday at 2am CET. This means that the ANGLE emission rate for each pair is constant for 1 week then updates to the new rate on each Thursday morning. Any user can change their weight allocation for a given gauge every 10 days.

Weights of a given user for a gauge is given in basis points (units of 0.01%), this means that a veANGLE owner has 10000 weights to allocate.

For instance, a user could decide to allocate 5000 to a gauge and 5000 to another. This means that this person would allocate 50% of its voting power to each of the two gauges.

A person could also decide not to allocate all its available voting power. 3000 weights could be given to a gauge, and leave 7000 unallocated.

{% hint style="info" %}
When updating gauge weights and putting more weight on one gauge with respect to another, users should be wary of doing decreases first then increases.
{% endhint %}

## ANGLE Issuance Rate

The rate of emission of ANGLE tokens will remain unchanged after the upgrade. For details about the ANGLE emission rate, please refer to [this page](../concepts/staking.md).

Essentially, the weekly decrease factor of 1.007827 of the ANGLE emissions will be guaranteed on-chain.

With such a decreasing factor, distribution with this system is bound to continue and to remain significant for a period of over 10 years.

veANGLE stakers can therefore feel confident staking the maximum duration of 4 years knowing that the gauge program is not temporary and won't be deprecated any time soon.

## Gauge Types

Curve introduced the gauge system for their CRV token emissions. Users lock their veCRV to vote on "weights" of different Curve liquidity pools. The idea with Angle gauges is to incentivize different types liquidity pools useful to the protocol:

* agEUR single side staking
* sanTokens owners
* Perpetual owners
* Liquidity pools on exchanges (like on Curve, on Uniswap)
* Liquidity pools on different chains (like agEUR/USDC on Quickswap on Polygon for instance)

The gauge system could also be used to incentivize different things than staking contracts. For instance, incentives for Convex voters on Curve could be linked to a gauge (in fact an EOA or a multisig) where veANGLE owners decide to send some rewards and responsible for then placing the incentives on Votium.

Overall, there is no restriction on which protocols or pairs can have a gauge weight other than that they should pass the gauge governance vote. The idea is however that gauges should all be linked with agEUR stablecoin or protocol.

Given that a wide range of contracts could be considered Angle protocol gauges, the system distinguishes several gauge types. Each gauge therefore has in addition to its weight from people who voted for it a type:

* Type 0 Gauges: corresponding to normal staking contracts of the protocol
* Type 1 Gauges: corresponding to Angle Perpetual contracts. Note that there will be no boosts for veANGLE holders in these contracts.
* Type 2 Gauges: for gauges which interface is not supported by the distributor contract. This could for instance correspond to gauges used for the distribution of ANGLE rewards to Convex voters. The address of the gauge would be the address of a multisig which would then transfer the reward to Convex
* Gauges with type > 2: this corresponds to gauges for staking contracts that are not on Ethereum mainnet. The addresses of these gauges is that of a contract that will bridge the rewards to the desired chain and then to the staking contract.

Each gauge type has its own weight. Assuming an inflation rate $$r$$ changing with every epoch (1 week), a gauge weight $$w_g$$ and a gauge type weight $$w_t$$, then the stream of inflation going to a gauge is:

$$
r' = w_g \times w_t \times r
$$

Every week, depending on gauge votes, the weight $$w_g$$ can change. Governance can also vote to update the weight $$w_t$$.
