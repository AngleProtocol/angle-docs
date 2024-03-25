---
description: How to bridge EURA and ANGLE to different networks with the Angle App
---

# 🌉 Bridge Angle stablecoins across chains

Angle App leverages the protocol's [cross-chain bridge setup](../../../other/cross-chain.md) built on LayerZero to enable [bridging its stablecoins and ANGLE](https://app.angle.money/bridges-agEUR) between many EVM-compatible networks.

To bridge stablecoins or ANGLE from a network to another, you simply need to head to the [app's bridge page](https://app.angle.money/bridges-agEUR) select the token you want to bridge, enter the amount, and select the destination network.

![Bridge app page](../../../.gitbook/assets/bridge2.png)

There are two other aspects you need to be careful about:

1. [**Bridge limits**](#bridge-limits), displayed below the `Bridge` button
2. Having enough funds on the **origin chain** to [pay for transaction fees](#funds-required-to-pay-for-bridge-transaction-fees) on the origin **and** destination chains.

{% hint style="info" %}
Not having enough funds on the origin chain to pay for gas is the most frequently encountered issue, and most likely the one you are facing as well. Try to buy more gas token and try the transaction again.
{% endhint %}

## Bridge limits

Angle's bridge system implements total and hourly limits for the amounts that can be bridged to a chain. These limits are particular to each asset (Angle stablecoin or ANGLE token) and to each chain.

The total limits limit how many tokens can be held by the bridge contract on each chain. The hourly limits limit how much can be bridged to and from each chain.

{% hint style="info" %}
If the limits are reached when processing a bridge transaction, you won't receive stablecoins or ANGLE in your wallet on the destination chain.

Instead, **you will receive lz tokens in your wallet that can be used to redeem the stablecoin or ANGLE later**, when the limits reset.
{% endhint %}

Information on the current limits are displayed in the callout below the inputs.

![Bridge app page](../../../.gitbook/assets/bridge3.png)

### How to get back stablecoins from lz tokens

On each network where stablecoins can be bridged, there is a lz-stablecoin contract. Typically on every chain where EURA can be bridged there is a lz-agEUR contract (due to the previous name of the stablecoin).

You can find their addresses on the [smart contracts addresses](https://developers.angle.money/overview/smart-contracts) page.

{% hint style="info" %}
Here, we specifically look at EURA bridging use case, but all of this applies to other stablecoins as well. Also, the example here is for Optimism, but it works the same on any chain where Angle Bridging system is live.
{% endhint %}

If you hit a bridge limit, you should have received lz-agEUR tokens in your wallet. In this case, you can go to the token contract ([example on Optimism](https://optimistic.etherscan.io/address/0x840b25c87b626a259ca5ac32124fa752f0230a72#writeProxyContract)).

![Receive lz-agEUR](/.gitbook/assets/receive-lz-ageur.png)

Then follow these steps:

1. Click on `Write as Proxy`
2. Connect your wallet to Etherscan by clicking on the `Connect to Web3` button.
3. Scroll down to the function `withdraw()`
4. Enter the amount of lz-agEUR you want to exchange for EURA, and your wallet address. _The amount input needs to be in the correct decimals format: you need to multiply the amount by `10^18`. For example, to exchange `123` lz-agEUR, you need to input `123000000000000000000`._
5. And send the transaction

[Example of a withdraw transaction](https://optimistic.etherscan.io/tx/0x20799daf2e30ccf2ec4cf1f66b85f01273b3fc26bc786ad25d7b187eb810f721)

![Connect lz-agEUR](/.gitbook/assets/connect-lzageur.png)

![Send tx Etherscan](/.gitbook/assets/send-tx-etherscan.png)

If the limits are still empty, you will just get the same amount of `lz-agEUR` back. You can check the current limits on the app [bridge page](https://app.angle.money/bridges-agEUR).

## Funds required to pay for bridge transaction fees

When bridging from a network to another, you need enough gas token on the origin chain to pay for bridge transactions **both on the origin and destination chains**.

For example, if you bridge from Polygon to Ethereum mainnet, where transaction fees are higher, you will need more MATIC than usual on Polygon to pay for the transactions.

If you do not have enough funds, the transaction might revert or you could get an `internal JSON RPC` error displayed on the Angle app.

{% hint style="info" %}
For example, with a gas price of 100 you will need ~0.03 gas token (ETH, MATIC, ...) on the origin chain to pay for the transaction.⁣
{% endhint %}

## I'm not sure if my bridge transaction was confirmed

If you don't know whether you should have received funds in your wallet after a bridge transaction, you should check on [LayerZeroScan](https://layerzeroscan.com/) with the hash of the bridge transaction from the origin network.

If the transaction on the destination chain is confirmed but you don't have the tokens in your wallet, you can read the paragraph about [how to get back stablecoins from lz tokens](#how-to-get-back-stablecoins-from-lz-tokens).
