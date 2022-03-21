---
description: Angle _New_ Module agTokens Vaults
---

# agTokens Vaults

The core mechanism of this module relies on a vault system. Users can deposit collateral in vault contracts, and borrow a certain amount of agTokens from this vault as a debt that will have to be repaid later. By doing so, they can keep their exposure to the tokens deposited as collateral, while being able to spend the borrowed funds. 

Vaults are defined by a specific set of information: 
- a collateral token that is deposited
- a debt token that is borrowed
- and a set of parameters: 
  - [minting fee](/new-module/fees.md#minting-fee)
  - [stability fee](/new-module/fees.md#stability-fee)
  - [liquidation surcharge](/new-module/fees.md#liquidation-surcharge)
  - [Minimum Collateral Ratio](/glossary.md)
  - dust amount

## Collateral Ratio

The most defining parameter of a vault is its **Collateral Ratio**. It defines the ratio between the value of the collateral deposited, and the value of the stablecoins borrowed. 

$$
\texttt{Collateral Ratio} = \frac{\texttt{collateral value}}{\texttt{debt value}}
$$

The higher the collateral ratio, the "safer" the vault, as the price decline of the collateral needed to get liquidated and lose the collateral is much bigger. 

Additionnally, each vault type has its own **Minimum Collateral Ratio**. It dictates the minimum amount of collateral required for 100 of stablecoins borrowed. If the collateral ratio drops below the MCR, the vault risk being liquidated. 

For example, if the Minimum Collateral Ratio of a vault type is at 150%, it means that users need to deposit at least x1.5 more than what they want to borrow. In practice, this means that users wanting to borrow 1,000 agEUR need to deposit at least 1,500€ of ETH for example. If the value of their ETH deposit drops, pushing their CR below 150%, they are in risk of getting liquidated. 


## Isolated positions & debt transfer
### Isolated positions
One interesting charateristic of vaults is that they are isolated meaning that a position of an address in a vault is totally separated from a position of the same address in another vault. 

One vault liquidation will have no impact on the others. 

### Debt transfers

Thanks to the isolatation of positions, one could become under a risk of liquidation, while the other has plenty collateral and a much higher collateral ratio. 

In this case, users are able to perform a debt transfer, meaning that they will transfer part of their debt from one of their vault to another. 

This will lower the collateral ratio of the first vault, and increase that of the second one. It allows users to rebalance their debt and collateral ratio between their different vaults. 

## Dust Amount

To make sure the protocol doesn't accumulate bad debt, the protocol needs to enforce a minimum amount of agEUR to be borrowed. This is required to make sure that each position has enough debt so that it's always worth to liquidate it. 

It's important to keep in mind that these debt-based models similar to Maker rely heavily on liquidations to remain robust and collateralized. If the amounts to liquidate are too small, the profit made by liquidators could be too low so that it doesn't even cover gas cost, and is not profitable anymore. In that case, the protocol would be left holding under-collateralized positions. 