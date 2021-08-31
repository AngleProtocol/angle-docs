---
description: The Decentralized Autonomous Organization driving Angle Protocol
---

# 🗳 Angle DAO

## 🔎 TL;DR

* Angle's DAO is responsible for tuning and improving it in order to make the protocol a building block of the DeFi space.
* The structure of the DAO has been forked from that of [Compound](https://compound.finance/governance).

## 🔘 Responsibilities

A core principle of Angle Protocol is its decentralized nature and the DAO that will work on it from the beginning. While Angle Protocol was designed to completely minimize the need for an active governance to maintain the peg of the stablecoins (arbitrageurs can directly do it), there is still need for a governance and a DAO to get involved in the protocol's maintenance.

The DAO will be responsible for parameters tuning, for deploying new stablecoins, for accepting new collateral types for a given stablecoin, for protocol upgrades and integrations.

The Angle DAO can make the following changes:

* Tune fee parameters for, among other things, users minting and burning, for Hedging Agents opening and closing their perpetuals, for the slippage of Standard Liquidity Providers, for the fraction of the fees that go to Standard Liquidity Providers, ...
* Grant/revoke roles
* Deploy new stablecoins
* Deploy/revoke new strategies to get yield
* Deploy/revoke collateral types
* Add/remove incentives contracts for stable holders, SLPs and HAs
* Upgrade oracles and other contracts throughout the system 
* Change bonding curve parameters
* Deploy the surplus of the protocol

## 🎨 Design

The Angle DAO is forked from the Compound Governor Beta and Timelock.

Angle Protocol implementation enables a flexible access control system. The Timelock is appointed as a governor, but there could be multiple governors in the system. It also does not have to be a governor forever. Angle Protocol can appoint autonomous governors to adjust parameters. Additionally, a tiered governance structure can be implemented where certain changes require higher quorum thresholds and longer timelocks, like what is done in Aave.

Ultimately the Angle DAO makes all of these decisions as the protocol evolves.

{% hint style="info" %}
Key parameters (like the quorum, the proposal threshold, the voting delay) are still to be tuned.
{% endhint %}

