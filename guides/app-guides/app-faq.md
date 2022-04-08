# App FAQ

## General

### Why do I need to approve the same token multiple times?

In Angle, all funds tied to a specific collateral/agToken pair are managed by an individual contract. This increases security, as failures of one stablecoin or collateral in the protocol should not impact the others. It also allows for more flexibility in the protocol.

The negative side-effect is that users need to approve collateral not just once, but for each collateral/agToken pair. Approvals should even be given twice for each pair: one for minting as a user and depositing as a SLP, and one to open positions as a Hedging Agent.

## agTokens Users

### Why can't I burn my stablecoins?

There might by two rare cases in which users are unable to burn agTokens:

1. The pool users want to withdraw collateral from does not have enough collateral in reserves because it is lent out. In this case, they should wait for the next `harvest()` call from strategies, which will send funds back to the pool.
2. Users cannot burn more agTokens for a collateral than what has been issued using this collateral.

In both cases, users can always burn the agTokens against another collateral.

## Hedging Agents

### Why can't I open a new position?

The goal of the protocol is to balance the size of open positions \(demand for volatility\) with the quantity of agTokens issued from collateral \(supply of volatility\) for each collateral/agToken pair.

The protocol tracks the ratio for each pair between the amount hedged by HAs and the available amount to hedge. This ratio is called the hedge ratio, and the protocol aims for a target. When the current hedge ratio goes above this target, the protocol prevents HAs \(traders\) to open new leverage positions, which would increase this imbalance.

### Why can't I update or close my position?

When a user opens a position, this position is locked for an hour. This means that they cannot remove collateral from their margin or close their position during this time. The lock time can be updated by governance.

It was put in place to mitigate the front-running risks that could happen, in particular using flashloans, as the protocol relies on oracle prices that could deviate from market price.

### Why did one of my open positions disappear?

If your open position is not displayed in your positions list, it certainly means that it has been closed. It could either have been liquidated because of a maintenance margin too low \(due to a decrease in price\), or force closed because of the hedge ratio being too high.

The protocol has a target hedge ratio, and a limit hedge ratio \(higher than the target\). When the hedge ratio goes above the target, traders are unable to open new positions. When it goes above the limit, some positions can be force-closed to make the hedge ratio go back to the target.

### Why did I receive sanTokens upon removing collateral/closing my positions?

In the case there is not enough funds in a pool Hedging Agents are withdrawing from, they first get the collateral present in the pool, and then receive an amount of sanTokens for the remaining value of collateral they should get. They can then sell those sanTokens whenever the pools have more funds, after a call to `harvest()` for instance.

## Standard Liquidity Providers

### Why are the APYs different for same asset pools?

All collateral/agTokens pools are separated and managed by independent contracts. This means that, even though pools for a given collateral can use the same strategies, it could be the case that they don't or that some parameters related to these strategies differ.

Additionally, the amounts put by users minting on these pools differ, which impact the multiplier effect explained [here](/core-module/standard-liquidity-providers/README.md#✖-multiplier-effect), and change the APYs for SLPs.

### Why can't I withdraw my collateral?

If SLPs want to withdraw more funds than what is immediately available in their pool (due to funds being lent out), their transactions will get reverted. To prevent this from happening, we display an alert preventing them from making the transaction.

They should wait for the next `harvest()` call from strategies, which should send funds back to the pool.
