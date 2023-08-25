---
description: Angle Borrowing Module Overview
---

# 🔭 Borrowing Module Overview

## Introduction

Angle Borrowing Module is one of the minting mechanisms for Angle stablecoins.

It is based on a **debt mechanism**, similar to the one used by Maker with DAI. Users can deposit tokens as collateral into the protocol, and borrow agTokens from this deposit depending on specific parameters.

This module is designed to be easily deployable across different EVM compatible networks and to work for any kind of stablecoin of the protocol.

It is also designed to work hands in hands with the other protocol's modules: agEUR, which can also be minted by the protocol's direct deposit modules is for instance fully interoperable between both modules.

{% hint style="info" %}
Smart contract addresses associated to the Borrowing module on different chains and for the different stablecoins of the protocol can be found [here](https://developers.angle.money/overview/smart-contracts).
{% endhint %}

## 🏦 Main Features

**Borrowing agTokens from collateral deposit:** With the Angle Borrowing module, users can deposit collateral tokens in a vault and mint (borrow) agTokens from their deposits according to specific parameters. This allows them to keep exposure to their tokens deposited as collateral, while benefitting from disposable liquidity in stablecoins.

**Leveraged-yield and self-repaying loans:** Any yield-bearing token can be accepted as a collateral. Users can deposit collateral, borrow stablecoins and get their debt automatically repaid by the increase in value of their collateral. They can also swap their borrowed stablecoins for more of the yield-bearing token enabling them to boost the yield they are earning.

**Leveraging collateral exposure:** Users can also leverage their collateral token exposure through vaults, to get onchain leverage up to x10 depending on the parameters set by governance.

**Capital-efficient interactions:** Borrowing stablecoins from deposited collateral, liquidating a vault, repaying a debt and getting collateral back: all of this can be done in just one transaction and without any capital commitment thanks to the protocol built-in swap features.

**Optimized liquidations amounts and discounts:** Angle liquidation system is conceived as an improvement over more traditional liquidation mechanism (like on Aave, Compound, Maker). It allows for variable liquidations amounts meaning that during a liquidation the fraction of the debt that can be repaid is not fixed. On top of that, discounts given to liqudiators are based on a Dutch auction mechanism which minimizes the discount liquidators get while making sure they can still be profitable. This protects borrowers getting liquidated and lets them keep a maximum amount of collateral in their vaults.

**Improved position management:** Users can easily transfer their debt from one position to another without having to actually transfer collateral between these positions. All positions in this system are composable NFTs.

{% hint style="info" %}
[This section](vaults/) presents in greater details vaults in Angle Borrowing Module.
{% endhint %}

## Cross-chain Compatibility

**The Borrowing module can scale to a wide range of different networks and stablecoins**.

This allows governance to easily deploy it on networks like layer 2s where transactions are more affordable than on the Ethereum mainnet.
The Borrowing module for agEUR is for instance natively deployed on Ethereum but also on Polygon, Optimism, Arbitrum and Avalanche.

While the different networks on which the Borrowing module may be deployed for a stablecoin are necessarily inter-connected thanks to bridges, they remain distinct environments. Available liquidity and liquidators are not the same across two different chains, and there are some potential risks with having the same protocol deployed on multiple chains.

The main risk in having the Borrowing module on multiple networks is that liquidations may not behave properly. With less liquidity, there is more slippage and liquidations can be less profitable, increasing the risk that they don't happen.

To prevent this, each instance of the Borrowing module relies on different parameters chosen by governance. For instance, for a same collateral asset on two chains, there may be different amount of agEUR that can be issued on each network: this allows to make sure that liquidations remain profitable on a network based on the available liquidity.

## Audits

The smart contracts of the Borrowing module have been audited by Chainsecurity. The code and audits have been published in [our dedicated repository](https://github.com/AngleProtocol/borrow-contracts). They can also be accessed in the [Audits section](../resources/audits/) of this docs.
