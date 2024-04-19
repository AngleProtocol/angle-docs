---
description: The Decentralized Autonomous Organization driving Angle Protocol
cover: ../.gitbook/assets/Angle-DAO-cover.jpg
coverY: -19
---

# 🗳 Angle DAO

## 🔎 TL;DR

- Angle is a decentralized protocol governed by a DAO responsible for tuning and improving the protocol.
- The Angle DAO is controlled by veANGLE holders through onchain votes. Angle governance enables the community of veANGLE holders to propose, vote, and implement changes through the administrative smart contract functions of the protocol.
- All the contracts of the Angle Protocol are controlled by a Timelock contract which ensures that no major change goes into effect before a 24h period allowing anyone to exit in due time if they are not inline with the vote as well as an emergency multisig to monitor and cancel potential governance attacks.
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

## 🗳 Angle onchain governance system

To implement changes to the protocol through the administrative smart contract functions its different modules support, Angle relies on an onchain governance system ruled by [veANGLE holders](./veANGLE/README.md).

This system is split between two main modules:

- a decision module: that is to say a voting mechanism
- an execution module capable of either bridging decisions to the chains the protocol is deployed on or simply executing these decisions on the chain where they are taken

![Angle Governance Overview](/.gitbook/assets/governance-voting-module.jpg)

