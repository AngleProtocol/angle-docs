---
description: Your official source of info for everything regarding the Merkl platform.
cover: ../../.gitbook/assets/merkl-cover.jpg
coverY: 0
---

# 🥨 Merkl

Merkl is a mechanism to incentivize Uniswap V3-like liquidity positions in a flexible and efficient way. It is built and maintained by Angle Labs, but is separate from the Angle Protocol.

In essence, Merkl is a platform where Liquidity Providers (LPs) on concentrated liquidity pools can receive token rewards from people incentivizing liquidity (incentivizors) in a tailored way.

Incentivizors enjoy **a full flexibility** on how they distribute their incentives: they can choose to favor LPs who bring more liquidity of one token, or those who have set tighter ranges than others. They can also select whether they want to incentivize out of range liquidity or not, and if they want some holders of a specific token to earn boosted rewards.

![Merkl Improvements](../../.gitbook/assets/improve-reward-mechanism.png)

{% hint style="info" %}
Merkl accepts incentives of any ERC-20 token on any pool of the supported AMMs. For the list of chains and AMMs supported by Merkl (along with other info for each chain), check out [this page](helpers.md).
{% endhint %}

Earning rewards on Merkl incurs **no risk of funds** and requires no specific smart contract interactions for LPs: they can retain the custody of their liquidity while receiving rewards. They can also customize their positions to maximize their earnings from fees and incentives, enjoying all possibilities enabled by concentrated liquidity type of AMMs.

