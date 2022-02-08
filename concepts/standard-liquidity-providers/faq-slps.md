---
description: Common questions about SLPs
---

# FAQ - Standard Liquidity Providers

## How do SLPs earn their interest?

When contributing to a collateral pool as a Standard Liquidity Provider, a SLP receive a token that we call **sanToken**, marking her belonging in the pool, just like a lender on Compound would receive a cToken. For instance, a SLP bringing USDC to the protocol for the agEUR coin would receive sanUSDC_EUR tokens based on the current exchange rate between the sanTokens and USDC.

By minting sanTokens, SLPs earn interest through the sanToken's exchange rate (sanRate), which increases in value relative to the underlying asset \(USDC in the example\) as transaction fees and interest accrue to that pool.

## How does the sanRate vary?

When a collateral is introduced for a given stablecoin, the sanRate \(how much USDC one sanUSDC_EUR is worth\) begins at 1 and increases at a rate depending on the transaction fees accumulated and on the lending returns.

For example, after one year, the sanRate might be equal to 1.2, meaning each sanUSDC_EUR can be used to redeem 1.2 USDC.

The sanRate is common for all SLPs.

## Do you have an example of how interest accrue?

Let's say that a SLP supplies 1000 USDC to the protocol for the agEUR stablecoin when the exchange rate between sanUSDC_EUR and USDC (sanRate) is 1.

Then, the SLP would receive 1000 \(1000/1\) sanUSDC_EUR.

A few months later, the SLP decides it's time to withdraw USDC from the protocol and the sanRate is now 1.2.

- The SLPs sanUSDC_EUR are now worth 1200 USDC \(1000 \* 1.2\)
- The SLP could withdraw her 1200 USDC, which would redeem all sanUSDC_EUR
- Or she could withdraw a portion, such as her original 1000 USDC, which would redeem 1000/1.2 = 833.33 sanUSDC-EUR, keeping 166.67 sanUSDC_EUR in her wallet

## Do SLPs get all transaction fees and lending returns from the protocol?

No. The portion of the fees going to SLPs are for each collateral/stablecoin pair controlled by two parameters: `feesForSLPs` and `interestsForSLPs`. These parameters can be changed by governance, meaning governance could choose to give more or less fees and interest to SLPs.

The ratio of `interestsForSLPs` is taken into account after the share of interest going to veANGLE holders (`interestsForSurplus`) has been distributed. For example, if `interestsForSurplus` is at 0.5 and `interestsForSLPs` at 0.6, then the share of interest going to SLPs is $0.6\times(1-0.5)=0.3$.

Furthermore, SLPs only receive transaction fees from transactions which concern the pool they contribute to. Transaction fees from a mint transaction affecting the USDC liquidity pool do not go to SLPs which contributed to the DAI liquidity pool.

## Why don't SLPs receive all the transaction fees and interest?

The reason why fees and interest are not all distributed to SLPs is that they are used to incentive veANGLE holders to take part in the governance of the protocol, and create an additional buffer the protocol can use in case of a collateral price drop in a situation where the protocol is not fully covered by HAs.

## Are sanTokens standard ERC-20 tokens?

sanTokens are ERC-20 tokens, visible on Etherscan. Just like any other token, they can be transferred to other addresses.

## Can I transfer or trade my SLPs position?

Yes, as mentionned above sanTokens are ERC-20 tokens that can be transferred, and tradable on the open market. This means that a SLP willing to cash out could sell her sanTokens on a secondary exchange (like Uniswap) and hence get collateral without interacting with the protocol.

## What's the advantage of being a SLP with Angle rather than going to other platforms that offer automatic yield like Aave or Compound?

SLPs with Angle enjoy an increased yield through the [multiplier effect](README.md#multiplier-effect). Because Angle's reserves are lent to other protocols, among which some funds are not from SLPs, SLPs can get more yield than what they would get on Compound or Aave because they receive yield on collateral they did not bring initially.

For instance if there is 150 of collateral in the protocol, among which 50 comes from SLPs, SLPs are entitled to get yield on the 50 they brought, but also on the 100 of collateral that was brought by users and hedging agents.
