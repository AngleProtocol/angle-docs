---
description: Merkl is a improved incentive mechanism for UniswapV3-like positions built by Angle Labs
---

# 🌲 Merkl, by Angle

Merkl is a mechanism to incentivize UniswapV3-type liquidity positions in a flexible and efficient way. It is built and maintained by Angle Labs, but is separate from Angle Protocol.

In essence, Merkl allows to customize how incentives are distributed to reward behaviors that bring value to liquidity pools & protocols. At the same time, liquidity providers can customize their positions to maximize their earning from fees and incentives, enjoying all possibilities enabled by Uniswap V3.

Additionally, any liquidity position managers like Gamma or Arrakis can be included in the distribution so that their underlying LPs receive their fair share of the incentives.

![Merkl by Angle](/.gitbook/assets/merkl-sharing-visual.jpg)

## Mechanism

An off-chain script reads all the swaps that took place on a pool and computes a reward score for each position according to:

- the fees earned by the position, which represent the liquidity of the position used by the pool
- the share of token A held by the position
- the share of token B held by the position

A different weight is attributed to each parameter. A list of the final scores is compressed into a merkle root and pushed on-chain. This tells the contract how much incentives each position should receive. A boost for addresses holding a specific token (like veANGLE for example) can be added to the reward score computation.

Reward scores are computed from the data over regular periods called epochs.

### The formula

The exact formula is as follows:

$$
[wFees \times(\texttt{fees earned by the position / fees earned by the pool)}+ wTokenA \times\texttt{(tokA in the position / tokA in the pool)}+ wTokenB \times \texttt{(tokB in the position / tokB in the pool)}] \times \texttt{govTok boost}
$$

## For Incentivizors

Any DAO or individual looking to incentivize a pool can use Merkl and customize their distribution to get the desired type of liquidity.

They first need to fill the pool and reward token address and quantity. A distribution duration is also required. If liquidity positions managers need to be included in the distribution, their specific addresses need to be specified.

Then, any of the distribution formula parameters can be customized. When this is done, the incentivizor just has to send the tokens to the distribution contract!

Any address holding a position or position manager token will be able to claim their rewards at the end of each epoch according to how they provided liquidity on the pool.

## For LPs

As a liquidity provider, you can now customize your position to optimize your returns on Uniswap V3 according to how the incentivizors set up the distribution formula.

The main choices for a LP are:

- how tight should the position’s range be
- what should the split between the two tokens be

For example, a tight range will virtually provide more liquidity and earn more fees and ANGLE rewards. However, it has more chance to become out-of-range and suffer from impermanent loss.

All pools using Merkl are listed at merkl.angle.money. There are links to Uniswap V3 and the supported liquidity managers for LPs to deposit their funds. If you are using a liquidity manager, be careful to understand how they rebalance the liquidity they manage.

Once liquidity is being provided, no additional steps are required to start receiving your rewards, and they can all be claimed directly from the Merkl page.

## Liquidity positions managers

Liquidity positions managers are services that take care of actively maintaining positions for LPs on AMMs like UniswapV3. Typically, they will pre-determine the width of the range to provide liquidity on, and rebalance the position when needed according to specific parameters.

As an incentivizor, having your LPs go through a liquidity manager can improve the pool liquidity and how it is maintained over time. Adding a liquidity manager to a traditional staking contract was not trivial, as the contract had to be updated. With Merkl, you can add any liquidity position manager to your distribution. If you want to do this, reach out in Merkl's Discord channel.

As Merkl’s script is computing the reward scores off-chain, the addresses receiving the rewards can easily be updated. This allows Merkl to incentivize users of any underlying positions manager. It can even allow for more specific customization, like rewarding someone using its position manager token as collateral on another contract for example.

## Links

- Merkl App
- Script code
- Merkl's Discord channel
