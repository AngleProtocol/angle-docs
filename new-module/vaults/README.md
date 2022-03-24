---
description: Angle Borrowing Module agTokens Vaults
---

# 🏦 agTokens Vaults

The core mechanism of this module relies on a vault system. Users can deposit collateral in `vaultManager` contracts, and borrow a certain amount of agTokens from this vault as a debt that will have to be repaid later. By doing so, they can keep their exposure to the tokens deposited as collateral, while being able to spend the borrowed funds. They can also use this mechanism to increase their exposure to the collateral they own, on-chain and in one transaction. 

**TLDR**
* Borrow agTokens from tokens deposited as collateral in the protocol
* Leverage collateral exposure in one transaction
* Transfer your debt between vaults to avoid liquidation


## Main features

The main features of vaults are the ability to borrow agTokens, and to leverage collateral exposure. 

### Borrowing agTokens

The main feature of vaults is the ability to **borrow** Angle stablecoins. A vault is opened when users deposit tokens as **[collateral](/new-module/glossary.md)** into a `VaultManager` contract. When doing so, they can choose to borrow a certain amount of agTokens against their collateral. The agTokens borrowed will be minted and deposited into their wallets, for them to use however they want. 

Once they have an open vault, users can borrow agTokens, repay their agTokens debt, and add or remove collateral from it.  

They also have to monitor their vaults' [health factor](/new-module/glossary.md). This metric keeps track of the "health" of the vault: it compares the collateral ratio of the vault with the minimum accepted. If the value of the collateral with respect to the agTokens borrowed decreases too much, the health factor will go below 1 and the vault can get **[liquidated](/new-module/liquidations.md)**. 

At some point, users that don't need their agTokens anymore can pay bak their debt, to get back what they originally deposited as collateral. 

Borrowing stablecoins is a very useful feature for users wanting to spend funds or profit from stablecoins yield, while keeping exposure to their original token. 

### Leveraging collateral exposure

The second feature is an extension of the first one. It lets users borrow agTokens to **leverage their collateral exposure** in one transaction. When users deposit collateral to open a vault, they can choose the Leverage feature and input the amount of additional exposure they want to the collateral token, up to a certain threshold. Then, the protocol will mint agEUR, swap it against the desired collateral, deposit it back into the vault, and repeat until the correct amount has been deposited. 

Similarly than in the above situation, if the value of the collateral decreases, the vault can get liquidated. 

Leveraging collateral exposure is a very useful feature for users wanting to safely increase exposure to their collateral token on chain, in a reasonable way and with a medium to long term horizon. 

## Additional details 

Vaults are defined by a specific set of information: 
- a collateral token that is deposited
- a debt token that is borrowed
- and a set of parameters: 
  - [collateral factor](/glossary.md)
  - [minting fee](/new-module/fees.md#minting-fee)
  - [stability fee](/new-module/fees.md#stability-fee)
  - [liquidation surcharge](/new-module/fees.md#liquidation-surcharge)
  - [dust amount](/new-module/vaults/README.md#dust-amount)

### Collateral Ratio

The most defining parameter of a vault is its **Collateral Ratio**. It defines the ratio between the collateral's value in stablecoin, and the value of the stablecoins borrowed. 

$$
\texttt{Collateral Ratio} = \frac{\texttt{collateral value}}{\texttt{debt value}}
$$

The higher the collateral ratio, the "safer" the vault, as the price decline of the collateral needed to get liquidated and lose the collateral is much bigger. 

Additionnally, each vault type has its own **collateral factor**. It dictates the minimum ratio between the value of stablecoins borrowed and the value of collateral deposited. If this ratio drops below the CF, the vault risk being liquidated. 

For example, if the CF of a vault type is at 2/3, or 150% of collateral ratio, users need to deposit at least x1.5 more than what they want to borrow. In practice, this means that users wanting to borrow 1,000 agEUR need to deposit at least 1,500€ of ETH for example. If the value of their ETH deposit drops, pushing their CR below 150%, they are in risk of getting liquidated. 


### Isolated positions & debt transfer
#### Isolated positions
One interesting charateristic of vaults is that they are isolated meaning that a position of an address in a vault is totally separated from a position of the same address in another vault. 

One vault liquidation has no impact on the others. 

#### Debt transfers

Thanks to the isolation of positions, one could become under a risk of liquidation, while the other has plenty collateral and a much higher collateral ratio. 

In this case, users are able to perform a debt transfer, meaning that they will transfer part of their debt from one of their vault to another. 

This lowers the collateral ratio of the first vault, and increases that of the second. It allows users to rebalance their debt and collateral ratio between their different vaults. 

### Dust Amount

To make sure the protocol doesn't accumulate bad debt, the protocol needs to enforce a minimum amount of agEUR to be borrowed. This is required to make sure that each position has enough debt so that it's always worth to liquidate it. 

It's important to keep in mind that these debt-based models similar to Maker rely heavily on liquidations to remain robust and collateralized. If the amounts to liquidate are too small, the profit made by liquidators could be too low so that it doesn't even cover gas cost, and is not profitable anymore. In that case, the protocol would be left holding under-collateralized positions. 