---
description: How to borrow agEUR from the Angle App
---

# Borrowing agEUR 

The [Angle Borrowing module](/borrowing-module/README.md) introduced new features to Angle and agEUR. You can now borrow agEUR or get leverage on your crypto directly from the [Angle App](https://app.angle.money/#/borrow). 

## Add collateral and Borrow agEUR

To borrow agEUR, you need to **deposit** collateral tokens into a **vault**. Different vaults accept different tokens which have their specific loan-to-value (LTV). This means that you will be able to borrow up to a certain amount of stablecoins from the amount deposited.  

For example, wETH LTV is at 84% meaning that if you deposit 1,000 € worth of wETH, you can borrow up to 840 agEUR from this vault. 

You can borrow agEUR in the same transaction that you deposit collateral to your vault. Once a vault is created, it is possible to deposit more collateral without borrowing more stablecoins. 

Here are the steps to follow to deposit collateral and borrow agTokens: 
1. Select the type of vault to create, defined by the collateral and stablecoin tokens
2. Select the `Add/Borrow` action
3. Enter the amount of collateral you want to deposit in the first input. 
4. Enter the amount of stablecoins you want to borrow in the second input. 
A summary of the changes on your vault and wallet will be displayed on the right. 
5.  Add the actions to go to the next step. You will find a summary of your transaction. You can then click on `Send` to send your transaction. 

{% hint style="info" %}
There is a minimum amount to borrow of 10,000 agEUR to limit the risk of having small bad debts that are not repaid by users nor liquidators. 
{% endhint %}


## Repay debt and withdraw collateral

Once a vault is created, you can repay part of your debt up to the dust amount. 

You can also withdraw some collateral up to the minimum LTV. 

If you want to repay all your debt and withdraw all your collateral, you can directly [close your vault](#close-vault).

Here are the step to Repay debt or Remove collateral: 
1. Select your vault you want to modify (make sure you select the correct ID)
2. Select the `Repay/Remove` action
3. Enter the amount of collateral you want to remove in the first input. 
4. Enter the amount of stablecoins debt you want to repay in the second input. 
A summary of the changes on your vault and wallet will be displayed on the right. 
5.  Add the actions to go to the next step. You will find a summary of your transaction. You can then click on `Send` to send your transaction. 

{% hint style="info" %}
There is a minimum amount of debt to keep (dust amount) of 10,000 agEUR to limit the risk of having small bad debts that are not repaid by users nor liquidators. 
{% endhint %}

{% hint style="info" %}
Depending on how much debt you are going to repay, you can only withdraw a limited amount of collateral so that your vault remains below the maximum LTV. 
{% endhint %}

## Close vault

If you want to repay all your debt and remove all your collateral, you can directly use the Close feature. This will repay all your debt and send you the remaining collateral. 

With Angle, you don't need to bring debt token to repay your debt. By leaving the `Use collateral only` option checked, the protocol will swap your collateral tokens to agEUR to repay your debt and send you the remaining funds. 

If you have agEUR in your wallet and prefer to use those, you can check the `Use agEUR` option. In this case, the protocol will use all the agEUR in your wallet to repay your debt, and some of your collateral if needed. Then, you will receive the remaining funds back in your wallet. 

To close your vault, you only need to verify the information and click on `Add step` to go to the next section, and validate the transaction. 

## Take debt from another vault

Another feature available with the Angle Borrowing module is to transfer the debt from one vault to another. 

For example, imagine your vault #1 is close to liquidation, and your vault #2 is over-collateralized. In this case, you can simply transfer debt from vault #1 to #2 and equilibrate the situation of the two vaults. 

To take debt from a vault: 
1. Select the vault you want to add debt to
2. Select the `Take Debt from` action
3. Select the vault you want to take debt from
4. Input the amount of debt you want to take from this vault into the originally selected one. 
5. Check all the information about the change of the concerned vaults, add the step and confirm the transaction. 

{% hint style="info" %}
This will increase the liquidation price of the vault you add debt, so make sure to double check your liquidation price before executing the transaction. 
{% endhint %}
