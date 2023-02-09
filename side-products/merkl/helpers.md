---
description: Helpers to use and integrate Merkl
---

# 🙌 Merkl Integration Helpers

## 🔗 Supported AMMs and Chains

| Supported AMMs & Chains | Epoch Time | Supported Liquidity Managers |
| ----------------------- | ---------- | ---------------------------- |
| UniswapV3 - Ethereum    | 24 hours   | Gamma, Arrakis               |
| UniswapV3 - Polygon     | 8 hours    | Gamma, Arrakis               |
| UniswapV3 - Optimism    | 24 hours   | Gamma, Arrakis               |
| UniswapV3 - Arbitrum    | 24 hours   | Gamma, Arrakis               |

## 🧑‍💻 Smart Contracts

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

## 🐋 Liquidity Position Managers Mapping

When depositing a reward, incentivizors should specify the addresses of the liquidity managers (or wrappers) they want to support as well as their type (is it an Arrakis contract or a Gamma contract?). Types (referred to in the code as wrapper types) are `uint32` numbers that each correspond to one specific liquidity position manager. Types are the same across the different chains on which Merkl is deployed.

| Wrapper Type | Position Manager                       |
| ------------ | -------------------------------------- |
| 0            | [Arrakis](https://www.arrakis.finance) |
| 1            | [Gamma](https://app.gamma.xyz)         |
