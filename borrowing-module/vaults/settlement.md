---
description: Settlement - Stopping all operations for a specific vault type
---

# 🗡 Vaults Settlement

As in the Core module, the Borrowing module has a **settlement mechanism** to protect the protocol against potential attacks, and quickly stop unsustainable operations.

It has been designed as a last resort to protect agTokens holders, and make sure they can redeem their stablecoins at a 1:1 rate against collateral even under an emergency situation. This reinforce the insurance that agTokens are **always backed by collateral**.

### Mechanism

The vault settlement should be used only in extreme cases, for example when vaults from a specific [`VaultManager`](../glossary.md) contract start to be under-collateralized, or liquidator stop liquidating unhealthy positions.

In that case, the settlement process allows Governance to stop the concerned vaults, and close all the positions by repaying the debts and paying back users that were over-collateralized. A settlement process could also be activated for all the vaults backing a specific stablecoin, or for the Borrowing module as a whole for example. This would actually stop the issuance of this stablecoin (or all stablecoins) through the Borrowing module.

### Settlement process

When a settlement process is activated, the Borrowing module usual functionalities of the concerned vaults stop to let the process unfold. At the beginning, an oracle rate for the collaterals used is recorded for the rest of the settlement.

The core of the settlement process works in two steps:

1. First, it allows owners of over-collateralized vaults to recover their full collateral after repaying all their debt.
2. Then, it lets owners of the concerned stablecoin redeem collateral at oracle value.

More precisely, after step 1:

* If the value of the collateral left in the `VaultManager` is less than the amount of stablecoins that have been issued: then stablecoins can be used to redeem a pro rata portion of the leftover collateral. For instance, if the leftover debt is 100 and there is only 90 of collateral left, then with 1 of stablecoin users can redeem 9/10 of collateral
* If the value of the leftover collateral is greater than the debt: then users can only redeem the corresponding value of collateral with their stablecoins, and leftover collateral will be usable by governance. Given that the module is made to be well over-collateralized, we expect that settlement situations, if they are triggered, will lead to this second scenario.

The stablecoins transferred to this contract to redeem collateral are later burned to erase the debts.

### Reinforcing trust in the protocol

The settlement processes of Angle Borrowing and Core modules are here to help ensure the redeemability of agTokens under all conditions.
