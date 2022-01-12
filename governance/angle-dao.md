---
description: The Decentralized Autonomous Organization driving Angle Protocol
---

# 🗳 Angle DAO

## 🔎 TL;DR

* Angle DAO is responsible for tuning and improving the protocol in order to make it sustainable and robust enough to become a building block of the DeFi space.
* Since the tokenomics upgrade to the veANGLE model, the Angle DAO is controlled by veANGLE holders through snapshot votes executed by a multi-sig composed of core team and community members.
* The Angle DAO is also responsible for deciding where to allocate the ANGLE tokens distributed as part of the liquidity mining program.

## 🔘 Responsibilities

While Angle Protocol was designed to completely minimize the need for an active governance to maintain the peg of the stablecoins (arbitrageurs can directly do it), there is still a need for an active governance to get involved in the protocol's decisions.

The Angle DAO is responsible for parameters tuning, deploying new stablecoins, accepting new collateral types for a given stablecoin, and for protocol upgrades and integrations.

In particular, it can make the following changes:

* Tune fee parameters for, among other things, users minting and burning, for Hedging Agents opening and closing their perpetuals, for the slippage of Standard Liquidity Providers, for the fraction of the fees that go to Standard Liquidity Providers, ...
* Grant/revoke roles
* Deploy new stablecoins
* Deploy/revoke new strategies to get yield and choose in which proportions to distribute this yield to SLPs
* Deploy/revoke collateral types
* Vote for [gauge rewards weights](veANGLE/gauges.md)
* Upgrade oracles and other contracts throughout the system
* Deploy the surplus of the protocol

## 🗣 Discussions and debates

For the DAO to be governed efficiently, the community needs to be able to discuss the different ways forwards and the improvements being proposed. This happens on our [Discord](https://discord.com/invite/5Af6xum9bc), where there is a dedicated **improvement-proposals** section.

More formal proposals are then dicussed in our governance forum at [gov.angle.money](https://gov.angle.money)

## 🗳 Voting

### General proposals

After proposals have been properly discussed, they can be voted on through a [Snapshot](https://snapshot.org/#/anglegovernance.eth/) vote. After the tokenomics upgrade of January 2022, veANGLE holders are the ones with voting power over the protocol. As such, they are the ones voting to approve and implement or dismiss a proposal concerning the Angle Protocol.

Finalized votes are then implemented by a multi-sig composed of core team and community members.

{% hint style="warning" %}
A signature from the multi-sig is required to enforce the outcomes of the Snapshot votes. In almost all cases, it will vote in-line with what is voted by veANGLE holders. However, proposals considered to be clear open attacks against the protocol will not be signed for.
{% endhint %}

### Voting on rewards distribution

Last, veANGLE holders of the DAO are responsible for deciding where the liquidity mining rewards get distributed. Voting on this happens on-chain and can be done through the gauge page of the [dao app](https://dao.angle.money). Users can allocate weights to the different pools they want rewards to be distributed to.

More info on the details of this process in the [Gauges](veANGLE/gauges.md) page.
