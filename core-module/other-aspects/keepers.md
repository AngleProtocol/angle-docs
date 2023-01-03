---
description: Helping the protocol achieve its desired outcome
---

# 🏭 Keepers

## 🔎 TL;DR

- Keepers help the protocol perform some tasks which cannot be performed automatically in the Core Module
- Angle Core Module needs keepers to arbitrage the stablecoins issued, to maintain the lending strategies, to monitor Hedging Agents' positions, and to update transaction fees parameters.

## 💡 Rationale

Keepers are external incentivized actors that help the protocol work smoothly. Since EVM-compatible blockchains are inherently passive, there is a need for external input from people telling the protocol to perform a certain action at a given moment.

Angle needs multiple types of keepers to get involved. Angle Labs, Inc. developped bots to help keepers achieve some of their operations.

## ⚖️ Arbitrage Keepers

Tokens issued by the protocol are tradable on exchanges and therefore have a market price. [To make the price of these tokens stable](/core-module/), the protocol relies on arbitrageurs which have profitable opportunities whenever the market prices of the tokens deviate from peg.

## 🍀 Keepers for [Yield Strategies](/core-module/lending.md)

Keepers are also the agents helping [the yield strategies](/core-module/lending.md) function effectively and integrate smoothly with the protocol. It is possible that, at a given moment a too important proportion of collateral, is being lent to a strategy. In this case, keepers are the ones adjusting the debt ratio of the strategy making sure that there are always enough reserves held in the protocol to pay users, SLPs, or HAs who would want to exit the protocol.

The adjustments are done within the defined target debt ratio of each strategy. SLPs willing to get as much returns as possible, or governance token holders acting for the good of the protocol are the ones usually calling the functions readjusting the debt ratio.

Governance is able to vote to set additional rewards in the form of governance tokens to the keepers calling the `harvest` function for each strategy.

## 🛡️ Keepers for [Hedging Agents](../../concepts/other-aspects/hedging-agents/)

As explained [in the Hedging Agents' part](/core-module/hedging-agents/faq-ha.md#what-happens-if-there-are-too-many-has-with-respect-to-the-amount-to-hedge-from-the-core-module), if HAs hedging is too important compared to what has been brought by users, then some positions need to be closed.

The same goes [for the liquidation of HAs](/core-module/hedging-agents/README.md#💧-has-liquidations): if the position of an HA is inferior to its maintenance margin, this position should be liquidated.

In both cases, the protocol, which is passive, relies on keepers for enforcing these rules.

Keepers are directly incentivized to close unhealthy positions. In the case of perpetuals that should be liquidated, keepers get a portion of the remaining cash out amount. For those being force-closed, keepers get a fraction of the closing fees.

In the case where there are too many HAs, keepers are able to select a list of HAs positions to close. In this case, they get higher rewards if cashing out these perpetuals bring the protocol near the desired coverage bounds. This is called force-closing positions.

In all cases, the amount that can be given to keepers is capped.

## Keepers for Transaction Fees and Slippage

[The slippage](/core-module/standard-liquidity-providers/README.md#🥅-slippage) incurred by Standard Liquidity Providers depends on the collateral ratio of the protocol for the concerned stablecoin. Governance may also choose to introduce a relation between users minting and burning fees and the protocol's collateral ratio for the stablecoin.

It would actually be pretty expensive to compute the collateral ratio of the protocol on-chain each time a SLP tries to withdraw. There is a need for keepers to call the function updating the transaction fees and the slippage induced in case of changes in the collateral ratio.

{% hint style="info" %}
No specific rewards have been set for these keepers yet. Governance may define an off-chain reward mechanism based on on-chain data.
{% endhint %}
