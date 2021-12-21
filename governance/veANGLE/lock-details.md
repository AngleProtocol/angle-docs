---
description: Details about the veANGLE lock
---

# 🔒 veANGLE lock details

## Non-transferrable tokens

The first thing to keep in mind when locking ANGLE into veANGLE is that veANGLE are **non-transferrable by design**. Once an address owns veANGLE, it can't transfer or sell them in any way.

## Decreasing veANGLE balance

After an address starts owning veANGLE, its balance will decrease with time to reflect the lock time expiration.

## Formula

Depending on the lock time, a specific amount of veANGLE will be received from the ANGLE locked. The lock scale is as follows:

- 1 ANGLE locked 4 years → 1 veANGLE
- 1 ANGLE locked 2 years → 0.5 veANGLE
- 1 ANGLE locked 1 year → 0.25 veANGLE

The general formula to compute the veANGLE balance at any point in time:

$$
Q_{\texttt{veANGLE}} =
\frac{\texttt{lock time remaining in seconds}}{4\times365\times24\times3600}
\times Q_{\texttt{ANGLE locked}}
$$

For example, 12 ANGLE locked for 2 year and 8 months (with 30d/month) would give:

$$
Q_{\texttt{veANGLE}} =
\frac{(2\times12 + 8)_{m}
\times30_{d}\times24_{h}\times3600_s}{4\times365\times24\times3600}
\times 12
$$

$$
Q_{\texttt{veANGLE}} =
\frac{960}{1460} \times 12 =
7.8904
$$

As said above, the quantity of veANGLE decreases constantly with time to reflect the reduction in lock time (lock expiration), down to 0 at expiration. For example, two months after the initial lock, the previous address would have a veANGLE balance of:

$$
Q_{\texttt{veANGLE}} =
\frac{900}{1460} \times 12 =
7.3973
$$
