---
description: Fees and revenue in Angle _New_ Module
---

# Fees and revenue

At the top level, two types of fees can be charged to users borrowing agEUR: 
- a minting fee
- a stability fee

Additionally, a fee called liquidation surcharge is captured by the protocol when liquidators send stablecoins to pay back vaults debt. 

Collecting these fees creates revenue for the protocol, which serves multiple purposes: 
- accumulating reserves for riskier assets in case positions get under-collateralized
- Helping maintain peg of agEUR in extreme market conditions, by incentivizing or disincentivizing borrowing
- accumulating surplus for veANGLE holders and the whole ANGLE ecosystem


## Fees
### Minting Fee
When users open a vault, they deposit collateral and can mint agEUR depending on the collateral ratio of the vault. At this point, they could be charged a minting fee that would increase their debt.  This fee is set by governance, and will most likely be set to 0 at the beginning. 

As an example, if the minting fee is 1%, after minting 100 agEUR users would find themselves with 101 agEUR of debt. 

### Stability Fee
This fee is similar to an interest rate charged on the loan taken by users while it remains outstanding. 

For example, if a user borrows 10,000 agEUR for 2 years and the stability fee is 3% / year, they will have an outstanding debt of 10,600 agEUR. 

It can be set by governance and could potentially be 0, though this is unlikely. 

### Putting this all together

If we try to consolidate all of this, we see that the fee structure in this module is not very complex. Basically, users pay three types of fees to the protocol in the form of an increase of their debt that will need to be paid back or collateralized. 

This debt increase through fees happen at three moments: 
1. When minting agEUR if there is a **minting fee**
2. During the life of the vault if agEUR is borrowed, through the **stability fee**
3. When a partial liquidation happens, through the **liquidation surcharge**


## Revenue

### Liquidation Surcharge

In the event of a [liquidation](/new-module/liquidations.md), the protocol captures a fee called the liquidation surcharge. This is taken from the amount of stablecoins sent by the liquidators to pay back the debt of the vault. 

### Storing and distributing revenue
All the revenue from this module is gathered in Treasury contracts. The funds are split between a reserve and the Governance according to a parameter that can be set by Governance. The Governor address can then pull funds dedicated to governance, to distribute them to veANGLE holders as interest. 
