---
description: A list of words and terms relating to the Angle Protocol
---

# 📒 Glossary

Here, you will find a list of the terms and expressions that are used across the protocol.

If you still have some questions, do not hesitate to reach out on the [Angle Discord](https://discord.gg/67WSSZqBG6) 📐.

| Term                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stablecoin**       | A cryptocurrency, or token, that is pegged to another asset. This means that the stablecoin in question is designed to mirror the value of the asset it is pegged to.                                                                                                                                                                                                                                                                                       |
| **agToken**          | Angle stablecoins. agTokens are stablecoins issued by the Angle Protocol modules. They are named from the asset they are pegged to. For example, agEUR is pegged to the EUR.                                                                                                                                                                                                                                                                                |
| **Module**           | A set of smart contracts interacting together for a specific use case.                                                                                                                                                                                                                                                                                                                                                                                      |
| **Core Module**      | The first set of smart contracts of the Angle Protocol deployed in November 2021 and used to mint and burn agTokens in a capital-efficient and over-collateralized way. More information [here](concepts/overview.md).                                                                                                                                                                                                                                      |
| **Borrowing Module** | A new set of smart contracts that is planned to be deployed around May 2022, to help grow agTokens minting while maintaining a robust peg.                                                                                                                                                                                                                                                                                                                  |
| **Governance**       | The group of stakeholders in the Angle Protocol that can decide the upgrades and improvements that should be made to the protocol. Currently, the Angle Governance is made up of the veANGLE holders.                                                                                                                                                                                                                                                       |
| **ANGLE**            | The original governance token of the Angle Protocol. It has been upgraded to a ve (voting-escrowed) model to align the motivations of the stakeholders with the protocol. More info in the [ANGLE page](governance/angle-token.md).                                                                                                                                                                                                                         |
| **veANGLE**          | Voting-esrowed ANGLE. They can be obtained by locking ANGLE from 1 week to 4 years. veANGLE can vote on Governance proposals, and earn a share of the weekly interest generated by the protocol. More in the [veANGLE page](governance/veANGLE/).                                                                                                                                                                                                           |
| **TVL**              | Acronym for Total Value Locked, the total amount of value locked up in smart contracts of the designated protocol.                                                                                                                                                                                                                                                                                                                                          |
| **Collateral**       | Cryptocurrency asset (USDC, DAI, wETH, wBTC, ...) held in reserves supporting the value of the stablecoins issued by the protocol. In the Core module, collateral can directly be swapped for agTokens. In the Borrowing module, collateral are the tokens users deposit into Angle Vaults to be able to borrow agTokens. If their debt becomes too big compared to their collateral, it can be taken from them to pay back the debt through a liquidation. |

| 🏭 **Keeper** | A keeper is an individual or a bot that carries out actions that are needed to keep the protocol functioning. They are usually incentivized to perform such actions. Both [Angle Core module](other-aspects/keepers.md) and Angle Borrowing module rely on keepers. |
| 🔱 **Oracle** | Oracles are third-party services that allow smart contracts within blockchains to receive external data from outside of their ecosystem. They are mainly used to make cryptocurrency market prices available and usable on-chain. The [Core module](other-aspects/oracles.md) relies on [Chainlink](https://chain.link) and [Uniswap V3 TWAP oracles](https://uniswap.org/blog/uniswap-v3/), while the Borrowing module solely relies on Chainlink. |