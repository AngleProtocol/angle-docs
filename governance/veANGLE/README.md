---
description: Locked ANGLE that provides multiple benefits
---

# ♠️ veANGLE

## Background

veANGLE stands for "voting-escrowed" ANGLE. After the Angle Governance upgrade, the veANGLE will become the new governance token of the Angle Protocol.&#x20;

It is a vesting and yield system based off of Curve’s veCRV and Frax's veFXS mechanisms. The key property of veANGLE, beyond being a governance token, is that it is not a transferable token and it does not trade on liquid markets.

{% hint style="info" %}
The implementation of veANGLE is underway and hasn't been implemented yet. It is expected for January 2022. This docs tries to explain how the model works in practice.
{% endhint %}

## 🧾 veANGLE Features

veANGLE can be obtained by locking ANGLE from 1 week to up to 4 years. A smaller balance of veANGLE is obtained when locking for a shorter time. veANGLE balances decrease linearly with time to reflect the reduction in lock-time, approaching 0 veANGLE when lock time is about to end.

As mentionned above, veANGLE will become the token used for voting on the Angle protocol for governance proposals and ANGLE emissions through gauge weights. As such, veANGLE holders will be shaping the future of the protocol.

To facilitate the voting process, the governance module of the protocol will change after the upgrade. Votes for governance proposals will happen on [Snapshot](https://snapshot.org/#/anglegovernance.eth), and will then get executed by a multi-sig. This multi-sig will be composed of a mix of core team members and external people, including public figures if possible (anon or not) to increase accountability.

{% hint style="info" %}
Votes for gauge weights will however take place on-chain. For more details on gauges, please refer to [this page](gauges.md).
{% endhint %}

Beyond **voting** on governance proposals and gauge weights, veANGLE is useful in two main aspects:

* ****[**Boosting** ANGLE rewards](boost.md) when providing liquidity to a gauge
* ****[**Earning** a share of the interests](interests.md) generated by the protocol

## 😎 veANGLE Benefits for the protocol

The veANGLE system is modular and all-purpose. In the future, it can evolve in many different ways like by earning additional yield in new places/features, or be treated as a governance token bond rate of sorts.

It is designed to benefit the ANGLE system as a whole by:

* Allocating voting power to long-term holders of ANGLE through veANGLE
* Incentivizing farmers to stake (or lock, both are used equivalently) ANGLE
* Creating a bond-like utility for ANGLE and create a benchmark APR rate for staked ANGLE

For more details on the benefits of the veANGLE model and its design, you can refer to the articles of the ANGLE Upgrade Series published on Angle's [blog](https://blog.angle.money):

* [Part 1: Introducing locked ANGLE tokens and their advantages for the protocol](https://blog.angle.money/angle-upgrade-series-part-1-introducing-locked-angle-tokens-and-their-advantages-for-the-protocol-cd4340f7654a)
* [Part 2: Incentives for veANGLE holders](https://blog.angle.money/angle-upgrade-series-part-2-incentives-for-veangle-holders-9c43051b9a0)

## Next ➡️

The following pages explain in more detail how the essential features of the veANGLE system work.