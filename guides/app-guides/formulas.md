---
description: List of formulas at on app.angle.money
---

# Formulas

## Trade Perpetuals (Hedging Agents)

### Margin

The margin displayed on your position is computed net of opening fees, i.e.

$$
\texttt{margin} = \texttt{initial margin - position size} \times \texttt{opening fees}
$$

### Leverage

In Angle, **leverage** is computed as:

$$\texttt{leverage} = \frac{\texttt{(margin + position Size)}}{\texttt{margin}}$$

#### Example

- Margin: 10,000 DAI
- Position size: 100,000 DAI

$$\texttt{leverage} = \frac{1 + 10}{1} = 11 $$

### Cash-out Amount

The Cash-out amount represents the amount you should receive in your wallet after closing the perpetual:

$$\texttt{cash-out amount} = \texttt{margin} \pm \texttt{gross PnL - closing fee} $$

With $$\texttt{grossPnL} = \texttt{position size}\times(1-\frac{\texttt{initialPrice}}{\texttt{currentPrice}})$$

### Profit & Loss (or PnL)

The PnL displayed on the app represents the gain or loss you would make if closing the position. It is computed **net** of fees.

$$ \texttt{PnL} = \texttt{cash-out amount - initial margin} $$
$$ \texttt{PnL} = \texttt{gross PnL - closing fee} $$

### Maintenance Margins

- DAI: 0.625%
- USDC: 0.625%
- FEI: 0.625%
- FRAX: 0.625%
- ETH: 6.25%

**Margin Ratio Formula**
In Angle, the margin ratio is computed as:

$$
\texttt{margin ratio} = \frac{\texttt{cash out amount}}{\texttt{position size}}
$$

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

## Deposit / SLP

### Slippage

In the `Deposit / SLP` page of the app, users may face a slippage when they exit from their position and sell their sanTokens. It depends on specific parameters for the collateral of interest and on the collateral ratio of the stablecoin in the Core module. This is put in place to incentivize them to stay in the protocol while it gets re-collateralized.

$$
\texttt{amnt received} = \texttt{amnt withdrawn} \times{(1 - \texttt{slippage})}
$$

The current slippage for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _Slippage_ in the _Fee Info > SLP_ section.

### Slippage on Fees for SLP

When the protocol gets close to be under-collateralized, it progressively keeps a bigger portion of the fees usually going to SLPs to grow the suplus and be able to pay back stable holders. Note that this doesn't impact the initial deposits of SLPs nor the fees earned up until the start of the slippageFee.

$$
\texttt{fees received} = \texttt{fees to SLPs} \times{(1-\texttt{slippage fee})}
$$

The current slippageFee for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _SlippageFee_ in the _Fee Info > SLP_ section.

## Global parameters

If you want to know the current protocol parameters in place, you can have a look at the analytics at [analytics.angle.money](https://analytics.angle.money) or directly in the [SDK](https://github.com/AngleProtocol/angle-sdk).
