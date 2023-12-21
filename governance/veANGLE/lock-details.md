---
description: Details about the veANGLE lock
---

# 🔒 Lock Details

## Lock specificities

### Non-tranferrable tokens

The first thing to keep in mind when locking ANGLE into veANGLE is that veANGLE are **non-transferrable by design**. Once an address owns veANGLE, it cannot transfer or sell them in any way.

### Single lock per address

On a similar page, each account can only have a single lock duration meaning that a single address cannot lock certain ANGLE tokens for 2 years then another set of ANGLE tokens for 3 years etc. All ANGLE per account must have a uniform lock time.

### Unallocated voting power when increasing lock

When increasing the veANGLE balance by locking more tokens or extending a lock, this new veANGLE balance is not taken into account in the current vote allocation. Be careful to apply this new voting power to the gauges if you want to.

## 📉 Decreasing veANGLE balance

After an address starts owning veANGLE, its balance decreases with time to reflect the lock time expiration. This decrease in veANGLE balance is reflected in real time when voting for gauge rewards, but not in the boost. More info in the [Boost Update](boost.md##Boost-Update) section of the boost page.

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

## Increasing a veANGLE balance

While a veANGLE balance automatically decays over time, there are two ways to increase a veANGLE balance and hereby increase voting power, boost or potential interest received:

- extend the lock expiration date
- add ANGLE to the lock

When increasing the veANGLE balance of an address, its voting power increases accordingly. However, if the address had previously allocated voting power for gauges, you will have to vote again to have your new voting power taken into account.

**Let’s look at it from an example**:

Let’s say that Carol locks 90 ANGLE for 4 years, giving her a balance of 90 veANGLE, and allocates 50% of her votes to Gauge A. This will take into account 45 veANGLE to allocate to Gauge A.

A year later, Carol’s veANGLE balance will have decreased by 25% as the lock expiration gets closer. She will have 0.75 x 90 = 67.5 veANGLE. The voting power allocated to Gauge A is currently 33.75 veANGLE.

Now, Carol decides to push back her lock’s expiration to 4 years again, giving her her original balance of 90 veANGLE back. She also adds 10 ANGLE to the lock, such that she has a 100 veANGLE balance.

Her voting power is now 100 veANGLE. **However,** only 33.75 of her total veANGLE balance is currently allocated to Gauge A. She needs to re-apply her votes for the balance increase to take effect.

If she wants to put 50% of her 100 veANGLE balance on Gauge A, she needs to do another voting transaction, allocating 50% to Gauge A. This new voting tx will take into account the new 100 veANGLE balance, and allocate half to this gauge.

If she had allocated all her voting power on multiple gauges, she would have to re-apply all of these votes with the new weights she wants to allocate.

{% hint style="info" %}
Votes on each gauge can be changed only every 10 days.
{% endhint %}

## 🤍 veANGLE Governance Whitelisting

Smart contracts & DAOs require whitelisting by governance to lock ANGLE for veANGLE. Only externally owned accounts (EOA) can directly call the veANGLE stake locking function.

In order to have your protocol or DAO own veANGLE, you can begin the governance process with the ANGLE community in the [governance forum](https://gov.angle.money) by submitting a whitelisting proposal.
