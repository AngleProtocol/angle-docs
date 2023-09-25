---
description: Guide for Liquidity Providers on concentrated liquidity AMMs to enjoy Merkl
---

# 🌊 Provide liquidity and claim through Merkl

As a Liquidity Provider, Merkl lets you customize your concentrated liquidity position to optimize your returns.

All pools using Merkl are listed at [merkl.angle.money](https://merkl.angle.money). There are links to the pools and to the supported liquidity managers for you to deposit your funds. [merkl.angle.money](https://merkl.angle.money) may not be the only place where to find Merkl pools and there may be other protocol relying on Merkl under the hood to incentivize their liquidity.

![Merkl Claim](/.gitbook/assets/merkl-claim2.png)

To receive rewards listed on Merkl, you can provide liquidity directly one of the listed pools, or on one of the supported position / liquidity managers. If you are using a liquidity manager, be careful to understand how the liquidity manager rebalances liquidity.

Merkl comes with an anti DoS filter which means that positions with less than \$20 of liquidity are not eligible for incentives.

The main choices you need to make when adding liquidity are:

- how tight should the position’s range be
- what should the split between the two tokens be

For example, a tight range will virtually provide more liquidity and earn more fees and rewards. However, it has more chances to become out-of-range and suffer from impermanent loss.

Once you have provided more than \$20 of liquidity, no additional steps are required to start receiving your rewards. You will be able to claim them directly from the Merkl page or from any other app which integrates Merkl. In particular, **you will not need to stake your tokens anywhere else**.
If you were providing liquidity on a pool (directly on the AMM or through a liquidity position manager) before the incentive was created on Merkl, you will also be eligible to claim your rewards when they are distributed.

![Merkl Script](/.gitbook/assets/docs-merkl-for-lps.png)

Rewards for Liquidity Providers on Merkl do not increase block by block, but can be claimed at [a frequency](./helpers.md#🔗-live-amms-and-chains) which depends on the chain.

{% hint style="info" %}
Note that rewards can be claimed to your address by any other address. If you are integrating Merkl as a smart contract and don't want rewards to be claimed on your behalf, you can call the `toggleOnlyOperatorCanClaim` function on the `Distributor` contract (address [here](./helpers.md#🧑‍💻-smart-contracts)).
{% endhint %}
