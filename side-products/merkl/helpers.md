---
description: Helpers to use and integrate Merkl
---

# ⛓ Integration Helpers

## 🔗 Live AMMs and Chains

| Live AMMs & Chains               | Epoch Time | Supported Liquidity Managers          |
| -------------------------------- | ---------- | ------------------------------------- |
| 🦄 UniswapV3 - Ethereum          | 12 hours   | Gamma, Arrakis, DefiEdge, Ichi        |
| 🦄 UniswapV3 - Polygon           | 6 hours    | Gamma, Arrakis, DefiEdge, Steer, Ichi |
| 🦄 UniswapV3 - Optimism          | 6 hours    | Gamma, Arrakis, DefiEdge, Steer       |
| 🦄 UniswapV3 - Arbitrum          | 6 hours    | Gamma, Arrakis, DefiEdge, Steer       |
| 🍣 SushiswapV3 - Ethereum        | 12 hours   |                                       |
| 🍣 SushiswapV3 - Polygon         | 6 hours    | Gamma, Steer, DefiEdge                |
| 🍣 SushiswapV3 - Optimism        | 6 hours    | Gamma, Steer                          |
| 🍣 SushiswapV3 - Arbitrum        | 6 hours    | Gamma, Steer, DefiEdge                |
| 🍣 SushiswapV3 - Base            | 6 hours    |                                       |
| 🥞 PancakeSwapV3 - Ethereum      | 12 hours   |                                       |
| 🥞 PancakeSwapV3 - Polygon zkEVM | 12 hours   |                                       |
| 🪞 Retro - Polygon               | 6 hours    | Gamma, Ichi                           |

Can't find your AMM in this list? You can add it by following this [guide](#pre-requisites).

## 🧑‍💻 Smart Contracts

Merkl is organized around 2 main contracts on each chain on which it is available:

- `Distributor`: where liquidity providers claim their rewards and stakeholders contest the proposed Merkle roots
- `DistributionCreator`: where incentivizors deposit their rewards and specify the distribution parameters they want for it

Both contracts are managed through a `CoreMerkl` contract managed by a multisig which has the power to settle disputes, change dispute parameters, to modify fees and their recipients, and to whitelist new addresses allowed to modify Merkle roots in the `Distributor` contract. It has no ability to alter distributions.

| Chain         | Contracts                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ethereum      | [Distributor](https://etherscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://etherscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://etherscan.io/address/0x0E632a15EbCBa463151B5367B4fCF91313e389a6), [Management Multisig](https://etherscan.io/address/0x529619a10129396a2F642cae32099C1eA7FA2834)                                             |
| Polygon       | [Distributor](https://polygonscan.com/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://polygonscan.com/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://polygonscan.com/address/0x9418d0aa02fce40804abf77bb81a1ccbeb91eafc), [Management Multisig](https://polygonscan.com/address/0xc0c07644631543c3af2fA7230D387C5fA418a131)                                 |
| Optimism      | [Distributor](https://optimistic.etherscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://optimistic.etherscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://optimistic.etherscan.io/address/0xc2c7a0d9a9e0467090281c3a4f28D40504d08FB4), [Management Multisig](https://optimistic.etherscan.io/address/0x17a7F6a839fea3b716b43f9414ffc93131878BD2) |
| Arbitrum      | [Distributor](https://arbiscan.io/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://arbiscan.io/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://arbiscan.io/address/0xA86CC1ae2D94C6ED2aB3bF68fB128c2825673267), [Management Multisig](https://arbiscan.io/address/0x3350bef226F7BdCA874C5561320aB7EF9DC89E70)                                                 |
| Polygon zkEVM | [Distributor](https://zkevm.polygonscan.com/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://zkevm.polygonscan.com/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://zkevm.polygonscan.com/address/0xC16B81Af351BA9e64C1a069E3Ab18c244A1E3049), [Management Multisig](https://zkevm.polygonscan.com/address/0x9439B96E39dA5AD7EAA75d7a136383D1D9737055)         |
| Base          | [Distributor](https://basescan.org/address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae), [DistributionCreator](https://basescan.org/address/0x8BB4C975Ff3c250e0ceEA271728547f3802B36Fd), [CoreMerkl](https://basescan.org/address/0xC16B81Af351BA9e64C1a069E3Ab18c244A1E3049), [Management Multisig](https://basescan.org/address/0x19c41F6607b2C0e80E84BaadaF886b17565F278e)                                             |

{% hint style="info" %}
Addresses of the `Distributor` and `DistributionCreator` contracts are the same across all chains.
{% endhint %}

## 🐋 Types and Specific Script Behavior

When depositing a reward, incentivizors should specify the addresses of the smart contracts they want to exclude from the distribution.

On top of that, while Gamma or Arrakis are automatically detected by the script, addresses of other types of liquidity position managers may need to be given to the contract when creating a distribution for the script to be able to specifically deal with them.

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

## ➕ Add an AMM to Merkl

### Pre-requisites

Merkl only supports liquidity managers which use the same architecture as Gamma or Arrakis. The liquidity manager must verify the following pre-requisites:

- Use a factory contract which creates vaults and emits an event when creating them
- Vaults issue a single ERC-20 token
- Vaults have a `pool()` function to get the DEX pool associated to the vault
- All the contracts must be verified

### Requesting support for a new liquidity manager

To add support for your liquidity manager you can create a ticket in our [Discord](https://discord.com/invite/5Af6xum9bc).

You will need to submit the following information for each chain/DEX pair you want to add:

- Chain (Arbitrum, Optimism, Polygon or Ethereum)
- DEX (UniswapV3, SushiSwapV3, ...)
- Address of your factory contract (or addresses if you have multiple factories)
- Address of one of the vaults created by each of your factory contracts

If you're already part of our Discord server, you can submit a ticket [here](https://discord.com/channels/835066439891157012/1077879915493466153) (Create a BD Ticket).
