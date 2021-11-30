---
description: List of formulas and parameters used in the Angle protocol and at app.angle.money
---

# Formulas & Parameters

## Minting & Burning

**USDC**

- Minting fee: 0.25%
- Burning fee: 0.45%

**DAI**

- Minting fee: 0.3%
- Burning fee: 0.5%

## Perpetuals (HA)

### Fees

- Entry: 0.3%
- Close: 0.5%

### Maintenance Margins

- DAI: 0.625%
- USDC: 0.625%
- FEI: 0.625%
- FRAX: 0.625%

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

### PnL

The PnL displayed on the app represents the gain or loss you would make if closing the position: it is **net** of fees.

$$ PnL = cashOutAmount - initialMargin $$
$$ PnL = grossPnL - closingFee $$

### Est. APR on open positions

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
