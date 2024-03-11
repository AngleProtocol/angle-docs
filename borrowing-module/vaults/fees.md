---
description: Fees and Revenue in Angle Borrowing Module
---

# 💵 Fees and revenue

## 🔎 TL;DR

- Angle Borrowing module makes revenue (in stablecoins) from the users borrowing its stablecoins, from liquidations
- If some vaults are liquidated too late, the protocol could also accrue a bad debt
- Surplus and bad debt are pooled across all existing `VaultManager` contracts

## Fees

### Rationale

At the top level, three different fees can be charged to users borrowing stablecoins:

- A mint fee
- A stability fee
- A repay fee

Note that some (or all) of these fees can be set to 0. Additionally, a fee called liquidation surcharge is captured by the protocol when liquidators send stablecoins to pay back vaults debt.

Collecting these fees creates revenue for the protocol, which serves multiple purposes:

- Accumulating reserves for riskier assets in case positions get under-collateralized
- Helping maintain peg of stablecoins in extreme market conditions, by incentivizing or disincentivizing borrowing
- Accumulating surplus for veANGLE holders and the whole ANGLE ecosystem

{% hint style="info" %}
The state of the fees taken for each type of vault can be checked directly on the [Analytics](https://analytics.angle.money) of the protocol.
{% endhint %}

### Mint Fee

When users open a vault, they deposit collateral and can mint stablecoins depending on the collateral ratio of the vault. At this point, they could be charged a mint fee that would increase their debt.

For example, if the mint fee is 1%, after minting 100 stablecoins users would find themselves with 101 stablecoin of debt.

This fee is set by governance, and it is most often set to 0, meaning it is an option available for governance.

### Stability Fee

The stability fee is similar to a **compounding interest rate** charged on the loan taken by users while it remains outstanding. Compounding means that the interest rate continuously accumulate on the debt.

#### Example

For example, if a user borrows 10,000 stablecoins (`x`) for a time `t` of 2 years and the stability fee `r` is 2% / year, they will have an outstanding debt `d` of:

$$
d = x\times(1+r)^{t} \\ d=10,000 \times 1.02^{2} \\ d=10,404
$$

If during year 3, the interest rate `r'` is 3%, then the debt `d` owed by the user will become:

$$
d=10,000 \times 1.02^{2} \times 1.03 \\ d=10 821.18
$$

It's important to keep in mind that this fee can be changed by governance, and could also potentially be set to 0.

### Repay Fee

Similarly than at mint, the protocol can charge a fee to users repaying their debt towards the protocol. In practice, this means that, for agEUR, a user repaying 110 agEUR of debt would have to bring 111.1 agEUR if there is a 1% repaying fee.

As for the mint fee, the repay fee is most often set to 0, and you should check the [analytics](https://analytics.angle.money) to check whether there has been updates.

### Liquidation Surcharge

In the event of a [liquidation](../../new-module/liquidations.md), the protocol captures a fee called the liquidation surcharge. This is taken from the amount of stablecoins sent by the liquidators to pay back the debt of the vault.

Its value is usually set around 2%.

### Putting this all together

In summary, users may pay fees to the protocol in the form of an increase of their debt that will need to be paid back or collateralized.

This debt increase through fees may happen at four (optional) moments:

1. When minting stablecoins if there is a **mint fee**
2. During the life of the vault if stablecoins are borrowed, through the **stability fee**
3. When repaying an agToken debt if there is a **repay fee**
4. When a liquidation happens, through the **liquidation surcharge**

## Bad debt

It is possible that some vaults end up fully liquidated with no collateral backing the leftover stablecoin debt. In this case, the protocol counts these leftover stablecoins as bad debt. The surplus that the protocol accumulates serves to offset this bad debt and to make sure that there's always more collateral backing the stablecoins issued.

In the case where the protocol accrues too much bad debt, there is a settlement mechanism that can remove a collateral asset from the protocol, pay back owners of over-collateralized vaults and settle remaining owners of stablecoins at oracle value.

## Revenue Distribution

All the revenue and bad debt from this module are gathered in `Treasury` contracts. The protocol relies on keepers to fetch revenue from all `VaultManager` contracts.

Interestingly, stablecoins are minted when revenue is accrued. The reason for this is that if there is only one borrower borrowing 100 stablecoins at a 1% interest rate, then after a year this borrower needs to repay 101 stablecoins. But if only 100 stablecoins have been issued, there's no way for this borrower to repay its debt: as such when accruing revenue from `VaultManager` contracts, the protocol mints stablecoins. The logic is that these stablecoins should in some way end up in the market for vault owners to buy them and repay their debt.
