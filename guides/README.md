---
description: Angle Protocol and App Guides
---

# 🎓 Guides

**In this section, you will find some guides to get onboarded to the different functionalities of the Angle Protocol and app.**

The Angle Protocol is currently available to anyone on different EVM compatible networks, and can be accessed through an app hosted at [app.angle.money](https://app.angle.money/) which contains most of the features related to the protocol. Here, you will more particularly learn how to:

- [Buy](/guides/app-guides/agEUR/swap.md), [borrow](/guides/app-guides/agEUR/borrow.md), or [bridge](/guides/app-guides/agEUR/bridge.md) Angle stablecoins.
- [Buy ANGLE tokens](ANGLE/buy.md) at the lowest price possible, [lock](ANGLE/lock.md) them to earn yield and vote on rewards distribution and governance proposals

## UI tour

### App Menu and Settings

On the top-left corner of the app, there is a menu with different features and settings. In the general menu, you can choose your network and the currency denominating the values you see on the app. By clicking on the icon to the right of your address, you can activate the transaction simulator mode detailed below.

Just below that, there is a `Settings` button. Among those settings, you can choose:

- A default slippage for your transactions
- To have unlimited or limited approvals
- To use permit signatures instead of approval transactions when possible
- To impersonate an address

#### Impersonator guide

[app.angle.money](https://app.angle.money) lets you impersonate other addresses, and see what the person controlling this address would view on the app.

Here are the steps to impersonate another address:

1. Connect your wallet.
2. Click on `Settings` in the top left corner.
3. At the bottom of the Settings section, there is an eye icon with an input to the right. Enter any address, and the connection will change.
4. You can now navigate the app as if you were controlling this address.

![Impersonator](/.gitbook/assets/impersonator.png)

Obviously, it is not possible to confirm any transaction while connected to the app through an external address. However, you can simulate transactions from other addresses with Tenderly directly on the app.

#### Transaction simulator with Tenderly

In the App menu, you can see an eye to the right of your address. When lighted, you won't be prompted to confirm the transactions, but you will be redirected to Tenderly where they will be simulated and you will see a summary.

This can be very useful if you're looking to test the app without actually passing transactions. It can help you make sure that you are not getting scammed and that transactions are happening as they should.

When impersonating another address, the simulation mode is active by default.

{% hint style="info" %}
The app presented here is developed by Angle Labs, Inc., a company contributing to the protocol. Anyone is welcome to build its app on top of Angle, and we'll make sure to promote any serious front interface of the protocol in this docs.
{% endhint %}
