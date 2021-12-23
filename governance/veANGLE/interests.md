---
description: How protocol interests are redistributed to veANGLE owners
---

# 📈 Interests for veANGLE holders

## 🔎 TL;DR

- One benefit of owning veANGLE is the redistribution of part of the interests earned by the protocol.
- Until the Angle Governance upgrade, the interests generated were redistributed to SLPs as profit, and to the protocol as surplus/reserve.
- Now, they are also shared to veANGLE holders as an incentive for taking part in the governance of the protocol.

![Angle Interests Redistribution](../../.gitbook/assets/angle-interests-redistribution.png)

## 💝 Interests redistribution

### Share of interests for veANGLE holders

The share of interests redistributed to veANGLE holders is a parameter that can be set and updated by Governance. The idea is that this parameter should be high enough to bring added value to veANGLE holders, but not too high to damage the reserves being built by the protocol and the yield earned by SLPs.

### Redistribution

The protocol will distribute interests in the form of Angle tokens, beginning by redistributing sanUSDC_EUR.

In practice, if the redistribution of interests to veANGLE token holder is at 30%, here is what is going to happen:

- 30% of all interests generated will be converted to USDC. For instance, interests accumulated under the form of FEI, FRAX and DAI will be swapped to USDC.
- The USDC will be deposited into the protocol against sanUSDC_EUR
- The sanUSDC_EUR will be redeemable by veANGLE holders

### ⏲️ Timeline

Fees are going to be distributed weekly. The porportional amount of fees that each user is to receive is calculated based on their veANGLE balance relative to the total veANGLE supply.

This amount is calculated at the start of the week. The actual distribution occurs at the end of the week based on the fees that were collected. As such, a user that creates a new vote-lock should expect to receive their first fee payout at the end of the following epoch week.

The available sanUSDC_EUR balance to distribute is tracked via something that is called the “token checkpoint”. This is updated at minimum every 24 hours. Fees that are received between the last checkpoint of the previous week and first checkpoint of the new week will be split evenly between the weeks.

## 💱 Swap Process

As mentionned above, all profits of the protocol are converted into USDC before being deposited in the protocol as sanUSDC_EUR.

The protocol has implemented its own process and smart contracts to handle the conversion: this is handled on a per-coin basis.

What has been implemented so far is conversions using UniswapV3 swaps as well as UniswapV2 and Sushiswap swaps.

Such swaps can only be performed by trusted addresses as it could lead people to front-run the protocol for swaps and plan for elaborate sandwich attacks.
