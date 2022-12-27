---
description: Common questions about SLPs
---

# FAQ - Standard Liquidity Providers

## How do SLPs earn their interest?

When contributing to a collateral pool as a Standard Liquidity Provider, SLPs receive a token that we call **sanToken**, marking their belonging in the pool, just like a lender on Compound would receive a cToken. For instance, a SLP bringing USDC to the Core module for the agEUR coin would receive sanUSDC_EUR tokens based on the current exchange rate between the sanTokens and USDC.

By minting sanTokens, SLPs earn interest through the sanToken's exchange rate (sanRate), which increases in value relative to the underlying asset \(USDC in the example\) as transaction fees and interest accrue to that pool.

## How does the sanRate vary?

When a collateral is introduced for a given stablecoin, the sanRate \(how much USDC one sanUSDC_EUR is worth\) begins at 1 and increases at a rate depending on the transaction fees accumulated and on the lending returns.

For example, after one year, the sanRate might be equal to 1.2, meaning each sanUSDC_EUR can be used to redeem 1.2 USDC.

The sanRate is common for all SLPs.

## Do you have an example of how interest accrue?

Let's say that a SLP supplies 1000 USDC to the Core module for the agEUR stablecoin when the exchange rate between sanUSDC_EUR and USDC (sanRate) is 1.

They would receive 1000 \(1000/1\) sanUSDC_EUR.

A few months later, the SLP decides it's time to withdraw USDC from the Core module and the sanRate is now 1.2.

- The SLP sanUSDC_EUR are now worth 1200 USDC \(1000 \* 1.2\)
- They could withdraw their 1200 USDC, which would redeem all sanUSDC_EUR
- Or they could withdraw a portion, such as their original 1000 USDC, which would redeem 1000/1.2 = 833.33 sanUSDC-EUR, keeping 166.67 sanUSDC_EUR in their wallets

## Do SLPs get all transaction fees and interest from Angle Core module?

No. The portion of the fees going to SLPs are for each collateral/stablecoin pair controlled by two parameters, which can be changed by governance to give more or less fees and interest to SLPs. The current parameters' values can be found in [Angle Analytics](https://analytics.angle.money) on each pool's page.

The interest for SLPs is taken into account after the share of interest going to veANGLE holders has been distributed. For example, if the interest for veANGLE holders is at 0.5 and the interest for SLPs at 0.6, then the share of interest going to SLPs is $0.6\times(1-0.5)=0.3$.

Furthermore, SLPs only receive transaction fees from transactions which concern the pool they contribute to. Transaction fees from a mint transaction affecting the USDC liquidity pool do not go to SLPs which contributed to the DAI liquidity pool.

## Why don't SLPs receive all the transaction fees and interest?

The reason why fees and interest are not all distributed to SLPs is that some are used to incentive veANGLE holders to take part in the governance of the protocol, and create an additional buffer the Core module can use in case of a collateral price drop in a situation where the Core module is not fully covered by HAs.

## Are sanTokens standard ERC-20 tokens?

sanTokens are ERC-20 tokens, visible on Etherscan. Just like any other token, they can be transferred to other addresses.

## Can I transfer or trade my SLPs position?

Yes, as mentionned above sanTokens are ERC-20 tokens that can be transferred, and tradable on the open market. This means that a SLP willing to cash out could sell her sanTokens on a secondary exchange (like Uniswap) and hence get collateral without interacting with Angle Core module.

## What's the advantage of being a SLP on Angle Core module rather than going to other platforms that offer automatic yield like Aave or Compound?

SLPs in Angle Core module enjoy an increased yield through the [multiplier effect](README.md#%E2%9C%96-multiplier-effect). Because Angle's Core module reserves are lent to other protocols, among which some funds are not from SLPs, SLPs can get more yield than what they would get on Compound or Aave because they receive yield on collateral they did not bring initially.

For instance if there is 150 of collateral in the Core module, among which 50 comes from SLPs, SLPs are entitled to get yield on the 50 they brought, but also on the 100 of collateral that was brought by users and hedging agents.
