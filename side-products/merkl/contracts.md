---
description: Merkl smart contract addresses and documentation
---

# 🧑‍💻 Merkl Smart Contracts

Merkl is organized around 2 main contracts on each chain on which it is available:

- `Distributor`: where liquidity providers claim their rewards and stakeholders contest the proposed Merkle roots
- `DistributionCreator`: where incentivizors deposit their rewards and specify the distribution parameters they want for it

Both contracts are managed through a `Core` contract by a management multisig which notably has the power to settle disputes, to change dispute parameters, to modify fees and their recipients, and to whitelist new addresses allowed to modify Merkle roots in the `Distributor` contract.

| Chain    | Contracts                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------- |
| Ethereum | [Distributor](TODO.md), [DistributionCreator](TODO.md), [Core](TODO.md), [Management Multisig](TODO.md) |
| Polygon  | [Distributor](TODO.md), [DistributionCreator](TODO.md), [Core](TODO.md), [Management Multisig](TODO.md) |
| Optimism | [Distributor](TODO.md), [DistributionCreator](TODO.md), [Core](TODO.md), [Management Multisig](TODO.md) |
| Arbitrum | [Distributor](TODO.md), [DistributionCreator](TODO.md), [Core](TODO.md), [Management Multisig](TODO.md) |
