---
description: The go-to source for all frequently asked questions about Angle Protocol
---

# ❓ Gloabl FAQ

## What is Angle Protocol?

Angle Protocol is a scalable, efficient, and over-collateralized stablecoin protocol. It could be used to issue virtually any type of stablecoins. The protocol has launched a Euro stablecoin, the agEUR, and it could be follow by other stablecoins in the near future, like or agCHF or agJPY.

Angle relies on two modules to issue stablecoins: the [Angle Core module](/core-module/overview.md), and the new [Angle Borrowing module](/borrowing-module/README.md).

## Have smart contracts been audited?

Yes. Angle Core module smart contracts have been audited by Chainsecurity (multiple times) and Sigma Prime. The code and audits have been published in [our different open-source repositories](https://developers.angle.money/overview/public-repositories).

## What stablecoins can be minted on Angle Protocol?

Angle Protocol can be used to issue virtually any type of stablecoins, provided that there is an oracle for it. The intial goal is to create Forex stablecoins with sufficient liquidity. To this extent, we want to focus on only a few different stablecoins at first, beginning with a EUR-pegged one.

Today, agEUR can be minted from USD stablecoins and from ETH. We are currently focused on developing the market for agEUR and expanding the protocol, before venturing into other stablecoins. One of these developments is the new [Borrowing module](/borrowing-module/README.md).

## When will new stablecoins be launched?

veANGLE holders will be able to vote for the launch of new stablecoins. Angle Core Team wants to wait to have enough liquidity and integrations on the agEUR before launching new ones.

## How can a new stablecoin be launched?

Angle Protocol relies on two different modules to issue stablecoins: the Core and Borrowing modules. When launching a new stablecoin, it is important to make sure that the different stakeholders and mechanisms can work as intended across both modules.

To grow demand for newly launched stablecoins, governance can offer staking contracts for the agToken liquidity providers to earn governance tokens. This aims to give users even more incentives to interact with the protocol and use the Angle stablecoins.

## Why are Angle's stablecoins stable?

Angle stablecoins are stable thanks to their efficient peg mechanism, relying on the full convertibility of the Core module between stablecoin and collateral, and the over-collateralization and efficient liquidation mechanism of the Borrowing module. Angle Borrowing module also enables indirect arbitrages which help it keep a soft peg.

Angle's only stablecoin so far agEUR is also deeply integrated on Curve, which protects its peg.

## How is Angle Protocol different from other stablecoins protocols?

As said previously, Angle relies on two different mechanisms to issue stablecoins. By working in cooperation, the two modules allow the stablecoins to be as robust as possible, while being flexible enough to grow and expand easily.

## In short, why Angle?

Many types of people can benefit from using Angle: the stable seekers who can get stablecoins simply by swapping it against collateral or borrowing from their deposit, the highly speculative people who can get a direct leverage through perpetual futures or vaults deposit, and the yield farmers who can simply deposit their collateral in the core module to earn interest.

The protocol is also decentralized, which allows anyone to interact with the user interface client, API or directly with the smart contracts on the Ethereum network. Being decentralized means that anyone is able to build any third-party service or application to interact with the protocol and enrich your product.

## How can I use the app?

In order to use the app, you can either interact directly with the smart contracts on the blockchain, through the front developped by the Angle Core Team at [app.angle.money](https://app.angle.money), or through any other app developed by another team. Note that the app is hosted publicly on IPFS, and not on private servers.

To interact with the app, you need an Ethereum wallet like Metamask, some ETH to pay for transaction fees (or some native tokens of the chain on which you're connected), and the base asset you would like to swap, deposit or get leveraged on. Once you have these things, you can either swap your assets for stablecoins, open a leveraged position, or simply deposit it and accumulate interests.

## Is there any risk?

No platform can be considered entirely risk free. The main risks related to the Angle platform are the smart contract risk (risk of a bug within the code) and the risk that the economic principles enabling the stablecoins to maintain their peg no longer hold.

Every possible step has been taken to minimize the risk as much as possible. The protocol code is public, open sourced, and has been audited. There are open bug bounties on Angle's [immunefi](https://immunefi.com) portal. There are also failure modes that can be activated by governance votes in some occasions.

## Do you have a governance token?

Yes, veANGLE (locked ANGLE) tokens are used as the governance token of the protocol. It is used to direct weekly ANGLE distribution and vote on governance proposals on [Snapshot](https://snapshot.org/#/anglegovernance.eth).

You can learn more about Angle DAO or about how voting-escrowed tokens work in the [governance section of this docs](governance/angle-dao.md).

Feel free to join the discussion in the governance forum at [gov.angle.money](https://gov.angle.money).

## Additional information and resources about Angle

- [Blog](https://blog.angle.money)
- [Developers Doc](https://developers.angle.money)

{% hint style="info" %}
💬 **Notice:** If you still have questions, please do not hesitate to join our [Angle Community Discord Server](https://discord.gg/67WSSZqBG6) 📐! The Angle team and community members are always happy to help you understand how Angle works and help you answer any questions you may have.
{% endhint %}
