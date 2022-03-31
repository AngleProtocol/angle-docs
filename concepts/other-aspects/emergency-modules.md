---
description: How the Core module behaves in case of distress
---

# 🚑 Risks and Emergency Modules

## 🔎 TL;DR

- Angle Core module is mostly at risk when a sudden collateral price decrease is combined with a severe drop in demand for leverage by Hedging Agents.
- The Core module has the safety modules and incentives to be able to resist and maintain peg even in extreme market conditions.

## ⚡ Angle Core module's Risks

As with any stablecoin protocol, the main risk is to be unable to maintain convertibility between stablecoins and collateral, which might affect peg. In this case, governance might have to deter exits with high fees, or to freeze transactions. As long as the Core module remains over-collateralized, there is no risk that this happens.

The Core module becomes under-collateralized if is not hedged enough by HAs, and there are not enough SLPs to over-collateralize it.

Here, we explore all the responses the Core module can give in case of distress. It is interesting to note that it is most at risk when both events occur: decrease in demand for leverage longs, and collateral prices drop \(or increase in the price of the asset the Core module tries to peg\). Contrary to other stablecoin protocols, the first condition is necessary, and a collateral price drop alone is not sufficient to put the Core module at risk of under-collateralization, and hence bank run.

## 🛡️ Hedging Agents Insurance

Hedging Agents can enter Angle Core module with even very small leverage like x1.01, or x1.1. To be over-collateralized, the Core module doesn't need HAs to take on highly leveraged positions.

Even if demand for perpetual futures decreases, the Core module should remain cheaper than most protocols allowing to get on-chain leverage, like Aave or Compound. In normal times, when demand for leverage is high and almost all the collateral is hedged, transaction fees are set so that it is slightly more expensive to open a position. When demand for perpetual futures drop, fees drop \(following the hedging curve\) and the Core module becomes much cheaper than other on-chain protocols.

It should also be cheaper to get leverage with the Core module than with centralized exchanges. With Angle, traders only pay entry and exit fees: there is no funding cost. It is more cost efficient for Hedging Agents that have a long-term horizon to open positions on Angle rather than on a centralized exchange, as this funding rate ususally represents a high cost.

Governance has the ability to vote to activate governance token distribution to Hedging Agents to increase incentives: HAs could be paid to get long \(even with really small multipliers\) using Angle Core module.

These three effects should help the Core module attract the remaining demand for leverage in times of deleveraging in the market, helping it stay solvent and over-collateralized.

## 💰 Core module Surplus

In normal times, the Core module accumulates some surplus from transaction fees and lending returns not distributed to SLPs. It can also generate revenue from collateral prices increase when the collateral is not fully covered by HAs.

While everything that can be done with this surplus is still to be determined \(like auctions where governance tokens are burnt against a portion of the surplus\), the surplus mostly serves as the first buffer to better deal with drops in collateral ratio.

## 🍀 Standard Liquidity Providers Insurance of the Insurance

If the incentives put in place do not attract enough HAs to fully insure the Core module against the volatility of the collateral and if there is not enough surplus accumulated, it can rely on the collateral brought by Standard Liquidity Providers to ensure full convertibility of the stablecoins. There is an equilibrium threshold to expect with Standard Liquidity Providers \(SLPs\). Indeed, the fewer SLPs there are, the more interesting it becomes to be a SLP because of the [multiplier effect](https://docs.angle.money/concepts/standard-liquidity-providers#multiplier-effect) that is spread among SLPs.

To prevent the cascading effect that could be induced if SLPs all exit the Core module, a slippage is introduced to discourage SLPs from exiting when the collateral ratio is too low: this is a way to make sure that there will always be SLPs in the Core module. Note here that HAs are never affected by exit restrictions: they can find incentives to enter at any point in time thus bringing extra-liquidity, regardless of whether there has been a price drop or not.

Besides, when the Core module starts to be too unhealthy, as explained [in this page](../standard-liquidity-providers/), there are recollateralization incentives for SLPs: a fraction of the transaction fees and lending yield going to SLPs can be automatically put aside, and only be recoverable by SLPs when the Core module is collateralized back again. This means that a new SLP giving money to recollateralize a pool may receive transaction fees and yield accumulated before her arrival in the pool.

Governance can also choose to distribute a bigger fraction of the transaction fees and lending returns to SLPs to make them stay, or to offer more governance tokens through the staking contracts

## 💱 Dynamic Transaction Fees for Users

In the meantime, transaction fees for users minting and burning adjust automatically based on the hedging ratio of the Core module. This means that it is more expensive for users to mint stablecoins \(thus adding collateral into the Core module\) if the collateral that is already there is not hedged enough by Hedging Agents.

Besides, if the collateral ratio keeps decreasing, governance can choose at its discretion to mitigate bank run scenari by increasing burn transaction fees by inducing a collateral ratio dependency.

You can have a look at [Angle's analytics](https://analytics.angle.money) page to follow the different hedge and collateral ratios, and the current transaction fees.

## ⌛ Collateral Diversification and Settlement

In the above sections, the situation with a single collateral type was described. It is important to note that the Core module accepts different collateral types, diversifying its overall riske. With asset diversification, Angle Core module is less prone to having the issue where one asset drops and affects the stability of the whole system.

If one collateral becomes too risky, the Core module has the ability to incentivize liquidity providers to contribute more to one pool than to another through staking incentives and transaction fees.

It is also possible to revoke a collateral for a given stablecoin if it reveals too risky: we call this process collateral settlement. If there is collateral left in the pool at this time, it is sent to another contract that is specifically designed to handle the settlement.

The goal of settlement is to choose how much each category of stakeholders is going to get based on their claims, and then to reimburse each users, HAs and SLPs which asked it based on that. This process has been thought to heavily favor governance token and owners.

The following page explains how in details this collateral settlement process works:

{% page-ref page="collateral-settlement.md" %}

## 📜 Stablecoins Independence

The Core module's stablecoins are independent from one another, meaning that if one stablecoin fails, other stablecoins will not be impacted. The collateral pools related to each stablecoin are different and separated from one another, and the contracts behind have different addresses.

![Division of pools and collaterals](../../.gitbook/assets/division-of-funds.jpg)

In case of a security breach, to trigger the emergency shutdown at the level of the Core module, all collateral for all stablecoins should be settled.
