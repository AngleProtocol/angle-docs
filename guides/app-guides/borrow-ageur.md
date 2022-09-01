---
description: How to borrow agEUR from the Angle App and use this to get leverage on your crypto
---

# Borrowing and Getting Leverage with agEUR

The [Angle Borrowing module](/borrowing-module/README.md) lets you borrow agEUR or get leverage on your crypto **on different chains**.

Essentially, you can deposit your crypto into what is called a vault, to get a stablecoins loan in exchange. If the value of the crypto you deposited goes below a certain amount compared to the value of your loan, you can get [liquidated](/borrowing-module/vaults/liquidations.md).

When borrowing agEUR, you can in the same transaction swap the borrowed agEUR into the token originally used as collateral and deposit the obtained tokens back into the vault. Learn more about the mechanism [here](/borrowing-module/vaults/README.md#leveraging-collateral-exposure): this essentially allows you to get leverage on any supported token.
At the difference of simple borrowing, leveraging increases your exposure to the collateral token and can make your overall position riskier.

All of these actions can be done directly from the [Borrow / Leverage page](https://app.angle.money/#/borrow) of the Angle app.

![Vaults lists](../../.gitbook/assets/vaults-list2.png)

## Add Collateral / Borrow agEUR

To borrow agEUR, you need to **deposit** collateral tokens into a **vault**. Different vaults accept different tokens which have their specific loan-to-value (LTV). This means that you are able to borrow up to a certain amount of stablecoins from the amount deposited.

For example, wETH LTV at 84% on Optimism means that if you deposit 1,000 € worth of wETH on Optimism, you can borrow up to 840 agEUR from this vault.

You can borrow agEUR in the same transaction that you deposit collateral to your vault. Once a vault is created, it is possible to deposit more collateral without borrowing more stablecoins.

Here are the steps to follow to deposit collateral and borrow agTokens:

1. Go to the `Borrow / Leverage` section of the [Angle App](https://app.angle.money/#/borrow)
2. Select the type of vault to create, defined by the collateral and stablecoin tokens
3. Select the `Add/Borrow` action
4. Enter the amount of collateral you want to deposit in the first input.
5. Enter the amount of stablecoins you want to borrow in the second input.
   A summary of the changes on your vault and wallet will be displayed on the right.
6. Add the actions to go to the next step. You will find a summary of your transaction.
7. Click on `Approve` to approve the tokens to be used by the protocol through a permit signature or an approval transaction.
8. (optional) If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction.
9. Finally, click on `Send` to send your transaction.

![Add/borrow agEUR](../../.gitbook/assets/add-borrow.png)
![Confirm tx borrow agEUR](../../.gitbook/assets/confirm-tx-borrow.png)

{% hint style="info" %}
Depending on the chain on which you are, there may be a minimum amount to borrow of agEUR. On Ethereum mainnet, this amount is 10,000 agEUR for instance. This is to limit the risk of having small bad debts that are not repaid by users nor liquidators.
{% endhint %}

## Leverage

Here are the steps to get leverage with Angle:

1. Go to the `Borrow / Leverage` section of the Angle App.
2. Select the type of vault to create, defined by the collateral and stablecoin tokens
3. Choose the `Leverage` action.
4. Input the amount of collateral that you want to deposit.
5. Input the amount of additional exposure you want on the collateral token, or choose your leverage from the slider.
6. Make sure to double check the summary on the screen and click on `Add step` to move on to the final section.
7. Approve your tokens to be used by the protocol through a permit signature or an approval transaction.
8. (optional) If your transaction requires a wrapping, you'll need to sign a permit for the router contract to interact with your vault and perform the desired transaction.
9. Finally, send the transaction to be executed.

When leveraging with Angle, the protocol borrows stablecoins from your vault to swap them to the collateral token you want to leverage on. It uses 1inch to swap tokens to get the best prices possible.

Depending on the size of the swap and available liquidity on-chain, there might be a slippage. In this case, you will find a slippage input to specify the maximum amount of price slippage you're ready to tolerate during your swap.

The value you input as slippage will change the amount of stablecoins borrowed to make sure you get the output amount you desire.

{% hint style="info" %}
If slippage is too low, it's possible that the swap won't give the required amount and that the transaction reverts. In this case, you will have to increase the slippage parameter to send the transaction.
{% endhint %}

![Leverage & slippage](../../.gitbook/assets/leverage-slippage.png)

## Repay Debt / Remove Collateral

Once a vault is created, you can repay part of your debt up to the dust amount. You can also withdraw some collateral up to the minimum LTV.

{% hint style="info" %}
If you want to repay all your debt and withdraw all your collateral, you can directly [close your vault](#close-vault).
{% endhint %}

When repaying your debt, you have two options: use your vault collateral, or use your debt token. If you choose to repay your debt with your vault collateral, the tokens will be swapped to debt tokens on your behalf and used to repay your debt.

For example here, the user is using his collateral (wETH) to repay 1,000 agEUR of debt, and removing 0.2 wETH from the vault.

![Repay and withdraw](../../.gitbook/assets/repay-w-collat-withdraw.png)

Here are the steps to Repay debt or Remove collateral:

1. Go to the `Borrow / Leverage` section of the [Angle App](https://app.angle.money/#/borrow)
2. Select the vault you want to modify (make sure you select the correct ID)
3. Select the `Repay/Remove` action
4. Enter the amount of collateral you want to remove in the first input.
5. Enter the amount of stablecoins debt you want to repay in the second input. A summary of the changes on your vault and wallet will be displayed on the right.
6. Add the actions to go to the next step. You can then click on `Send` to send your transaction.

## Close Vault

If you want to repay all your debt and remove all your collateral, you can directly use the `Close` feature. This repays all your debt and sends you the remaining collateral.

With Angle, you don't need to bring debt token to repay your debt. By leaving the `Use collateral only` option checked, the protocol will swap your collateral tokens to agEUR to repay your debt and send you the remaining funds.

If you have agEUR in your wallet and prefer to use those, you can check the `Use agEUR` option. In this case, the protocol will use all the agEUR in your wallet to repay your debt, and some of your collateral if needed. Then, you will receive the remaining funds back in your wallet.

To close your vault, you only need to verify the information and click on `Add step` to go to the next section, and validate the transaction.

![Close vault](../../.gitbook/assets/close-vault.png)

{% hint style="info" %}
It might be that you want to repay your debt or close your vault by using agEUR, but don't have enough in your wallet. In this case, if you select the `Use agEUR` option, the contract will use all the agEUR in you wallet and the remaining debt will be repaid by swapping the required amount of collateral into agEUR. You will the leftover collateral amount.
{% endhint %}

When using collateral to close a vault (or simply to repay a debt), the protocol swaps collateral tokens into debt tokens (ETH to agEUR for example). Just like for leverage transactions, it uses 1Inch, a DEX aggregator, to get the best prices possible.

Depending on the size of the swap and on the liquidity available on-chain, there can be slippage. In this case, you will have a slippage input to specify the maximum amount of price slippage you want to tolerate during your swap.

This applies when [repaying debt](#repay-debt--remove-collateral), [closing vault](#close-vault) or getting leverage.

## Take Debt from Another Vault

Another feature available with the Angle Borrowing module is to transfer the debt from one vault to another.

For example, imagine your vault #1 is close to liquidation, and your vault #2 is over-collateralized. In this case, you can simply transfer your debt from vault #1 to #2 and balance the situation of the two vaults.

To take debt from a vault:

1. Go to the `Borrow / Leverage` section of the [Angle App](https://app.angle.money/#/borrow)
2. Select the vault you want to add debt to
3. Select the `Take Debt from` action
4. Select the vault you want to take debt from
5. Input the amount of debt you want to take from this vault into the originally selected one.
6. Check all the information about the change of the concerned vaults, add the step and confirm the transaction.

{% hint style="info" %}
Transferring debt to a vault increases its liquidation risk.
{% endhint %}

![Take debt from](../../.gitbook/assets/take-debt-from.png)

## Monitoring your positions

Borrowing agEUR incurs some liquidation risks. In the case of vaults which were opened using leverage transactions, this risk is even more acute.

The `Borrow / Leverage` page of the Angle App lets you keep an eye on your Health Factor and LTV to make sure you are safe from liquidation, and entices you to take action in case of.
