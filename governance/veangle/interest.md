---
description: How protocol interest are redistributed to veANGLE owners
---

# 📈 Interest

## 🔎 TL;DR

* One benefit of owning veANGLE is the redistribution of part of the interest earned by the protocol.
* Until the Angle Governance upgrade, the interest generated were redistributed to SLPs as profit, and to the protocol as surplus/reserve.
* Now, they are also shared to veANGLE holders as an incentive for taking part in the governance of the protocol.

![Angle Interests Redistribution](../../.gitbook/assets/angle-interests-redistribution.png)

## 💝 Interest redistribution

### Share of interest for veANGLE holders

The share of interest redistributed to veANGLE holders is currently at 50%, and can be updated by Governance. The idea is that this parameter should be high enough to bring added value to veANGLE holders, but not too high to damage the reserves being built by the protocol and the yield earned by SLPs.

### Redistribution

The protocol distributes interest in the form of tokens native to Angle, beginning with sanUSDC\_EUR.

In practice, the redistribution of interest to veANGLE token holder is currently at 50%. Here is how it is happening:

* 50% of all interest generated are converted to USDC. For instance, interest accumulated under the form of FEI, FRAX, DAI, and ETH are swapped to USDC.
* The USDC are deposited into the protocol against sanUSDC\_EUR.
* The sanUSDC\_EUR are then redeemable by veANGLE holders according to the distribution detailed below.

### ⏲️ Timeline

Fees are going to be distributed weekly. The proportional amount of fees that each user is to receive is calculated based on their veANGLE balance relative to the total veANGLE supply.

This amount is calculated at the start of the week. The actual distribution occurs at the end of the week based on the fees that were collected. As such, users that create a new vote-lock should expect to receive their first fee payout at the end of the following epoch week.

The available sanUSDC\_EUR balance to distribute is tracked via something that is called the “token checkpoint”. This is updated at minimum every 24 hours. Fees that are received between the last checkpoint of the previous week and first checkpoint of the new week are split evenly between the two weeks.

## 💱 Swap Process

As mentionned above, all profits of the protocol are converted into USDC before being deposited in the protocol as sanUSDC\_EUR.

The protocol has implemented its own process and smart contracts to handle the conversion: this is handled on a per-coin basis.

What has been implemented so far is conversions using a mix of UniswapV3, UniswapV2, and Sushi swaps.

Such swaps can only be performed by trusted addresses as it could lead people to front-run the protocol for swaps and plan for elaborate sandwich attacks.
