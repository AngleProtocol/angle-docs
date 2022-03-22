---
description: A list of words and terms relating to the Angle New Module
---

# 📚 Glossary - New Module

Here, you will find a list of the terms and expressions that are used in this module.

If you still have some questions, do not hesitate to reach out on the [Angle Discord](https://discord.gg/67WSSZqBG6) 🕹️.

| Term | Description |
| ---- |-----------  |
| Collateral | Collateral is usually something of value deposited as a guarantee against a loan or a service. In our case, the collateral are the tokens users deposit into Angle Vaults to be able to borrow agEUR. If their debt becomes too big compared to their collateral, it can be taken from them to pay back the debt through a liquidation.         |
| Collateral Ratio (CR) | The collateral ratio is a ratio that determines the value of the tokens deposited as collateral compared to the value of the outstanding debt. It is expressed as $\texttt{CR = collateral value / debt value}$, or 150% for example.  |
| Collateral Factor (CF) | This is a parameter that gives the minimum collateral ratio possible for each vault type. If the collateral ratio of a vault goes below this value, the vault can get liquidated. The collateral factor is expressed as a fraction. For example, if $\texttt{CF} = 2/3$, the minimum collateral ratio possible for a position would be $\texttt{minCR} = \frac{1}{2/3} = 3/2 = 150\%$|
| Health Factor (HF) | The Health Factor is what defines the "health" of a vault. If HF goes below 1, the vault can get liquidated. $\texttt{HF = CR * CF}$. For example, if a vault has a CR of 170% for a CF of 2/3 (minCR of 150%), the Health Factor is at $\texttt{HF} = 1.70 * 2/3 = 1.13$|
| Taregt Health Factor | The target health factor is the target that determines how much of a vault debt needs to be repaid by a liquidator. |
| Liquidation | A liquidation happens when a vault collateral ratio goes below the MCR. In this case, the users that opened the vault will keep their stablecoins but will lose part or all of their collateral. More in the [liquidation](/new-module/liquidations.md) section. |
| Stability Fee | An interest rate paid by agEUR minters for their loans. It is controlled by governance.|
| Dust  | Dust is the minimum amount of agEUR that can be borrowed from a single vault. This is required to avoid having too small and unealthy debt positions sticking around.  |
| Flash Loan | Flash Loans are a type of transaction in which agEUR are borrowed and repaid within the same transaction, such that it doesn't require any collateral.  More info in the [flash loan](/new-module/flash-loan.md) section.          |

