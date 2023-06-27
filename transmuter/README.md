---
description: Transmuter Overview
---

# ⚗️ Transmuter Overview

## Introduction

Transmuter is one of the main minting mechanisms for Angle stablecoins.

It is conceived as a stablecoin backed by a basket of different assets (ideally denominated in the stablecoin's base currency) which can be used to mint or burn the stablecoin at oracle value.

It comes with built-in and automated mechanisms to maintain the exposure to each asset in the reserves within reasonable bounds. This enables the system to properly segregate and diversify the risks between the assets in the backing, and guarantees at the same time that in case of black swan events the system does not end up over-exposed to the weakest assets of its reserves.

Transmuter supports three main primary user actions: **Mint, Burn and Redeem**. The mint and burn actions rely on the idea that each asset in the reserves has a target price (absolute or variable) that is used to assess whether the current oracle price of the asset is depegging or not.

Practically speaking, these three operations work as follows:

- **Mint:** Stablecoins can be minted at oracle value from any of the supported assets with adaptive fees provided that the deviation of the asset used with respect to its target price is reasonable
- **Burn:** Stablecoins can be burnt at oracle value for any of the assets in the backing with adaptive fees, provided that the deviation of all assets to their respective target price are reasonable. The idea is to avoid capital outflows changing the exposures of the system in times of uncertainty.
- **Redeem:** Stablecoins can be redeemed at any time against a proportional amount of each asset in the backing. Users should have a way to exit at any time, and so this feature is available in any conditions.

While we go deeper in the following pages about the core principles behind the Transmuter system, this schema illustrates, in the case of agEUR, what the system's global mechanism looks like:

![Transmuter Global Mechanism for agEUR](../.gitbook/assets/docs-Transmuter-global-mechanism.jpg)

## 🏦 Main Properties

Built in the aftermath of the USDC depeg as an improvement over price stability modules for stablecoin protoocols, the Transmuter system is designed with the following key properties:

**Scalability:** Angle Transmuter enables minting and burning with limited fees from a wide range of assets. Its mechanisms work similarly with $1m TVL as with $1bn TVL

**Resilience:** The underlying mechanisms of the Transmuter system are all fully autonomous and predictable by all types of stakeholders. In case of a black swan event, Transmuter provides reasons to bet on the stablecoin returning to its target price.

**Trustlessness:** Transmuter is able to autonomously withstand unforeseen events, such as collateral depegs or hacks, without
requiring any governance intervention.

**Fairness:** There cannot be any bank run as redemptions are thought to break sequentiality between users.

**Robustness:** Transmuter can be used as a basket of different stablecoins or assets allowing collateral risk to be well diversified.

**Safety:** If fees are properly set, the design provides incentives to bring the basket of reserves to a target desired allocation. In case of a depeg, it is unprofitable to perform trades that leave the protocol holding weak assets.

**Gas-efficiency:** Thanks to a range of different optimizations, the system is able to minimize the gas needed to interact with it.

**Modularity:** The system can not only accept any type of asset in the backing, its implementation is such that it can work for any type of stablecoin. It is also compatible with the other Angle protocol's minting modules.

## Audits

The smart contracts of the Transmuter have been audited by Code4rena. The code and audits have been published in [our dedicated repository](https://github.com/AngleProtocol/angle-transmuter). They can also be accessed in the [Audits section](../resources/audits/) of this docs.

## Deployments

The Transmuter system is so far only deployed on Ethereum for agEUR. Related smart contract addresses can be found [here](https://developers.angle.money/overview/smart-contracts).
