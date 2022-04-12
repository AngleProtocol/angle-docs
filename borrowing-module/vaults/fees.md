---
description: Fees and Revenue in Angle Borrowing Module
---

# 💵 Fees and revenue

## 🔎 TL;DR

* Angle Borrowing module makes revenue (in stablecoins) from the users borrowing its stanlecoins, from liquidations and possibly from flash-loans
* If some vaults are liquidated too late, the protocol could also accrue a bad debt
* Surplus and bad debt are pooled across all existing `VaultManager` contracts, and a portion of the protocol revenue is distributed to veANGLE holders.

## Fees

### Rationale

At the top level, two types of fees can be charged to users borrowing agTokens:

* A minting fee
* A stability fee

Additionally, a fee called liquidation surcharge is captured by the protocol when liquidators send stablecoins to pay back vaults debt.

Collecting these fees creates revenue for the protocol, which serves multiple purposes:

* Accumulating reserves for riskier assets in case positions get under-collateralized
* Helping maintain peg of agTokens in extreme market conditions, by incentivizing or disincentivizing borrowing
* Accumulating surplus for veANGLE holders and the whole ANGLE ecosystem

### Minting Fee

When users open a vault, they deposit collateral and can mint agTokens depending on the collateral ratio of the vault. At this point, they could be charged a minting fee that would increase their debt. This fee is set by governance, and will most likely be set to 0 at the beginning.

As an example, if the minting fee is 1%, after minting 100 agTokens users would find themselves with 101 agTokens of debt.

### Stability Fee

The stability fee is similar to a **compounding interest rate** charged on the loan taken by users while it remains outstanding. Compounding means that the interest rate continuously accumulate on the debt.

#### Example

For example, if a user borrows 10,000 agTokens (`x`) for a time `t` of 2 years and the stability fee `r` is 2% / year, they will have an outstanding debt `d` of:

$$
d = x\times(1+r)^{t} \\ d=10,000 \times 1.02^{2} \\ d=10,404
$$

If during year 3, the interest rate `r'` is 2%, then the debt `d` owed by the user will become:

$$
d=10,000 \times 1.02^{2} \times 1.03 \\ d=10 821.18
$$

It's important to keep in mind that this fee can be changed by governance, and could also potentially be set to 0.

### Liquidation Surcharge

In the event of a [liquidation](../../new-module/liquidations.md), the protocol captures a fee called the liquidation surcharge. This is taken from the amount of stablecoins sent by the liquidators to pay back the debt of the vault.

### Putting this all together

If we try to consolidate all of this, we see that the fee structure in this module is not very complex. Basically, users pay three types of fees to the protocol in the form of an increase of their debt that will need to be paid back or collateralized.

This debt increase through fees happen at three moments:

1. When minting agTokens if there is a **minting fee** (which is optional)
2. During the life of the vault if agTokens is borrowed, through the **stability fee**
3. When a partial liquidation happens, through the **liquidation surcharge**

## Bad debt

It is possible that some vaults end up fully liquidated with no collateral backing the leftover stablecoin debt. In this case, the protocol counts these leftover stablecoins as bad debt. The surplus that the protocol accumulates serves to offset this bad debt and to make sure that there's always more collateral backing the stablecoins issued.

In the case where the protocol accrues too much bad debt, there is a settlement mechanism that can remove a collateral asset from the protocol, pay back owners of over-collateralized vaults and settle remaining owners of stablecoins at oracle value.

## Revenue Distribution

All the revenue and bad debt from this module are gathered in `Treasury` contracts. The protocol relies on keepers to fetch revenue from all `VaultManager` contracts.

Interestingly, stablecoins are minted when revenue is accrued. The reason for this is that if there is only one borrower borrowing 100 stablecoins at a 1% interest rate, then after a year this borrower needs to repay 101 stablecoins. But if only 100 stablecoins have been issued, there's no way for this borrower to repay its debt: as such when accruing revenue from `VaultManager` contracts, the protocol mints stablecoins. The logic is that these stablecoins should in some way end up in the market for vault owners to buy them and repay their debt.

If there is no bad debt, surplus accumulated is split between a reserve and the Governance according to a parameter that can be set by Governance. Keepers again are then in charge of pushing the surplus to a `surplusManager` address, that should distribute them to veANGLE holders as interest later.
