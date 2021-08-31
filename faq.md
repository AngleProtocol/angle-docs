---
description: The go-to source for all frequently asked questions about Angle!
---

# ❓ FAQ

## What is Angle?

Angle is a scalable, efficient, over-collateralized and liquid decentralized stablecoin protocol. Angle could be used to issue virtually any type of stablecoins, and it will start by launching a EUR followed soon after by other stablecoins like USD.

## How does Angle work?

1. Angle enables people to swap their collateral against stablecoins at oracle value. Anyone can come with an accepted collateral \(like wETH\), and swap it to get a corresponding amount of stablecoins. It is also possible to swap Angle's stablecoins for an accepted collateral type of the system. For a USD stablecoin collateralized by wBTC and wETH, with 1 wETH worth 1000$ you can get 1000 tokens. And if 1 wBTC is worth 10000$, with 1000 tokens, you can get either 1 wETH or 0.1 wBTC.
2. To be able to always swap collateral against stablecoins and stablecoins against collateral, the protocol needs to remain over-collateralized regardless of the variations of the price of the collateral: it does so by issuing perpetual futures, which are leveraging contracts. People can come to Angle, bring some collateral and choose the amount of collateral from stable seekers they want to cover: they then get leveraged with the multiplier of their choice and at the same time they insure the protocol against the volatility of its collateral. If there is 1 wETH that was brought to get stablecoins by a stable seeker, someone can come to Angle, bring collateral \(like 0.5 wETH\) and choose to cover this 1 wETH \(hence getting a 3x leverage\). This means that this person gets the capital gains or has to pay for the loss she would have made if she had owned this 1 wETH from the beginning.
3. Angle can hence be seen a marketplace between stability and volatility: stable seekers get direct stability and people who want leverage and volatility get the volatility of the collateral brought by stable seekers. Yet, there may not always be a full demand for the offer in volatility taking the form of the perpetual futures. Angle needs a buffer of collateral to account for that. The protocol therefore enables people to come deposit collateral and serve as this buffer: these liquidity providers automatically accumulate interest on the collateral they deposited.

## When will Angle be live?

Angle Core Team is currently developing the protocol. Audit will soon be done and a public testnet is going to be released in September. We hope to be live on mainnet by the month of October.

{% hint style="info" %}
Some elements like the collateral types accepted for each stablecoin may still change before launch.
{% endhint %}

## What stablecoins will I be able to issue with Angle?

Angle can be used to issue virtually any type of stablecoins, provided that there is an oracle for it. The main goal is to create Forex stablecoins with sufficient liquidity, to this extent, we will focus in the beginning on creating only few different stablecoins.

The plan is to begin with a EUR stablecoin, and to follow-up soon after with a USD stablecoin.

Governance will be able to vote for new stablecoins.

## When will new stablecoins be launched?

Governance and Angle DAO will have the power to vote for the launch of new stablecoins. It is the will of Angle Core Team to create an Angle stable Dollar short after the launch of the stable Euro, and to wait to have enough liquidity and integrations on existing stablecoins before launching new ones.

Angle Core Team hopes that the DAO will share this stance, which will dictate the timeline with which new stablecoins are deployed.

## How to launch a stablecoin?

Angle is a 3-sided platform that relies on 3 different types of agents to make the protocol work. When launching a new stablecoin, it is important to make sure that different stakeholders arrive in the right order.

To bootstrap each stablecoin, SLPs will be the first allowed to come in, then both HAs and users will be able to get in at the same time. This is a way to make sure that stablecoins will start by being over-collateralized.

To grow demand for newly launched stablecoins, governance will try to offer staking contracts for stable holders to get governance tokens. This aims to give users even more incentives to interact with the protocol, which will in turn encourage LPs to also interact with the protocol.

## What collateral types will be accepted by Angle?

The idea at first is to be kind of conservative and only accept few but carefully chosen collateral types.

The plan for the moment is to have:

* Angle's stable EUR \(agEUR\) backed by USDC and DAI.
* Angle's stable USD \(agUSD\) backed by USDC, DAI, wETH and wBTC when launched.

USDT and other USD stablecoins may also be accepted collateral types for both stablecoins.

Governance will be able to whitelist new collateral types.

## Why are Angle's stablecoins stable?

Angle proposes a full and unrestricted convertibility between stablecoins and collateral at a 1:1 rate. To get 1 of stablecoin with Angle, you only need 1 of collateral, and from your stablecoins, you can always get the corresponding value of collateral.

Being able to swap 1 of collateral for 1 stablecoin, and 1 stablecoin for 1 of collateral is what makes the stablecoins stable.

## How is Angle's protocol different from other stablecoins?

