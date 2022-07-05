---
description: Use Angle on different chains and layers
---

# ⛓ Angle cross-chain infrastructure

## Angle on different networks

Angle Protocol is composed of two set of smart contracts: the Core module, and the Borrowing module. 

While the Core module is only deployed on Ethereum mainnet, the Borrowing module is also deployed on other chains and layer 2s. This allows for native minting of agEUR on these other networks. 

{% page-ref page="borrowing-module-cross.md" %}


## Bridging between different networks

Bridges are what allow agEUR and the ANGLE token to be available on different chains. At the top level, the bridges for agEUR (and ANGLE) all do the same thing: they lock agEUR (or ANGLE) in a smart contract on the origin network, and mint new tokens on the destination network. When bridging back agEUR (or ANGLE) from the destination chain, tokens are burnt there and released from the smart contract on the origin chain.

AgEUR can be bridged between different networks using our new LayerZero infrastructure. It was previously relying on Multichain, which is still used for ANGLE. 

{% page-ref page="layer-zero-setup.md" %}

{% page-ref page="multichain-setup.md" %}

Angle bridges and cross-chain setup and trade-offs have been detailed in [this governance post](https://gov.angle.money/t/angle-bridge-and-cross-chain-setup/389). If any information is unclear, don't hesitate to comment it!  


{% hint style="info" %}
Angle related contract addresses across different chains and layer 2s can be found [here](https://developers.angle.money/protocol-overview/smart-contracts/sidechains-layer2s-contracts).
{% endhint %}
