---
description: Locked ANGLE that provides multiple benefits
cover: ../../.gitbook/assets/VEANGLE-cover.jpg
coverY: 0
---

# ♠ veANGLE

## Background

veANGLE stands for "voting-escrowed" ANGLE, and is the governance token of the Angle Protocol.

It is a modular and all-purpose vesting and yield system based off of Curve’s veCRV mechanism. The key property of veANGLE, beyond being a governance token, is that it is non-transferable and it does not trade on liquid markets.

## 🧾 veANGLE Features

veANGLE can be obtained by locking ANGLE from 1 week to up to 4 years. A smaller balance of veANGLE is obtained when locking for a shorter time. veANGLE balances decrease linearly with time to reflect the reduction in lock-time, approaching 0 veANGLE when lock time is about to end and ANGLE locked to be released.

As mentioned above, veANGLE is the token used for [voting for governance proposals](../angle-dao.md) and as such, veANGLE holders are the ones shaping the future of the protocol.

Beyond **voting** on governance proposals, veANGLE are occasionally redistributed a portion of the earnings the protocol makes through its normal activities, or through other operations (e.g. airdrops) as an incentive for taking part in the governance of the protocol. When rewards are distributed to veANGLE holders, this is done proportionally to the veANGLE balance of each address.

{% hint style="info" %}
The history of rewards allocated to veANGLE holders can be found on Angle app [here](https://app.angle.money/lock).
{% endhint %}

## Lock specificities

### Non-tranferrable tokens

The first thing to keep in mind when locking ANGLE into veANGLE is that veANGLE are **non-transferrable by design**. Once an address owns veANGLE, it cannot transfer or sell them in any way.

### Single lock per address

On a similar page, each account can only have a single lock duration meaning that a single address cannot lock certain ANGLE tokens for 2 years then another set of ANGLE tokens for 3 years etc. All ANGLE per account must have a uniform lock time.

### 📉 Decreasing veANGLE balance

After an address starts owning veANGLE, its balance decreases with time to reflect the lock time expiration. This decrease in veANGLE balance is reflected in real time when voting on governance proposals.

### ⚗️ Formula

Depending on the lock time, a specific amount of veANGLE are generated from the ANGLE locked. The lock scale is as follows:

- 1 ANGLE locked 1 year → 0.25 veANGLE
- 1 ANGLE locked 2 years → 0.5 veANGLE
- 1 ANGLE locked 4 years → 1 veANGLE

The general formula to compute the veANGLE balance at any point in time is:

$$
Q_{\texttt{veANGLE}} =
\frac{\texttt{lock time remaining in seconds}}{4\times365\times24\times3600}
\times Q_{\texttt{ANGLE locked}}
$$

It's only at the end of the lock time that it becomes possible to recover the locked ANGLE tokens.

During lock time, users can also increase their veANGLE balance by locking up ANGLE, extending the lock end date, or both.

**Example:** 12 ANGLE locked for 2 years and 8 months (with 30d/month) would give:

$$
Q_{\texttt{veANGLE}} = \frac{(2\times12 + 8)_{m} \times30_{d}\times24_{h}\times3600_s}{4\times365\times24\times3600} \times 12
$$

$$
Q_{\texttt{veANGLE}} = \frac{960}{1460} \times 12 = 7.8904
$$

As detailed above, the quantity of veANGLE decreases constantly with time to reflect the reduction in lock time (lock expiration), down to 0 at expiration. For example, two months after the initial lock, the previous address would have a veANGLE balance of:

$$
Q_{\texttt{veANGLE}} = \frac{900}{1460} \times 12 = 7.3973
$$

### Increasing a veANGLE balance

While a veANGLE balance automatically decays over time, there are two ways to increase a veANGLE balance and hereby increase voting power or potential interest received:

- extend the lock expiration date
- add ANGLE to the lock

When increasing the veANGLE balance of an address, its voting power increases accordingly.

## 🤍 veANGLE Governance Whitelisting

Smart contracts & DAOs require whitelisting by governance to lock ANGLE for veANGLE. Only externally owned accounts (EOA) can directly call the veANGLE stake locking function.

In order to have your protocol or DAO own veANGLE, you can begin the governance process with the ANGLE community in the [governance forum](https://gov.angle.money) by submitting a whitelisting proposal.
