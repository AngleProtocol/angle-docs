---
description: Angle _New_ Module
---

# _Angle Borrowing Module_

Angle Borrow module goal is to help expand the Angle Protocol through another minting mechanism for Angle stablecoins. It is based on a debt mechanism, similar to those used by Maker with DAI, or Abracadbra with MIM. Users can deposit tokens as collateral into the protocol, and borrow agTokens from this deposit depending on specific parameters. 

The main advanatages of Angle Borrow module are: 
* No need for hedging agents to cover the protocol
* Easier to add new collaterals
* Users can keep exposure to their collateral tokens while using agEUR

These advantages help further expand Angle and its agTokens, both in terms of the stablecoins issued, their volume, and the chains and networks where they can be issued/redeemed. It has been designed to work hand in hand with the current one, and strenghten the Angle Protocol. AgTokens, like agEUR, are fully interoperable between both modules.

## Expanding agTokens

Easily adding new collateral tokens and deploying on other chains and networks makes it much easier for Angle to expand agTokens. Additionally, three other aspects make this module a more useful tool to push the growth of agEUR and the next Angle stablecoins. 

### No need for hedging agents
With the original module, launching a new agToken required finding enough demand for collateral/stablecoin long positions to hedge the reserves of the protocol. Additionally, users had to swap their original tokens to mint, depriving them of the exposure to their original tokens at the expense of the Angle stablecoin.

### Easier to add new collaterals
The independance of this new module structure makes it much easier to deploy new collaterals to mint agTokens. Furthermore, each collateral can have specific parameters and risk limits. A same token can also be deployed multiple times with different set of parameters. 

Coupled with the above difference, it makes this module much easier to deploy on other chains and networks. 

### Keeping exposure to collateral

As explained above, this module allows users to deposit tokens as collateral into the protocol, and mint agTokens that represent a debt they have toward the protocol. As opposed to the previous Angle module, users don't have to They have to pay an interest on this debt, and eventually pay it back at one point or another. If the value of their collateral compared to their debt drops below a certain safety level, called the minimum collateral ratio, the vault can get closed (liquidated). The important thing to note here is that there is no need for additional agents to come in to secure the protocol when agTokens are minted. 

### Boosting agTokens' expansion
By not being restricted by the demand for hedging agents or the loss of exposure to collateral for minters, and with its ability to safely and easily add new collaterals, this new module gives more opportunities to users to mint agTokens. This should increase the demand for agEUR and future agTokens to help the protocol grow to become the go-to decentralised stablecoin protocol. 


