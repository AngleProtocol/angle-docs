---
description: Find out how to use the Angle Protocol through the interface at https://app.angle.money
---

# 📔 App Guides

In this section, you will learn how to play with the [app](https://app.angle.money) developed by Angle Labs, Inc. and more particularly to:

- [Swap](/guides/app-guides/agEUR/swap.md), [borrow](/guides/app-guides/agEUR/borrow.md), [bridge](/guides/app-guides/agEUR/bridge.md), and [buy agEUR from credit card](agEUR/on-ramp-off-ramp.md)
- Get [leverage](/guides/app-guides/trade/leverage.md) on your collateral from agEUR debt, or trade on-chain forex with EURUSD [Perpetuals](trade/perpetuals.md).
- Invest in yield strategies and [stake your funds](earn/staking.md) to earn ANGLE tokens or other incentives.
- [Buy ANGLE](ANGLE/buy.md) at the lowest price, [lock](ANGLE/lock.md) them to earn yield and [vote on rewards distribution](ANGLE/gauges-voting.md) and [governance proposals](ANGLE/snapshot-votes.md).

## UI tour

This app contains most of the features related to the protocol. Pages can be accessed from the sidebar on the left under three main sections: **agEUR**, **Trade**, **Earn**, and **ANGLE**.

Audits and smart contract insurance partners can also be found in the **Safety** section. Everything you need to know about the protocol can be found under the **Learn** section at the bottom.

### App Menu and Settings

On the top-left corner, there is an app menu with different features and settings. In the general menu, you can choose your network and the currency denominating the values you see on the app. By clicking on the icon to the right of your address, you can activate the transaction simulator mode detailed below.

Just below that, there is a `Settings` button. Among those settings, you can choose:

- A default slippage for your transactions
- To have unlimited or limited approvals
- To use permit signatures instead of approval transactions when possible
- To impersonate an address

#### Impersonator guide

[app.angle.money](https://app.angle.money) lets people impersonate other addresses, and see what the person controlling this address would view on the app.

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
