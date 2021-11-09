---
description: >-
  Angle is a capital-efficient, over-collateralized and liquid decentralized
  stablecoin protocol.
---

# Angle Documentation Portal

Welcome to the Angle Protocol Documentation Portal! It contains essential info and key links to understand the fundamentals of the Angle protocol.

So grab a coffee ☕ and enjoy the read!

{% hint style="success" %}
Please join the discussion on the Angle Community [Discord Server](https://discord.gg/67WSSZqBG6) 🕹️, our community is looking forward to helping you use Angle, improve the protocol or even build on top of it!
{% endhint %}

{% hint style="info" %}
📅 Angle Protocol has been live on the Ethereum mainnet since the 3rd of November 2021 🍁.
{% endhint %}

## Introduction to Angle

### 🏅 Over-Collateralized, Decentralized, and Capital-Efficient Stablecoin Protocol

Angle is the first over-collateralized, decentralized and capital-efficient stablecoin protocol. It offers full convertibility between stable assets and collateral at oracle value: you can swap 1 of collateral against 1 of stablecoin and conversely.

This makes the protocol both capital efficient and highly liquid.

### 🛣️ Roadmap

Angle Protocol could be used to issue any stablecoin. and has started on mainnet with agEUR, a Euro stablecoin. Besides creating the first liquid Euro stablecoin, the goal of Angle is to create stablecoins for other types of assets.

Stable CHF, GBP, JPY and KRW should be following agEUR.

### 🎨 Protocol Design

The protocol involves 3 agents, very common in other DeFi protocols, which all bring something to Angle, while benefitting from the protocol:

- **Stable Seekers/Holders, or Users:** they can swap collateral against stable assets, and conversely swap stable assets against a whitelisted collateral of their choice at oracle value, with no slippage and small transaction fees.
- **Hedging Agents (HAs):** they can open on-chain leveraged positions on Angle. They need to bring accepted collateral to the protocol, and are able to take positions on perpetuals futures on the available collateral/stablecoins pairs. By doing so, they insure the protocol against the volatility of the collateral brought by stable seekers. This volatility is transferred to these traders, and the protocol is able to ensure users of the convertibility of the stablecoins they own even in case of collateral price drops.
- **Standard Liquidity Providers (SLP)** : they lend collateral to the protocol in return of a share of minting and burning fees, and of the rewards earned from investing part of the protocol reserves into yield-earning strategies.

In short, Angle matches people who want stability (stable seekers) and people who want volatility (Hedging Agents). Yet, there isn't always a perfect match between supply and demand of volatility, meaning that the protocol's collateral may not be fully covered at all times by Hedging Agents. The additional collateral brought by Standard Liquidity Providers, serve as a buffer in this marketplace.

The protocol is implemented as a set of **smart contracts** on top of the Ethereum blockchain.

## ❓[FAQ](faq.md)

Check Frequently Asked Questions for a deeper introduction to Angle and its key features.

## 📚[Glossary](glossary.md)

If you are unsure about any specific terms, feel free to check the glossary.

## 🕹️ [Discord](https://discord.gg/3vaHCJw7Mz)

Angle is currently being developed by its Core Team and community. Any help and initiative is more than welcome!

There is a large number of ways to build decentralized stablecoins, and we, at Angle, see the stablecoin space as a large playground where we explore ways to make a cool, sustainable and robust design.

Angle community Discord server is where we collectively organize ourselves to build the best protocol possible, help everyone understand what Angle is about, and most of all have fun playing with DeFi!

## ⚒️ [Developers Doc](https://developers.angle.money)

Angle has a technical doc for developers and users to understand how Angle protocol works under the hood and how to build on top of it. Check it out if you want to understand how the protocol's smart contracts are organized.

{% hint style="info" %}
All the protocol's smart contracts have been audited by Chainsecurity and Sigma Prime. You can find the audit reports [here](resources/security/README.md)
{% endhint %}

## Other Resources

- 📡 [Website](https://angle.money)
- 🐦 [Twitter](https://twitter.com/AngleProtocol)
- 🌳 [Medium/Blog](https://blog.angle.money)
- 💻 [Github](https://github.com/AngleProtocol)
- 📀 [App](https://app.angle.money)
- 🗂️ [Analytics](https://analytics.angle.money/#/home)

{% embed url="https://blog.angle.money/introducing-angle-protocol-3e3e603d3f60" %}
Angle Introduction Article
{% endembed %}

## ✏️ [Contributing to this doc](https://github.com/AngleProtocol/angle-docs)

This documentation portal is the up-to-date source of truth for Angle Protocol functionality and production contracts. If there is anything unclear or out of date, please [submit a pull request](https://github.com/AngleProtocol/angle-docs) to the `angle-docs` repository.

The Angle Protocol has been designed for an international audience. Anyone is therefore welcome to translate pages of this documentation portal or articles published in the [Angle blog](https://blog.angle.money) in its home language.

In order for your translation to appear on this doc, you need to:

1. Make sure that your translation has been reviewed by members of your local community on Angle Discord. We will not accept any translation that has not been checked by other community members.
2. Submit a pull request to the `angle-docs` repository and respect the formatting and conventions already in place for the `russian` section of the docs.

![Join Angle Playground!](.gitbook/assets/angle_multi_back.jpg)
