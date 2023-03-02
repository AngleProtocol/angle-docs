---
description: Guide for people using Merkl to incentivize pools
---

# 💰 Incentivizor Guide

DAOs or individuals looking to incentivize a pool can use Merkl and customize their distribution to get the desired type of liquidity.

Incentives can be placed on [this app](https://merkl.angle.money) or directly from the [`DistributionCreator` contract](helpers.md) on the chain of your choice (check out the example script [here](integration-guide.md#send-rewards-to-pools)).

Regardless of the method you are using, before depositing an incentive, make sure that you have read the disclaimer for incentivizors. The `DistributionCreator` contract will require you to sign this disclaimer and post your signature on-chain.

{% content-ref url="incentivizor-tc.md" %}
[incentivizor-tc.md](incentivizor-tc.md)
{% endcontent-ref %}

## 💻 On [merkl.angle.money](https://merkl.angle.money)

You just need to fill the address of the pool you want to incentivize, the address of the reward token and the amount of rewards to send over the chosen duration of the distribution.

{% hint style="info" %}
Reward tokens need to be whitelisted before being used, and for whitelisted tokens, there is a minimum amount that needs to be sent for distributions to be considered valid. If the reward token you want to use has not been whitelisted, send us a message on the Merkl channel of the [Angle Discord server](https://discord.gg/ByFYzSUt).
{% endhint %}

If some smart contract addresses need to be excluded from the distribution, make sure to add them as well.

Merkl natively and automatically supports [different liquidity position managers](helpers.md) on which people can provide liquidity and still be rewarded. Note though that supported liquidity position managers (like Gamma or Arrakis) may not automatically deploy an instance on every pool, so you may want to check which of the supported liquidity position managers are technically available for your pool.

Then, you can customize any any of the distribution formula parameters can be customized. When this is done, the app will prompt you to sign the disclaimer message (if it has not already been done), and then to post the transaction sending the tokens to the distribution contract!

Any address holding a position or a position manager token will be able to claim their rewards at the end of each epoch according to how they provided liquidity on the pool.

![Merkl Script](/.gitbook/assets/docs-merkl-for-distributors.png)
