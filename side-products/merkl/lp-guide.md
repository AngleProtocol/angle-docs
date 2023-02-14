---
description: Guide for liquidity providers
---

# 🌊 Liquidity Provider Guide

As a liquidity provider, Merkl lets you customize your position to optimize your returns on AMMs like Uniswap V3 according to how incentivizors set up the distribution formula for the pool you're on.

All pools using Merkl are listed at [merkl.angle.money](https://merkl.angle.money). There are links to the pools and to the supported liquidity managers for you to deposit your funds. [merkl.angle.money](https://merkl.angle.money) may not be the only place where to find Merkl pools and there may be solutions relying on Merkl under the hood on other dApps.

To receive rewards listed on Merkl, you may provide liquidity either directly on the AMM (e.g. UniswapV3) or on one of the supported position / liquidity managers. If you are using a liquidity manager, be careful to understand how they rebalance the liquidity they manage.

The main choices you need to make when adding liquidity are:

- how tight should the position’s range be
- what should the split between the two tokens be

For example, a tight range will virtually provide more liquidity and earn more fees and rewards. However, it has more chance to become out-of-range and suffer from impermanent loss.

Once you have provided liquidity, no additional steps are required to start receiving your rewards, and you will be able to claim them directly from the Merkl page, or from any other app which integrates Merkl. In particular, you will not need to stake your tokens anywhere else.
If you were providing liquidity on a pool (directly on the AMM or through a liquidity positon manager) before the incentive was created on Merkl, you will also be eligible to claim your rewards when they are posted.

Rewards for liquidity providers on Merkl do not increase block by block, but are posted at [a frequency](./helpers.md#🔗-supported-amms-and-chains) which depends on the chain.

{% hint style="info" %}
Note that rewards can be claimed to your address from any other address. If you are integrating Merkl as a smart contract and don't want rewards to be claimed on your behalf, you can call the `toggleOnlyOperatorCanClaim` function on the `Distributor` contract (address [here](./helpers.md#🧑‍💻-smart-contracts)).
{% endhint %}
