---
description: How to borrow agEUR from the Angle App
---

# 🏦 Borrow

The [Angle Borrowing module](/borrowing-module/README.md) lets you borrow agEUR from crypto collateral **on different chains**.

Essentially, you open a vault with a specific token as collateral, and can get a stablecoin loan in exchange. If the value of the vault collateral goes below a certain amount compared to the value of your loan, you can get [liquidated](/borrowing-module/vaults/liquidations.md).

When opening a vault, you can deposit any token and it will be automatically swapped into the selected vault collateral. When borrowing agEUR, you can directly swap the borrowed agEUR into more of the token originally used as collateral to get leverage. All of this is done in the same transaction.

Learn more about the mechanism [here](/borrowing-module/vaults/README.md#leveraging-collateral-exposure).

In this guide, we will look at how to **borrow agEUR** from a collateral deposit.

## Add Collateral & Borrow agEUR

To borrow agEUR, you need to **deposit** collateral tokens into a **vault**. Different vaults accept different tokens which have their specific loan-to-value (LTV). This means that you are able to borrow up to a certain amount of stablecoins from the amount deposited.

To borrow agEUR, you need to open a vault with a specific token as collateral. However, you can deposit any token you want to the protocol. It will be swapped to the collateral token of the selected vault. Each collateral has its specific loan-to-value (LTV). This means that you are able to borrow up to a certain amount of stablecoins from the amount deposited.

For example, wETH LTV at 84% on Optimism means that if you deposit 1,000 € worth of wETH on Optimism, you can borrow up to 840 agEUR from this vault.

You can borrow agEUR in the same transaction that you deposit collateral to your vault. Once a vault is created, it is possible to deposit more collateral without borrowing more stablecoins, and the other way around.

Here are the steps to follow to deposit collateral and borrow agTokens:

1. Go to the `Borrow` section of the [app](https://app.angle.money/#/borrow) and choose the network on which you want to open your vault
2. Select the type of vault to create, defined by the collateral and stablecoin token
3. Select the token and amount you want to deposit in the first input. If the token is different from the vault collateral, the former will be swapped to the latter.
4. Enter the amount of stablecoins you want to borrow in the second input.
5. Click on the bottom right button to `Approve` and `Send` your transaction.
6. (optional) If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction.

In the below example, the 200 DAI will be swapped to wETH to be deposited as collateral in the vault, and 50 agEUR will be borrowed.

![Add/Borrow agEUR](/.gitbook/assets/add-borrow2.png)

{% hint style="info" %}
A summary of the changes on your vault and wallet will be displayed on the right. You can access all the steps of the transaction by clicking on the `Transaction Details` dropdown.
{% endhint %}

## Using a yield-bearing asset as collateral to borrow agEUR

Some vaults have collateral tokens that earn a return for holder, like staked Curve LP tokens.

Using these allow you to get paid while borrowing agEUR. Opening a vault with yield-bearing assets is similar, but one feature becomes much more valuable: the ability to deposit any token.

In the case of yield-bearing asset, the tokens sent to the protocol will be swapped to the underlyings of the yield-bearing asset, and deposited in the platform they earn yield from. For example, in the case of Curve LP tokens, the underlyings will be deposited on Curve, the LP tokens obtained will be staked on Convex, and this will be used as collateral for a vault.

{% hint style="info" %}
To check out all these steps, click on the `Transaction Details` on the right side of the screen.
{% endhint %}

The following example will deposit 20 FRAX in the Curve FRAX/USDC pool, stake the LP tokens on Stake DAO, deposit them as collateral in the vault and borrow 10 agEUR from it.

![Add/Borrow agEUR](/.gitbook/assets/borrow-lp.png)

## Repay your debt or close your vault

Once a vault is created, you can repay part of your debt or close it completely. You can also withdraw some collateral up to the minimum LTV.

When repaying your debt, you can either use your vault collateral balance, your wallet balance, or a mix of both. If you choose to repay your debt with your vault collateral, the tokens will be swapped to debt tokens on your behalf and used to repay your debt.

Here are the steps to Repay debt, withdraw collateral, or close your vault:

1. Go to the `Borrow` section of the [app](https://app.angle.money/#/borrow)
2. Click on the `Repay` button on your vault.
3. Tick the box above the inputs if you want to repay all your debt and close your vault. You will get all the remaining collateral.
4. Enter the amount of collateral you want to remove and the token you want to receive in your wallet.
5. Enter the amount collateral you want to use to repay your debt in the bottom left input.
6. Enter the amount of debt token from your wallet balance you want to use to repay your debt.
7. Click on `Send` to confirm the transaction.

For example, in the following screenshot, 0.01 wETH will be swapped into ~12.45 agEUR to repay part of the vault's debt, and 10 agEUR from the wallet will be used to repay some of the remaining agEUR debt.

![Repay and withdraw](/.gitbook/assets/repay2.png)

{% hint style="info" %}
A summary of the changes on your vault and wallet will be displayed on the right. You can access all the steps of the transaction by clicking on the `Transaction Details` dropdown.
{% endhint %}

## Monitoring your positions

After opening vaults, you can monitor their health on the main Borrow page.

![Vaults list](../../../.gitbook/assets/vaults-list.png)
