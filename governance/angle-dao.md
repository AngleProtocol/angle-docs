---
description: The Decentralized Autonomous Organization driving Angle Protocol
cover: ../.gitbook/assets/Angle-DAO-cover.jpg
coverY: -19
---

# 🗳 Angle DAO

## 🔎 TL;DR

- Angle DAO is responsible for tuning and improving the protocol in order to make it sustainable and robust enough to become a building block of the DeFi space.
- The Angle DAO is controlled by veANGLE holders through Snapshot votes executed by a multi-sig composed of community members.
- The Angle DAO is also responsible for deciding where to allocate the ANGLE tokens distributed as part of the liquidity mining program.

## 🔘 Responsibilities

The Angle DAO is responsible for parameters tuning, deploying new stablecoins, accepting new collateral types for a given stablecoin, for treasury management and for protocol upgrades and integrations.

In particular, it can make the following changes:

- Tune fee parameters. In the Borrowing module, the DAO can for instance change the collateral factors or the borrowing interest rates
- Grant/revoke roles
- Deploy new stablecoins
- Deploy/revoke collateral types across the different modules of the protocol
- Vote for [gauge rewards weights](veANGLE/gauges.md)
- Upgrade oracles and other contracts throughout the system
- Deploy the surplus of the protocol
- Launch new Direct deposit modules
- Launch new Angle Protocol products

## 🗣 Discussions and debates

Governance proposals and improvements are first discussed on our [Discord](https://discord.com/invite/5Af6xum9bc), where there is a dedicated **improvement-proposals** section.

More formal proposals (which are closer to being implemented) are then discussed in our governance forum at [gov.angle.money](https://gov.angle.money)

## 🗳 Voting

### General proposals

After proposals have been properly discussed, they can be voted on through a [Snapshot](https://snapshot.org/#/anglegovernance.eth/) vote.

veANGLE holders are the ones with voting power over the protocol: they are the ones voting to approve and implement or dismiss a proposal concerning the Angle Protocol. If they don't want to participate in Snapshot all votes, they have the opportunity to [delegate their voting power](../guides/app-guides/ANGLE/snapshot-votes.md) to other addresses.

Each vote requires a quorum of 10% of veANGLE holders to be considered valid.

Finalized votes are then implemented by a multi-sig composed of community members. The fact that a multisig needs to implement transactions makes Angle governance system immune to onchain governance attacks.

Angle Protocol is available on different EVM compatible chains. There is one multisig per chain, each with the same signers detailed below. The addresses of the multisigs on all the different networks supported by Angle can be found [here](https://developers.angle.money/overview/smart-contracts).

{% hint style="warning" %}
A signature from the multi-sig is required to enforce the outcomes of the Snapshot votes. In almost all cases, it will implement what is voted by veANGLE holders. However, proposals considered to be clear open attacks against the protocol will not be signed for. Having a multisig enforcing proposals is hence tantamount to having a `Timelock` contract for the protocol that can prevent the enforcement of malicious governance proposals.
{% endhint %}

### Governance Multi-Sig Signers

On each of the chain on which Angle protocol is deployed, the protocol's multisig is composed of the same 6 people (three Angle Labs team members and three "public" crypto people). It requires a minimum of 4 signatures to execute a transaction. The multi-sig signers are:

- Pablo Veyrat: [@pablo_veyrat](https://twitter.com/pablo_veyrat)
- Guillaume Nervo: [@GuillaumeNervo](https://twitter.com/GuillaumeNervo)
- Picodes: [@thePicodes](https://twitter.com/thePicodes)
- Sébastien Derivaux: [@SebVentures](https://twitter.com/SebVentures)
- Julien Bouteloup: [@bneiluj](https://twitter.com/bneiluj)
- [0xMaki](https://twitter.com/0xMaki)

### Voting on rewards distribution

Last, veANGLE holders of the DAO are responsible for deciding where the liquidity mining rewards get distributed. Voting on this happens onchain and can be done through the gauge page of the [app](https://app.angle.money/gauge). Users can allocate weights to the different pools they want rewards to be distributed to.

More info on the details of this process in the [Gauges](veANGLE/gauges.md) page.
