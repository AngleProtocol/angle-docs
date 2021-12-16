---
description: The ANGLE governance token for Angle DAO
---

# 🚀 ANGLE Token

## 🔎 TL;DR

Angle Protocol is governed by its DAO through the ANGLE governance token.

## 🎨 Design and Inflation

ANGLE's total initial supply is 1 billion and there is no planned token inflation.

The only situation in which the total supply might increase is in the case of a protocol failure or in a black swan event, if the governance needs to sell tokens through the [bonding curve](bonding-curve.md) to recollateralize the protocol.

If the protocol has a too big surplus, some tokens could also be burnt through buybacks, like what Maker does in some situations.

The only address with minting capability is the Angle DAO Timelock. The design of the token has been heavily inspired by Uniswap's UNI token, and its distribution from Curve's CRV token.

## 🧬 Tokenomics

The main purposes of the ANGLE token are to get as many people involved as possible in the governance of the protocol, to help the protocol own and control a portion of its reserves and to incentivize users, Standard Liquidity Providers and Hedging Agents. Its ownership should be decentralized.

The vision for the ANGLE distribution is that it needs to be multi-year, extended, and sustainable until the protocol reaches ubiquity. With this in mind, the token distribution is broken down as follows:

![ANGLE Distribution](../../.gitbook/assets/allocation.png)

### Liquidity Mining

40% of tokens will be distributed through staking contracts for agTokens holders, HAs, SLPs. LP on other external pools will also probably be incentivized. For more details on Angle's staking contracts, you can look at this [page](../../concepts/staking.md).

Every week, governance will be able to adjust the distribution of tokens between each stakeholder. The amount of ANGLE distributed will be divided by 1.5^(1/52) = 1.007827 every week, equivalent to dividing the tokens emission by 1.50 every year.

Details on how ANGLE token owners can vote to allocate the liquidity mining supply are available in [this page](../voting.md).

### DAO Treasury: Bonding Curve and Future Protocol Incentives

20% of the tokens are controlled by the DAO Treasury: the DAO will be able to vote for how and where to allocate these tokens.

Overall, the idea of the Angle Core Team is to distribute it as follows:

* 18% Through the [bonding curve](bonding-curve.md) when it is activated. Whenever the market price of the tokens will be superior to that proposed by the protocol, people will be incentivized to buy to the protocol. The goal is that the money received will serve as a surplus to the protocol.
* 2% For future protocol incentive: this pocket controlled by the DAO can be seen as a buffer to avoid token inflation, it could for instance be distributed in the bonding curve or in staking contracts.

{% hint style="info" %}
The distribution of tokens between the bonding curve and future protocol incentives specified here may change because community will always end up deciding. Besides, distribution through the bonding curve will not be activated from the start, but can be at anytime by the governance.
{% endhint %}

### Grants and Partnerships

12% of the initial ANGLE are held by the Core Team in a multi-sig. These tokens are available for distribution to the Community as grants or bug bounties, to strategic partners like exchanges for listing, but also to the most active and helpful community members as well as to advisors helping the protocol grow.

### Core team and early backers

Tokens subject to a **3 years linear vesting**, to make sure that the core team and early backers remain fully committed to the protocol and the community.

* 18% to the Angle Core Team
* 10% to early backers

With this vesting schedule, liquidity distributed through liquidity mining to the Community is guaranteed to be bigger than that going to team and early backers.

For more details on the tokenomics, this article adds some details:

{% embed url="https://blog.angle.money/angle-protocol-tokenomics-29ea8b7bf001" %}
Angle Tokenomics
{% endembed %}

![Angle](../../.gitbook/assets/ICONS\_ANGLE\_LOGO\_COLOR\_GRADIENT.svg)
