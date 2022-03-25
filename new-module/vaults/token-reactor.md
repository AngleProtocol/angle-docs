---
description: Minting agEUR from specific tokens
---

# 🛩 Token Reactors

Thanks to the previous features of whitelisting addresses and accepting riskier collaterals with tailored parameters, Angle Borrow module can also be used to mint agEUR for specific use cases only. 

## Investing minted agTokens

For example, the agTokens minted from a specific vault can be used only by a whitelisted strategy contract, which invests them directly on behalf of users. The parameters for this type of vault is set according to the risk of the assets accepted as collateral, and the collateral ratio of the vault is programatically managed by the underlying strategy to reduce the chances of getting liquidated. 

## Offering yield on any tokens

This effectively creates staking pools for volatile assets. Users depositing their tokens in a token reactor can earn yield in agTokens on top of these volatile assets, that potentially increase in value themselves. This gives them additional utility. 