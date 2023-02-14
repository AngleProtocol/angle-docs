---
description: Guide for people using Merkl to incentivize pools
---

# 💰 Incentivizor Guide

DAOs or individuals looking to incentivize a pool can use Merkl and customize their distribution to get the desired type of liquidity.

Incentives can be placed on [this app](https://merkl.angle.money) or directly from the `DistributionCreator` contract on the chain of your choice (addresses [here](helpers.md)).

Regardless of the method you are using, before depositing an incentive, make sure that you have read the disclaimer for incentivizors. The `DistributionCreator` contract will require you to sign this disclaimer and post your signature on-chain.

{% content-ref url="incentivizor-tc.md" %}
[incentivizor-tc.md](incentivizor-tc.md)
{% endcontent-ref %}

## 💻 On [merkl.angle.money](https://merkl.angle.money)

You just need to fill the address of the pool you want to incentivize, the address of the reward token and the amount of rewards to send over the chosen duration of the distribution.

{% hint style="info" %}
Reward tokens need to be whitelisted before being used, and for whitelisted tokens, there is a minimum amount that needs to be sent for distributions to be considered valid. If the reward token you want to use has not been whitelisted, send us a message on the Merkl channel of the [Angle Discord server](https://discord.gg/ByFYzSUt).
{% endhint %}

If liquidity positions manager need to be included in the distribution, check whether they are supported for the AMM you are incentivizing [on this page](helpers.md), and then specify the address of the wrapper contract (address of the Arrakis token for instance).

Then, you can customize any any of the distribution formula parameters can be customized. When this is done, the app will prompt you to sign the disclaimer message (if it has not already been done), and then to post the transaction sending the tokens to the distribution contract!

Any address holding a position or position manager token will be able to claim their rewards at the end of each epoch according to how they provided liquidity on the pool.
