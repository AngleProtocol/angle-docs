---
description: Minting agEUR from specific tokens
---

# 🛩 Token Reactors

Thanks to the previous features of whitelisting addresses and accepting riskier collaterals with tailored parameters, Angle Borrow module could also be used to mint agEUR for specific use cases only. 

## Investing minted agTokens

For example, we could imagine a situation in which the agTokens minted from a Token Reactor could be used only by a whitelisted strategy contract, which would invest them directly on behalf of users. The parameters for this type of vault would be set according to the risk of the assets accepted as collateral, and the collateral ratio of the vault would be programatically managed by the underlying strategy to reduce the chances of getting liquidated. 

## Offering yield on potentially any tokens

This would effectively create staking pools for volatile assets. Users depositing their tokens there would earn yield in agTokens on top of these volatile assets that potentially increase in value, giving them additional utility.  