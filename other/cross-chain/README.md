---
description: Use Angle on different chains and layers
---

# ⛓ Angle Cross-Chain Infrastructure

## Angle on different networks

Angle Protocol is composed of two set of smart contracts: the Core module, and the Borrowing module.

While the Core module is only deployed on Ethereum mainnet, the Borrowing module is also deployed on other chains and layer 2s. This allows for native minting of agEUR on these other networks.

{% hint style="info" %}
Smart contract addresses associated to the Borrowing module on different chains can be found [here](https://developers.angle.money/overview/smart-contracts).
{% endhint %}

## 🌉 Bridging between networks

Bridges are what allow agEUR and the ANGLE token to be available on different networks. At the top level, the bridges for agEUR (and ANGLE) all do the same thing: they burn (or lock) tokens on the origin network, and mint new tokens on the destination network. When bridging back tokens from the destination chain, tokens are burnt (or locked) there and minted (or released) from the smart contract on the origin chain.

AgEUR and ANGLE can be bridged between networks using Angle's infrastructure, compatible with multiple bridge solutions. Bridging agEUR is available natively on the [Angle App](https://app.angle.money/#/bridges).

![lz bridge infra user](../../.gitbook/assets/bridge-infra-user.jpg)

{% hint style="info" %}
When bridging to a network, you need enough gas token on the origin chain to pay for bridge transactions **both on the origin and destination chains**. For example, if you bridge from Polygon to Ethereum mainnet where tx fees are higher, you will need more MATIC than usual on Polygon to pay for the transactions.
{% endhint %}

### Angle bridge infrastructure details

Usually, bridges work by minting their own version of the tokens being bridged. To compensate, Angle allows approved bridges versions of agEUR to be swapped 1:1 to a canonical ("official") version of agEUR on every chain.

To limit the risk associated with each bridge, a total and hourly cap on the quantity of each token that can be bridged to & from specific networks has been implemented.

### About LayerZero

Some bridges, like [LayerZero](https://layerzero.network/), are integrated natively with agEUR meaning that users should not see the intermediary bridge token and directly receive canonical agEUR in one transaction.

LayerZero is by the way the solution that is used under the hood for bridging on the Angle App.

With LayerZero, bridging transactions can revert on the origin chains when the amount to be bridged is above the limit that can currently be bridged. In this case, users can directly get their tokens back.

On the destination chains, transactions involving LayerZero cannot revert. While the Angle App prevents users from bridging in the case where bridge limits are attained, users interacting programatically with the bridge contracts in such situations can still get their tokens back on the destination chain by interacting with the "bridge" (non-official) LayerZero token contract.

### Bridge Solutions

| Chain         | agEUR                                                                                                       | ANGLE                                                          |
| ------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Polygon       | [LayerZero](https://app.angle.com/#/bridge), [Polygon PoS bridge](https://wallet.polygon.technology/bridge) | [Polygon PoS bridge](https://wallet.polygon.technology/bridge) |
| Optimism      | [LayerZero](https://app.angle.com/#/bridge)                                                                 | ❌                                                             |
| Arbitrum      | [LayerZero](https://app.angle.com/#/bridge)                                                                 | ❌                                                             |
| Avalanche     | [LayerZero](https://app.angle.com/#/bridge)                                                                 | [Multichain Bridge](https://app.multichain.org/#/router)       |
| BSC           | [LayerZero](https://app.angle.com/#/bridge)                                                                 | [Multichain Bridge](https://app.multichain.org/#/router)       |
| Fantom        | [Multichain Router](https://app.multichain.org/#/router)                                                    | [Multichain Bridge](https://app.multichain.org/#/router)       |
| Harmony       | [Multichain Router](https://app.multichain.org/#/router)                                                    | [Multichain Bridge](https://app.multichain.org/#/router)       |
| Fuse          | [Multichain Router](https://app.multichain.org/#/router)                                                    | ❌                                                             |
| NEAR / Aurora | [Rainbow Bridge](https://rainbowbridge.app/transfer)                                                        | [Rainbow Bridge](https://rainbowbridge.app/transfer)           |
| Solana        | [Wormhole](https://wormholebridge.com/#/transfer)                                                           | [Wormhole](https://wormholebridge.com/#/transfer)              |

_**Multichain Router**: token can be bridged **between** chains with Router support for this token. **Multichain Bridge**: token can be bridged only from Ethereum mainnet to the specified chain, and not between chains._

{% hint style="info" %}
Angle related contract addresses across different chains and layer 2s can be found [here](https://developers.angle.money/protocol-overview/smart-contracts/sidechains-layer2s-contracts).
{% endhint %}
