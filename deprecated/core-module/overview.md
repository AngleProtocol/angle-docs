---
description: The Core Concepts of Angle Core module
---

# 🔭 Angle Core Module Overview

{% hint style="info" %}
The Core module of the protocol was wound down in May 2023. The documentation is left here as a helper for other projects who would want to leverage on the ideas of the Core module.
If you were a [hedging agent](../core-module/hedging-agents/README.md), your position was settled at its cash-out value at the Ethereum block 16818578. You can use the guide [here](https://anglemoney.notion.site/HA-redemptions-process-e35a2b428cc84d39b8191f07a3b41940) to claim your tokens.
If you were a Standard Liquidity Provider (SLP), you may still unstake and withdraw your funds from the Angle App. Note that the protocol yield strategies could be restarted independently of agEUR and that as such it's currently still possible to deposit in the protocol's Core module to get sanTokens. Note as well that SLPs received a portion of the profits the protocol made from the Euler hack recovery. This resulted in a 4% increase in the value of the sanTokens of the protocol.
If you were holding agEUR minted through the Core module, there is nothing specific that you need to do. agEUR can still be minted or burnt through other means than this Core module.
{% endhint %}

Angle Core Module relies on three groups of stakeholders: stable seekers and holders, Hedging Agents and Standard Liquidity Providers.

{% hint style="info" %}
While the Angle Core module was only used for agEUR, it could have been generalized to other stablecoins. To this extent, the concepts here are not described for agEUR specifically, but for a stablecoin in general.
{% endhint %}

{% hint style="info" %}
Smart contract addresses associated to the Core module for agEUR can be found [here](https://developers.angle.money/overview/smart-contracts/mainnet-contracts).
{% endhint %}

## Three Groups of Stakeholders

The Angle Core module relies on three types of agents which all benefit from it to maintain the stability of Angle stablecoins:

- **Stable Seekers or Users:** they can swap collateral against stable assets and conversely swap stable assets against a whitelisted collateral of their choice at oracle value and with no slippage. They pay small transaction fees when they mint and/or burn. Let's say that the price of wETH is 1000€, and the transaction fees 0.3%, then it is possible to swap 1 wETH for 997 EUR stablecoins. Conversely, with 1000 EUR stablecoins, if transaction fees are 0.3%, it is possible to get 0.997 wETH.
- **Hedging Agents (HAs):** they get leveraged positions with the multiple of their choice on a pair collateral/stablecoin in the form of perpetual futures. By doing so, they insure the Core module against the volatility of the collateral. On the one hand, if the price of the collateral they contribute to increases with respect to the value of the stablecoin, they can make leveraged capital gains, but on the other hand if the price decreases, they can lose a portion of the collateral they initially brought.
- **Standard Liquidity Providers (SLPs):** they lend money to the Core module and in return get part of the transaction fees induced by stable seekers minting and burning, as well as part of the returns made from lending some of the reserves to lending protocols (like Compound or Aave). They serve as the insurance of the insurance that is made up of HAs. They may face a small slippage when they exit if the Core module is not well collateralized.

![Angle's Stakeholders](../.gitbook/assets/core-agents-mechanism.jpg)

## Next ➡️

In the following pages, we will dive a bit more in-depth in the specificities of each stakeholder of Angle Core module, and explain in more detail how some essential bricks work.