* Just like Maker, Angle is an over-collateralized protocol, but contrarily to it, it is capital efficient: to issue 1 stablecoin, you only need 1 of collateral, no more.
* Angle's convertibility is not done at the expense of the robustness of the protocol. Thanks to its over-collateralized nature, and contrarily to most algorithmic designs, Angle is still bank run resistant.
* Because of the swaps between stablecoins and collateral allowed by the protocol, the stablecoins are highly liquid. With Angle, people could very easily get stable Euros from their crypto collateral and more generally stablecoins pegged to currencies which are not well represented on-chain. 

## Besides stablecoins, what are Angle's other advantages?

* Angle can be used to get direct leverage on collateral. As a Hedging Agent of Angle's protocol, you can come to Angle and choose to get the leverage multiplier you want on the pair collateral/stablecoin of your choice, with no funding rates.
* Angle proposes higher staking rewards than what you could get with most common lending protocols. As a Standard Liquidity Provider \(SLP\) of Angle's protocol, you get part of the transaction fees induced by users interacting with the protocol, and part of the lending returns obtained by lending the protocol's reserves. If there is 150 in the protocol that is lent, 50 coming from SLP, then SLPs could get yield on 150 although they just contributed to 50.

## In short, why Angle?

Many types of people will be able to benefit from using Angle: the stable seekers who can get stablecoins simply by swapping it against collateral, the highly speculative people who can get a direct leverage through perpetual futures on a pair collateral/stablecoin, the yield farmers who can simply deposit their collateral in the protocol, automatically accumulate interest on it and get a higher yield than what they would get on other lending platforms like Compound.

The protocol is also completely open source, which allows anyone to interact with the user interface client, API or directly with the smart contracts on the Ethereum network. Being open source means that you are able to build any third-party service or application to interact with the protocol and enrich your product.

## How do I use the service?

In order to use the service, you can directly interact from the blockchain, from the front app currently developed by Angle's team, or from any front app developed by another team.

In any case, you will need an ERC-20 Ethereum wallet, some ETH to pay for transaction fees, and the base asset you would like to swap, deposit or get leveraged on. Once you have these things, you can either swap your assets for stablecoins, get leveraged on it, or simply deposit it and accumulate interests.

## What is the cost of the service?

The platform has variable fees. For stable seekers minting and burning fees around 0.3% are taken, meaning that with 1 ETH worth 1000$, a stable seeker will get 997 agUSD. Mint and burn fees depend on how much of the collateral is covered by Hedging Agents. In some cases, mint and burn fees may also have a dependance on the collateral ratio of the protocol.

For Hedging Agents getting perpetual futures from the protocol, there are some fees induced at position opening and close. Opening and closing fees depend on how much of the collateral is already covered by Hedging Agents. Fees will vary along 0.3%.

## Where are the funds stored?

The funds of Angle's protocol are stored in smart contracts. There will be one smart contract storing the funds per pair collateral/stablecoin. The code of the smart contract is public, open source and will be formally verified and audited by third party auditors.

A portion of the funds will be transferred to strategies responsible for getting yield on these funds. These strategies may end transferring some funds to protocols like Compound or Aave.

## Is there any risk?

No platform can be considered entirely risk free. The risks related to the Angle platform are the smart contract risk \(risk of a bug within the protocol code\) and the risk that the protocol is not able to maintain over-collateralization and to sustain the convertibility of the minted tokens.

Every possible step has been taken to minimize the risk as much as possible, the protocol code is public and open source and it will be audited. There are failure modes that can be activated by governance votes in some occasions. There will also be bug bounty campaigns.

## Do you have a governance token?

Yes, it is the ANGLE token.

{% hint style="info" %}
This token may not be available and distributed initially at launch to the wide community.
{% endhint %}

ANGLE will be the centre of gravity of Angle Protocol governance: it will be used to vote and decide on the outcome of Angle Improvement Proposals. Apart from this, ANGLE could be used when collateral settlement is triggered to be treated preferentially and get a higher chance of being reimbursed full claim.

Documentation on tokenomics and governance is available in the whitepaper. Further detail will be given in other papers.

Feel free to join the discussion in the governance forum when it is live.

## When will staking be available?

It will happen after launch. Exact time to be determined.

## Is there a private token sale?

No, we do not have a private sale.

## Will there be a public token sale?

No, we do not have a public sale.

## Additional information and resources about Angle

Feel free to refer to the [whitepaper](whitepaper.md) for a deeper dive into Angle Protocol mechanisms.

{% hint style="info" %}
💬 **Notice:** If you still have questions, please do not hesitate to join our [Angle Community Discord Server](https://discord.gg/67WSSZqBG6) 🕹️! The Angle team and community members are always happy to help you understand how Angle works and help you answer any questions you may have.
{% endhint %}

