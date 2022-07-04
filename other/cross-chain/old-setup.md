---
description: Old Angle cross-chain setup with Multichain
---

# Angle old cross-chain setup

Angle originally relied on Multichain to bridge tokens. Here is the bridge setup for agEUR and ANGLE before July 2022 and the implementation of LayerZero contracts. 

## 🌉 Bridge Solutions

| Chain         | Bridge                                                                 | agEUR  | ANGLE         |
| ------------- | ---------------------------------------------------------------------- | ------ | ------------- |
| Avalanche     | [Multichain](https://app.multichain.org/#/router) (previously Anyswap) | Router | Bridge        |
| Fantom        | [Multichain](https://app.multichain.org/#/router)                      | Router | Bridge        |
| BSC           | [Multichain](https://app.multichain.org/#/router)                      | Router | Bridge        |
| Harmony       | [Multichain](https://app.multichain.org/#/router)                      | Router | Bridge        |
| Fuse          | [Multichain](https://app.multichain.org/#/router)                      | Router | Not available |
| NEAR / Aurora | [Rainbow Bridge](https://rainbowbridge.app/transfer)                   | Bridge | Bridge        |
| Polygon       | [Polygon PoS Bridge](https://wallet.polygon.technology/bridge/)        | Bridge | Bridge        |
| Solana        | [Wormhole](https://wormholebridge.com/#/transfer)                      | Bridge | Bridge        |

_**Router**: token can be bridged **between** chains with Router support for this token. **Bridge**: token can be bridged only from Ethereum mainnet to the specified chain, and not between chains._

{% hint style="info" %}
Angle related contract addresses across the different sidechains, layer 2s and blockchains Angle is integrated with can be found [here](https://developers.angle.money/protocol-overview/smart-contracts/sidechains-layer2s-contracts).
{% endhint %}
