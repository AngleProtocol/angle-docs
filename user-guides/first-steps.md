---
description: Learn how to use the Angle app
---

# 👟 First steps and settings

## Introduction

The Angle app, available at [app.angle.money](http://app.angle.money), allows you to interact with the Angle stablecoin protocol by connecting a wallet such as Rabby Wallet, Metamask, Trust Wallet, Coinbase Wallet and more.

With the Angle app, you can:

* [Earn yield on your stablecoins](earn-yield-on-your-stablecoins/)
* [Swap your assets for Angle stablecoins & ANGLE tokens](swap-crypto-to-angle-stablecoins.md)
* [Bridge Angle stablecoins](bridge-angle-stablecoins.md)
* [Buy Angle stablecoins with fiat currency](buy-angle-stablecoins.md)
* [Borrow EURA stablecoins](borrow.md)
* [Lock your ANGLE tokens to vote governance proposals](lock-angle-tokens.md)

<figure><img src="../.gitbook/assets/‎User guide 1 first steps and settings.‎001.jpeg" alt=""><figcaption><p>Homescreen of the Angle app</p></figcaption></figure>

## Settings

Settings are accessible by clicking on the gear icon in the top right corner of the app. The Angle application offers various settings to enhance your experience:

* **Set a default slippage for your transactions**\
  This percentage determines how much the price can move from the time you send your transaction to the time it is executed. Setting this can help prevent your order from being filled if the market moves suddenly and the price moves against you.
* **Have limited or unlimited approvals**\
  Approvals allow a dapp to access your funds in order to execute a transaction (e.g., a swap). When a approval is required before a transaction, you can choose whether to give an infinite approval or just the minimum amount to the smart contract.
* **Spy an address**\
  You can browse the app by connecting an address that isn't yours. This allows you to explore various features using the balances and amounts associated with that specific address. You will not be able to sign any transactions with this address since it is not yours. However, you can simulate transactions (see below).
* **Select your preferred display currency**\
  You can choose between USD, EUR, ETH and BTC.

<figure><img src="../.gitbook/assets/‎Suite first steps.‎001.jpeg" alt=""><figcaption><p>Angle app settings</p></figcaption></figure>

## Impersonate **an address**

The Angle app lets you impersonate other addresses to see what the user of those addresses would experience on the app.

1. Open the Angle app at [https://app.angle.money/](https://app.angle.money/)
2. Click on the gear icon to open the settings
3. Enter an address in the `Spy Address` field
4. Navigate the Angle app as if you own this address

<figure><img src="../.gitbook/assets/‎User guide 1 first steps and settings.‎003.jpeg" alt=""><figcaption><p>Enter the address you want to impersonate in the "Spy Address" field</p></figcaption></figure>

<figure><img src="../.gitbook/assets/‎User guide 1 first steps and settings.‎002.jpeg" alt=""><figcaption><p>The Savings amounts in the app are displayed as if the spied address is connected</p></figcaption></figure>

{% hint style="info" %}
You cannot confirm transactions while using an external address that you do not own. However, you can still simulate transactions with Tenderly in the Angle app.
{% endhint %}

## S**imulate a transaction with Tenderly**

You can simulate a transaction on Tenderly before executing it. This allows you to get an overview of the transaction’s impact before executing it, and avoid scams. You can simulate a transaction with your own address or by impersonating another address.

1. Go to the settings in the top right corner of the app.
2. Enter an address in the `Spy Address` field
3. Perform a transaction (swap, bridge, deposit etc)

You will automatically be redirected to Tenderly where your transaction will be simulated with a summary.

Simulating a transaction allows you to test the app without actually executing a real transaction. It can help you make sure you are on the right app, and not getting scammed.

When impersonating another address, the simulation mode is activated by default.

<figure><img src="../.gitbook/assets/Capture d’écran 2024-07-25 à 14.33.48.png" alt=""><figcaption><p>Transaction simulation automatically opened in Tenderly</p></figcaption></figure>
