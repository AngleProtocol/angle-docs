---
description: Use Angle Protocol tokens on different chains!
---

# ⛓️ Multichain Angle

Angle Protocol is deployed on Ethereum mainnet, but its corresponding tokens and stablecoins are meant to be bridged on other layers and sidechains.

For the case of agEUR for instance, minting and burning still takes place on Ethereum, but agEUR can be accessed on other chains/L2s. Keeping minting and burning of agEUR on Ethereum mainnet helps to ensure the integrity of the reserves backing the token and prevent liquidity fragmentation.

Bridges are what allow agEUR and the ANGLE token to be available on different chains. Since agEUR only exists natively on Ethereum mainnet, the bridges for agEUR and ANGLE all do the same thing: they lock agEUR (or ANGLE) in a smart contract on ETH side, and mint on the corresponding chain. When bridging back agEUR (or ANGLE) from the corresponding chain, tokens are burnt there and released from the smart contract on Ethereum mainnet.

## 🌉 Bridge Solutions

| Chain         | Bridge                                                          |
| ------------- | --------------------------------------------------------------- |
| Polygon       | [Polygon PoS Bridge](https://wallet.polygon.technology/bridge/) |
| Solana        | [Wormhole](https://wormholebridge.com/#/transfer)               |
| NEAR / Aurora | [Rainbow Bridge](https://rainbowbridge.app/transfer)            |

{% hint style="info" %}
Angle related contract addresses across the different sidechains, layer 2s and blockchains Angle is integrated with can be found [here](https://developers.angle.money/protocol-overview/smart-contracts/sidechains-layer2s-contracts).
{% endhint %}

