---
description: Use Angle Protocol tokens on different chains!
---

# ⛓ Cross-Chain ANGLE and agEUR

Angle Protocol is deployed on Ethereum mainnet, but its corresponding tokens and stablecoins are meant to be bridged on other layers and sidechains.

For the case of agEUR for instance, minting and burning still takes place on Ethereum, but the token is available on other chains.&#x20;

{% hint style="info" %}
Keeping minting and burning of agEUR on Ethereum mainnet helps to ensure the integrity of the reserves backing the token and prevent liquidity fragmentation. In the medium-term, native minting of agEUR on chains other than Ethereum should be allowed.
{% endhint %}

Bridges are what allow agEUR and the ANGLE token to be available on different chains. Since agEUR (and ANGLE) only exists natively on Ethereum mainnet, the bridges for agEUR (and ANGLE) all do the same thing: they lock agEUR (or ANGLE) in a smart contract on ETH side, and mint new tokens on the corresponding chain. When bridging back agEUR (or ANGLE) from the corresponding chain, tokens are burnt there and released from the smart contract on Ethereum mainnet.

Additonally, [Multichain](https://multichain.org)'s router allows assets bridged from Ethereum mainnet to move **between** chains. They added support for **agEUR**, which can now be bridged across all chains supported by the router: Ethereum, Avalanche, Fantom, Fuse, BSC, and Harmony.&#x20;

ANGLE isn't supported by the router yet and still needs to be bridged from and to Ethereum mainnet. This means that if you want to bridge ANGLE from Fantom to Avalanche, you first need to bridge the Fantom ANGLE to the Ethereum mainnet before bridging it to Avalanche.

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
