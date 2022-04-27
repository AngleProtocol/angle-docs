---
description: The go-to source for all frequently asked questions about Angle Core module
---

# ❓ FAQ

## What is Angle Core module?

Angle Core module is an efficient, over-collateralized, and liquid decentralized stablecoin protocol. It could be used to issue virtually any type of stablecoins.

## How does Angle Core module work?

1. Angle Core module enables people to swap their collateral against stablecoins at oracle value. Anyone can come with an accepted collateral (like wETH), and swap it to get a corresponding amount of stablecoins. It is also possible to swap Angle's stablecoins for an accepted collateral type of the system. For a EUR stablecoin collateralized by wBTC and wETH, with 1 wETH worth 1000€ you can get 1000 agEUR. If 1 wBTC is worth 10000€, with 1000 agEUR, you can get either 1 wETH or 0.1 wBTC.
2. To be able to always swap collateral against stablecoins and stablecoins against collateral, the Core module needs to remain over-collateralized regardless of the variations of the price of the collateral: it does so by issuing perpetual futures, which are leveraging contracts. People can come to Angle, bring some collateral and choose the amount of collateral from stable seekers they want to cover: they then get leveraged with the multiplier of their choice and at the same time they insure the protocol against the volatility of its collateral. If there is 1 wETH that was brought to get stablecoins by stable seekers, someone can come to Angle, bring collateral (like 0.5 wETH) and choose to cover this 1 wETH (hence getting a 3x leverage). This means that they get the capital gains or have to pay for the loss they would have realized if they had owned this 1 wETH from the beginning.
3. Angle Core module can hence be seen a marketplace between stability and volatility: stable seekers get direct stability and people who want leverage and volatility get the volatility of the collateral brought by stable seekers. Yet, there may not always be a full demand for the offer in volatility taking the form of the perpetual futures. Angle Core module needs a buffer of collateral to account for that. Therefore, it enables people to come deposit collateral and serve as this buffer: these liquidity providers automatically accumulate interest on the collateral they deposited.

## Have smart contracts been audited?

Yes, Angle Core module smart contracts have been audited by Chainsecurity and Sigma Prime. The code and audits have been published in [our repository](https://github.com/AngleProtocol/angle-core). They can also be accessed in the [Audits section](../resources/audits/) of this docs.

## What collateral are accepted by Angle Core module?

Currently, USDC, DAI, FRAX, FEI, and ETH/wETH can be used to mint agEUR.

## How is Angle's Core module different from other stablecoin protocols?

- Angle Core module is over-collateralized but capital efficient: to issue 1 stablecoin, you only need 1 of collateral, no more.
- Angle stablecoins' convertibility is not done at the expense of the robustness of the protocol. Thanks to its over-collateralized nature, and contrarily to most algorithmic designs, the Core module is still bank run resistant.
- Because of the swaps between stablecoins and collateral allowed by the Core module, the stablecoins are highly liquid. With Angle, people could very easily get stable Euros from their crypto collateral and more generally stablecoins pegged to currencies which are not well represented on-chain.

## Besides stablecoins, what are Angle Core module other advantages?

- Angle Core module can be used to get direct leverage on collateral. As a Hedging Agent in Angle Core module, you can come to Angle and choose to get the leverage multiplier you want on the pair collateral/stablecoin of your choice, with no funding rates.
- Angle offers higher staking rewards than what you could get with most common lending protocols. As a Standard Liquidity Provider (SLP) of Angle Core module, you get part of the transaction fees induced by users interacting with it, and part of the lending returns obtained by lending the reserves. If there is 150 in the Core module that is lent, 50 coming from SLP, then SLPs could get yield on 150 although they just contributed to 50.

## How can I use the Core module app?

In order to use the app, you can either interact directly with the smart contracts on the blockchain, through the front developped by the Angle Core Team at [app.angle.money](https://app.angle.money), or through any other app developed by another team. Note that the app is hosted publicly on IPFS, and not on private servers.

To interact with the app, you need an Ethereum wallet like Metamask, some ETH to pay for transaction fees, and the base asset you would like to swap, deposit or get leveraged on. Once you have these things, you can either swap your assets for stablecoins, open a leveraged position, or simply deposit it and accumulate interests.

## What are the costs?

Angle core module has dynamic fees. For stable seekers minting and burning fees vary around 0.3%, meaning that with 1 ETH worth 1000€, a stable seeker can get 997 agEUR. Mint and burn fees depend on how much of the collateral is covered by Hedging Agents. In some cases, mint and burn fees may also have a dependency on the collateral ratio of the Core module.

For Hedging Agents getting perpetual futures from the Core module, there are some fees induced at position opening and closing. Opening and closing fees depend on how much of the collateral is already covered by Hedging Agents. Fees vary around 0.3% as well.

You can see the specific fees implemented in detail in Angle's [analytics](https://analytics.angle.money).

## Where are the funds stored in the Core module, and how are they separated?

The funds of Angle Core module are stored in smart contracts. There is one smart contract for each collateral/stablecoin pair, such that funds are distributed amongst multiple contracts. A portion of the funds is transferred to strategies responsible for earning yield. These strategies transfer some funds to other protocols like Compound or Aave.

The code of the smart contracts is open source and has been be formally verified and audited by third party auditors.

## Is there any risk specific to the Core module?

As well as the global risks detailed [here](../global-faq.md#is-there-any-risk), the Core module relies on hedging agents covering its reserves, and SLPs over-collateralizing it. If the Core module is not covered or over-collateralized enough, it could be under the risk of not having enough collateral to back the stablecoins issued. However, even in this situation a failure of the protocol is unlikely as it would require all stablecoin holders to want to burn at the same time.

## Additional information and resources about the Core module

- [Blog](https://blog.angle.money)
- [Developers Doc](https://developers.angle.money)
- [Core module overview](overview.md)

{% hint style="info" %}
💬 **Notice:** If you still have questions, please do not hesitate to join our [Angle Community Discord Server](https://discord.gg/67WSSZqBG6) 📐! The Angle team and community members are always happy to help you understand how Angle works and help you answer any questions you may have.
{% endhint %}
