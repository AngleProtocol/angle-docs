---
description: How Transmuter can be composable with other
---

# Transmuter Composability

## Composability with other Angle Mechanisms

Transmuter is a stablecoin system. It can be a full protocol working on its own, but it can also be used as a module within a bigger stablecoin protocol.

Transmuter has its own internal accounting metrics (it never looks for instance into the $\texttt{totalSupply}$ of the stablecoin it is minting). This means that it is possible to have other smart contracts with a minting right on the stablecoin handled by Transmuter without breaking the logic of the system.\\

On the Angle case, Transmuter is particularly well suited to work in parallel with Angle Borrowing module, with the protocol's flash-loan systems, or with its direct deposit modules.

## Compatibility with other Stablecoins Systems
