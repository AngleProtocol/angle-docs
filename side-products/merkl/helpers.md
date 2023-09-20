---
description: Utils to distribute rewards with Merkl
---

# ⛓ Distribution Utils

## 🔗 Live AMMs and Chains

| Live AMMs & Chains               | Epoch Time |
| -------------------------------- | ---------- |
| 🦄 UniswapV3 - Ethereum          | 12 hours   |
| 🦄 UniswapV3 - Polygon           | 6 hours    |
| 🦄 UniswapV3 - Optimism          | 6 hours    |
| 🦄 UniswapV3 - Arbitrum          | 6 hours    |
| 🍣 SushiswapV3 - Ethereum        | 12 hours   |
| 🍣 SushiswapV3 - Polygon         | 6 hours    |
| 🍣 SushiswapV3 - Optimism        | 6 hours    |
| 🍣 SushiswapV3 - Arbitrum        | 6 hours    |
| 🍣 SushiswapV3 - Base            | 6 hours    |
| 🥞 PancakeSwapV3 - Ethereum      | 12 hours   |
| 🥞 PancakeSwapV3 - Polygon zkEVM | 12 hours   |
| 🪞 Retro - Polygon                | 6 hours    |
| ⚔️ Camelot - Arbitrum            | 6 hours    |
| 🔵 BaseSwap - Base               | 6 hours    |

{% hint style="info" %}
Can't find your AMM in this list? You can add it by following the guides below.
{% endhint %}

To find the list of supported liquidity managers for each of these chains, you can directly look into the ALMs appearing on the pools displayed on [the Merkl app](https://merkl.angle.money).

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

## Add a new AMM or chain to Merkl

Merkl can be expanded to any chain and any concentrated liquidity AMM that works similarly to UniswapV3. To get your AMM or chain supported on Merkl, please create a BD ticket in our [Discord](https://discord.com/invite/5Af6xum9bc) and fill out [this form](https://tally.so/r/3XJODP).

## ➕ Add an ALM to Merkl

### Pre-requisites

Merkl only supports liquidity managers which use the same architecture as Gamma or Arrakis. The liquidity manager must verify the following pre-requisites:

- Use a factory contract which creates vaults and emits an event when creating them
- Vaults issue a single ERC-20 token
- Vaults have a `pool()` function to get the DEX pool associated to the vault
- All the contracts must be verified

### Requesting support for a new liquidity manager

To add support for your liquidity manager you can create a BD ticket in our [Discord](https://discord.com/invite/5Af6xum9bc) and fill out [this form](https://tally.so/r/w4JYLr).

## Add a new reward token to Merkl

Reward tokens sent through Merkl need to be whitelisted before being used. To get your token whitelisted, please fill [this form](https://tally.so/r/3y2bqx), open a pull request with your token information [on this repo](https://github.com/AngleProtocol/angle-assets) and create a BD ticket in our [Discord](https://discord.com/invite/5Af6xum9bc).
