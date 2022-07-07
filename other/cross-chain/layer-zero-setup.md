---
description: Angle LayerZero bridge infrastructure
---

# 🌉 Angle LayerZero bridge infrastructure

Angle is integrated with a [LayerZero](https://layerzero.network/) infrastructure to bridge agEUR. LayerZero is a decentralized message passing solution made up of relayers sending messages between networks, and of contracts sending and receiving the messages and the tokens.

At the top level, users have to specify an amount and a destination chain, and are able to send agEUR from one chain to the other with one transaction.

## Bridging details

Like with any other bridge in Angle, there are both total and hourly limits to the amount of tokens that can bridged that were implemented as safeguards.

Bridging transactions can revert on the origin chains when the amount to be bridged is above the limit that can currently be bridged. In this case, users directly get their tokens back.

In the case when there is not enough funds on the destination chain, the Angle app prevents users to bridge to these networks. If some users interact with the contracts programatically and reach the limits, transactions will not revert. In this case, they will be able to get their tokens back on the destination chain in different ways.
