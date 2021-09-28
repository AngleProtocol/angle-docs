---
description: Selling governance tokens against the protocol's stablecoins
---

# 🧮 Bonding Curve

## 🔎 TL;DR

* It is going to be possible to buy Angle's governance tokens through a bonding curve using the protocol's stablecoins.
* The more tokens are bought from the bonding curve, the more expensive it gets to buy new tokens.

## 💡 Need for a Bonding Curve

Angle leaves the possibility to buy governance tokens using the protocol's stablecoins. For instance, it will be possible to buy ANGLE tokens using Angle's agEUR, or Angle's agUSD.

The stablecoins used to buy the governance tokens will be burnt. This is hence a way to directly increase the protocol's collateral ratio, to get some surplus for the protocol and to reduce risk.

{% hint style="info" %}
The bonding curve may not be directly activated at protocol launch.
{% endhint %}

## 🏷️ Price for the Governance Tokens

The price at which these tokens will be bought will evolve depending on the quantity of tokens that has already been sold by the bonding curve and it will diverge to infinity as all tokens are sold.

The curve will have the following shape:

$$
\texttt{current price} = \frac{\texttt{start price}}{(1-\frac{\texttt{amount sold}}{\texttt{total amount to be sold}})^2}
$$

The more tokens would have been sold, the more expensive it is going to be to buy new tokens.

If someone wants to buy a quantity `x` of ANGLE, then the price this person would have to pay is the integral of the price for amount sold varying between current amount sold and current amount sold + `x`:

$$
\frac{\texttt{start price}\times \texttt{amount to sell}^2}{\texttt{amount to sell} -\texttt{amount sold} -x} - \frac{\texttt{start price}\times \texttt{amount to sell}^2}{\texttt{amount to sell} -\texttt{amount sold}}
$$

## 📑 Variability of the Parameters

In very few cases, governance will be able to vote and change the start price \(and/or\) the total amount of governance tokens to sell with this mechanism.

This is mostly going to be the case when the protocol is at risk. To recollateralize the protocol, governance will be able to change the start price and decrease it below market price, to make buying governance tokens from the protocol more attractive to external users. This mechanism is equivalent to Maker's Flop auctions.

