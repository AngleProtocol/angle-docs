---
description: Growing surplus, incentivizing veANGLE holders, and offering yield to the core module's liquidity providers
---

# 📈 Lending Strategies - Yield on Reserves

## 🔎 TL;DR

- The core module earns interest on the reserves it holds by lending it to other platforms.
- To do so, the core module relies on strategies which decide how much and in which core modules reserves should be placed.
- Angle Core module is modular: there can be multiple strategies for a single collateral, each interacting with multiple platforms.
- Strategies are what enable the core module to offer higher yield to SLPs than what they would get by lending directly to other core modules.

## 💡 Rationale

Lending a fraction of the reserves to other lending platforms is part of what makes the core module attractive to Standard Liquidity Providers. By lending reserves, it can at the same time offer interest to Standard Liquidity Providers, accumulate some reserves, and incentivize veANGLE holders.

The distribution of interest between SLPs, veANGLE holders, and reserves, is dictated by two parameters that can be found in [Angle Analytics](https://analytics.angle.money). More information in the [SLPs FAQ page](standard-liquidity-providers/faq-slps.md#do-slps-get-all-transaction-fees-and-lending-returns-from-the-protocol).

![](../.gitbook/assets/angle-strategies-flow.png)

## 🎨 Design

The design of that has been heavily inspired by what [Yearn](https://yearn.finance) does. Angle core module relies on strategies, that themselves use Lender's contracts interacting with lending and other yield farming core modules.

Just like on Yearn, new strategies to get some yield on the core module's collateral can be added along the way by governance votes. Each strategy can also support multiple lending platforms or core modules.

Each collateral for each stablecoin has its set of strategies to get some yield on it. For instance, for a agEUR stablecoin backed by USDC and DAI, we may have for the USDC collateral a single strategy trying to always optimize to get the best APY between Compound and Aave, and for the DAI stablecoin two strategies, one that just consists in lending to Compound and one that consists in optimizing between Aave and Cream.

The first strategy implemented simply consists in optimizing lending between Compound and Aave and pick the one with the best APY.

Since gas cost is quite high in Ethereum, users minting and burning, SLPs depositing and withdrawing, as well as HAs opening and closing positions never interact directly with strategy contracts. When they send or withdraw collateral to the core module, their collateral goes or is taken from the core module's reserves, and it is not directly lent or withdrawn from strategies.

The way collateral is lent or withdrawn from strategies and their corresponding lending platforms is through keepers calling the `harvest`function to withdraw or lend collateral to strategies.

{% hint style="info" %}
It was preferred to get inspiration from Yearn rather than using Yearn directly in order to keep full control on the reserves and to remove a third party integration which would have taken up some fees.
{% endhint %}

## 💹 Debt Ratio

For each strategy associated to a collateral, it is possible to compute a debt ratio that corresponds to the ratio between what has been lent and the total amount of collateral in the pool \(what's kept in reserves + what has been lent across all strategies\). Each strategy has its target debt ratio. Below this debt ratio, keepers can call the `harvest` function to give more collateral to the strategy and above this debt ratio, collateral can be withdrawn from the strategy and hence from the corresponding lending platforms.

{% hint style="info" %}
Keepers cannot choose the amount they lend or withdraw from lending platforms: this is automatically computed using the strategy's target debt ratio at each call to `harvest.`
{% endhint %}

## ✖️ Back To The Multiplier Effect For SLPs

Thanks to the lending strategies, SLPs get rewards not only from their capital, but also from that of Users and HAs. This allow them to get potentially higher yield than if they were farming only with their capital. More info in the SLP page below.

{% content-ref url="standard-liquidity-providers/README.md" %}
[standard-liquidity-providers/README.md](standard-liquidity-providers/README.md#%E2%9C%96-multiplier-effect)
{% endcontent-ref %}
