---
description: Guide for people using Merkl to incentivize pools
---

# Incentivizor Guide

## For Incentivizors

Any DAO or individual looking to incentivize a pool can use Merkl and customize their distribution to get the desired type of liquidity.

They first need to fill the pool and reward token address and quantity. A distribution duration is also required. If liquidity positions managers need to be included in the distribution, their specific addresses need to be specified.

Then, any of the distribution formula parameters can be customized. When this is done, the incentivizor just has to send the tokens to the distribution contract!

Any address holding a position or position manager token will be able to claim their rewards at the end of each epoch according to how they provided liquidity on the pool.

## Liquidity positions managers

Liquidity positions managers are services that take care of actively maintaining positions for LPs on AMMs like Uniswap V3. Typically, they will pre-determine the width of the range to provide liquidity on, and rebalance the position when needed according to specific parameters.

As an incentivizor, having your LPs go through a liquidity manager can improve the pool liquidity and how it is maintained over time. Adding a liquidity manager to a traditional staking contract was not trivial, as the contract had to be updated. With Merkl, you can add any liquidity position manager to your distribution. If you want to do this, reach out in Merkl's Discord channel.

As Merkl’s script is computing the reward scores off-chain, the addresses receiving the rewards can easily be updated. This allows Merkl to incentivize users of any underlying positions manager. It can even allow for more specific customization, like rewarding someone using its position manager token as collateral on another contract for example.

While Merkl works for liquidity position managers,
