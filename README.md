---
description: >-
  Angle is a decentralized, capital efficient and over-collateralized stablecoin protocol.
---

# Angle Documentation Portal

Welcome to the Angle Protocol Documentation Portal! It contains essential info and key links to understand the fundamentals of the Angle protocol.

So grab a coffee ☕ and enjoy the read!

## 🏅 Introduction to Angle

Angle is a decentralized, capital efficient and over-collateralized stablecoin protocol composed of smart contracts mostly deployed on the Ethereum blockchain. The protocol was launched in November 2021 and you can start using it at [app.angle.money](https://app.angle.money).

It can be used to issue stablecoins, called agTokens, that are pegged to a specific value. This means that these tokens are designed to mirror the value of the asset they are pegged to.

Angle has started with agEUR, a Euro (EUR - €) stablecoin on Ethereum mainnet.

On top of its stablecoin product, Angle protocol also offers to its users ways to:

- Trade perpetual futures
- Earn yield from strategies
- Get leverage on a wide range of assets

The protocol consists of several different modules, or set of smart contracts, from which agTokens can be issued or minted. While Angle was launched with a single minting module (the [Core module](core-module/overview.md)), a [Borrowing module](borrowing-module/) allowing to borrow Angle stablecoins against deposited collateral will soon be released. The protocol is also engaged into Algorithmic Market Operations (AMOs) where agTokens are invested in protocols for Angle to get a yield on.

### Core module

Angle Core module relies on three types of agents, that form a balanced ecosystem maintaining agTokens' peg (or stability). These agents are [users](core-module/stable-seekers/README.md) minting and burning the stablecoins, [Hedging Agents](core-module/hedging-agents/README.md) covering the protocol collateral from price changes, and [Standard Liquidity Providers](core-module/standard-liquidity-providers/README.md) helping to over-collateralize the protocol in exchange for yield.

Learn more in the [Core module documentation](core-module/overview.md), and start using it at [app.angle.money](https://app.angle.money).

### Borrowing module

The Borrowing module of the protocol allows users to deposit collateral and borrow agTokens (debt) against this collateral. It is designed to enable getting leverage on almost any asset through an agToken loan, or to simply let people get access to stablecoins while keeping their exposure to a volatile asset or to a yield-bearing token.

Inspired from more traditional borrowing protocols (like [Maker](https://makerdao.com/en/), [Abracadabra](https://abracadabra.money), [Liquity](https://www.liquity.org), [Aave](https://aave.com), [Compound](https://compound.finance), ...), it comes with its set of new features and improvements which make it efficient. Among other things:

- All operations are designed to be capital efficient
- The borrowing experience is optimized with notably an improved liquidation engine which allows liquidated addresses to face minimal losses compared with what they can experience in more traditional models.

Learn more in the new [Borrowing module documentation](borrowing-module/).

### Other Aspects

Angle is not limited to these key components. It is notably involved in algorithmic market operations where agTokens are invested directly by Angle in other protocols.

Angle also relies on a [Governance module](governance/angle-dao.md) to manage the protocol.

## 🛣️ Roadmap

Beyond creating the first liquid and decentralized Euro stablecoin on Ethereum, the main goal of Angle is to create a money layer for DeFi. Angle will not only expand to multiple blockchains or open networks, it will also seek to launch stablecoins for other types of assets.

You can read our [Roadmap blog post](https://blog.angle.money/expanding-beyond-220m-tvl-6475711f458b) from March 3rd 2022 to learn more.

## 📐 [Discord](https://discord.gg/3vaHCJw7Mz)

Angle is currently being developed by its Core Team and community. Any help and initiative is more than welcome!

There are a large number of ways to build decentralized stablecoins. We, at Angle, see the stablecoin space and DeFi more broadly as a large playground where we explore ways to invent cool, sustainable and robust primitives.

Angle community Discord server is where we collectively organize ourselves to build the best protocol possible, help everyone understand what Angle is about, and most of all have fun playing with DeFi!

{% hint style="success" %}
📐 If there is anything unclear in this docs or out of date or if you feel like you have feedback on the protocol, this Discord is the best place to let us know!
{% endhint %}

## ⚒️ [Developers Doc](https://developers.angle.money)

Angle is an open protocol on which anyone can permissionlessly build or suggest improvements. The protocol relies on an open-source codebase available [on Github](https://github.com/AngleProtocol).

To make things more intelligible, we have a technical doc for developers and users to understand how Angle protocol works under the hood and how to build on top of it. Check it out if you want to understand how the protocol's smart contracts are organized.

{% hint style="info" %}
The protocol's smart contracts have been audited by Chainsecurity and Sigma Prime. You can find the audit reports [here](resources/audits/README.md).
{% endhint %}

## ⭐ [Popularization](resources/popularization/)

If you want to get easier to access or less technical documents about the protocol, you should take a look at this section.

## Other Resources

- 📡 [Website](https://angle.money)
- 🐦 [Twitter](https://twitter.com/AngleProtocol)
- 🌳 [Medium/Blog](https://blog.angle.money)
- 💻 [Github](https://github.com/AngleProtocol)
- 📀 [App](https://app.angle.money)
- 🗂️ [Analytics](https://analytics.angle.money/#/home)
- 💬 [Governance Forum](https://gov.angle.money)

## ✏️ [Contributing to this doc](https://github.com/AngleProtocol/angle-docs)

This documentation portal is the up-to-date source of truth for Angle Protocol functionality and production contracts. If there is anything unclear or out of date, please [submit a pull request](https://github.com/AngleProtocol/angle-docs) to the `angle-docs` repository.

The Angle Protocol has been designed for an international audience. Anyone is therefore welcome to translate pages of this documentation portal or articles published in the [Angle blog](https://blog.angle.money) in its home language.

In order for your translation to appear on this doc, you need to:

1. Make sure that your translation has been reviewed by members of your local community on Angle Discord. We will not accept any translation that has not been checked by other community members.
2. Submit a pull request to the `angle-docs` repository and respect the formatting and conventions already in place for the `russian` section of the docs.
