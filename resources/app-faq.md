# 🧐 App FAQ

## General

### Why do I need to approve the same token multiple times?

In Angle, all funds tied to a specific collateral/agToken pair are managed by an individual contract. This increases security, as failures of one stablecoin or collateral in the protocol shouldn't impact the others. It also allows more flexibility in the protocol.

The negative side-effect is that users need to approve collateral not just once, but for each collateral/agToken pair. Approvals should even be given twice for each pair: one for minting as a user and depositing as a SLP, and one to open positions as a Hedging Agent.

### What happens if the protocol doesn't have enough funds in reserve?

If users or SLPs want to withdraw more funds that are currently in a pool (due to funds being lent out), their transactions will get reverted. To prevent this from happening, we display an alert informing the users and preventing them to make the transaction.

In the case of Hedging Agents, the protocol always let them get out of a position to close their exposure. However, if there isn't enough funds as well, Hedging Agents will first get the collateral present in the pool, and then receive an amount of sanTokens from the collateral/stablecoin pool they had a position on for the remaining value of collateral they should get. They can then try to sell those sanTokens whenever the protocol gets more funds.

## Hedging Agents

### Why can't I open a new position?

The goal of the protocol is to balance the size of open positions (demand for volatility) with the quantity of agTokens issued from collateral (supply of volatility) for each collateral/agToken pair.

The protocol has a target ratio of his balance called the target hedge amount. When the current hedge ratio goes above this target, the protocol prevents HAs (traders) to open new leverage positions, which would increase this imbalance.

### Why can't I update or close my position?

When a user opens a position, this position is locked for an hour. This means that users can't remove margin or close the position during this time. The lock time can be updated by governance.

It was put in place to mitigate the front-running risks that could happen, in particular using flashbots, as the protocol relies on oracle prices that could deviate from market price.

### Why did one of my open positions disappear?

If your open position is not displayed in your positions list, it means it has been closed. It could either have been liquidated because of a maintenance margin too low (due to a decrease in price), or force closed because of the hedge ratio being too high.

The protocol has a target hedge ratio, and a limit hedge ratio (higher than the target). When the hedge ratio goes above the target, traders are unable to open new positions. When it goes above the limit, some positions can be force-closed to make the hedge ratio go back to the target.

## Standard Liquidity Providers

### Why are the APYs different for same asset pools?

As detailed here [link to the global FAQ], all collateral/agTokens pools are separated and managed by independent contract. This means that, even though pools for a given collateral can use the same strategies, it could be the case that they don't or that some parameters related to these strategies differ.

Additionally, the amount put by users minting on these pools will differ, which will impact the multiplier effect explained here [link to multiplier effect explanation], and change the APYs for SLPs.
