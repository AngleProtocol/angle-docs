---
description: Whitelisting addresses, volatile assets as collateral, and token reactors
---

# Special features


## Whitelisting Addresses

While there will be one contract per vault type handling positions, some collateral types could be made permissioned meaning that only some pre-defined addresses would be allowed to borrow from it.

This could serve different use cases. 

### For specific collateral types

The whitelisting of addresses could be used to deploy specific collateral types (like real-world assets for example). In this case, governance may need to keep tight control on who can borrow to avoid exploits. 

### For specific entities

A DAO or a company could have a significant amount of a specific token. With this whitelisting feature, the protocol would build a tailored vault type, with specific parameters and potentially pre-defined spending conditions of the loan. 

Let's look at a few examples: 

Let's say that a company has ETH in reserves, and want to provide liquidity in the agEUR/USDC Uniswap V3 pool. In this case, we could imagine a specific vault type that could only use the borrowed funds to provide liquidity to the UniV3 agEUR/USDC pool with a pre-defined ratio. In this case, this vault could benefit from a higher collateral factor or a lower stability fee for example. 

We can also imagine the case of a DAO with governance tokens reserves. In this case, the DAO might want to benefit from the use of a stablecoin for its operations, or to invest it in pre-defined strategies. In this case, the protocol would be able to build a tailored vault, that would allow to borrow agEUR from this governance token, but at a lower collateral factor. 

## Token Reactors

Expanding on this idea, Angle Borrow module can also be used to mint agEUR from riskier tokens. The minted agEUR could be used only by a whitelisted strategy contract, which would invest them directly in pre-defined strategies on behalf of users. The parameters for this type of vaults would be set according to the risk of the assets accepted as collateral, and the collateral ratio of the vault would be programatically managed by the underlying strategy to reduce the chances of getting liquidated. 

This would allow users to earn yield in agTokens on top of volatile assets that potentially increase in value, giving them additional utility. 