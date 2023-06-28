---
description: Implementation details for Transmuter
---

# 🖥️ Implementation details for Transmuter

## 🌌 Reactive Fees & Path Independence

Fees for a specific action (mint or burn) are defined by the values they should take at certain exposures.

For instance, the system may be set such at exposure 0% for $\texttt{EUR}_A$ after a mint, mint fees must be $f=0.1\%$, at 30% $f=0.3\%$, at 32% $f=0.34\%$ and at 40% $f=100\%$.

The Transmuter system is implemented such that in the same block (and putting gas cost considerations aside), splitting an order in multiple sub orders involving the same asset gives exactly the same output as making one single order. On top of that, it also enables people to specify when minting or burning whether they want to get an exact amount of tokens in output or to bring an exact amount of tokens in input, with both methods being purely equivalent.

## ⛽️ Gas optimizations

### 💎 Diamond proxy pattern

The Transmuter system works with external oracles to price the reserve assets. To avoid exploits, fees for each asset should be set with the oracle deviation thresholds of all other assets in mind.

Because the burn and redemption operations imply reading into the oracles of all the assets in the system, gas costs scale linearly with the amount of assets accepted in the system. Transmuter is implemented as a single contract relying on a diamond proxy pattern so the logic associated to the oracle for each asset can all be taken into account in the same contract thus reducing gas costs for calling oracles for each asset.

Beyond this, the diamond proxy pattern opens some composability and flexibility in how the system is implemented. Transmuter can read into several oracles (like UniswapV3 TWAPs or Chainlink) for a single asset, and take the value that is most at its advantage.

In fact, any oracle type can be supported provided that the values given for both the target price and for the current price are both non manipulable.

### 🧾 Smart accounting

To track the exposure to each asset in the backing and compute the value of the adaptive fees, the system needs to store the amount of stablecoins that have been issued from each of the assets in the backing.

During a redemption, stablecoins are burnt for a portion of each asset. If there are $$N$$ assets, then it means that $$N$$ values in storage must be updated. To avoid the multiplication of storage updates, Transmuter relies on a $$\texttt{normalizer}$$ variable.

If $$x_i$$ stablecoins are issued from asset $$i$$, then Transmuter tracks the amount of stablecoins issued from $$i$$ by keeping in storage: $$r_i=\frac{x_i}{\texttt{normalizer}}$$.

If someone redeems $$y$$ stablecoins out of the $$Y$$ that had been issued by the system, the $$\texttt{normalizer}$$ variable becomes: $$\texttt{normalizer}\times(1-\frac{y}{Y})$$

After the $$\texttt{normalizer}$$ update, the amount of stablecoins issued from asset $i$ becomes:

$$\frac{x_i}{\texttt{normalizer}} \times \texttt{normalizer}\times(1-\frac{y}{Y}) = x_i (1-\frac{y}{Y})$$
