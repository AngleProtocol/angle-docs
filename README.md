---
description: Welcome to the Angle Protocol Documentation Portal!
cover: .gitbook/assets/Angle-Documentation-Portal-cover.jpg
coverY: -82
---

# 📐 Angle Documentation Portal

## 🏅 Introduction to Angle

Angle is a decentralized, capital efficient and over-collateralized stablecoin protocol composed of smart contracts running on open blockchains. It was launched in November 2021 and you can use it at [app.angle.money](https://app.angle.money).

{% embed url="https://www.youtube.com/embed/DDoY_CUrd7M" %}

It can be used to issue stablecoins, called agTokens, designed to mirror the value of an asset they are pegged to.

The protocol consists of several different modules, or sets of smart contracts, from which stablecoins can be issued or minted. While Angle launched its first stablecoin agEUR with a single minting module (the [Core module](./deprecated/core-module/overview.md) - that was wound down in May 2023), a [Borrowing module](borrowing-module/) allowing to borrow Angle stablecoins against deposited collateral and a price stability module called [Transmuter](transmuter/README.md) have then been introduced.

The protocol is also engaged into [Direct Deposit Modules](other/amo.md), also called Algorithmic Market Operations (AMOs), allowing it to boostrap liquidity for agTokens in other protocols.

### [Stablecoins](stablecoins.md)

Angle is so far behind one stablecoin, agEUR, pegged to the value of the Euro - €.

### [Borrowing module](borrowing-module/)

Angle Borrowing module is deployed on multiple EVM compatible networks beyond Ethereum (like Polygon or Optimism). It allows users to deposit collateral and borrow agTokens (debt) against their collateral. It is designed to enable getting leverage on almost any asset through an agToken loan, or to simply let people get access to stablecoins while keeping their exposure to a volatile asset or to a yield-bearing token.

Inspired from more traditional borrowing protocols (like [Maker](https://makerdao.com/en/), [Liquity](https://www.liquity.org), [Aave](https://aave.com), [Compound](https://compound.finance), ...), it comes with its set of new features and improvements which make it overall more capital efficient to use and more borrower friendly.

### [Transmuter](transmuter/)

Transmuter is deployed on Ethereum. It works as a basket of different stablecoins that can be used to mint agEUR. Thanks to its dynamic fee model and its internal circuit breakers, the system is able to autonomously control its exposures to the assets it has in reserves and guarantee that agEUR's backing is properly diversified. It is on top of that a trustless system that lets anyone and at any time (including during black swan events) redeem agEUR for a portion of the assets in the backing.

It is designed as a resilient improvement over the price stability module systems of [Maker](https://makerdao.com/en/) and [FRAX](https://frax.finance/) that showed their limits during the USDC depeg situation in March 2023.

{% hint style="info" %}
Transmuter is not live yet. Depending on governance approval, it should be released in July 2023.
{% endhint %}

### Other Aspects

Angle is not limited to this key component. It has notably a complex [bridge infrastructure](other/cross-chain.md) designed to facilitate the cross-chain liquidity of its stablecoins. It also natively supports [flash loans](other/flash-loans.md) for some of its stablecoins.

### 🗳 Governance

Angle is a decentralized protocol governed by [a DAO](governance/angle-dao.md) encapsulating all holders of a governance token called veANGLE. Holders of the token have voting powers to propose and make changes to the underlying code of the Angle Protocol.

## 📐 [Discord](https://discord.gg/3vaHCJw7Mz)

While Angle was initially created by a team of developers at a company called Angle Labs, Inc, it is rapidly decentralizing and receives contributions from the external developer community as well as ongoing contributions from Angle Labs.

Angle community Discord server is where the community collectively organizes itself to build the best protocol possible, help everyone understand what Angle is about, and most of all have fun playing with DeFi!

## ⚒️ [Developers Doc](https://developers.angle.money)

Angle is an open protocol on which anyone can permissionlessly build or suggest improvements. The protocol relies on an open-source codebase available [on Github](https://github.com/AngleProtocol).

There is a technical doc for developers and advanced users to understand how Angle protocol works under the hood and how to build on top of it.

{% hint style="info" %}
The protocol's smart contracts have undergone several audits by Chainsecurity, Sigma Prime, and Code4rena. You can find the different audit reports [here](resources/audits/).
{% endhint %}

## 📱 Side Products

Products developed for the Angle Protocol can also bring value to the wider DeFi userbase. Some of them are being released as standalone products so that anyone can benefit from them.

This is notably the case of [🥨 Merkl](side-products/merkl/README.md.md), an incentive framework for AMMs with concentrated liquidity (like Uniswap V3) ran by Angle Labs.

## 🖼 Branding

If you're writing an article, creating designs and animations about Angle, check out this [assets repository](https://github.com/AngleProtocol/angle-assets) with all the visual elements about the Angle brand, including logos, icons and images.

## ✏️ [Contributing to this doc](https://github.com/AngleProtocol/angle-docs)

This documentation portal is maintained by Angle Labs, Inc. It is built to be the up-to-date source of truth for Angle Protocol production contracts and for Angle Labs products. If there is anything unclear or out of date, please [submit a pull request](https://github.com/AngleProtocol/angle-docs) to the `angle-docs` repository.

Angle is designed for an international audience. Anyone is therefore welcome to translate pages of this documentation portal or articles published in the [Angle blog](https://angle.money/blog) in its home language.

In order for your translation to appear on this doc, you need to:

1. Make sure that your translation has been reviewed by members of your local community on Angle Discord. We will not accept any translation that has not been checked by other community members.
2. Submit a pull request to the `angle-docs` repository and respect the formatting and conventions already in place for the `russian` section of the docs.
