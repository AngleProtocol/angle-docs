---
description: Angle Borrowing Module Overview
---

# 🔭 Borrowing Module Overview

## Introduction

Angle Borrowing Module goal is to help **expand the Angle Protocol** through another minting mechanism for Angle stablecoins. It is based on a **debt mechanism**, similar to those used by Maker with DAI, or Abracadbra with MIM. Users can deposit tokens as collateral into the protocol, and borrow agTokens from this deposit depending on specific parameters.

The main advantages of Angle Borrowing module are:

* No need for hedging agents to cover the protocol
* Easier to add new collaterals
* Users can keep exposure to their collateral tokens while using agEUR

These advantages help **further expand Angle and its agTokens**, both in terms of the stablecoins issued, their volume, and the chains and networks where they can be issued & redeemed. It has been designed to work hand in hand with the current one, and strenghten the Angle Protocol. AgTokens, like agEUR, are fully interoperable between both modules.

## Main Features

### 🏦 Vaults

**Borrowing agTokens from collateral deposit:** With the Angle Borrowing module, users can deposit collateral tokens in a vault and mint (borrow) agTokens from their deposits according to specific parameters. This allow them to keep exposure to their tokens deposited as collateral, while benefitting from disposable liquidity in stablecoins.

**Capital-efficient interactions:** Borrowing stablecoins from deposited collateral, liquidating a vault, repaying a debt and getting collateral back: all of this can be done in just one transaction and without any capital commitment thanks to the protocol built-in swap features.

**Leveraging collateral exposure:** Users can also leverage their collateral token exposure through vaults, to get on-chain leverage up to x10 depending on the parameters set by governance.

**Optimized liquidations amounts:** Angle vaults liquidations have been reworked to allow for variable liquidations, letting users keep a maximum amount of collateral in their vaults when getting liquidated. This ensures that liquidators get just what they need and not a too important discount which protects borrowers.

**Improved position management:** Users can easily transfer their debt from one position to another without having to actually transfer collateral between these positions.

**Self repaying loans:** Any yield-bearing token could be accepted as a collateral. **** Users can deposit collateral, borrow stablecoins and get their debt automatically repaid by the increase in value of their collateral.

{% hint style="info" %}
[This section](vaults/) presents in greater details vaults in Angle Borrowing Module.
{% endhint %}

### 🛩 Token Reactors

**Earning native yield on top of volatile tokens**

Angle Borrowing module also introduces Token Reactors. They allow users or DAOs to deposit volatile tokens in specific vaults to earn yield on their deposits. This is made possible by minting agTokens that are invested directly in pre-defined strategies earning yield while maintaining a healthy collateral ratio.

More about tokens reactors [here](../angle-borrowing-module/token-reactor.md).

### ⚡️ Flash-loans

Another side feature of these smart contracts are the possibility of taking out **flash-loans using agTokens**.

More about flash-loans [here](flash-loans.md).
