---
description: A list of words and terms relating to the Angle New Module
---

# 📚 Glossary - New Module

Here, you will find a list of the terms and expressions that are used in this module.

If you still have some questions, do not hesitate to reach out on the [Angle Discord](https://discord.gg/67WSSZqBG6) 🕹️.

| Term | Description |
|  |  |
| Collateral Ratio (CR) | The collateral ratio is a ratio that determines the value of the tokens deposited as collateral compared to the value of the outstanding debt. It's expressed as $\texttt{CR = collateral value / debt value}$, 150% for example. It can also be called Collateral Factor, expressed as $1/CR$, 2/3 for example                                                   |
| Minimum Collateral Ratio (MCR) | The Minimum level of collateral ratio accepted. If the CR of the vault goes below this value, the vault can get liquidated.  Similarly, $MCF = 1/ MCR$ |
| Health Factor | The Health Factor is another term to describe the situation of a position. $\texttt{HF = collateral value * MCR / debt value}$   |
| Liquidation | A liquidation happens when a vault collateral ratio goes below the MCR. In this case, the users that opened the vault will keep their stablecoins but will lose part or all of their collateral. More in the [liquidation](/new-module/liquidations.md) section. |
| Stability Fee | An interest rate paid by agEUR minters for their loans. It is controlled by governance.|
| Dust  | Dust is the minimum amount of agEUR that can be borrowed from a single vault. This is required to avoid having too small and unealthy debt positions sticking around.                                                                                            |
| Flash Loan | Flash Loans are a type of transaction in which agEUR are borrowed and repaid within the same transaction, such that it doesn't require any collateral.  More info in the [flash loan](/new-module/flash-loan.md) section.          |


