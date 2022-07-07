---
description: Borrowing module deployment on other chains and its implications
---

#  🏦 Cross-chain borrowing module

The [Angle Borrowing module](/borrowing-module/README.md), allowing users to borrow and get leverage with agEUR, can be easily deployed to other EVM compatible networks. 

You can check all the networks Angle is deployed on and the smart contracts addresses [here](https://developers.angle.money/overview/smart-contracts).

## Advantages of sidechains and layer 2s

On those networks, transactions are usually more affordable. As a consequence, it is possible to open smaller vaults and borrow less agEUR. This makes Angle more accessible to a wide pool of potential users. 

At the same time, the share of the debt to be liquidated can be smaller, as transactions costs are smaller for liquidators. This makes Angle more borrower friendly in those environments. 

## Risks when deploying on other networks

Though the differents networks are becoming more connected with each other thanks to bridges, they are still distinct environments. Available liquidity and liquidators are not the same in all those networks. 

The main risk in deploying the Borrowing module on another network is that liquidations don't behave properly. With less liquidity, there is more slippage and liquidations can be less profitable, increasing the risk that they don't happen. 

To prevent this, the Borrowing module is deployed on each network with a specific cap of total agEUR debt to make sure liquidations remain profitable depending on the liquidity available on those networks.



