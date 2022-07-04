---
description: Use Angle on different chains and layers
---

# ⛓ Angle cross-chain infrastructure

## Deploying on different networks

Angle Protocol is composed of two set of smart contracts: the Core module, and the Borrowing module. 

While the Core module is only deployed on Ethereum mainnet, the Borrowing module can be deployed easily on other chains and layer 2s. This allows for native minting of agEUR on these other chains. 

{% page-ref page="borrowing-module-cross.md" %}


## Bridging between different networks

Bridges are what allow agEUR and the ANGLE token to be available on different chains. At the top level, the bridges for agEUR (and ANGLE) all do the same thing: they lock agEUR (or ANGLE) in a smart contract on the origin network, and mint new tokens on the destination network. When bridging back agEUR (or ANGLE) from the destination chain, tokens are burnt there and released from the smart contract on the origin chain.

AgEUR can be bridged between different networks using our new LayerZero infrastructure. It was previously relying on Multichain, which is still used for ANGLE. 

{% page-ref page="layer-zero-setup.md" %}

{% page-ref page="old-setup.md" %}


{% hint style="info" %}
Angle related contract addresses across different chains and layer 2s can be found [here](https://developers.angle.money/protocol-overview/smart-contracts/sidechains-layer2s-contracts).
{% endhint %}
