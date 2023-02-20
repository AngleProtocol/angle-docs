---
description: Helpers to use and integrate Merkl
---

# 🙌 Merkl Integration Helpers

## 🔗 Supported AMMs and Chains

| Supported AMMs & Chains | Epoch Time | Supported Liquidity Managers |
| ----------------------- | ---------- | ---------------------------- |
| 🦄 UniswapV3 - Ethereum | 24 hours   | Gamma, Arrakis               |
| 🦄 UniswapV3 - Polygon  | 24 hours   | Gamma, Arrakis               |
| 🦄 UniswapV3 - Optimism | 24 hours   | Gamma, Arrakis               |
| 🦄 UniswapV3 - Arbitrum | 24 hours   | Gamma, Arrakis               |

## 🧑‍💻 Smart Contracts

Merkl is organized around 2 main contracts on each chain on which it is available:

- `Distributor`: where liquidity providers claim their rewards and stakeholders contest the proposed Merkle roots
- `DistributionCreator`: where incentivizors deposit their rewards and specify the distribution parameters they want for it

Both contracts are managed through a `CoreMerkl` contract by a management multisig which notably has the power to settle disputes, to change dispute parameters, to modify fees and their recipients, and to whitelist new addresses allowed to modify Merkle roots in the `Distributor` contract.

| Chain    | Contracts                                                                                                                                                                                                                                                          |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ethereum | [Distributor](TODO.md), [DistributionCreator](TODO.md), [CoreMerkl](https://etherscan.io/address/0x0E632a15EbCBa463151B5367B4fCF91313e389a6), [Management Multisig](https://etherscan.io/address/0x529619a10129396a2F642cae32099C1eA7FA2834)                       |
| Polygon  | [Distributor](TODO.md), [DistributionCreator](TODO.md), [CoreMerkl](https://polygonscan.com/address/0x9418d0aa02fce40804abf77bb81a1ccbeb91eafc#code), [Management Multisig](https://polygonscan.com/address/0xc0c07644631543c3af2fA7230D387C5fA418a131)            |
| Optimism | [Distributor](TODO.md), [DistributionCreator](TODO.md), [CoreMerkl](https://optimistic.etherscan.io/address/0xc2c7a0d9a9e0467090281c3a4f28D40504d08FB4), [Management Multisig](https://optimistic.etherscan.io/address/0x17a7F6a839fea3b716b43f9414ffc93131878BD2) |
| Arbitrum | [Distributor](TODO.md), [DistributionCreator](TODO.md), [CoreMerkl](https://arbiscan.io/address/0xA86CC1ae2D94C6ED2aB3bF68fB128c2825673267), [Management Multisig](https://arbiscan.io/address/0x3350bef226F7BdCA874C5561320aB7EF9DC89E70)                         |

## 🐋 Liquidity Position Managers Mapping

When depositing a reward, incentivizors should specify the addresses of the liquidity managers (or wrappers) they want to support as well as their type (is it an Arrakis contract or a Gamma contract?). Types (referred to in the code as wrapper types) are `uint32` numbers that each correspond to one specific liquidity position manager. Types are the same across the different chains on which Merkl is deployed.

| Wrapper Type | Position Manager                       |
| ------------ | -------------------------------------- |
| 0            | [Arrakis](https://www.arrakis.finance) |
| 2            | [Gamma](https://app.gamma.xyz)         |

{% hint style="info" %}
While this docs is regularly updated, [this page](https://github.com/AngleProtocol/merkl-calculator/blob/staging/src/types/index.ts) remains the most up to date source of truth for the mapping between position managers and wrapper types.
{% endhint %}
