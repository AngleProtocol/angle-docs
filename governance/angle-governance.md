---
description: The Decentralized Autonomous Organization driving Angle Protocol
---

# 🗳 Angle Governance

## 🔎 TL;DR

- Angle Governance is responsible for tuning and improving the protocol in order to make it sustainable and robust enough so it can become a building block of the DeFi space.
- Angle Governance contracts have been copied from OpenZeppelin and Compound implementations. More info in the [developers documentation](https://developers.angle.money/side-smart-contract-modules/governance).

## Parameters

Every protocol governance has a set of parameters that frame how proposals can be submitted, voted, accepted and executed. They usually include at least a voting period, a quorum (minimum of votes in favor/neutral required for a proposal to be approved), and a proposal threshold (minimum number of tokens required to submit a proposal). In Angle governance, these parameters are set as follows:

- Voting period: 3 days
- Quorum: 25M ANGLE, or 2.5% of the total supply.
- Proposal threshold: 2.5M ANGLE, or 0.25% of the total supply.

These parameters have been set relatively low at the beginning, to ensure that the community is able to take part and lead the governance of the protocol from the start. Later on, when Angle's governance is more established, some of these parameters could be updated by the Governance.

## 🔘 Responsibilities

While Angle Protocol was designed to completely minimize the need for an active governance to maintain the peg of the stablecoins (arbitrageurs can directly do it), there is still a need for an active governance to get involved in the protocol's decisions.

The DAO will be responsible for parameters tuning, deploying new stablecoins, accepting new collateral types for a given stablecoin, and for protocol upgrades and integrations.

The Angle Governance can make the following changes:

- Tune fee parameters for, among other things, users minting and burning, for Hedging Agents opening and closing their perpetuals, for the slippage of Standard Liquidity Providers, for the fraction of the fees that go to Standard Liquidity Providers, ...
- Grant/revoke roles
- Deploy new stablecoins
- Deploy/revoke new strategies to get yield
- Deploy/revoke collateral types
- Add/remove incentives contracts for stable holders, SLPs and HAs
- Upgrade oracles and other contracts throughout the system
- Change bonding curve parameters
- Deploy the surplus of the protocol

A core aspect of Angle Protocol is its decentralized nature. As such the end goal is to decentralize its governance as well. At first, governance proposals will be enforced through a multisig held by the Core Team. In the long-term, we hope that Angle DAO can take the lead and govern the protocol by itself.

## 🎨 Design

The Angle DAO is forked from the Compound Governor Beta and Timelock.

Angle Protocol implementation enables a flexible access control system. The Timelock is appointed as a governor, but there could be multiple governors in the system. It also does not have to be a governor forever. Angle Protocol can appoint autonomous governors to adjust parameters. Additionally, a tiered governance structure can be implemented where certain changes require higher quorum thresholds and longer timelocks, like what is done in Aave.

Ultimately the Angle DAO makes all of these decisions as the protocol evolves.
