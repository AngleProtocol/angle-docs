---
description: How to bridge agEUR and ANGLE to different networks with the Angle App
---

# 🌉 Bridging Angle tokens

Angle App leverages the protocol's [cross-chain bridge setup](../../../other/cross-chain.md) built on LayerZero to enable [bridging agEUR and ANGLE](https://app.angle.money/#/bridges-agEUR) between many EVM-compatible networks.

To bridge agEUR or ANGLE from a network to another, you simply need to select the token you want to bridge, enter the amount, and select the destination network.

![Bridge app page](../../../.gitbook/assets/bridge.png)

There are two other aspects you need to be careful about:

1. **Bridge limits**
2. Enough funds on the **origin chain** to pay for tx fees on the origin and destination chains.

## Bridge limits

Angle's LayerZero implementation has a total and a hourly limit. The total limits limit how much token can be held by the bridge contract on each chain. The hourly limits limit how much can be bridged to and from each chain.

If the limits are reached, you won't be able to bridge and will have to wait until they are reset. Information on the current limits is displayed in the callout below the inputs.

![Bridge app page](/.gitbook/assets/bridge-limits-info.png)

## Funds required to pay for transaction fees

When bridging from a network to another, you need enough gas token on the origin chain to pay for bridge transactions **both on the origin and destination chains**.

For example, if you bridge from Polygon to Ethereum mainnet, where tx fees are higher, you will need more MATIC than usual on Polygon to pay for the transactions.
