---
description: Guide for people using Merkl through liquidity managers
---

# Distribute liquidity from DEX pools through liquidity managers

## How Merkl handles liquidity managers

Merkl is designed to distribute incentives placed on liquidity pools to liquidity providers. When providing liquidity through liquidity managers such as Gamma or Arrakis, by default the incentives will be distributed to the liquidity manager contract investing end-users assets into the pools.

For the incentive to reach end-users, Merkl tracks the amount of LP ERC-20 token distributed by the liquidity managers and redistribute the incentives earned by the liquidity manager contract proportionally to the amount of LP ERC-20 tokens held by each end-user. To do so, the liquidity manager must be tracked by Merkl.

## Tracked Liquidity Managers by DEX

### UniswapV3

#### Arbitrum

- Gamma
- Arrakis
- DefiEdge

#### Optimism

- Gamma
- Arrakis
- DefiEdge

#### Polygon

- Gamma
- Arrakis
- DefiEdge

#### Ethereum

- Gamma
- Arrakis
- DefiEdge

### SushiswapV3

No liquidity managers integrated yet.

### Retro

No liquidity managers integrated yet.

## Tracking a new liquidity manager

### Pre-requisites

Merkl only supports liquidity managers which use the same architecture as Gamma or Arrakis. The liquidity manager must have :

- A factory contract which creates vaults and emits an event when creating them
- Vaults must issue a single ERC-20 token
- Vaults must have a `pool()` function to get the DEX pool associated to the vault
- All the contracts must be verified

### Requesting support for a new liquidity manager

To add support for your liquidity manager you can create a ticket in our [Discord](https://discord.com/invite/5Af6xum9bc).

You will need to submit the following information for each chain/DEX pair you want to add :

- Chain (Arbitrum, Optimism, Polygon or Ethereum)
- DEX (UniswapV3, SushiSwapV3 or Retro)
- Address of your factory contract (or addresses if you have multiple factories)
- Address of one of the vaults created by each of your factory contracts

If you're already part of our Discord server, you can submit a ticket [here](https://discord.com/channels/835066439891157012/1077879915493466153) (Integrate Liquidity Manager to Merkl Ticket).
