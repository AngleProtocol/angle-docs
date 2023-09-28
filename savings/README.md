---
description: Learn more about Angle Savings System
---

# 💸 Angle Savings System

Angle Savings system is an addition to the Angle Protocol that allows any agToken holder to earn savings, paid in stablecoins.

Angle stablecoins do not automatically earn a yield, rather these must be staked in some specific contracts (potentially available on different chains) in order to start earning.

The yield that is paid through these contracts comes from the interest revenue Angle Protococol is generating on its assets across its different modules:

- yield-bearing collateral assets held as part of the Transmuter
- interest rates paid by borrowers within the Borrowing module

{% embed url="https://www.youtube.com/embed/9LKDbLzNYdU" %}

{% hint style="info" %}
On [Angle Analytics](https://facts.angle.money), it's possible to track how much a year the protocol is earning across each collateral asset, its estimated yearly interest revenue and the current savings rate for supported stablecoins.
{% endhint %}

Angle Savings system is designed so that the protocol never distributes more than what it generates.

## Rates

The rate that is paid by Angle savings system on a stablecoin depends on the return over assets the protocol is generating for this asset. Assuming all stablecoins are in Angle savings contracts, and assuming no cut taken by the protocol, the protocol could pay up to this return over assets to all stablecoin holders.

As in normal times, not all stablecoins are in savings contracts, the protocol can pay more than its return over assets to stablecoin holders. As such, by entering into Angle Savings sytem, **you're earning a multiplier** on the yield the protocol is making on its reserves for this stablecoin.

Practically, the rate for a given stablecoin is defined such that:

$$
\texttt{rate} = \min(x\times \frac{\texttt{Protocol yearly interest revenue on this stablecoin}}{\texttt{stablecoin.balanceOf(savings contract)}},y)
$$

The parameter `y` is the max rate that can be set and `x` is a buffer that the protocol is taking.

Equivalently, this formula above can be rewritten in terms of return over assets and utilization of the savings contract:

$$
\texttt{rate} = \min(x\times \frac{\texttt{RoA}}{\texttt{Utilization}},y)
$$

For agEUR, the parameters chosen are y=10% and x=0.9.

### Rate Updates

The rate schedule above cannot be implemented automatically in a non manipulative way, and Angle relies on its governance multisig to enforce it.

While only the governance multisig can set the maximum rate (`y`) value, the guardian multisig can update the rate of the savings contract under the following conditions:

- last rate update was at least 7 days ago
- or, the current rate is too high and causing the protocol to lose money based on the current utilization of the savings contract. Formally the condition for the guardian multisig to intervene in this case writes:
  $$\texttt{contract rate}\times \texttt{stablecoin.balanceOf(savings contract)}_t \geq \texttt{Protocol yearly interest revenue}_t$$
- or, the rate based on the schedule would be different from the current rate encoded in the contract by 0.5%. This writes:
  $$|\min(x\times \frac{\texttt{Protocol yearly interest revenue}}{\texttt{stablecoin.balanceOf(savings contract)}},y) - \texttt{contract rate}| \geq 0.5\%$$

{% hint style="info" %}
If you're looking to build on top of Angle Savings contracts, check out [this guide](https://developers.angle.money/developer-guides/savings) from our developers documentation.
{% endhint %}

## Fees and Usage

Angle Savings contracts are simple ERC4626 contracts, which means that upon staking an Angle stablecoin in a savings contract you receive a classical ERC20 token that can then be transferred, staked, lent or used in any way you want.

The value of these tokens is not designed to remain pegged to their respective underlying asset, but increases over time as yield accrues to it. **Angle staked tokens are yield bearing and not rebasing** and the exchange rate between Angle stablecoins and their staked equivalent is encoded in the savings smart contract.

While you may be able to acquire Angle staked tokens on DEXes, there is no need to, and depositing Angle stablecoins can be done **without any slippage** directly with the staking smart contract.

This system comes with **no deposit or withdraw fees**. And upon depositing in it, you immediately start earning. For instance 1 agEUR deposited in a savings contract and withdrawn after a 12s block would have earned the equivalent of 12s of the yearly rate encoded in the contract.

{% hint style="info" %}
[Angle App](https://app.angle.money) is an example of frontend that supports depositing directly and with no slippage into the contract, provided that you are coming with agEUR. Check out the guide for using stEUR on Angle App [here](../guides/app-guides/agEUR/stEUR.md).
{% endhint %}
