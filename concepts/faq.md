---
description: The go-to source for all frequently asked questions about Angle!
---

# ❓ FAQ

## What is Angle?

Angle is a scalable, efficient, over-collateralized and liquid decentralized stablecoin protocol. Angle could be used to issue virtually any type of stablecoins. The protocol is launching a Euro stablecoin, the agEUR, followed by other stablecoins in the near future, like or agCHF or agJPY.

## How does Angle work?

1. Angle enables people to swap their collateral against stablecoins at oracle value. Anyone can come with an accepted collateral (like wETH), and swap it to get a corresponding amount of stablecoins. It is also possible to swap Angle's stablecoins for an accepted collateral type of the system. For a EUR stablecoin collateralized by wBTC and wETH, with 1 wETH worth 1000€ you can get 1000 agEUR. If 1 wBTC is worth 10000€, with 1000 agEUR, you can get either 1 wETH or 0.1 wBTC.
2. To be able to always swap collateral against stablecoins and stablecoins against collateral, the protocol needs to remain over-collateralized regardless of the variations of the price of the collateral: it does so by issuing perpetual futures, which are leveraging contracts. People can come to Angle, bring some collateral and choose the amount of collateral from stable seekers they want to cover: they then get leveraged with the multiplier of their choice and at the same time they insure the protocol against the volatility of its collateral. If there is 1 wETH that was brought to get stablecoins by stable seekers, someone can come to Angle, bring collateral (like 0.5 wETH) and choose to cover this 1 wETH (hence getting a 3x leverage). This means that they get the capital gains or have to pay for the loss they would have realzied if they had owned this 1 wETH from the beginning.
3. Angle can hence be seen a marketplace between stability and volatility: stable seekers get direct stability and people who want leverage and volatility get the volatility of the collateral brought by stable seekers. Yet, there may not always be a full demand for the offer in volatility taking the form of the perpetual futures. Angle needs a buffer of collateral to account for that. The protocol therefore enables people to come deposit collateral and serve as this buffer: these liquidity providers automatically accumulate interest on the collateral they deposited.

## Have smart contracts been audited?

Yes, Angle's smart contracts have been audited by Chainsecurity and Sigma Prime. The code and audits have been published in [our repository](https://github.com/AngleProtocol/angle-core).

## What stablecoins can be minted on Angle?

Angle can be used to issue virtually any type of stablecoins, provided that there is an oracle for it. The intial goal is to create Forex stablecoins with sufficient liquidity. To this extent, we want to focus on only a few different stablecoins at first, beginning with a EUR-pegged one.

Today, agEUR can be minted from USD stablecoins. We are currently focused on developing the market for agEUR and expanding the protocol, before venturing into other stablecoins.

## When will new stablecoins be launched?

Governance and Angle DAO will be able to vote for the launch of new stablecoins. Angle Core Team wants to wait to have enough liquidity and integrations on the agEUR before launching new ones.

## How to launch a stablecoin?

Angle is a 3-sided platform that relies on 3 different types of agents to make the protocol work. When launching a new stablecoin, it is important to make sure that different stakeholders arrive in the right order.

To grow demand for newly launched stablecoins, governance can offer staking contracts for stable holders to get governance tokens. This aims to give users even more incentives to interact with the protocol, which in turn encourages LPs to also interact with the protocol.

## What collateral are accepted by Angle?

Currently, USDC, DAI, FRAX, and FEI can be used to mint agEUR.

## Why are Angle's stablecoins stable?

Angle proposes a full and unrestricted convertibility between stablecoins and collateral at a 1:1 rate. To get 1 of stablecoin with Angle, you only need 1 of collateral, and from your stablecoins, you can always get the corresponding value of collateral.

Being able to swap 1 of collateral for 1 stablecoin, and 1 stablecoin for 1 of collateral is what makes the stablecoins stable.

## How is Angle's protocol different from other stablecoins?

* Just like Maker, Angle is an over-collateralized protocol, but contrarily to it, it is capital efficient: to issue 1 stablecoin, you only need 1 of collateral, no more.
* Angle's convertibility is not done at the expense of the robustness of the protocol. Thanks to its over-collateralized nature, and contrarily to most algorithmic designs, Angle is still bank run resistant.
* Because of the swaps between stablecoins and collateral allowed by the protocol, the stablecoins are highly liquid. With Angle, people could very easily get stable Euros from their crypto collateral and more generally stablecoins pegged to currencies which are not well represented on-chain.

