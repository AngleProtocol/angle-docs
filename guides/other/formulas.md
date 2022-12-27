---
description: Formulas at stake when interacting with app.angle.money
---

# Formulas

## Borrow

### Loan To Value - LTV

This is the value of the vault debt compared to that of the collateral.

$$
\texttt{LTV} = \frac{\texttt{debt}}{\texttt{collateral}}
$$

### Health Factor - HF

This is an indication of the health of the vault. Below 1, vaults can get liquidated.

$$
\texttt{HF} = \frac{1}{\texttt{LTV}} \times {\texttt{max. LTV}}
$$

## Perpetuals

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
- FRAX: 0.625%
- ETH: 6.25%

**Margin Ratio Formula**
In Angle, the margin ratio is computed as:

$$
\texttt{margin ratio} = \frac{\texttt{cash out amount}}{\texttt{position size}}
$$

## Staking

### Standard Liquidity Providers

The Staking page of the app lists all the opportunities for agEUR holders. It also contains the logic linked to Standard Liquidity providers of the protocol.

#### Slippage

Users may face a slippage when they exit from their SLP position and sell their sanTokens. It depends on specific parameters for the collateral of interest and on the collateral ratio of the stablecoin in the Core module. This is put in place to incentivize them to stay in the protocol while it gets re-collateralized.

$$
\texttt{amnt received} = \texttt{amnt withdrawn} \times{(1 - \texttt{slippage})}
$$

The current slippage for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _Slippage_ in the _Fee Info > SLP_ section.

#### Slippage on Fees for SLP

When the protocol gets close to be under-collateralized, it progressively keeps a bigger portion of the fees usually going to SLPs to grow the suplus and be able to pay back stable holders. Note that this doesn't impact the initial deposits of SLPs nor the fees earned up until the start of the slippage fee.

$$
\texttt{fees received} = \texttt{fees to SLPs} \times{(1-\texttt{slippage fee})}
$$

The current slippage fee for SLP can be consulted in the [analytics](https://analytics.angle.money/) by selecting a pool and looking at _SlippageFee_ in the _Fee Info > SLP_ section.

## Global parameters

If you want to know the current protocol parameters in place, you can have a look at the analytics at [analytics.angle.money](https://analytics.angle.money) or directly in the [SDK](https://github.com/AngleProtocol/angle-sdk).
