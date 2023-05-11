---
description: Earning rewards with Angle
---

# 🦄 Earning ANGLE and other rewards

ANGLE tokens are issued every week and distributed to different stakeholders of the Angle ecosystem based on what is voted by veANGLE holders [here](https://app.angle.money/gauge). Among other things, the protocol incentivizes Uniswap V3 Liquidity Providers of some specific pools.

The [Earn page](https://app.angle.money/earn) of the app lists all the yield opportunities linked to Angle and displays in particular the pools and farms where it is possible to earn ANGLE tokens. It is on this page that liquidity providers on Angle gauges (including Uniswap V3 pools) can claim their ANGLE rewards.

In this guide, we explain how to be eligible for ANGLE rewards as a UniswapV3 liquidity provider and how all LPs on gauges can claim their rewards.

## Incentives for Uniswap V3 Liquidity Providers

Angle implements a specific mechanism to reward Uniswap V3 Liquidity Providers (LPs). This mechanism rewards LPs granularily according to the efficiency of the liquidity they provide. In turn, they have the opportunity to provide liquidity in the way they want and can fully benefit from the flexibility offered by Uniswap V3.

{% hint style="info" %}
You can find more details on the mechanism in [the original announcement](https://blog.angle.money/a-new-incentivization-mechanism-for-uniswap-v3-liquidity-8ce32fa611b1). The [Merkl product](../../../../side-products/merkl/README.md) maintained by Angle Labs is a generalization of this incentive framework for any type of pool and of reward token.
{% endhint %}

### Off-chain Reward Computation Script

Incentives going to Uniswap V3 pools are split between Uniswap Liquidity Providers depending on the usefulness of their liquidity (that is to say the in-range liquidity) as well as the amount of agEUR in their position. This methodology is based on an [off-chain script](https://gist.github.com/Picodes/0b738ec92f7bd72ec6e77ffdf5d1c5e2) that computes rewards for each address and updates a Merkle root (i.e summary) of the distribution on-chain once every week so that LPs can regularly claim their ANGLE rewards.

Practically speaking, the reward computation script looks into each Uniswap V3 pool directly and sees at each swap which addresses held the pool's liquidity as well as the amount agEUR in their position. It then computes computes a reward for each address with in-range liquidity based on the following parameters:

1. The share of fees earned by this address, telling the virtual liquidity provided
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

As a LP, you can provide liquidity directly on [Uniswap V3](https://app.uniswap.org/#/add/), or with any of the integrated Uniswap position manager. Liquidity do not need to be staked or put in any specific contract for it to be eligible to rewards.

Currently, the protocol has integrated [Arrakis](https://www.arrakis.finance/) and [Gamma](https://www.gamma.xyz/), which means that if you deposit liquidity on Uniswap through Arrakis or Gamma, the reward computation script will automatically detect that you are involved in the Uniswap V3 pool.

When you are going through a liquidity manager, make sure to understand how they manage your liquidity, and if the positions are in-range. If they are not, you will not be earning ANGLE rewards.

For example, Arrakis manages liquidity passively, and agEUR/USDC has some times been out-of-range. Gamma does an active liquidity management, and rebalances the ranges regularly. You can find more information on the Gamma's side [here](https://twitter.com/GammaStrategies/status/1571865274076352512?s=20&t=PtrXjbL4ViqYiUgC85q-Zg).

### FAQ

#### How can I be eligible for the ANGLE rewards?

By providing liquidity on any of the Angle Uniswap V3 pools incentivized on the app [Earn page](https://app.angle.money/earn), either directly through [Uniswap](https://app.uniswap.org/#/add/), or through Arrakis or Gamma. Note that you do not need to "stake" your liquidity anywhere to be eligible for ANGLE rewards.

#### What do I need to do if I was previously staking?

If you were previously staking through Arrakis/Gelato, you are still earning ANGLE rewards if the Arrakis position ([agEUR-USDC](https://beta.arrakis.finance/vaults/1/0xEDECB43233549c51CC3268b5dE840239787AD56c) example) is in-range.

#### Is out-of-range liquidity being incentivized?

No. Only in-range liquidity used during swaps is being accounted for to receive incentives.

#### When can I claim my ANGLE rewards?

ANGLE rewards from the past week can be claimed once per week, every Thursday. Rewards accumulate if you don't claim them, meaning you can leave your liquidity idle for a while without claiming: your rewards will not be lost.

#### Where can I claim my rewards?

On the app [Earn page](https://app.angle.money/earn) (more [below](#claiming-angle-tokens)), or directly from the [MerkleRoot Distributor contract](https://etherscan.io/address/0x5a93D504604fB57E15b0d73733DDc86301Dde2f1).

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

## Claiming ANGLE tokens

The App Earn page leaves multiple options for claiming your ANGLE tokens if you're involved in a gauge of the protocol:

- Claim from multiple gauges in **one transaction** by clicking on the `Claim Rewards` button on the right. When using this modal, you can select/unselect the gauges you want to claim rewards from and then:
  - **`Claim ANGLE`**: this claims your ANGLE rewards from all the selected gauges (except the UniswapV3 related ones) in one transaction.
  - **`Claim and Lock ANGLE`**: this claims your ANGLE rewards from all the selected gauges (except the UniswapV3-related ones) in one transaction **and** lock them into your existing ANGLE lock. This increases your veANGLE balance and doesn't affect your lock expiration date. _NB: this is only possible if you already have ANGLE locked. You can lock ANGLE [here](https://app.angle.money/lock)._

![Claim rewards modal](/.gitbook/assets/claim-rewards-modal.png)

- Claim from a specific gauge by clicking on the `Claim` button in the modal below the input:

![Claim button](/.gitbook/assets/claim-rewards-from-pool.png)

- Rewards obtained by providing liquidity on Uniswap V3 need to be claimed through another button available on this page

![Claim UniV3](/.gitbook/assets/claim-uniV3.png)
