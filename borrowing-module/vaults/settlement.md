---
description: Settlement - Stopping all operations for a specific vault type
---

# Vault Settlement

As in the Core module, the Borrowing module has a settlement mechanism to stop unsustainable vault types and pay back users. Its goal is to ensure that agTokens issued through this module are **always backed by collateral**. 

## Idea
The vault settlement should be used only in extreme cases, for example when vaults from a specific [`VaultManager`](/borrowing-module/glossary.md) contract start to be under-collateralized and liquidator stop liquidating unhealthy positions. 

In that case, the settlement process allows to stop the vaults of this `VaultManager`, and close all the positions by repaying all debts and paying back users that were over-collateralized. A settlement process of the whole Angle Borrowing module could be activated by initiating a settlement for all its `VaultManager` contracts.

## Settlement process

The settlement process works in two steps: 
1. First, it allows owners of over-collateralized vaults to recover their full collateral after repaying all their debt. 
2. Then, it lets owners of the concerned stablecoin redeem collateral at oracle value.

More precisely, after step 1:

- If the value of the collateral left in the `VaultManager` is less than the amount of stablecoins that have been issued: then stablecoins can be used to redeem a pro rata portion of the leftover collateral. For instance, if the leftover debt is 100 and there is only 90 of collateral left, then with 1 of stablecoin users can redeem 9/10 of collateral
- If the value of the leftover collateral is greater than the debt: then users can only redeem the corresponding value of collateral with their stablecoins, and leftover collateral will be usable by governance. Given that the module is made to be well over-collateralized, we expect that settlement situations, if they are triggered, will lead to this second scenario.

The stablecoins transferred to this contract to redeem collateral are later burned to erase the debts. 