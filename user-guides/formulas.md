---
description: List of formulas used in the Angle protocol and at app.angle.money
---

# Formulas

## Perpetuals (HA)

### Maintenance Margins

- DAI: 0.625%
- USDC: 0.625%
- FEI: 0.625%
- FRAX: 0.625%

**Margin Ratio Formula**
In Angle, the margin ratio is computed as:

$$
marginRatio = \frac{cashOutAmount}{positionSize}
$$

### Leverage

In Angle, **leverage** is computed as:

$$leverage = \frac{(margin + position Size)}{margin}$$

**Example**

- Margin: 10,000 DAI
- Position size: 100,000 DAI

$$leverage = \frac{1 + 10}{1} = 11 $$

### Cash Out Amount

The Cash Out Amount represents the amount you should receive in your wallet after closing the perpetual:

$$cashOutAmount = initialMargin \pm grossPnL - closingFee $$

With $grossPnL = positionSize\times(1-\frac{initialPrice}{currentPrice})$

### PnL

The PnL displayed on the app represents the gain or loss you would make if closing the position. It is computed **net** of fees.

$$ PnL = cashOutAmount - initialMargin $$
$$ PnL = grossPnL - closingFee $$

### Est. APR on open positions

_In perpetuals/open position page of the app_

ANGLE rewards for position holders depends on the Position Size, as what matters for the protocol is how much collateral is hedged. However, the APR is computed from the initial margin, as this is what users bring to the protocol.

**Example:**

- Margin: 10,000 DAI
- Position Size: 100,000 DAI
- Leverage: 11
- Rewards distribution: 5 ANGLE / week / 1,000 DAI in position
- ANGLE price: 0.80 DAI

$$

APR =
\frac{5\times{52}
\times{100}
\times{0.80}}
{10,000}


$$

$$ APR = 2.08 = 208\% $$

## Depositing Liquidity (SLP)

_In the Yield page of the app_
_Both the Slippage and SlippageFee can vary depending on the collateral/stablecoin pair._

### Slippage

SLP can face a slippage when withdrawing funds depending on the collateral ratio of the pool they are withdrawing from. This is put in place to incentivize them to stay in the protocol while it gets re-collateralized.

The current slippage for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _Slippage_ in the _Fee Info > SLP_ section.

### Slippage on Fees for SLP

When the protocol gets close to be under-collateralized, it progressively keeps a bigger portion of the fees usually going to SLPs to grow the suplus and be able to pay back stable holders. Note that this doesn't impact the initial deposits of SLPs nor the fees earned up until the start of the slippageFee.

The current slippageFee for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _SlippageFee_ in the _Fee Info > SLP_ section.

## Global parameters

If you want to know the current protocol parameters in place, you can have a look at the analytics at [analytics.angle.money](https://analytics.angle.money) or directly in the [SDK](https://github.com/AngleProtocol/angle-sdk).

$$
$$
