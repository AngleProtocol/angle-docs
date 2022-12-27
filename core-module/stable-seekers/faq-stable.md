---
description: Common questions about getting and exchanging the Protocol's stablecoins
---

# FAQ - Stable Seekers and Holders

## Could I use the Angle Core module as a decentralized exchange?

Angle Core module can be used as a decentralized exchange where there is no slippage for swapping.

For example, if Angle's agEUR is backed by wETH and USDC, a user wishing to swap wETH against wBTC with no slippage can choose to come to Angle, swap wETH against agEUR, and then use these agEUR to redeem wBTC.

## What happens if I want a collateral that is not present in sufficient quantity against my agEUR?

Angle Core module leaves the choice to its users as for the collateral type they can get when burning their stablecoins.

It is however possible that there is an imbalance between the value of the different collateral pools backing a stablecoin. If 100 agEUR are backed by 10 DAI and 150 USDC, the transactions of users asking DAI against 100 agEUR will fail because there are not enough DAI in reserves to reimburse the users.

In this case, users will have to burn agEUR in exchange for USDC.

## Do I still own the collateral I bring to the Core module to mint agEUR?

No. Angle Core module works with swaps from a user perspective, meaning that the collateral brought to get stablecoins no longer belongs to the person who brought it: it belongs to the Core module which keeps it in reserves and uses it to back the minted stablecoin.
