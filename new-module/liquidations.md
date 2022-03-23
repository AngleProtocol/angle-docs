---
description: Liquidations in Angle _New_ Module
---

# Liquidations

To make sure collateral is always backing agTokens issued, Angle Vaults can get liquidated if the value of the collateral deposited gets too low compared to the value of the agTokens borrowed. This is determined by a parameter called the [collateral factor](/new-module/glossary.md). 

**TLDR**
* Vaults with a health factor below one risk getting liquidated
* Liquidated vaults can lose part or all their collateral
* Angle has special liquidations features such as a variable liquidation amount, a dynamic discount for liquidators, and a discount booster for veANGLE holders

## How liquidations work

### Health Factor
Each vault has its own collateral ratio. Together with the collateral factor, they are used to compute the health factor of an open vault. For example:

$$
\texttt{HF = CR * CF} \\
\texttt{HF} = 160/100 * 2/3 = 1.07
$$

If this health factor goes below 1, it means that the value of the collateral backing the stablecoin is too low compared to what was defined by the protocol and the position can get liquidated. 

### What happens to a position getting liquidated

Liquidating a position means repaying part or the entirety of the vault's debt (agTokens) against the collateral it holds (ETH or any other collateral token), usually at a discount.

After getting liquidated, a vault will either be closed, or both the amount of debt and collateral will have been reduced in a way that puts the Health Factor of the vault back above a heatlhy target. 

This means that users will either lose their collateral completely, but won't have anything to pay back anything to the protocol, or lose part of their collateral and still have some debt towards the protocol. 

## Details about liquidations within Angle 

### Liquidation Surcharge (fee)
When a vault gets fully or partially liquidated, a liquidation surcharge is applied to what is being paid by the liquidator and captured by the protocol. In practice, this means that if the liquidation surcharge is 2%, when a liquidator repays 100 of the debt of a vault only 98 will be repaid and 2 will go to the protocol. 

This is a way for the protocol to grow reserves especially from collaterals that often get liquidated. 

### Variable Liquidations Amount

In Angle Borrow module, **the amount of debt to repay during a liquidation is dynamic** and computed such that after the liquidation, the liquidated vault ends up in a level of “health” defined by a target parameter: the [target health factor](/new-module/glossary.md). In some conditions, liquidators may be able to liquidate all of a position’s available debt or collateral to avoid leaving an amount of debt that is too small for the owner to be incentivized to come to repay. 

In most cases though, liquidated vaults may get less than 50% of their position liquidated: this system is designed to be far more borrower friendly than existing alternatives.

More details in section 4.3 of the [Angle Borrow Module Whitepaper](/whitepaper.md#angle-borrowing-module).

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

## Example

Now that we are aware of the different aspects of liquidations in the Angle Borrow module, let's look at an example. 

Let's say that we have the following parameter: 
- `CF` = 2/3, as the collateral factor
- `c` = 200, as the collateral value expressed in stablecoin
- `d` = 150, as the debt value or stablecoins borrowed
- `s` = 2%, as the liquidation surcharge
- `e` = 10%, as the liquidation discount
- `x`, as the amount of stablecoins / debt repaid by the liquidator

At this point, the vault has a Health Factor of:
$$
HF = \frac{c\times CF}{d}= \frac{200\times 2/3}{150} = 0.89
$$

As HF < 1, the vault should get liquidated. After being liquidated, the new Health Factor of a vault becomes:
$$
HF_{post}(x) = \frac{c_{post}\times CF }{d_{post}} = \frac{(c - \frac{x}{1-e})\times CF }{d-x(1-s)}
$$

Let's say that the Target Health Factor is such that the amount to repay is $x = 100$. We can decompose each component of the vault, and we get: 

$$
c_{post} = 200 - \frac{100}{1-0.90} ≈ 200 - 111 ≈ 89
$$
$$
d_{post} = 150 - 100(1-0.02) = 150 - 98 = 52
$$

Such that the new health factor after the liquidation becomes: 
$$
HF_{post}(x) = \frac{c_{post}\times CF }{d_{post}} ≈ \frac{89\times 2/3 }{52} ≈ 1.14
$$

### In practice

In practice, there is a target health factor and the amount repaid by liquidators `x` is determined from the above equation such that 

$$
HF_{post}(x) = \texttt{target health factor}
$$

### No capital requirements

When liquidating a position, the liquidator can initiate the transaction without capital, and receive the collateral to then swap it against the required amount of stablecoin to pay back the debt by the end of the transaction.  