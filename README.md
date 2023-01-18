---
description: Welcome to the Angle Protocol Documentation Portal!
---

# Angle Documentation Portal

## 🏅 Introduction to Angle

Angle is a decentralized, capital efficient and over-collateralized stablecoin protocol composed of smart contracts running on open blockchains. It was launched in November 2021 and you can use it at [app.angle.money](https://app.angle.money).

{% embed url="https://www.youtube.com/embed/DDoY_CUrd7M" %}

It can be used to issue stablecoins, called agTokens, that are pegged to a specific value. This means that these tokens are designed to mirror the value of the asset they are pegged to.

Angle has started with agEUR, a Euro (EUR - €) stablecoin.

On top of its stablecoin product, Angle Protocol also offers ways to:

* Trade perpetual futures
* Earn yield from strategies
* Get leverage on a wide range of assets

The protocol consists of several different modules, or sets of smart contracts, from which agTokens can be issued or minted. While Angle was launched with a single minting module (the [Core module](core-module/overview.md)), a [Borrowing module](borrowing-module/) allowing to borrow Angle stablecoins against deposited collateral has been introduced.

The protocol is also engaged into Algorithmic Market Operations (AMOs), or Direct Deposit Modules, where agTokens are invested in protocols for Angle to get a yield on.

### [Core module](core-module/overview.md)

Angle Core module is deployed on Ethereum mainnet and is used for agEUR. It relies on three types of agents that form a balanced ecosystem maintaining agTokens' peg (or stability). These agents are [users](core-module/stable-seekers/) minting and burning the stablecoins, [Hedging Agents](core-module/hedging-agents/) covering the protocol collateral from price changes, and [Standard Liquidity Providers](core-module/standard-liquidity-providers/) helping to over-collateralize the protocol in exchange for yield.

### [Borrowing module](borrowing-module/)

Angle Borrowing module is deployed on multiple EVM compatible networks, including Ethereum mainnet, sidechains like Polygon and layer 2s like Optimism. It allows users to deposit collateral and borrow agTokens (debt) against this collateral. It is designed to enable getting leverage on almost any asset through an agToken loan, or to simply let people get access to stablecoins while keeping their exposure to a volatile asset or to a yield-bearing token.

Inspired from more traditional borrowing protocols (like [Maker](https://makerdao.com/en/), [Liquity](https://www.liquity.org), [Aave](https://aave.com), [Compound](https://compound.finance), ...), it comes with its set of new features and improvements which make it efficient. Among other things:

* All operations are designed to be capital efficient
* The borrowing experience is optimized with notably an improved liquidation engine which allows liquidated addresses to face minimal losses compared with what they can experience in more traditional models.

### Other Aspects

Angle is not limited to these key components. It has notably a complex [bridge infrastructure](other/cross-chain.md) designed to facilitate the cross-chain liquidity of agTokens.

### 🗳 Governance

Angle is a decentralized protocol governed by [a DAO](governance/angle-dao.md) encapsulating all holders of a governance token called veANGLE. Holders of the token have voting powers to propose and make changes to the underlying code of the Angle Protocol.

## 🛣️ Roadmap

Beyond creating the first liquid and decentralized Euro stablecoin, the main goal of Angle is to create a money layer for DeFi. Angle will not only expand to multiple blockchains or open networks, it will also seek to launch stablecoins for other types of assets.

## 📐 [Discord](https://discord.gg/3vaHCJw7Mz)

While Angle was initially created by a team of developers at a company called Angle Labs, Inc, it is progressively decentralising and receives contributions from the external developer community as well as ongoing contributions from Angle Labs.

Angle community Discord server is where the community collectively organizes itself to build the best protocol possible, help everyone understand what Angle is about, and most of all have fun playing with DeFi!

## ⚒️ [Developers Doc](https://developers.angle.money)

Angle is an open protocol on which anyone can permissionlessly build or suggest improvements. The protocol relies on an open-source codebase available [on Github](https://github.com/AngleProtocol).

There is a technical doc for developers and advanced users to understand how Angle protocol works under the hood and how to build on top of it.

{% hint style="info" %}
The protocol's smart contracts have undergone several audits by Chainsecurity and Sigma Prime. You can find the different audit reports [here](resources/audits/).
{% endhint %}

## ✏️ [Contributing to this doc](https://github.com/AngleProtocol/angle-docs)

This documentation portal is maintained by Angle Labs, Inc. It is built to be the up-to-date source of truth for Angle Protocol functionality and production contracts. If there is anything unclear or out of date, please [submit a pull request](https://github.com/AngleProtocol/angle-docs) to the `angle-docs` repository.

The Angle Protocol is designed for an international audience. Anyone is therefore welcome to translate pages of this documentation portal or articles published in the [Angle blog](https://angle.money/#/blog) in its home language.

In order for your translation to appear on this doc, you need to:

1. Make sure that your translation has been reviewed by members of your local community on Angle Discord. We will not accept any translation that has not been checked by other community members.
2. Submit a pull request to the `angle-docs` repository and respect the formatting and conventions already in place for the `russian` section of the docs.
