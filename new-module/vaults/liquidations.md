---
description: Liquidations in Angle Borrowing Module
---

# 🎳 Liquidations

To make sure collateral is always backing agTokens issued, Angle Vaults can get liquidated if the value of the collateral deposited gets too low compared to the value of the agTokens borrowed. This is determined by two similar parameters, the [collateral factor](glossary.md) or the [health factor](glossary.md).

As we will see in the [Variable liquidations amount](liquidations.md#variable-liquidations-amount), liquidations in Angle Borrowing module have been designed to be as much borrower friendly as possble.

### TL;DR

* Vaults with a health factor below one risk getting liquidated
* Liquidated vaults can lose part or all their collateral
* Angle has special liquidations features such as a variable liquidation amount, a dynamic discount for liquidators, and a discount booster for veANGLE holders

## How liquidations work

### Health Factor

Each vault has its own collateral ratio. Together with the collateral factor, they are used to compute the health factor of an open vault. For example:

$$
\texttt{HF = CR * CF} \\ \texttt{HF} = 160/100 * 2/3 = 1.07
$$

If this health factor goes below 1, it means that the value of the collateral backing the stablecoin is too low compared to what was defined by the protocol and the position can get liquidated, like in the example below. 


### What happens to a position getting liquidated

Liquidating a position means repaying part or the entirety of the vault's debt (agTokens) against the collateral it holds (ETH or any other collateral token), usually at a discount.

After getting liquidated, a vault will either be empty, or both the amount of debt and collateral will have been reduced in a way that puts the Health Factor of the vault back above a healthy target.

This means that users will either lose their collateral completely, but won't have anything to pay back anything to the protocol, or lose part of their collateral and still have some debt towards the protocol.

From a liquidator perspective, there is **no capital requirement when liquidating Angle Vaults**. Liquidator receive the collateral of the vault first, before having to repay the collateral. 

![Vault before liquidation](../../.gitbook/assets/Vault%20before%20a%20liquidation.png)

***

## Details about liquidations within Angle

### Liquidation Surcharge (fee)

When a vault gets fully or partially liquidated, a liquidation surcharge is applied to what is being paid by the liquidator and captured by the protocol. In practice, this means that if the liquidation surcharge is 2%, when a liquidator repays 100 of the debt of a vault only 98 will be repaid and 2 will go to the protocol.

This is a way for the protocol to grow reserves especially from collaterals that often get liquidated.

### Variable Liquidations Amount

In Angle Borrow module, **the amount of debt to repay during a liquidation is dynamic** and computed such that after the liquidation, the liquidated vault ends up in a level of “health” defined by a target parameter: the [target health factor](glossary.md). This is determined by the following equation:

$$
HF_{post}(x_{max}) = \frac{(c - \frac{x}{1-e})\times CF }{d-x(1-s)} = \texttt{Target Health Factor}
$$

With:

* `x` as the amount of stablecoin debt to repay
* `c` as the collateral's value in stablecoin
* `d` as the amount of stablecoin debt of the vault
* `e` as the liquidation discount, and
* `s` as the liquidation surcharge

In some conditions, the variables at liquidation are such that $HF_{post}(x_{max})$ is a decreasing function of `x`: the health factor can't be put back at a healthy value. In this case, liquidators are able to liquidate all of a position’s collateral to avoid leaving an amount of debt that is too small to repay. In such situation, it is possible that some of the debt is left unpaid. This will be pooled across contracts and accounted for as bad debt, to make sure no surplus is distributed until this debt is erased.

In practice, full liquidations should be extremely occasional and most vaults should get less than 50% of their position liquidated. This allows them to keep as much collateral in their vault as possible, and makes this system much more borrower friendly than existing alternatives.

### Dynamic Discount

To incentivize liquidations, the protocol lets liquidators buy the available collateral at a **discount**, meaning that they get back more collateral than the amount of stablecoins they brought.

For example, if the liquidation discount is 5%, the liquidator will be able to get 100 of collateral by paying back only 95 of stablecoin debt.

This discount is dynamic, increasing linearly with a decrease of the vault Health Factor to incentivize liquidators more as the vault risk increases. It is defined by:

$$
e(HF) = a(1-HF)
$$

With `a` as the liquidation booster, a factor determining the slope of the function.

### Liquidation Booster

By being stakeholders in the protocol, liquidators holding veANGLE could get a higher discount than others depending on their veANGLE balance.

This would give utility to veANGLE, as well as incentivize veANGLE to liquidate before others, further aligning the interests of veANGLE holders with the protocol.

$$
a = \texttt{baseBoost} \times f(\texttt{veANGLE balance})
$$

Where `f` is a piecewise linear increasing function of the veANGLE balance, capped by a certain amount.

### No capital requirements

As said above, a liquidator can liquidate a vault without bringing in any capital. They will receive the collateral at the beginning of the transaction, so they can swap it against the required amount of stablecoins to pay back the debt by the end of the transaction.

This decreases **a lot** the barriers to entry for potential liquidators and makes it more competitive, which is better for borrowers. 

### Amount of debt to repay

The amount of stablecoins debt `x` to be repaid by the liquidator is determined by the Target Health Factor parameter such that:

$$
HF_{post}(x) = \texttt{target health factor}
$$


## Example

Now that we are aware of the different aspects of liquidations in the Angle Borrow module, let's look at an example.

Let's say that we have the following parameter:

* `CF` = 2/3, as the collateral factor
* `c` = 120, as the collateral value expressed in stablecoin
* `d` = 90, as the debt value or stablecoins borrowed
* `s` = 2%, as the liquidation surcharge
* `e` = 10%, as the liquidation discount
* `x`, as the amount of stablecoins / debt repaid by the liquidator

At this point, the vault has a Health Factor of:

$$
HF = \frac{c\times CF}{d}= \frac{120\times 2/3}{90} = 0.89
$$

As HF < 1, the vault should get liquidated. After being liquidated, the new Health Factor of a vault should be:

$$
HF_{post}(x) = \frac{c_{post}\times CF }{d_{post}} = \frac{(c - \frac{x}{1-e})\times CF }{d-x(1-s)} = \texttt{target health factor}
$$

Let's say that the Target Health Factor is equal to 1.25, such that we get an amount to repay x = 67 after solving the equation. We can decompose each component of the vault, and we get:

$$
c_{post} = 120 - \frac{67}{1-0.10} ≈ 120 - 74,5 ≈ 45,5
$$

$$
d_{post} = 90 - 67(1-0.02) = 90 - 66 = 24
$$

In this example, the liquidator repays 67 of stablecoin, and get back ~74,5 of collateral. 

![Vault before liquidation](../../.gitbook/assets/Vault%20before%20a%20liquidation.png)

![Angle vault after liquidation](../../.gitbook/assets/Vault%20post%20liquidation.png)

## Developers doc

If you want more details about how liquidations work from a Solidity perspective, you can have a look at our [developers documentation](https://developers.angle.money/overview/guides/liquidations-borrowing).
