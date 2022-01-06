---
description: Details of Staking with Angle Protocol
---

# 🎁 Staking - Getting Governance Tokens

## 🔎 TL;DR

A portion of Angle's governance tokens are distributed to protocol and agToken users.

## 💡 Rationale

Angle aims to be a decentralized protocol. To this extent, the protocol will only succeed if the ownership of the governance token backing the protocol is decentralized.

A vast portion of the governance tokens are distributed through staking contracts by the protocol to protocol and agToken users. This include Hedging Agents, SLPs, and agToken LPs on specific pools.

While Hedging Agents automatically can accumulate governance tokens automatically as they stay in the protocol, Standard Liquidity Providers as well as stable holders have to stake their tokens (sanTokens for SLPs and agTokens for stable holders) in specific contracts to earn governance tokens. The protocol leaves them the opportunity to stake directly and seamlessly from the app after having minted.

## 💐 Token Distribution

The distribution of governance tokens between the different staking contracts (called gauges) happens through weekly votes from veANGLE token holders. They assign specific weights to the different gauges, and the sum of their votes will dictate the next rewards distribution.

400,000,000 ANGLE (40% of the total supply) is being distributed through staking. The amount being distributed are divided by 1.5^(1/52) = 1.007827 every week, equivalent to dividing the distribution by 1.50 every year.

![ANGLE Distribution](../.gitbook/assets/Liquidity-Mining-Distributed-Supply-Over-Time.png)

We built some simulations to evaluate how supply evolves over time, you can take a look at this [Google Sheet](https://docs.google.com/spreadsheets/d/1yraSUH_7D-VMnCUsIYWWdW1pxL7bDxN3o0M5japQmeY/edit#gid=0).

## 🪐 Gauges and rewards allocation

Each staking contract receiving rewards should have a dedicated gauge. Gauges are used so that veANGLE holders can dedicate their voting powers to influence the distribution of ANGLE rewards between the different staking contracts.

veANGLE holders assign specific weights of their voting power to the different gauges, and the sum of all the veANGLE assigned to each gauge by all holders will determine the quantity of rewards to be distributed. Once weights are allocated, they will be reverberated in the following weeks without users having to do anything except if they want to change it.

{% hint style="info" %}
The rewards weight allocation can change each week depending on the changes in voting power allocated. The process is detailed [here](../governance/veANGLE/gauges.md).
{% endhint %}

## 💥 Boost on rewards

Stakers on contracts internal to Angle can boost the rewards they receive by holding veANGLE. Note that this doesn't impact the inflation rate, and only change the rewards they receive compared to other LPs on this pool.

This boost can go up to x2.5 the base quantity of rewards, and depends on the liquidity on the staking contract and the veANGLE balance of the stakers. All the information about the boost can be found on the [boost](../governance/veANGLE/boost.md) page.

{% hint style="info" %}
The boost on rewards apply only to staking contracts internal to Angle (gauge type 0, more info in the [gauge](../governance/veANGLE/gauges.md) page), and not external ones taking place on other protocols or networks.
{% endhint %}
