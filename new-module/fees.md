---
description: Fees in Angle _New_ Module
---

# Fees

At the top level, two types of fees can be charged to users borrowing agEUR: 
- a minting fee
- a stability fee

These fees serve multiple purposes: 
- accumulating reserves for riskier assets in case positions get under-collateralized
- Helping maintain peg of agEUR in extreme market conditions, by incentivizing or disincentivizing borrowing
- accumulating surplus for veANGLE holders and the whole ANGLE ecosystem

Additionnally, a fee called liquidation surcharge is charged on vaults that get liquidated. 

## The different types of fees
### Minting Fee
When users open a vault, they deposit collateral and can mint agEUR depending on the collateral ratio of the vault. This is when the minting fee is charged.  This fee is set by governance, and can also be put to 0. 

For example, if the minting fee is 1%, after minting 100 agEUR users would find themselves with 101 agEUR of debt. 

### Stability Fee
This fee is similar to an interest rate charged on the loan taken by users while it remains outstanding. 

For example, if a user borrows 10,000 agEUR for 2 years and the stability fee is 3% / year, they will have an outstanding debt of 10,600 agEUR. 

It can be set by governance and could potentially be 0, though this is unlikely. 

### ?? Liquidation Surcharge ??

In the event of a [liquidation](/new-module/liquidations.md), a fee called liquidation surcharge is charged to the vault owner. This will reduce the health factor of the position at liquidation. If it brings this factor too low, the position will be entirely liquidated, and the liquidation surcharge will go to the protocol. If the collateral ratio of the position at liquidation after the surcharge is still high enough, it will increase the vault's remaining debt. 

## Putting this all together

If we try to consolidate all of this, we see that the fee structure in this module is not very complex. Basically, users pay three types of fees to the protocol in the form of an increase of their debt that will need to be paid back or collateralized. 

This debt increase through fees happen at three moments: 
1. When minting agEUR if there is a **minting fee**
2. During the life of the vault if agEUR is borrowed, through the **stability fee**
3. When a partial liquidation happens, through the **liquidation surcharge**