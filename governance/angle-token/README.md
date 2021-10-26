---
description: The ANGLE governance token for Angle DAO
---

# 🚀 ANGLE Token

## 🔎 TL;DR

Angle Protocol is governed by the community through the ANGLE governance token.

## 🎨 Design and Inflation

ANGLE's total initial supply is 1 billion and there is no planned token inflation.

The only situation in which the total supply might increase is in the case of a protocol failure, if the governance needs to sell tokens through the [bonding curve](bonding-curve.md) to recollateralize the protocol.

If the protocol has a too big surplus, some tokens could also be burnt, like what Maker does in some situations.

The only address with minting capability is the Angle DAO Timelock. The design of the token has been heavily inspired by Uniswap's UNI token.

## 🧬 Tokenomics

The goals is for ANGLE's ownership to be decentralized, and that it the token be distributed to people from the community which use the protocol or collateralize it as HAs or SLPs.

ANGLE tokens will be distributed as follows:

### Liquidity Mining

- 40% of tokens will be distributed through staking contracts for agTokens holders, HAs and SLPs. LP on other external pools will also probably be incentivized. Governance will be able to adjust the distribution of tokens between each stakeholders. The amount of ANGLE distributed will be divided by 1.5^(1/52) = 1.007827 every week, equivalent to dividing the tokens emission by 1.50 every year.

### DAO Treasury

**Bonding curve and future protocol incentives**

- 18% Through the [bonding curve](bonding-curve.md) when it is activated. Whenever the market price of the tokens will be superior to that proposed by the protocol, people will be incentivized to buy to the protocol. The goal is that the money received will serve as a surplus to the protocol.
- 2% For future protocol incentive: this is a pocket that is controlled by the DAO and that can be seen as a buffer to avoid token inflation, it could for instance be distributed in the bonding curve or in staking contracts.

{% hint style="info" %}
The distribution of tokens between the bonding curve and future protocol incentives specified here may change slightly.
{% endhint %}

### Grants and Partnerships

- 10% to Angle's current and future strategic partners
- 2% for grants and advisors of Angle Labs

### Core team and early backers

Tokens subject to a **3 years linear vesting**, to make sure that the core team and early backers remain fully committed to the protocol and the community.

- 18% to the Angle Core Team
- 10% to early backers

{% hint style="info" %}
Distribution through the bonding curve will not be activated from the start, but can be at anytime by the governance.
{% endhint %}

![Angle](../../.gitbook/assets/ICONS_ANGLE_LOGO_COLOR_GRADIENT.svg)
