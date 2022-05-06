---
description: Flash loans using agTokens
---

# ⚡️ Angle flash-loans

It is possible to take potentially uncapped and free flash-loans with agTokens.

## What are flash loans?

They are a type of loans that allow to borrow and repay tokens in one transaction. Thanks to that, the entity taking out the loan don't need to put down any collateral, as the lender is guaranteed to be paid back if the transaction is executed. This also allows them to borrow/mint huge amounts of agTokens through flash-loans.

The main use case for flash loans is arbitrage between pools, which usually helps rebalancing liquidity over the ecosystem.

![Flash loans explained](../.gitbook/assets/Flash-loans.png)

## Flash loans with agTokens

Contrary to what is done in other lending protocols like Aave, tokens lent by the protocol during flash loans are not taken from a liquidity pool, but they are directly minted from the protocol's contracts.

More info on how to take a flash-loan with Angle in our [developers documentation](https://developers.angle.money/overview/guides/flashloans).
