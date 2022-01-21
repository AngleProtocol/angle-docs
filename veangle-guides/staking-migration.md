---
description: Staking migration guide
---

# Staking Migration

With the veANGLE upgrade, some staking contracts of the protocol became irrelevant and new staking cotnracts were deployed meaning liquidity has to be migrated. This includes:

* All sanTokens staking contracts
* Gelato Uniswap agEUR/USDC LP
* Gelato Uniswap agEUR/wETH LP
* SushiSwap agEUR/ANG LP

Rewards to old staking contracts were interrupted on the 19th of January 2021 at 4:30pm UTC, and rewards to new staking contracts started on the 20th of January at 00:00 AM UTC.&#x20;

{% hint style="info" %}
Following [this Snapshot vote](https://snapshot.org/#/anglegovernance.eth/proposal/0xbd5e7b645853f2231626286223a8eca2b7533856b6b5c647426745292825f175), agEUR single-sided staking was removed, and is no longer incentivized by the protocol. New staking contracts involving just agEUR (or lent) should be released in the coming weeks. In the meantime, we encourage people who do not want to pay the gas fees to either wait a little and hold their agEUR or bridge it to other chains to enjoy cheap yield farming opportunities.
{% endhint %}

## Migrating the funds

Stakers will need to take three steps to migrate their funds:

1. Unstake from old contracts in the `Deprecated` section of [this page](https://dao.angle.money/#/stake) of our DAO App. If this section does not appear, it simply means that you have nothing to unstake from the old staking contracts.
   * Optional: Lock ANGLE into veANGLE (required to get an APR boost when staking on the new contracts)
2. Click on `All` in [the new staking page](https://dao.angle.money/#/stake) to see all available staking contracts
3. Approve new contracts
4. Stake on new contracts
