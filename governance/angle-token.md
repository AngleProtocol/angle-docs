---
description: The ANGLE governance token for Angle DAO
---

# 🚀 ANGLE Token

## 🎨 Design and Inflation

ANGLE's total initial supply is 1 billion and there is no planned token inflation.

The only address with minting capability is the Angle DAO Multisig.

ANGLE's tokenomics was upgraded in January 2022 with the ability to lock ANGLE into veANGLE, similarly to what Curve does with CRV/veCRV. More info about veANGLE can be found [here](veANGLE/).

## 🧬 Tokenomics

The ANGLE token is the backbone of the Angle Protocol allowing it to be governed in a fully decentralized way.

The vision for the ANGLE distribution is that it needs to be multi-year, extended, and sustainable until the protocol reaches ubiquity. With this in mind, the token distribution was broken down as follows:

![ANGLE Distribution](../.gitbook/assets/angle-token-allocation.jpg)

### 🪐 Liquidity Mining

40% of tokens are being distributed through whitelisted staking contracts (called gauges) for like agTokens holders, HAs, SLPs as well as LPs on other external pools and protocols (like UniV3 or Curve).

The amount of ANGLE distributed is divided by 1.5^(1/52) = 1.007827 every week, equivalent to dividing the tokens emission by 1.50 every year.

![ANGLE issuance schedule](../.gitbook/assets/liquidity-incentives-distribution.jpg)

{% hint style="info" %}
On the 19th of October 2022, [it was voted](https://snapshot.org/#/anglegovernance.eth/proposal/0x478e838b67f2dffcff6160d4c8adc9622d67db985c981e4cad45c031e284fd63) to reduce ANGLE inflation by 20% with respect to the planned schedule. The week over week decrease factor of 1.007827 remains the same though.
{% endhint %}

#### Eligible gauges

Contracts where ANGLE inflation is routed need to be whitelisted by the Angle DAO through a governance vote. Usually, these are specific contracts where users must put their liquidity (LP tokens, sanTokens, agEUR, ...) if they want to get access to the ANGLE emissions.

{% hint style="info" %}
Available gauges of the protocol can be found [here](https://developers.angle.money/overview/smart-contracts/mainnet-contracts#gauges). Note that whitelisted contracts can be killed which means that a contract can stop receiving ANGLE rewards if voted by Angle DAO. In this case, accumulated ANGLE rewards can still be claimed after the gauge has been removed.
{% endhint %}

In the case of perpetuals and if perpetuals are rewarded with ANGLE tokens, Hedging Agents do not need to stake any token on a contract and they're rewarded automatically as they have an open position.

It is possible though for the DAO to incentivze stakeholders on contracts that are not Angle native. This is notably the case of Curve LPs which can be directly incentivized with ANGLE tokens on Curve. In this particular case, there is no Angle native staking contract, but ANGLE emissions can still be routed through the contracts.

Compared with external staking contracts, some internal Angle gauge contracts present specific features designed to favor veANGLE holders. For instance, stakers can boost the rewards they receive by holding veANGLE. Note that this doesn't impact the inflation rate, and only change the rewards they receive compared to other LPs on this pool.

This boost can go up to x2.5 the base quantity of rewards, and depends on the liquidity on the staking contract and the veANGLE balance of the stakers. All the information about the boost can be found on the [boost](../../governance/veANGLE/boost.md) page.

#### Gauge Voting

Every week, governance is able to adjust the distribution of ANGLE tokens between the different types of eligible stakeholders through [gauge votes](../governance/veANGLE/gauges.md).

Precisely speaking, veANGLE holders assign specific weights of their voting power to the different gauges, and the sum of all the veANGLE assigned to each gauge by all holders determines the quantity of rewards to be distributed. Once weights are allocated, they are reverberated in the following weeks without users having to do anything except if they want to change it.

{% hint style="info" %}
The rewards weight allocation can change each week depending on the changes in voting power allocated. The process is detailed [here](../../governance/veANGLE/gauges.md).
{% endhint %}

5% of the ANGLE's weekly emissions are still controlled by the Core Team to be allocated without any vote by veANGLE holders. Idea is that the Core team can use this allocation for short-term programs used to bootstrap liquidity in some particular places that do not have to be whitelisted.

{% hint style="info" %}
[This document](https://docs.google.com/spreadsheets/d/1fxTBGEnOnzvpdBaeiDzy1j-g5-s75IhGPU8aOdu786g/edit?usp=sharing) summarizes where these 5% of the weekly ANGLE emissions are deployed.
{% endhint %}

Leftover tokens meant to be distributed by this medium are stored on the [`AngleDistributor` contract](https://etherscan.io/address/0x4f91F01cE8ec07c9B1f6a82c18811848254917Ab).

### DAO Treasury

20% of the tokens are controlled by the DAO Treasury: the DAO is able to vote for how and where to allocate these tokens.

This Treasury can be used to build protocol reserves through different incentives like Olympus Pro bonding programs, DAO-to-DAO swaps, or more, and to increase incentives through specific rewards programs.

ANGLE tokens from the DAO Treasury are stored on the governance multisig.

2% of these funds were however put in a [multisig](https://etherscan.io/address/0xe02f8e39b8cfa7d3b62307e46077669010883459) controlled by the Angle Core Team (called the `AngleMaster`) to get more flexibility when it comes to implementing programs like Olympus Pro.

This multisig is a 2/3 Gnosis multisig controlled by distinct Core Team members of the protocol (the 3 co-founders of the project).

### Grants and Partnerships

12% of the initial ANGLE are held by the Core Team in a multi-sig. These tokens are available for distribution to the Community as grants or bug bounties, to strategic partners like exchanges for listing, but also to the most active and helpful community members as well as to advisors helping the protocol grow.

Tokens from this pocket are stored in the `AngleMaster` multisig. Note that 1 of these 12% of tokens have been lent to Wintermute, our partner in charge of market making in centralized exchanges.

### Core team and early backers

These tokens are subject to a **3 years linear vesting**, to make sure that the core team and early backers remain fully committed to the protocol and the community.

- 18% to Angle Core Team
- 10% to early backers

With this vesting schedule, liquidity distributed through liquidity mining to the Community is guaranteed to be bigger than that going to team and early backers.

In order to reduce the exposure of the funds potentially at risk in this contrat (this contract has been forked from Maker's `DssVest`), not all the 18% of the tokens that have to be distributed to the team + early backers + advisors have been initially put in the [Vesting contract](https://etherscan.io/address/0x43365213237ab259c707bc2cbc3e07d123ae2ad5). The `AngleMaster` multisig regularly transfers tokens to this contract based on what's leftover in it.