Merkl is compatible with [liquidity position managers](helpers.md) like [Gamma](https://app.gamma.xyz) or [Arrakis](https://www.arrakis.finance). This means that it's possible to provide liquidity via Gamma on a pool and to be rewarded without taking any further action (no need to stake the Gamma or Arrakis token). **As such, using Merkl to incentivize a pool is perfectly equivalent to incentivizing an Arrakis or a Gamma token directly. It's even better in the sense that users don't have to stake their tokens when using Merkl.**

Merkl has a low maintenance fee applied to incentives distributed. Excluding gas when claiming rewards, there is no cost to use the platform for Liquidity Providers.

## ⚙️ Mechanism

Merkl is based on an off-chain script that looks at the on-chain data of the incentivized pools. It then computes the rewards for all LPs of these pools according to the preferences of the incentivizor. Based on this, the script aggregates all reward distribution data in a Merkle tree, then compressed it into a Merkle root and pushes on-chain to allow LPs to claim their rewards.

The script is ran regularly for the period between when it is executed and its last execution. Every time the script is ran, it only looks at the on-chain data related specifically to this period of time.

![Merkl Script](../../.gitbook/assets/docs-merkl-script.png)

### 💪 Customizable Distribution Formula

Precisely speaking, for a given pool with two tokens (A and B), the script looks into the swaps that took place on the pool during the period for which it is ran and computes a reward score for each position according to:

- the fees earned by the position during the period, which represent the liquidity of the position used by the pool
- the amount of token A held by the position during swaps on the pool compared to the total amount of token A in the pool
- the amount of token B held by the position during swaps on the pool compared to the total amount of token B in the pool

A different weight, chosen by the incentivizor, is attributed to each parameter. On top of that, incentivizors can further customize the distribution of the rewards for the pool by optionally allowing addresses holding a specific token (veANGLE or veCRV for example) to earn boosted rewards.

The exact distribution formula for a position in such a pool during a time period is as follows:

$$
[w_{\texttt{fees}} \times \frac{\texttt{fees by position}}{\texttt{fees by pool}}+ w_{\texttt{A}} \times \frac{\texttt{A in position}}{\texttt{A in pool}}+ w_{\texttt{B}} \times \frac{\texttt{B in position}}{\texttt{B in pool}} ] \times \texttt{optional gov token boost}
$$

{% hint style="info" %}
For big pools with a lot of swaps, the script may not look at data from all the swaps that occurred during the given time period, but only sample the biggest of them.
{% endhint %}

### 🧳 Liquidity Position Managers

As detailed in the introduction, Merkl is compatible with liquidity position managers actively maintaining positions for LPs on concentrated liquidity AMMs. The way the script works for such managers (or wrappers) is that it does not differentiate managers from other "normal" addresses when computing rewards. It then splits the rewards going to the position manager address proportionally between all holders of its token.

With Merkl, if you incentivize a pool that is compatible with one of the liquidity managers supported by the system, it should be automatically detected by the script and users indirectly providing liquidity through those position managers will be able to directly claim their rewards from Merkl contracts.

As the system is off-chain, new types of position managers can easily be added into the system. For instance, it would be possible to reward users of protocols that use position manager tokens on other contracts, as a collateral to borrow for example.

{% hint style="info" %}
The list of liquidity position managers supported for each AMM and chain can be found on [this page](helpers.md). If you want to add support for a type of liquidity position manager that is not supported or directly reward the underlying users of a smart contract that indirectly controls AMM liquidity, drop a message on the Merkl channel of the [Angle Discord server](https://discord.gg/ByFYzSUt).
{% endhint %}

#### Blacklist and LP contracts unable to claim rewards

If there is a liquidity manager or another smart contract not natively supported by Merkl that holds LP tokens of the pool you are incentivizing, it will be eligible to rewards like any other liquidity provider. If the contract is not able to deal with token rewards (by forwarding them to another address distributing it to underlying stakeholders for example), then these rewards may be lost. If rewards sent through Merkl remain unclaimed for a period of more than 1 year, we reserve the right to recover and redistribute them.

To avoid this kind of situation, the Merkl system lets you blacklist addresses which should be excluded from the reward distribution. If 10 tokens of a distribution should go to a blacklisted LP address, they will be split between the other LPs.

### ⏳ Distribution Epochs

The time periods (also called epochs) over which the script is ran for all the pools of a chain vary depending on the chain. Epoch lengths basically range between 2 hours to 3 days.

{% hint style="info" %}
You can find the epoch length for each chain [here](helpers.md).
{% endhint %}

The length of an epoch is also the de facto amount of time between two reward distributions. For instance, if epoch length is 1 day for Ethereum, then Uniswap V3 LPs can claim new rewards at most every day on Merkl.

As Merkl's script aggregates all the pools on all supported AMMs for a chain, liquidity providers on different pools across different platforms on the same chain can claim all their rewards once at the end of every epoch.

In addition, as the system relies on a single Merkle root to handle distribution per chain, liquidity providers can claim all their token rewards (from potentially different pools on virtually many concentrated-liquidity AMMs) in just one transaction.

Note that the script is compatible with multiple incentivizors incentivizing LPs of the same pool, potentially with different parameters. If you are providing liquidity on a pool, you will claim from all the incentivizors who incentivized the pool when claiming your rewards. In other words, many teams can incentivize the same pool at the same place.

There is no need for liquidity providers to claim rewards at every epoch. Every Merkle Tree update takes into account the previous state of the reward tree and just adds new rewards on top (which is then reflected in the published Merkle root). Unclaimed rewards for an epoch can be claimed at any time in the future, along with all the rewards distributed in between.

### 🤺 Dispute Periods

The script computing rewards and updating the reward Merkle root on-chain is ran by Angle Labs. Merkle roots pushed on-chain are based on off-chain computations from on-chain data. Anyone can fetch the on-chain data required to run the script and verify the results sent.

To allow anyone to permissionlessly verify that the system is working properly, and to reduce the system's exposure to potential hacks or failures, every new Merkle root update is followed by a dispute period. A new Merkle root that aggregates reward distribution data for a chain is only effective after this dispute period.

Anyone can contest the result of a distribution during the dispute period. A dispute can be triggered by sending a pre-defined amount of `disputeToken` (most likely agEUR) to the contract distributing rewards. During a dispute, the Merkle root of the distribution contract is frozen to its last valid version. Disputes can then either be considered as valid, in which case the disputer is refunded and the disputed Merkle root is revoked, or invalid. If it is invalid the disputer loses its funds and the dispute period is restarted from scratch (which means the disputed tree is still not considered valid).

Dispute token, amount, and length can be obtained by directly querying the contract handling reward distribution on the chain of interest.

### ⚱️ Fee Structure

Merkl is free to use for liquidity providers claiming rewards. There is a maintenance fee of 3% applied to incentives that are sent by incentivizors.

This fee can be waived for pools which contain some specific approved tokens. In particular, there are no fees for incentives sent to pools which have agEUR.

## Resources

### 📖 Guides

Merkl is a solution any DAO or protocol can use to incentivize liquidity, and any liquidity provider can tap into to earn extra incentives without having to take any action after depositing liquidity in a pool.

Pools supported by Merkl are all listed at [merkl.angle.money](https://merkl.angle.money). Incentives on pools can also be deposited from there.

The system for depositing incentives and claiming rewards **can be easily integrated on any dApp**. [This guide](integration-guide.md) explains among other things how to list the liquidity pools of your choice on your dApp and how to build claim transactions for your users.

If you simply want to use Merkl, check out these guides to [make the best of Merkl as a liquidity provider](lp-guide.md) or to [distribute incentives](incentivizor-guide.md) with the system.

### Audits

Merkl smart contracts have been audited by Code4rena. Find the audit reports [here](https://code4rena.com/reports/2023-06-angle).

### 🔗 Links

- [Merkl App](https://merkl.angle.money)
- [Smart contracts addresses](helpers.md#smart-contracts)
- [Smart contracts code](https://github.com/AngleProtocol/merkl-contracts)
- [Disclaimer for incentivizors](incentivizor-tc.md)
