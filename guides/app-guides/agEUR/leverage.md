---
description: How to get leverage on crypto with Angle Borrowing module
---

# ⚖️ Get leverage on crypto through stablecoin debt

The [Angle Borrowing module](/borrowing-module/README.md) lets you borrow Angle from crypto collateral **on different chains** and use it to **leverage your exposure to your collateral**.

When using the leverage section of the app, you can, in a single transaction, borrow stablecoins like agEUR and directly swap them into more of the token originally used as collateral to leverage your exposition.

## Add collateral & get leverage

Here are the steps to leverage your collateral exposure:

1. Go to the `Leverage` section of the [app](https://app.angle.money/borrow) and choose the network on which you want to open your vault.
2. Select the type of vault to create, defined by the collateral and stablecoin token. Note that depending on the collateral/stablecoin pair you choose, your price exposure may completely vary.
3. Select the token and amount you want to deposit in the first input. If the token is different from the vault collateral, the former will automatically be swapped to the latter.
4. Enter the amount of additional exposure of collateral you want in the second input.
5. Click on the bottom right button to send your transaction. You can also `simulate` the transaction before confirming it.
   _If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction._

In this example, a user deposits 20 FRAX in an LUSD vault, and ask for 40 LUSD of additional exposure. In the background, the 20 FRAX are swapped to LUSD and enough agEUR to buy 40 LUSD tokens are borrowed from the vault and swapped to LUSD. The user USD exposure goes from 20 to 60.

After the operation, this vault would have 60 LUSD as collateral and ~38.23 agEUR of debt.

![Leverage with LUSD](/.gitbook/assets/leverage-lusd.png)

## Leverage your yield

Some vaults accept yield-bearing tokens as collateral. The borrowing power of these vaults can be used to borrow Angle stablecoins and swap it for more of the yield-bearing tokens, effectively multiplying your returns.

For example, if the borrowing cost is 0.5% and a collateral with an APR of 3% is used, a 4x leverage can **increase the effective returns** up to 10.5%, assuming collateral price remains constant.

To open a vault with yield-bearing assets as collateral, you can follow the same steps described above after selecting a vault with a return displayed in a blue tag.

![Leveraging yield](/.gitbook/assets/leverage-yield.png)

## Repay your debt or close your vault

Once a vault is created, the process to close your vault, to repay your debt, or simply to claim your accrued token rewards is exactly the same as what is described in [this guide](./borrow.md).