## Besides stablecoins, what are Angle's other advantages?

* Angle can be used to get direct leverage on collateral. As a Hedging Agent of Angle's protocol, you can come to Angle and choose to get the leverage multiplier you want on the pair collateral/stablecoin of your choice, with no funding rates.
* Angle proposes higher staking rewards than what you could get with most common lending protocols. As a Standard Liquidity Provider (SLP) of Angle's protocol, you get part of the transaction fees induced by users interacting with the protocol, and part of the lending returns obtained by lending the protocol's reserves. If there is 150 in the protocol that is lent, 50 coming from SLP, then SLPs could get yield on 150 although they just contributed to 50.

## In short, why Angle?

Many types of people can benefit from using Angle: the stable seekers who can get stablecoins simply by swapping it against collateral, the highly speculative people who can get a direct leverage through perpetual futures on a pair collateral/stablecoin, the yield farmers who can simply deposit their collateral in the protocol, automatically accumulate interest on it and get a higher yield than what they would get on other lending platforms like Compound.

The protocol is also completely open source, which allows anyone to interact with the user interface client, API or directly with the smart contracts on the Ethereum network. Being open source means that you are able to build any third-party service or application to interact with the protocol and enrich your product.

## How can I use the app?

In order to use the app, you can either interact directly with the smart contracts on the blockchain, through the front developped by the Angle Core Team at [app.angle.money](https://app.angle.money), or through any other app developed by another team. Note that the app is hosted publicly on IPFS, and not on private servers.

To interact with the app, you need an Ethereum wallet like Metamask, some ETH to pay for transaction fees, and the base asset you would like to swap, deposit or get leveraged on. Once you have these things, you can either swap your assets for stablecoins, open a leveraged position, or simply deposit it and accumulate interests.

## What are the costs?

Angle Protocol has dynamic fees. For stable seekers minting and burning fees vary around 0.3%, meaning that with 1 ETH worth 1000€, a stable seeker can get 997 agEUR. Mint and burn fees depend on how much of the collateral is covered by Hedging Agents. In some cases, mint and burn fees may also have a dependency on the collateral ratio of the protocol.

For Hedging Agents getting perpetual futures from the protocol, there are some fees induced at position opening and closing. Opening and closing fees depend on how much of the collateral is already covered by Hedging Agents. Fees vary around 0.3% as well.

You can see the specific fees implemented in detail in Angle's [analytics](https://analytics.angle.money).

## Where are the funds stored in the protocol, and how are they separated?

The funds of Angle's protocol are stored in smart contracts. There is one smart contract for each collateral/stablecoin pair, such that funds are distributed amongst multiple contracts. A portion of the funds is transferred to strategies responsible for earning yield. These strategies transfer some funds to other protocols like Compound or Aave.

The code of the smart contracts is open source and has been be formally verified and audited by third party auditors.

## Is there any risk?

No platform can be considered entirely risk free. The risks related to the Angle platform are the smart contract risk (risk of a bug within the protocol code) and the risk that the protocol is not able to maintain over-collateralization and to sustain the convertibility of the minted tokens.

Every possible step has been taken to minimize the risk as much as possible. The protocol code is public, open sourced, and has been audited. There are open bug bounties on Angle's [immunefi](https://immunefi.com) portal. There are also failure modes that can be activated by governance votes in some occasions.

## Do you have a governance token?

Yes, veANGLE (locked ANGLE) tokens are used as the governance token of the protocol. It is used to direct weekly ANGLE distribution and vote on governance proposals on [Snapshot](https://snapshot.org/#/anglegovernance.eth).

You can learn more about how voting-escrowed tokens work in the [veANGLE](../governance/veANGLE/) page.

Feel free to join the discussion in the governance forum at [gov.angle.money](https://gov.angle.money).

## Additional information and resources about Angle

* [Blog](https://blog.angle.money)
* [Developers Doc](https://developers.angle.money)

{% hint style="info" %}
💬 **Notice:** If you still have questions, please do not hesitate to join our [Angle Community Discord Server](https://discord.gg/67WSSZqBG6) 🕹️! The Angle team and community members are always happy to help you understand how Angle works and help you answer any questions you may have.
{% endhint %}
