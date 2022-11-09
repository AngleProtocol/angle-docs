---
description: How to get leverage on crypto with Angle Borrowing module
---

# Get leverage on crypto through agEUR debt

The [Angle Borrowing module](/borrowing-module/README.md) lets you borrow agEUR from crypto collateral **on different chains** and use it to **leverage your exposure to your collateral**.

When borrowing agEUR, you can directly swap the borrowed agEUR into more of the token originally used as collateral to leverage your exposition in the same transaction. Follow this guide to learn how.

## Add collateral & get leverage

Here are the steps to leverage your collateral exposure:

1. Select the collateral and amount you want to deposit.
2. Select the additionnal exposure you want. Your leverage will be indicated on the bar below the `Additional Exposure` input.
3. Confirm the transaction.

In this example, a user deposits 1,000 OP tokens, and ask for 1,000 OP of additional exposure. What happens in the background is that enough agEUR to buy 1,000 OP tokens are borrowed from the vault and swapped to OP, increasing the user exposure from 1,000 to 2,000 OP.

After the operation, this vault has 2,000 OP tokens as collateral and ~881 agEUR of debt.

![Leverage with OP](/.gitbook/assets/leverage-OP.png)

## Repay your debt or close your vault.

Once a vault is created, you can repay part of your debt up to the dust amount, or close it completely. You can also withdraw some collateral up to the minimum LTV.

When repaying your debt, you have two options: use your vault collateral, or use your debt token. If you choose to repay your debt with your vault collateral, the tokens will be swapped to debt tokens on your behalf and used to repay your debt.

Here for example, wETH will be swapped into 1 agEUR to repay part of the vault's debt. 0.01 wETH of the vault's collateral will also be withdrawn.

![Repay and withdraw](/.gitbook/assets/repay-with-collat.png)

Here are the steps to Repay debt, withdraw collateral, or close your vault:

1. Go to the `Leverage` section of the [Angle App](https://app.angle.money/#/leverage)
2. Click on the `Repay` button on your vault.
3. Tick the box above the inputs to repay all your debt and close your vault. You will get all the remaining collateral.
4. Enter the amount of collateral you want to remove
5. Enter the amount of stablecoins debt you want to repay in the second input.
6. Choose whether to use your collateral or your agEUR wallet balance to repay your debt.
7. Click on `Send` to confirm the transaction.

## Monitoring your positions

After opening vaults, you can monitor their health on the main Leverage page.

![Vaults list](../../../.gitbook/assets/vaults-list.png)
