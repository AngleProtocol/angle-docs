---
description: The ANGLE governance token for Angle DAO
---

# 🚀 ANGLE Token

## 🔎 TL;DR

Angle has a governance token, that we call so far the ANGLE token, collectively responsible for managing the Angle DAO.

## 🎨 Design and Inflation

ANGLE's total initial supply is 1 billion and there should be almost no inflation of the total supply.

The only situation in which the total supply is likely to inflate is where governance needs to be able to sell more tokens through the [bonding curve](bonding-curve.md) to recollateralize the protocol and thus needs to issue fresh new tokens for that.

If the protocol has a too big surplus, some tokens could also be burnt, like Maker does in some situations.

The only address with minting capability is the Angle DAO Timelock. The design of the token has been heavily inspired by Uniswap's UNI token. 

## 🧬 Tokenomics

The idea with Angle's governance token is to make its ownership decentralized and to distribute it to actors in the community which use the protocol or collateralize it as SLPs or HAs.

The governance token will be distributed as follows:

* 40% Through staking contracts for stable holders and SLPs or directly to HAs for the community. This mode of distribution is equivalent to that of Compound with the COMP tokens given to lenders and borrowers. Governance will be able to adjust the speed and amount of distribution for each stakeholder. The idea is to favor the SLPs of the different collateral pools.
* 18% Through the [bonding curve](bonding-curve.md) when it is activated. Whenever the market price of the tokens will be superior to that proposed by the protocol, people will be incentivized to buy to the protocol. The goal is that the money received will serve as a surplus to the protocol.
* 18% To Angle Core Team. These tokens are subject to a 3-year vesting to make sure that founders and team remain fully committed to the protocol and the community.
* 10% To seed investors (subject to the same 3-year linear vesting as Angle Core Team)
* 10% To Angle's current and future strategic partners
* 2% For grants and advisors of Angle Labs
* 2% For future protocol incentive: this is a pocket that is controlled by the DAO and that can be seen as a buffer to avoid token inflation, it could for instance be distributed in the bonding curve or in staking contracts

{% hint style="info" %}
Distribution through staking contracts and bonding curve may not initially be activated from scratch. In the beginning it is well possible that governance token ownership is still in majority controlled by Angle Labs. It is however the will of the team to rapidly push for decentralization.
{% endhint %}

{% hint style="info" %}
The numbers specified here may slightly change. It is for instance possible that a fraction of the 10% given to current and future strategic partners ends up being distributed through staking contracts. The same goes for the bonding curve. A smaller fraction of tokens may be sold by this medium; what's not sold by it will be distributed via staking.
{% endhint %}

