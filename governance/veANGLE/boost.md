---
description: How veANGLE can boost ANGLE rewards for LPs
---

# 💥 Boost

## 🔎 TL;DR

- Liquidity providers on Angle gauges can boost their ANGLE rewards by holding veANGLE.
- This boost can represent up to to x2.5 the base rewards an address without any veANGLE could get.
- To compute the boost, the total veANGLE supply of an address is applied to all the contracts this address is staking on.

{% hint style="warning" %}
Boost on rewards only apply to some specific gauges. More info on such gauges [here](https://developers.angle.money/overview/smart-contracts/mainnet-contracts#gauges).
{% endhint %}

## 🚜 Farming Boost

Holding veANGLE give users more weight when collecting certain farming rewards. A big majority of the farming rewards that are distributed directly through the protocol are eligible for veANGLE boosts.

A user veANGLE boost does not increase the overall emission of rewards. The boost is an additive boost that is added to each farmer's yield proportional to their veANGLE balance.xz

## 🧮 Boost Computation

Angle forked its staking contract model (also called liquidity gauge) from Curve which has a similar boost system.

Not all ANGLE emissions are distributed through staking contracts: for some UniswapV3 gauges, rewards are distributed through an offchain mechanism involving no staking contract. On these gauges, boosts apply as well and the logic with which boosts are computed in this case is similar to how this is done in the staking contracts used for other Angle gauges.

With this in mind, how are boosts computed for Angle staking contracts? Basically, Angle staking contracts consider that an address holding veANGLE is providing more liquidity than it really is.

In a given gauge, owning veANGLE increases a LP's share of the pool thus increasing the rewards received. As usual, LPs holding no veANGLE are considered as providing 100% of their liquidity. If an address owns enough veANGLE, the contract considers that it brings up to 250% its original liquidity, or a x2.5 boost compared to the original 100%.

Then, this x2.5 multiplier in liquidity provided translates into a boost on rewards depending on the total liquidity provided in the pool and how it is considered by the boost calculator.

{% hint style="info" %}
Note that as the quantity of veANGLE owned by LPs on a pool increases, the amount of rewards received by non-veANGLE holders decreases, as they represent a smaller share of the liquidity.
{% endhint %}

### 🖋️ Details

#### Understanding the formula

Let:

$$
x_{lp} = \texttt{My liquidity in this pool} \\ tot_{lp} = \texttt{Total liquidity in this pool} \\ x_{veANGLE} = \texttt{My veANGLE balance} \\ s_{veANGLE} = \texttt{Total veANGLE supply}
$$

The complete formula to compute the liquidity the staking contract considers provided and therefore the boost applied is:

$$
\min(x_{lp} + 1.5\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}}, 2.5 \times x_{lp})
$$

To get the max possible boost on rewards, an address needs to get 100% of its provided liquidity taken into account by the protocol. This is equivalent to having the term on the left greater or equal than the value of the liquidity provided:

$$
x_{lp} + 1.5\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}} \geq 2.5 \times x_{lp}
$$

$$
\cancel{1.5}\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}} \geq \cancel{1.5} \times x_{lp}
$$

$$
\frac{x_{veANGLE}}{s_{veANGLE}} \geq \frac{x_{lp}}{tot_{lp}}
$$

$$
\texttt{Share of veANGLE supply} \geq \texttt{Share of liquidity in the pool}
$$

**An address having a higher share of the total veANGLE supply than its share of liquidity provided in the pool for which the boost is being computed is considered as having x2.5 more liquidity than an address with no veANGLE.**

All gauges therefore have different requirements meaning some pools are easier to boost than others. In the end, it all depends on how much others have locked and how much the liquidity gauge has.

### Examples

Now that we understand how veANGLE holders get a boost on capital compared to non-holders, let’s look at how this translates into an **actual boost on rewards received.**

**Example 1:** One holder of veANGLE with a big share of the pool:

- Address A and B are providing 100 of liquidity each in pool P.
- They are receiving 50% of the rewards each.

Now, let’s say that A owns the total supply of veANGLE.

- The boost calculator now considers that A brings $$2.5  \times100 = 250$$ of liquidity to the pool.
- Address A now owns $$\frac{250}{250+100} = 71.5\%$$ of the pool, and address B 28.5%.
- Address A rewards multiplier is at x1.43 (from 50% to 71.5%).

**Example 2:** Two holders of veANGLE, with very different shares of the pool.

- Now say that address A provides 100 and address B 9900.
- If none of them hold veANGLE, they are respectively earning 1% and 99% of the rewards.
- Now let’s consider that A owns 1% or more of the veANGLE supply (i.e. as much as or more than its share of the pool).
- Again, the boost calculator now considers that it brings $$2.5  \times100 = 250$$ of liquidity to the pool.
- Therefore, address A is now earning $$\frac{250}{250+9900} = 2.46\%$$ of the rewards, or a x2.46 multiplier.
- On the other hand, if B, which owns much more liquidity than A, had 1% of the veANGLE supply as well, its considered liquidity would go from 9900 to: $$9900 + 1.5 \times 10,000 \times 1\% = 10050$$
- Its share of earnings would go from 97.54% to: $$\frac{10050}{250+ 10050} = 97.57\%$$
  A very small increase compared to address A.
- In this situation, address A share of rewards and boost would go from 2.46 to:
  $$\frac{250}{250+ 10050} = 2.43\%$$

**Example 3:** Introducing address C

Staying in example 2's situation, let's introduce an address C providing 2000 of liquidity. In this case, the considered liquidity for B and C becomes:

- Address B considered liquidity:
  $$9900 + 1.5 \times 12,000 \times 1\% = 10080$$

- Address C considered liquidity:
  $$2000 + 1.5 \times 12,000 \times 1\% = 2180$$

And address A, B, and C share of rewards become:
$$\texttt{address A: }\frac{250}{250 + 10080 + 2180} = 2\%$$
$$\texttt{address B: }\frac{10080}{250 + 10080 + 2180} = 80.58\%$$
$$\texttt{address C: }\frac{2180}{250 + 10080 + 2180} = 17.42\%$$

#### Remarks

As expected from the formula, LPs owning a bigger share of the pool need to hold a bigger share of the veANGLE supply to significantly increase their boost. Similarly, the smaller the share of the pool owned initially, the bigger the increase in rewards.

Due to all the variables in the boost calculation, it is very tricky to do so manually and users should refer to our calculator on the DAO page.

## Boost Update

For gauges which rely on staking contracts (and not on the offchain script to stream rewards), implementation details are such that a user's veANGLE balance used to calculate the boost is stored at the time of the last action or checkpoint within a liquidity gauge contract. This means that this user's boost could stay higher than it actually is with their current veANGLE balance. It has two main side effects.

On the one hand, after locking tokens, users need to call the **deposit, withdraw (with amount > 0), or user_checkpoint() functions** from the liquidity gauge (staking contract) to apply or update their veANGLE balance and boost. It’s therefore more gas efficient to lock ANGLE before depositing liquidity into a gauge.

On the other hand, as the voting power decreases with time, the liquidity gauge keeps considering the original, higher veANGLE balance than what users actually have, giving them a higher boost than they should. Therefore, it's at their advantage to apply a boost and do no further actions until they vote-lock more tokens.

However, once the vote-lock expires, everyone can “kick” users by creating a checkpoint for that address and, essentially, resetting their actual voting power and boost.

{% hint style="info" %}
For more details on boosting, Curve has written [some docs](https://curve.readthedocs.io/dao-gauges.html) about it too. The formula used by Curve is put differently than we put it here but the outputs are exactly the same.
{% endhint %}
