---
description: How to get stEUR using the Angle app
---

# 💰 Get stEUR

[stEUR](../../../savings/README.md) is a staked version of EURA earning a native Euro yield paid in EURA.

In this guide, we explain how you can use the Angle app to start being exposed to this yield.

{% hint style="info" %}
For a high level overview of how stEUR works, you can check [this video](https://www.youtube.com/watch?v=9LKDbLzNYdU).
{% endhint %}

## Swapping or Staking to stEUR

While stEUR can only be minted by staking (without slippage) EURA in a contract, the [Angle app](https://app.angle.money/savings) enables getting stEUR from any token.

What happens under the hood is that the app page to get stEUR integrates Odos routing technology to make the trades from any token to stEUR efficient.

When coming with EURA, the app modal remains the same (and displays slippage elements) even though this is not relevant for EURA<->stEUR trades. So you can disregard this information in the case where your input token is EURA.

![Getting stEUR from EURA](/.gitbook/assets/stEURScreen.png)

Note that the exchange rate between EURA and stEUR:

- is not 1 to 1 and increases over time. So it's normal if the app shows less than 1 stEUR for EURA provided
- depends on the chain on which you're doing the trade. The value of stEUR is not uniform across all chains.

If you want more details on how Odos swaps work within the context of Angle app, check out [this guide](./swap.md) about getting EURA.

## Unstaking

Like for the staking part, the app enables, using Odos technology, unstaking stEUR to EURA and in the same transaction swapping it to any token of your choice.

As there is no lock-up on the stEUR contract, unstaking can be done at any time and without any prior notice without giving away any of the yield accumulated.

## Estimating potential earnings

The app provides some additional info to all EURA stakers. If you want to estimate how you could be earning from an amount of EURA staked or from any token swapped to stEUR, just input this amount, and the app will show you how it's going to impact your yearly earnings.

![Estimate your earnings with Angle App](/.gitbook/assets/stEURAnalytics.png)
