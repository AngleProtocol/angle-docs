---
description: Helpers to use and integrate Merkl
---

# ⛓ Integration Helpers

## 🔗 Live AMMs and Chains

| Live AMMs & Chains        | Epoch Time | Supported Liquidity Managers |
| ------------------------- | ---------- | ---------------------------- |
| 🦄 UniswapV3 - Ethereum   | 6 hours    | Gamma, Arrakis               |
| 🦄 UniswapV3 - Polygon    | 6 hours    | Gamma, Arrakis               |
| 🦄 UniswapV3 - Optimism   | 6 hours    | Gamma                        |
| 🦄 UniswapV3 - Arbitrum   | 6 hours    | Gamma                        |
| 🍣 SushiswapV3 - Ethereum | 6 hours    |                              |
| 🍣 SushiswapV3 - Polygon  | 6 hours    |                              |
| 🍣 SushiswapV3 - Optimism | 6 hours    |                              |
| 🍣 SushiswapV3 - Arbitrum | 6 hours    |                              |

## 🧑‍💻 Smart Contracts

Merkl is organized around 2 main contracts on each chain on which it is available:

- `Distributor`: where liquidity providers claim their rewards and stakeholders contest the proposed Merkle roots
- `DistributionCreator`: where incentivizors deposit their rewards and specify the distribution parameters they want for it

Both contracts are managed through a `CoreMerkl` contract by a management multisig which notably has the power to settle disputes, to change dispute parameters, to modify fees and their recipients, and to whitelist new addresses allowed to modify Merkle roots in the `Distributor` contract.

| Chain    | Contracts                                                                                                                                                                                                                                                                                                                                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ethereum | [Distributor](https://etherscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://etherscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://etherscan.io/address/0x0E632a15EbCBa463151B5367B4fCF91313e389a6), [Management Multisig](https://etherscan.io/address/0x529619a10129396a2F642cae32099C1eA7FA2834)                                             |
| Polygon  | [Distributor](https://polygonscan.com/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://polygonscan.com/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://polygonscan.com/address/0x9418d0aa02fce40804abf77bb81a1ccbeb91eafc), [Management Multisig](https://polygonscan.com/address/0xc0c07644631543c3af2fA7230D387C5fA418a131)                                 |
| Optimism | [Distributor](https://optimistic.etherscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://optimistic.etherscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://optimistic.etherscan.io/address/0xc2c7a0d9a9e0467090281c3a4f28D40504d08FB4), [Management Multisig](https://optimistic.etherscan.io/address/0x17a7F6a839fea3b716b43f9414ffc93131878BD2) |
| Arbitrum | [Distributor](https://optimistic.etherscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://optimistic.etherscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://arbiscan.io/address/0xA86CC1ae2D94C6ED2aB3bF68fB128c2825673267), [Management Multisig](https://arbiscan.io/address/0x3350bef226F7BdCA874C5561320aB7EF9DC89E70)                         |

{% hint style="info" %}
Addresses of the `Distributor` and `DistributionCreator` contracts are the same across all chains.
{% endhint %}

## 🐋 Types and Specific Script Behavior

When depositing a reward, incentivizors should specify the addresses of the smart contracts they want to exclude from the distribution. On top of that, while Gamma or Arrakis are automatically caught up by the script (and so you do not need to expressely specify them when creating a distribution), addresses of other types of liquidity position managers may need to be given to the contract when creating a distribution for the script to be able to specifically deal with them.

Overall, when creating a distribution, you may tell the script to apply a specific set of rules to some addresses by specifying for these addresses a predefined type.

Types are `uint32` numbers and they are the same across the different chains on which Merkl is deployed.

| Type | Rules                                  |
| ---- | -------------------------------------- |
| 0    | [Arrakis](https://www.arrakis.finance) |
| 2    | [Gamma](https://app.gamma.xyz)         |
| 3    | Blacklist                              |

{% hint style="info" %}
While this docs is regularly updated, [this page](https://github.com/AngleProtocol/merkl-calculator/blob/staging/src/types/index.ts) remains the most up to date source of truth for the mapping between types and how the script should handle them.
{% endhint %}