{% hint style="warning" %}
All governance contract addresses can be found [here](https://developers.angle.money/overview/smart-contracts). The code for these smart contracts is available [here](https://github.com/AngleProtocol/angle-governance) and it is possible to interact with Angle voting module directly from the Angle App [here](https://app.angle.money).
{% endhint %}

### 🗣 Discussions and debates

Before involving any onchain action, the first step in any governance process is getting a proposal out to be debated.

Governance proposals and improvements are usually first discussed on our [Discord](https://discord.gg/47mmUUwfMu), where there is a dedicated **proposals** section.

More formal proposals (which are closer to being implemented) are then discussed in our governance forum at [gov.angle.money](https://gov.angle.money).

### Voting/Decision module

Once proposals have been discussed, they can be voted on Angle voting module. This module is deployed on Ethereum and is based largely on [OpenZeppelin Governor Bravo contracts](https://docs.openzeppelin.com/contracts/4.x/governance#proposal_lifecycle) that Compound or Uniswap rely on among others.

Practically speaking, through this system, anyone with enough voting power can submit a proposal to Angle governance smart contracts, under the form of onchain code. For any submitted proposal, there is a delay before it goes into effect. Once this delay is passed, veANGLE holders or their delegates can vote on the submitted code.

{% hint style="warning" %}
There is no front interface available to submit proposals. The [angle-governance](https://github.com/AngleProtocol/angle-governance) repository comes with prepared scripts and helpers to facilitate the submission of proposals onchain.
{% endhint %}

If a majority of veANGLE holders vote in favor of a proposal, and if the amount of voters with respect to the total supply of veANGLE at the start of the vote is big enough, proposals can then be pushed to the execution module of the protocol. If there is no majority of support or no quorum for the proposal, then it is simply cancelled and cannot lead to any onchain modification of the protocol's state.

Angle is by essence a cross-chain protocol with multiple contracts deployed across various networks. The hub for Angle governance is Ethereum, this is where the voting module of the protocol is deployed. Typically, veANGLE holders can vote on Ethereum for proposals that concern modules of the protocol deployed on Optimism.

#### Delegation

Participating in Angle onchain governance votes means owning veANGLE tokens. Any veANGLE token holder can participate in a governance vote without having to take any specific action beyond just voting.

Note that to be eligible to participate in a vote, you need to have secured a veANGLE position before the start of the vote. For every vote, the balance of veANGLE eligible to vote that is looked into is that at the timestamp at which the vote started. If you get some veANGLE after this timestamp, your balance will not be taken into account in the vote.

Due to the onchain nature of it, voting comes with a gas cost. Angle governance comes with a delegation feature that lets any veANGLE holder delegate its voting power to another address so that it does not have to worry about participating in every vote.

Once you have delegated to an address, you can at anytime delegate back to yourself to get your voting power. If you have never delegated your voting power, you do not need to delegate to yourself to participate in voting.

Note that due to how the veANGLE contract works, if you have delegated voting power, if you lock more ANGLE or increase the duration of your lock, you have to delegate your voting weight again.

#### Advanced features

Angle voting module comes with several add-ons with respect to the base `GovernorBravo` implementation from Compound or Uniswap

- **Fractional voting:** Angle Governance makes use of [ScopeLift’s fractional voting](https://github.com/ScopeLift/flexible-voting/blob/master/src/GovernorCountingFractional.sol). This allows for users to split their voting power between for/against/abstain. It also allows smart contracts/custodians to pass through the voting power to liquidity providers based on their relative LP stake.
- **Short-circuit:** It may be the case that the voting period is too short if a majority of veANGLE holders have already expressed their votes. Angle governance system enables votes to finish before the end if an oustanding majority of voters voted in favor.
- **Preventing late quorum:** If someone votes on a proposal and causes it to reach quorum right before the end of the voting period, then voting period can be extended for a period
- **Relative quorums:** quorums are expressed as fractions of the total veANGLE voting power

#### Parameters

With all this in mind, Angle voting module has been deployed with the following parameters:

- `proposalThreshold = 100k veANGLE`: amount of veANGLE tokens needed to create an onchain governance proposal
- `quorum = 20%`: This is the share of the veANGLE tokens which must be voting on a vote for it to be actually valid.
- `votingDelay = 24h`: amount of time between which a proposal is posted and vote on it starts.
- `votingPeriod = 4 days`: period of time during which it is possible to vote.
- `voteExtension = 3 hours`: how long a vote can be extended if someone causes it to reach quorum right before the end of the vote.
- `shortCircuitThreshold = 75%`: if the share of voters is higher than this short circuit threshold, then proposal does not have to go through the whole voting period before being executable.

### Execution module

The role of Angle execution module is to either execute the successfully voted proposals if these concern Ethereum actions or to bridge the voted payloads to the desired chains in the other case.

#### Timelock contract

On every chain where the protocol is deployed, there is a `Timelock` contract which is governor of all the protocol contracts (Borrowing module, Transmuter, ...) of its chain. When a payload is pushed into a protocol `Timelock` contract, **there is a 24h period** before this payload can effectively be implemented onchain and pushed to the destination contract.

Having timelocks ensures that protocol stakeholders always have the possibility to transparently see in advance any potential change and exit the protocol before it is implemented if they believe that it can be detrimental to them.

#### Canceller role and emergency multisig

The issue with such permissionless system is that it could expose the protocol to majority attacks, where people take control of the majority of the voting power and create votes designed to transfer the seizable funds of the protocol towards their addresses.

To protect against this kind of hacks, on all the `Timelock` deployments of the protocol there is an address which has the power to cancel the votes that succeed for these not to be executed. As governance is cross-chain, this is also a way to be robust against potential bridge hacks.

This canceller role is held by a multisig referred to as the emergency multisig of the protocol. In the previous implementation of the governance of the protocol, this multisig used to be the governance multisig of the protocol with admin rights over its different instances.

The precise role of this multisig is now to cancel proposals and votes that are blatant attacks against the protocol's stakeholders.

As Angle Protocol is available on different EVM compatible chains, there is one emergency multisig per chain. The addresses of the multisigs on all the different networks supported by Angle can be found [here](https://developers.angle.money/overview/smart-contracts).

The emergency multisigs are all composed of the same 6 people (three Angle Labs team members and three "public" crypto people). They require a minimum of 4 signatures to execute a transaction. The multi-sig signers are:

- Pablo Veyrat: [@pablo_veyrat](https://twitter.com/pablo_veyrat)
- Guillaume Nervo: [@GuillaumeNervo](https://twitter.com/GuillaumeNervo)
- Picodes: [@thePicodes](https://twitter.com/thePicodes)
- Sébastien Derivaux: [@SebVentures](https://twitter.com/SebVentures)
- Julien Bouteloup: [@bneiluj](https://twitter.com/bneiluj)
- [0xMaki](https://twitter.com/0xMaki)

Beyond the ability to cancel proposals on the Timelock contract (but not to push new proposals), on every chain, this emergency multisig also has [the guardian role](guardian.md) enabling it to take rapid action (to like pause the protocol) in case of unforeseen events.

#### Cross-chain

For successful votes on non-Ethereum proposals, payloads to execute are bridged to the chain of interest using LayerZero message passing technology before being sent to the `Timelock` contract of the concerned chain.

The execution flow for Angle governance can then be summarized as follows.

If the vote concerns an Ethereum action:

- The payload to execute is sent to the Ethereum `Timelock` contract. The Ethereum Timelock contract only accepts payload from the `AngleGovernor` contract
- After the timelock period ends, if the payload is not veto-ed by Angle Emergency multisig on Ethereum, it can be executed on Ethereum.

If the vote concerns an action on another chain:

- The payload to execute is sent to a contract on Ethereum that uses LayerZero to pass the message to the destination chain.
- Once the payload is received on the destination chain, it is sent to the `Timelock` contract of this chain, before being executed (if not cancelled by the emergency multisig).

#### Modularity and future design iterations

Right now, the Timelock contracts of the protocol only have one governing address, it is:

- on Ethereum: the `GovernorBravo` contract
- on other chains: the contract receiving LayerZero messages

Angle Governance system is fully modular. While it can work in a self-sufficient way as it is right now, governance could decide to add new governance frameworks also able to push payloads to the Timelock contract of their respective chain.

This could typically be used to add support for new, more comprehensive and cheaper voting systems handling for instance storage proofs and voting from L2s.

On another level, the contracts handling the access control of the protocol can support different governance addresses. While currently, on a given chain, the `Timelock` contract is the sole address with this role, governance could also vote onchain to grant this governor role to other addresses in parallel.

### Snapshot voting

For some proposals about offchain policy changes on for instance the governance processes of the protocol or about contracts of the protocol which have not been linked yet to the execution module, the protocol has a [Snapshot](https://snapshot.org/#/anglegovernance.eth/) space where veANGLE holders can vote and express their positions using gasless offchain signatures.

This Snapshot space can also be used to run temperature checks before votes that could be potentially disputed.

## Security

Angle governance infrastructure relies on different audited building blocks:

- the voting module and the `Timelock` contracts rely on reference implementations by OpenZeppelin
- the part of the execution module designed to bridge payloads from one chain to another is forked from [contracts developed and audited by LayerZero](<(https://github.com/LayerZero-Labs/omnichain-governance-executor/tree/main/audits)>) for this exact use case.
- The delegation mechanism for the voting module is forked from [FRAX audited delegation system](https://github.com/FraxFinance/frax-governance/blob/e465513ac282aa7bfd6744b3136354fae51fed3c/src/VeFxsVotingDelegation.sol) for veTokens.
- The smart contracts for the veANGLE token [have been audited by Chainsecurity](../resources/audits/README.md).
