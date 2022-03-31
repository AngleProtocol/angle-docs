---
description: Minting agTokens from specific tokens
---

# 🛩 Token Reactors

Thanks to the previous features of whitelisting addresses and accepting riskier collaterals with tailored parameters, Angle Borrowing module can also be used to mint agTokens for specific use cases only. This gives for instance the opportunity for DAOs to get yield on idle treasury assets.

## Investing minted agTokens

For example, the agTokens minted from a specific vault can be used only by a whitelisted strategy contract, which invests them directly on behalf of users. The fact that the contract controls the agTokens makes it less risky to use these assets as a collateral: the contract can indeed pull the agTokens before a liquidation happens if the price of the collateral decreased by too much. In fact, the collateral ratio of the vault is programatically managed by the underlying strategy to reduce the chances of getting liquidated.

On top of that, the parameters for this type of vault are set according to the risk of the assets accepted as collateral.

## Offering yield on any tokens

This effectively creates staking pools for volatile assets. Users depositing their tokens in a token reactor can earn yield in agTokens on top of these volatile assets, that potentially increase in value themselves. This gives additional utility to a long tail of unused assets in DeFi, and more generally open the gates for any DAO to get yield on idle treasury assets.

## Increasing agTokens liquidity

On top of offering native yield on volatile tokens, Angle Token Reactors also allow to increase agTokens liquidity across DeFi, making it a much better stablecoin for users.
