---
description: Angle Borrowing Module Overview
---

# 🔭 Borrowing Module Overview

## Introduction

Angle Borrowing Module goal was introduced after the Core module of the protocol as a way to help **expand the Angle Protocol** through another minting mechanism for Angle stablecoins.

This module works hand in hand with the Core module and agTokens, like agEUR, are fully interoperable between both modules. It is available natively on Ethereum mainnet and on other EVM compatible networks like Polygon or Optimism. 

It is based on a **debt mechanism**, similar to the one used by Maker with DAI, or Abracadbra with MIM. Users can deposit tokens as collateral into the protocol, and borrow agTokens from this deposit depending on specific parameters.

## Main Features

### 🏦 Vaults

**Borrowing agTokens from collateral deposit:** With the Angle Borrowing module, users can deposit collateral tokens in a vault and mint (borrow) agTokens from their deposits according to specific parameters. This allow them to keep exposure to their tokens deposited as collateral, while benefitting from disposable liquidity in stablecoins.

**Capital-efficient interactions:** Borrowing stablecoins from deposited collateral, liquidating a vault, repaying a debt and getting collateral back: all of this can be done in just one transaction and without any capital commitment thanks to the protocol built-in swap features.

**Leveraging collateral exposure:** Users can also leverage their collateral token exposure through vaults, to get on-chain leverage up to x10 depending on the parameters set by governance.

**Optimized liquidations amounts and discounts:** Angle liquidation system is conceived as an improvement over more traditional liquidation mechanism (like on Aave, Compound, Maker). It allows for variable liquidations amounts meaning that during a liquidation the fraction of the debt that can be repaid is not fixed. On top of that, discounts given to liqudiators are based on a Dutch auction mechanism which minimizes the discount liquidators get while making sure they can still be profitable. This protects borrowers getting liquidated and lets them keep a maximum amount of collateral in their vaults.

**Improved position management:** Users can easily transfer their debt from one position to another without having to actually transfer collateral between these positions. All positions in this system are composable NFTs.

**Self repaying loans:** Any yield-bearing token could be accepted as a collateral. Users can deposit collateral, borrow stablecoins and get their debt automatically repaid by the increase in value of their collateral.

{% hint style="info" %}
[This section](vaults/) presents in greater details vaults in Angle Borrowing Module.
{% endhint %}

### 🛩 Token Reactors

Angle Borrowing module also introduces Token Reactors to allow DAOs and DeFi users to earn a native yield on top of volatile tokens.

The Reactor mode allows users or DAOs to deposit volatile tokens in specific vaults to earn yield on their deposits. This is made possible by minting agTokens that are invested directly in pre-defined strategies earning yield while maintaining a healthy collateral ratio on the agEUR loan.

{% hint style="info" %}
DAOs could leverage Angle token Reactors of the Angle Protocol to make a revenue out of their otherwise idle treasury assets. Learn more about it [here](../angle-borrowing-module/token-reactor.md).
{% endhint %}

## Audits

The smart contracts of the Borrowing module have been audited by Chainsecurity. The code and audits have been published in [our dedicated repository](https://github.com/AngleProtocol/angle-borrow). They can also be accessed in the [Audits section](../resources/audits/) of this docs.
