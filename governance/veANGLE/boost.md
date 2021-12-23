---
description: How veANGLE can boost ANGLE rewards for LPs
---

# 💥 Boost

## 🔎 TL;DR

* Liquidity providers staking on Angle can boost their ANGLE rewards by holding veANGLE.
* This boost can represent up to to x2.5 the base rewards an address without any veANGLE could get.
* To compute the boost, the total veANGLE supply of an address is applied to all the contracts this address is staking on.

## 🚜 Farming Boost

Holding veANGLE will give users more weight when collecting certain farming rewards. A big majority of the farming rewards that are distributed directly through the protocol are eligible for veANGLE boosts.

One notable exception is that of the rewards given to hedging agents taking part in Angle Perpetual contracts.

Besides, external farming that are promoted by other protocols (such as Sushi Onsen) or that are available on other chains are typically not available for veANGLE boosts since they are independent of the mainnet Angle protocol itself.

{% hint style="info" %}
A user's veANGLE boost does not increase the overall emission of rewards. The boost is an additive boost that is added to each farmer's yield proportional to their veANGLE balance.
{% endhint %}

## 🧮 Boost Computation

Angle forked its staking contract model (also called liquidity gauge) from Curve which has a similar boost system.

Basically, this staking contract considers that an address holding veANGLE is providing more liquidity than it really is.

In a given gauge, owning veANGLE will increase a LP's share of the pool thus increasing the rewards received. As usual, LPs holding no veANGLE are considered as providing 100% of their liquidity. If an address owns enough veANGLE, the contract can consider that it brings up to 250% its original liquidity, or a x2.5 boost compared to the original 100%.

Then, this x2.5 multiplier in liquidity provided will translate into a boost on rewards depending on the total liquidity provided in the pool and how it is considered by the boost calculator.

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
\begin{equation} \min(x_{lp} + 1.5\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}}, 2.5 \times x_{lp}) \end{equation}
$$

An address owning 0 veANGLE will get rewarded as usual.&#x20;

To get the max possible boost on rewards, an address needs to get 100% of its provided liquidity taken into account by the protocol. This is equivalent to having the term on the left greater or equal than the value of the liquidity provided:

$$
\begin{equation} x_{lp} + 1.5\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}} \geq 2.5 \times x_{lp} \end{equation}
$$

$$
\begin{equation} \cancel{1.5}\times tot_{lp}\times \frac{x_{veANGLE}}{s_{veANGLE}} \geq \cancel{1.5} \times x_{lp} \end{equation}
$$

$$
\begin{equation} \frac{x_{veANGLE}}{s_{veANGLE}} \geq \frac{x_{lp}}{tot_{lp}} \end{equation}
$$

$$
\begin{equation} \texttt{Share of veANGLE supply} \geq \texttt{Share of liquidity in the pool} \end{equation}
$$

**An address having a higher share of the total veANGLE supply than its share of liquidity provided in the pool for which the boost is being computed will be considered as having x2.5 more liquidity than an address with no veANGLE.**

All gauges therefore have different requirements meaning some pools are easier to boost than others. In the end, it all depends on how much others have locked and how much the liquidity gauge has.

### Examples

Now that we understand how veANGLE holders get a boost on capital compared to non-holders, let’s look at how this translates into an **actual boost on rewards received.**

**Example 1:** One holder of veANGLE with a big share of the pool:

* Address A and B are providing 100 of liquidity each in pool P.
* They are receiving 50% of the rewards each.

Now, let’s say that A owns the total supply of veANGLE.

* The boost calculator now considers that A brings $$2.5  \times100 = 250$$ of liquidity to the pool.
* Address A now owns $$\frac{250}{250+100} = 71.5\%$$ of the pool, and address B 28.5%.
* Address A rewards multiplier is at x1.43 (from 50% to 71.5%).

**Example 2:** Two holders of veANGLE, with very different shares of the pool.

* Now say that address A provides 100 and address B 9900.
* If none of them hold veANGLE, they are respectively earning 1% and 99% of the rewards.
* Now let’s consider that A owns 1% or more of the veANGLE supply (i.e. as much as or more than its share of the pool).
* Again, the boost calculator now considers that it brings $$2.5  \times100 = 250$$ of liquidity to the pool.
* Therefore, address A is now earning $$\frac{250}{250+9900} = 2.46\%$$ of the rewards, or a x2.46 multiplier.
* On the other hand, if B, which owns much more liquidity than A, had 1% of the veANGLE supply as well, its considered liquidity would go from 9900 to: $$9900 + 1.5 \times 10,000 \times 1\% = 10050$$.
* Its share of earnings would go from 97.54% to $$\frac{10050}{250+ 10050} = 97.57\%$$.

#### Remarks

As expected from the formula, LPs owning a bigger share of the pool need to hold a bigger share of the veANGLE supply to significantly increase their boost. Similarly, the smaller the share of the pool owned initially, the bigger the increase in rewards will be.

Due to all the variables in the boost calculation, it is very tricky to do so manually and users should refer to our calculator on the DAO page.

## Boost Update

Implementation details are such that a user gets the boost at the time of the last action or checkpoint within a liquidity gauge contract.&#x20;

On the one hand, after locking tokens, to apply or update a boost users need to **deposit, withdraw, or claim** from the liquidity gauge. It’s therefore more gas efficient to lock ANGLE before depositing liquidity into a gauge.

On the other hand, since the voting power decreases with time, it is favorable for users to apply a boost and do no further actions until they vote-lock more tokens.

However, once the vote-lock expires, everyone can “kick” the user by creating a checkpoint for that user and, essentially, resetting the user to no boost if they have no voting power at that point already.

{% hint style="info" %}
For more details on boosting, Curve has written [some docs](https://curve.readthedocs.io/dao-gauges.html) about it too. The formula used by Curve is put differently than we put it here but the outputs are exactly the same.
{% endhint %}
