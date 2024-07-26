---
description: Learn how to use the Angle app
---

# 👟 First steps

## Introduction

The Angle App, available at [app.angle.money](http://app.angle.money), allows you to interact with the Angle stablecoin protocol by connecting your wallet.

With the Angle app, you can:

* [Earn yield on your stablecoins](earn-yield-on-your-stablecoins/)
* [Swap your assets for Angle stablecoins & ANGLE tokens](swap-crypto-to-angle-stablecoins.md)
* [Bridge Angle stablecoins](bridge-angle-stablecoins.md)
* [Borrow EURA stablecoins](borrow.md)
* [Buy Angle stablecoins with fiat currency](buy-angle-stablecoins.md)
* [Lock your ANGLE tokens to vote governance proposals](lock-angle-tokens.md)

<figure><img src="../.gitbook/assets/‎User Guide.‎001.jpeg" alt=""><figcaption><p>Homescreen of the Angle app</p></figcaption></figure>

## Settings

Settings are accessible by clicking on the gear icon in the App. The Angle application offers various settings to enhance your experience:

* **Set a default slippage for your transactions**\
  This percentage determines how much the price can move from the time you send your transaction to the time it is executed. Setting this can help prevent your order from being filled if the market moves suddenly and the price moves against you.
* **Have limited or unlimited approvals**\
  Approvals allow a dapp to access your funds in order to execute a transaction (e.g., a swap). When a approval is required before a transaction, you can choose whether to give an infinite approval or just the minimum amount to the smart contract.
* **Use permit signatures instead of approval transactions when possible**\
  Permit signatures allow you to sign an approval message offchain. That way you don't need to send an onchain transaction and pay a gas fee to grant an approval to a smart contract.
* **Simulate a transaction**\
  You can simulate a transaction on Tenderly before executing it. This allows you to get an overview of the transaction’s impact before executing it, and avoid scams. You can simulate a transaction with your own address or by impersonating another address.
* **Select your preferred display currency**\
  You can choose between USD, EUR, ETH and BTC.

<figure><img src="../.gitbook/assets/Capture d’écran 2024-07-25 à 14.32.26.png" alt=""><figcaption><p>Settings</p></figcaption></figure>

## Impersonate **an address**

The Angle app lets you impersonate other addresses to see what the user of those addresses would experience on the app.

1. Open the Angle App at [https://app.angle.money/](https://app.angle.money/)
2. Click on the gear icon to open the settings
3. Enter an address in the `Spy Address` field
4. Navigate the Angle app as if you own this address

<figure><img src="../.gitbook/assets/Capture d’écran 2024-07-25 à 14.32.55 (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You cannot confirm transactions while using an external address that you do not own. However, you can still simulate transactions with Tenderly in the Angle app.
{% endhint %}

## S**imulate a transaction with Tenderly**

1. In the Settings of the App, toggle the `Simulate transaction` box
2. Enter an address in the `Spy Address` field
3. Perform a transaction (swap, bridge, deposit etc)

You will automatically be redirected to Tenderly where your transaction will be simulated with a summary.

Simulating a transaction allows you to test the app without actually executing a real transaction. It can help you make sure you are on the right app, and not getting scammed.

When impersonating another address, the simulation mode is activated by default.

<figure><img src="../.gitbook/assets/Capture d’écran 2024-07-25 à 14.33.48.png" alt=""><figcaption><p>Transaction simulation automatically opened in Tenderly</p></figcaption></figure>
