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

{% hint style="info" %}
The voting process deciding the rewards allocation takes place each week, and is detailed [here](../governance/voting.md).
{% endhint %}
