---
description: The Decentralized Autonomous Organization driving Angle Protocol
---

# 🗳 Angle DAO

## 🔎 TL;DR

- Angle DAO is responsible for tuning and improving the protocol in order to make it sustainable and robust enough to become a building block of the DeFi space.
- The Angle DAO manages the protocol through a governance module controlled by the ANGLE token. Angle governance contracts have been imported from OpenZeppelin and Compound implementations. More technical info can be found in the [developers documentation](https://developers.angle.money/side-smart-contract-modules/governance).
- The Angle DAO is also responsible for deciding where to allocate the ANGLE tokens distributed as part of the liquidity mining program.

## 🔘 Responsibilities

While Angle Protocol was designed to completely minimize the need for an active governance to maintain the peg of the stablecoins (arbitrageurs can directly do it), there is still a need for an active governance to get involved in the protocol's decisions.

The Angle DAO is responsible for parameters tuning, deploying new stablecoins, accepting new collateral types for a given stablecoin, and for protocol upgrades and integrations.

In particular, it can make the following changes:

- Tune fee parameters for, among other things, users minting and burning, for Hedging Agents opening and closing their perpetuals, for the slippage of Standard Liquidity Providers, for the fraction of the fees that go to Standard Liquidity Providers, ...
- Grant/revoke roles
- Deploy new stablecoins
- Deploy/revoke new strategies to get yield and choose in which proportions to distribute this yield to SLPs
- Deploy/revoke collateral types
- Add/remove incentives contracts for stable holders, SLPs and HAs
- Upgrade oracles and other contracts throughout the system
- Change bonding curve parameters
- Deploy the surplus of the protocol

The Angle protocol naturally accumulates some surplus from transaction fees, yield and collateral appreciation. The DAO is also be responsible for deciding what to do with this surplus.
While a portion should serve as a buffer to continue to absorb collateral volatility and earn yield to grow over time, this surplus could for instance be allocated to support initiatives around the protocol or for ANGLE buybacks under the form of auctions like is done by Maker DAO.

Last, the DAO is responsible for deciding where the liquidity mining supply is to be distributed. Voting for this takes place on [Snapshot](https://snapshot.org/#/anglegovernance.eth/), and the results of the vote are for the moment implemented by a multi-sig controlled by members of the Angle Core Team.

## Parameters

Every protocol governance has a set of parameters that frame how proposals from the DAO can be submitted, voted, accepted and executed. They usually include at least a voting period, a quorum (minimum of votes in favor/neutral required for a proposal to be approved), and a proposal threshold (minimum number of tokens required to submit a proposal). In Angle governance module, these parameters are set as follows:

- Voting period: 3 days
- Quorum: 5M ANGLE, or 0.5% of the total supply.
- Proposal threshold: 2.5M ANGLE, or 0.25% of the total supply.

These parameters have been set relatively low at the beginning, to ensure that the community will quickly be able to take part and lead the governance of the protocol. Later on, when Angle's governance is more established, some of these parameters could be updated by the DAO.

## 🎨 Design

The Angle governance module is forked from OpenZeppelin Governor Bravo and Timelock.

Still, the Angle Protocol implementation enables a flexible access control and governance module systems. The Timelock contract is appointed as a governor, but there could be multiple governors in the system. It also does not have to be a governor forever. Angle Protocol can appoint autonomous governors to adjust parameters. Additionally, a tiered governance structure can be implemented where certain changes require higher quorum thresholds and longer timelocks, like what is done in Aave.

Ultimately the Angle DAO makes all of these decisions as the protocol evolves.
