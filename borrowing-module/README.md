---
description: Angle Borrowing Module Overview
---

# 🔭 Borrowing Module Overview

## Introduction

Angle Borrowing Module is another minting mechanism for Angle stablecoins.

This module works hand in hand with the Core module and agTokens, like agEUR, are fully interoperable between both modules. It is available natively on Ethereum mainnet and on other EVM compatible networks like Polygon or Optimism.

It is based on a **debt mechanism**, similar to the one used by Maker with DAI. Users can deposit tokens as collateral into the protocol, and borrow agTokens from this deposit depending on specific parameters.

{% hint style="info" %}
Smart contract addresses associated to the Borrowing module on different chains can be found [here](https://developers.angle.money/overview/smart-contracts).
{% endhint %}

## 🏦 Main Features

**Borrowing agTokens from collateral deposit:** With the Angle Borrowing module, users can deposit collateral tokens in a vault and mint (borrow) agTokens from their deposits according to specific parameters. This allows them to keep exposure to their tokens deposited as collateral, while benefitting from disposable liquidity in stablecoins.

**Capital-efficient interactions:** Borrowing stablecoins from deposited collateral, liquidating a vault, repaying a debt and getting collateral back: all of this can be done in just one transaction and without any capital commitment thanks to the protocol built-in swap features.

**Leveraging collateral exposure:** Users can also leverage their collateral token exposure through vaults, to get on-chain leverage up to x10 depending on the parameters set by governance.

**Optimized liquidations amounts and discounts:** Angle liquidation system is conceived as an improvement over more traditional liquidation mechanism (like on Aave, Compound, Maker). It allows for variable liquidations amounts meaning that during a liquidation the fraction of the debt that can be repaid is not fixed. On top of that, discounts given to liqudiators are based on a Dutch auction mechanism which minimizes the discount liquidators get while making sure they can still be profitable. This protects borrowers getting liquidated and lets them keep a maximum amount of collateral in their vaults.

**Improved position management:** Users can easily transfer their debt from one position to another without having to actually transfer collateral between these positions. All positions in this system are composable NFTs.

**Leveraed-yield and self-repaying loans:** Any yield-bearing token can be accepted as a collateral. Users can deposit collateral, borrow stablecoins and get their debt automatically repaid by the increase in value of their collateral. They can also swap their borrowed stablecoins for more of the yield-bearing token enabling them to boost the yield they are earning.

{% hint style="info" %}
[This section](vaults/) presents in greater details vaults in Angle Borrowing Module.
{% endhint %}

## Cross-chain Compatibility

As mentionned above, **the Borrowing module can scale to a wide range of different networks**.

This can allow governance to deploy it on networks like layer 2s where transactions are more affordable than on the Ethereum mainnet. On these networks, network fees are cheaper which makes Angle accessible to a wider range of potential users.

Though the differents networks are becoming more connected with each other thanks to bridges, they are still distinct environments. Available liquidity and liquidators are not the same in all those networks, and there are some potential risks with having the same protocol deployed on multiple chains.

The main risk in having the Borrowing module on multiple networks is that liquidations don't behave properly. With less liquidity, there is more slippage and liquidations can be less profitable, increasing the risk that they don't happen.

To prevent this, each instance of the Borrowing module relies on different parameters chosen by governance. For instance, one parameter that is often tuned from one place to another is the amount of agEUR that can be issued on a network: this allows to make sure that liquidations remain profitable on a network based on the available liquidity.

## Audits

The smart contracts of the Borrowing module have been audited by Chainsecurity. The code and audits have been published in [our dedicated repository](https://github.com/AngleProtocol/borrow-contracts). They can also be accessed in the [Audits section](../resources/audits/) of this docs.
