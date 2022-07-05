---
description: Angle LayerZero bridge infrastructure
---

# 🌉 Angle LayerZero bridge infrastructure

Angle is also based on a [LayerZero](https://layerzero.network/) infrastructure to bridge agEUR. LayerZero is a decentralized message passing solution made up of relayers sending messages between networks, and of contracts sending and receiving the messages and the tokens.

At the top level, users will just have to specify an amount and a destination chain, and will be able to send agEUR from one chain to the other with one transaction. 

![lz bridge infra user](../../.gitbook/assets/bridge-infra-user.png)

## Bridging details

There are both total and hourly limits to the amount of tokens that can bridged that were implemented as safeguards. 

Bridging transactions can revert on the origin chains when the amount to be bridged is above the limit that can currently be bridged. In this case, users directly get their tokens back. 

In the case when there is not enough funds on the destination chain, the Angle app will prevent users to bridge to these networks. If some users interact with the contracts programatically and reach some limits, they can get their tokens back in different ways. 



