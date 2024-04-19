---
description: How to borrow Angle stablecoins from the Angle App
---

# 🏦 Borrow

The [Angle Borrowing module](/borrowing-module/README.md) lets you borrow Angle stablecoins like EURA from crypto collateral **on different chains**.

Essentially, you open a vault with a specific token as collateral, and can get a stablecoin loan in exchange. If the value of the vault collateral goes below a certain amount compared to the value of your loan, you can get [liquidated](/borrowing-module/vaults/liquidations.md).

When opening a vault, you can deposit any token and it will be automatically swapped into the selected vault collateral. When borrowing a stablecoin, you can directly swap the borrowed stablecoin into more of the token originally used as collateral to get leverage. All of this is done in the same transaction.

Learn more about the mechanisms [here](/borrowing-module/vaults/README.md#leveraging-collateral-exposure).

{% hint style="info" %}
The borrowing page functionalities are the same whether you're coming it to it for EURA or another stablecoin. In this guide, we specifically look at EURA borrowing use cases, but anything that is true for EURA holds for others.
{% endhint %}

## Add Collateral & Borrow

To borrow an Angle stablecoin, you need to **deposit** collateral tokens into a **vault**. Different vaults accept different tokens which have their specific loan-to-value (LTV). This means that you are able to borrow up to a certain amount of stablecoins from the amount deposited.

For example, wETH LTV at 84% on Optimism for EURA means that if you deposit 1,000 € worth of wETH on Optimism, you can borrow up to 840 EURA from this vault.

You can deposit any token you want in the app, and it will be swapped to the collateral token of the selected vault. You can also borrow a stablecoin in the same transaction that you deposit collateral to your vault. Once a vault is created, it is possible to deposit more collateral without borrowing more stablecoins, and the other way around.

Here are the steps to follow to deposit collateral and borrow stablecoins:

1. Go to the `Borrow` section of the [app](https://app.angle.money/borrow) and choose the network on which you want to open your vault
2. Select the type of vault to create, defined by the collateral and stablecoin token and click on borrow
3. Then, select the token and amount you want to deposit in the first input. If the token is different from the vault collateral, the former will automatically be swapped to the latter.
4. Enter the amount of stablecoins you want to borrow in the second input.
5. Click on the bottom right button to send your transaction. You can also `simulate` the transaction before confirming it.
   _If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction._

In the below example, 200 DAI are swapped to ~0.15 wETH to be deposited as collateral in the vault, and 50 EURA are borrowed.

![Add/Borrow EURA](/.gitbook/assets/add-borrow2.png)

{% hint style="info" %}
A summary of the changes on your vault and wallet is displayed on the right. You can access all the steps of the transaction by clicking on the `Transaction Details` dropdown.
{% endhint %}

Note that once a vault is opened, you can monitor its health and status from the main Borrow page. From there, you can also choose to add collateral or borrow more from it. To do this just click on the `Add / Borrow` button of your opened vault.

![Vaults list](../../../.gitbook/assets/vaults-list.png)

## Leverage

When using the borrow section of the app, you can, in a single transaction, borrow stablecoins like EURA and directly swap them into more of the token originally used as collateral to leverage your exposition.

To do this, when selecting the type of vault to create, click on leverage. Then:

1. Select the token and amount you want to deposit in the first input. If the token is different from the vault collateral, the former will automatically be swapped to the latter.
2. Enter the amount of additional exposure of collateral you want in the second input.
3. Click on the bottom right button to send your transaction. You can also `simulate` the transaction before confirming it.
   _If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction._

In this example, a user deposits 20 FRAX in an LUSD vault, and ask for 40 LUSD of additional exposure. In the background, the 20 FRAX are swapped to LUSD and enough EURA to buy 40 LUSD tokens are borrowed from the vault and swapped to LUSD. The user USD exposure goes from 20 to 60.

After the operation, this vault would have 60 LUSD as collateral and ~38.23 EURA of debt.

![Leverage with LUSD](/.gitbook/assets/leverage-lusd.png)

## Using a yield-bearing asset as collateral to borrow

Some vaults have collateral tokens that earn a return for holders, like staked Curve LP tokens.

Using these allow you to get paid while borrowing a stablecoin. Opening a vault with yield-bearing assets is similar, but one feature becomes much more valuable: the ability to deposit any token.

In the case of yield-bearing assets, the tokens sent are swapped to the underlyings of the yield-bearing asset, and deposited in the platform they earn yield from. For example, in the case of Curve LP tokens, the underlyings are deposited on Curve, the LP tokens obtained staked on Convex, and used as collateral in a vault.

All external rewards accumulated by the vault's staked collateral can be [claimed](#claim-your-rewards) from the Angle app in one transaction, such that there is **no opportunity cost to use Angle** to stake tokens and borrow stablecoins from it.

{% hint style="info" %}
To check out all these steps, click on the `Transaction Details` on the right side of the screen.
{% endhint %}

In the following example, 20 FRAX are deposited in the Curve FRAXUSDC pool, the LP tokens are staked on Stake DAO, and deposited as collateral in the vault. 10 EURA are also borrowed from the vault.

This feature can be interesting when using the leverage functionality of the app. By getting leverage on yield bearing tokens, you can effectively enable multiply your returns.

For example, if the borrowing cost is 0.5% and a collateral with an APR of 3% is used, a 4x leverage can **increase the effective returns** up to 10.5%, assuming collateral price remains constant.

![Add/Borrow EURA](/.gitbook/assets/borrow-lp.png)

## Repay your debt or close your vault

Once a vault is created, you can repay part of your debt or close it completely. You can also withdraw some collateral up to the minimum LTV.

When repaying your debt, you can either use your vault collateral balance, your wallet balance, or a mix of both. If you choose to repay your debt with your vault collateral, the tokens are swapped to debt tokens on your behalf and used to repay your debt.

Here are the steps to Repay debt, withdraw collateral, or close your vault:

1. Go to the `Borrow` section of the [app](https://app.angle.money/borrow)
2. Click on the `Remove / Repay` button on your vault.
3. Enter the amount of collateral you want to remove and the token you want to receive in your wallet.
4. Enter the amount of debt token from your wallet balance you want to use to repay your debt.
5. Click on the bottom right button to send your transaction. You can also `simulate` the transaction before confirming it.

![Repay and withdraw](/.gitbook/assets/repay2.png)

{% hint style="info" %}
A summary of the changes on your vault and wallet is displayed on the right. You can access all the steps of the transaction by clicking on the `Transaction Details` dropdown.
{% endhint %}

## Monitoring your positions

You can monitor your vaults' health from the main Borrow page.

![Vaults list](../../../.gitbook/assets/vaults-list.png)

Two of the important quantities to monitor for open vaults are:

- their loan-to-value (LTV): value of vaults' debt compared to that of their collateral.
- their health factor (HF): indicator for the health of vaults. Below 1, vaults can get liquidated.

These are computed as follows:

$$
\texttt{LTV} = \frac{\texttt{debt}}{\texttt{collateral}}
$$

$$
\texttt{HF} = \frac{1}{\texttt{LTV}} \times {\texttt{max. LTV}}
$$

## Claim your rewards

Staked tokens accumulating external rewards can be used as collateral in an Angle vault. You can **claim all your vaults collateral rewards** directly **from the Angle App** in just one transaction. To do so, click on the `Claim` button at the right of the highlighted card below.

![CLaim vaults rewards](../../../.gitbook/assets/claim-vault-rewards.png)
