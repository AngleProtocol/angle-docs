---
description: The ANGLE governance token for Angle DAO
cover: ../.gitbook/assets/ANGLE-TOKEN-cover.jpg
coverY: 0
---

# 🚀 ANGLE Token

## 🎨 Design and Inflation

ANGLE's total initial supply is 1 billion and there is no planned token inflation.

The only address with minting capability is the Angle Governor Multisig.

## 🧬 Tokenomics

The ANGLE token is the backbone of the Angle Protocol allowing it to be governed in a fully decentralized way.

The vision for the ANGLE distribution is that it needs to be multi-year, extended, and sustainable until the protocol reaches ubiquity. With this in mind, the token distribution was broken down as follows:

![ANGLE Distribution](../.gitbook/assets/angle-token-allocation.jpg)

### 🪐 Liquidity Mining

40% of tokens are being distributed through whitelisted contracts (called gauges) for agTokens holders providing liquidity on external pools and protocols (like UniV3 or Curve).

The amount of ANGLE distributed is divided by 1.5^(1/52) = 1.007827 every week, equivalent to dividing the tokens emission by 1.50 every year.

![ANGLE issuance schedule](../.gitbook/assets/liquidity-incentives-distribution.jpg)

#### Eligible gauges

Contracts and places where ANGLE inflation is routed need to be whitelisted by the Angle DAO through a governance vote.

{% hint style="info" %}
Available gauges of the protocol can be found [here](https://developers.angle.money/overview/smart-contracts/mainnet-contracts#gauges). Note that whitelisted contracts can be killed which means that a contract can stop receiving ANGLE rewards if voted by Angle DAO. In this case, accumulated ANGLE rewards can still be claimed after the gauge has been removed.
{% endhint %}

Some Angle gauges (type 0 gauges and some type 2 gauges) present specific features designed to favor veANGLE holders. People eligible for rewards within these gauges can earn a boost in the emissions they receive if they hold veANGLE tokens. Note that this doesn't impact the inflation rate, and only changes the rewards they receive compared to other LPs on the concerned pools.

This boost can go up to x2.5 the base quantity of rewards. It also depends on the liquidity available for rewards and on the veANGLE balance of the stakers. More information about boosting can be found on the [boost](veANGLE/boost.md) page.

#### Gauge Voting

Every week, governance is able to adjust the distribution of ANGLE tokens between the different types of eligible stakeholders through [gauge votes](veANGLE/gauges.md).

Precisely speaking, veANGLE holders assign specific weights of their voting power to the different gauges, and the sum of all the votes assigned to each gauge by veANGLE holders determines the quantity of rewards to be distributed. Once weights are allocated, they are reverberated in the following weeks without users having to do anything except if they want to change it.

{% hint style="info" %}
The rewards weight allocation can change each week depending on the changes in voting power allocated. The process is detailed [here](veANGLE/gauges.md).
{% endhint %}

5% of the ANGLE's weekly emissions are still controlled by the guardian multisig signers to be allocated without any vote by veANGLE holders. Idea is that this allocation can be used for short-term programs to bootstrap liquidity in some particular places that do not have to be whitelisted.

{% hint style="info" %}
[This document](https://docs.google.com/spreadsheets/d/1fxTBGEnOnzvpdBaeiDzy1j-g5-s75IhGPU8aOdu786g/edit?usp=sharing) summarizes where historically these 5% of the weekly ANGLE emissions are deployed.
{% endhint %}

Leftover tokens meant to be distributed by this medium are stored on the [`AngleDistributor` contract](https://etherscan.io/address/0x4f91F01cE8ec07c9B1f6a82c18811848254917Ab).

### DAO Treasury

20% of the tokens are controlled by the DAO Treasury: the DAO is able to vote for how and where to allocate these tokens.

This Treasury can be used to build protocol reserves through different incentives like DAO-to-DAO swaps, or more, and to increase incentives through specific rewards programs.

ANGLE tokens from the DAO Treasury are stored on the governance multisig.

2% of these funds were however put in a [multisig](https://etherscan.io/address/0xe02f8e39b8cfa7d3b62307e46077669010883459) controlled by the guardian multisig signer (called the `AngleMaster`) to get more flexibility when it comes to implementing programs like Olympus Pro.

This multisig is a 2/3 Gnosis multisig controlled by the 3 co-founders of the protocol.

### Grants and Partnerships

12% of the initial ANGLE are held by Angle Labs in a multi-sig. These tokens are available for distribution to the Community as grants or bug bounties, to strategic partners like exchanges for listing, but also to the most active and helpful community members as well as to advisors helping the protocol grow.

Tokens from this pocket are stored in the `AngleMaster` multisig.

### Angle Labs team and early backers

These tokens are subject to a **linear vesting of 3 years (starting October 2021)**.

* 18% to Angle Labs team members
* 10% to early backers

With this vesting schedule, liquidity distributed through liquidity mining to the Community is guaranteed to be bigger than that going to team and early backers.

In order to reduce the exposure of the funds potentially at risk in this contract (this contract has been forked from Maker's `DssVest`), not all the 18% of the tokens that have to be distributed to the team + early backers + advisors have been initially put in the [Vesting contract](https://etherscan.io/address/0x43365213237ab259c707bc2cbc3e07d123ae2ad5). The `AngleMaster` multisig regularly transfers tokens to this contract based on what's leftover in it.

## Changelog

* January 2022: ANGLE's tokenomics was upgraded with the ability to lock ANGLE into veANGLE, similarly to what Curve does with CRV/veCRV. More info about veANGLE can be found [here](veANGLE/).
* October 2022: [it was voted](https://snapshot.org/#/anglegovernance.eth/proposal/0x478e838b67f2dffcff6160d4c8adc9622d67db985c981e4cad45c031e284fd63) to reduce ANGLE inflation by 20% with respect to the planned schedule. The week over week decrease factor of 1.007827 remains the same though.
* March 2023: ANGLE emissions were paused during this period and resumed late April 2023.
