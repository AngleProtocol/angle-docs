---
description: Details on Angle Uniswap V3 incentive mechanism for LPs
---

# 🦄 Incentives for Uniswap V3 Liquidity Providers

Angle implements a specific mechanism to reward Uniswap V3 Liquidity Providers (LPs) according to their added value to the protocol. Basically, it allows to reward LPs more granularily according to the efficiency of the liquidity they provide. In turn, they have the opportunity to provide liquidity in more complex ways that benefit from all Uniswap V3 possibilities.

{% hint style="info" %}
You can find more details on the mechanism in [the original announcement](https://blog.angle.money/a-new-incentivization-mechanism-for-uniswap-v3-liquidity-8ce32fa611b1).
{% endhint %}

In this guide, we detail how the incentives are split and how you can provide liquidity on Angle Uniswap V3 pools to earn ANGLE rewards.

## Incentives distribution

Every week, the distribution of incentives going to each pool is voted by veANGLE holders [here](https://app.angle.money/#/gauge).

### Off-chain Reward Computation Script

Incentives going to Uniswap V3 pools are split between Uniswap Liquidity Providers depending on the usefulness of their liquidity (that is to say the in-range liquidity) as well as the amount of agEUR in their position. This methodology is based on an [off-chain script](https://gist.github.com/Picodes/0b738ec92f7bd72ec6e77ffdf5d1c5e2) that computes rewards for each address and updates a Merkle root (i.e summary) of the distribution on-chain once every week so that LPs can regularly claim their ANGLE rewards.

Practically speaking, the reward computation script looks into each Uniswap V3 pool directly and sees at each swap which addresses held the pool's liquidity as well as the amount agEUR in their position. It then computes computes a reward for each address with in-range liquidity based on the following parameters:

1. The share of fees earned by this address, telling us the virtual liquidity provided
2. The share of agEUR they hold compared to the total pool size
3. The share of the other token they hold compared to the total pool size

These parameters are then adjusted by a boost according to the veANGLE balance of each Liquidity Provider.

The exact formula is then as follows:

$$
[0.4 \times(\texttt{fees earned by the position / fees earned by the pool)}+ 0.4 \times
\texttt{(agEUR in the position / agEUR in the pool)}+ 0.2 \times \texttt{(other token in the position / other token in the pool)}] \times \texttt{veANGLE boost}
$$

One big difference with incentives mechanisms relying on wrapping Uniswap V3 positions into ERC20 is that with this mechanism LPs can provide liquidity on any range they want, and any Uniswap liquidity manager can be integrated.

For example, a tight range will virtually provide more liquidity and earn more fees and ANGLE rewards. However, it has more chance to become out-of-range and suffer from [impermanent loss](https://www.youtube.com/watch?v=8XJ1MSTEuU0).

![UniV3 LP on Angle](/.gitbook/assets/uniV3-lp.png)

### Providing liquidity

As a LP, you can provide liquidity directly on [Uniswap V3](https://app.uniswap.org/#/add/), or with any of the integrated Uniswap position manager.

Currently, the protocol has integrated [Arrakis](https://www.arrakis.finance/) and [Gamma](https://www.gamma.xyz/), which means that if you deposit liquidity on Uniswap through Arrakis or Gamma, the reward computation script will automatically detect that you are involved in the Uniswap V3 pool.

When you are going through a liquidity manager, make sure to understand how they manage your liquidity, and if the positions are in-range. If they are not, you will not be earning ANGLE rewards.

For example, Arrakis manages liquidity passively, and agEUR/USDC has some times been out-of-range. Gamma does an active liquidity management, and rebalances the ranges regularly. You can find more information on the Gamma's side [here](https://twitter.com/GammaStrategies/status/1571865274076352512?s=20&t=PtrXjbL4ViqYiUgC85q-Zg).

### FAQ

#### How can I be eligible for the ANGLE rewards?

By providing liquidity on any of the Angle Uniswap V3 pools incentivized on the app [Earn page](https://app.angle.money/#/earn), either directly through [Uniswap](https://app.uniswap.org/#/add/), or through Arrakis or Gamma.

#### What do I need to do if I was previously staking?

If you were previously staking through Arrakis/Gelato, you are still earning ANGLE rewards if the Arrakis position ([agEUR-USDC](https://beta.arrakis.finance/vaults/1/0xEDECB43233549c51CC3268b5dE840239787AD56c) example) is in-range.

#### Is out-of-range liquidity being incentivized?

No. Only in-range liquidity used during swaps is being accounted for to receive incentives.

#### When can I claim my ANGLE rewards?

ANGLE rewards from the past week can be claimed once per week, every Thursday. Rewards accumulate if you don't claim them, meaning you can leave your liquidity idle for a while without claiming: your rewards will not be lost.

#### Where can I claim my rewards?

On the app [Earn page](https://app.angle.money/#/earn), or directly from the [MerkleRoot Distributor contract](https://etherscan.io/address/0x5a93D504604fB57E15b0d73733DDc86301Dde2f1).

#### Why is my APR is different from what is displayed?

Your actual APR depends on the volume of the pool, the range you are providing liquidity on, and the price of the pool.

These are not constant and vary continuously.

#### What is the Boosted APR?

The Boosted APR is the APR you earn when holding enough veANGLE to get the max boost.

#### Which pools are concerned?

Currently the Uniswap V3 pools that are eligible to this system are the following:

- [Uniswap V3 agEUR-ETH](https://info.uniswap.org/#/pools/0x8db1b906d47dfc1d84a87fc49bd0522e285b98b9) (0.05%) on Ethereum mainnet
- [Uniswap V3 agEUR-USDC](https://info.uniswap.org/#/pools/0x735a26a57a0a0069dfabd41595a970faf5e1ee8b) (0.01%) on Ethereum mainnet
- [Uniswap V3 agEUR-USDC](https://info.uniswap.org/#/polygon/pools/0x3fa147d6309abeb5c1316f7d8a7d8bd023e0cd80) (0.01%) on Polygon
