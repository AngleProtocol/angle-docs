# ⚙️ Angle AMOs

## What are AMOs

AMO stands for algorithmic market operations. AMOs are operations performed by contracts to mint or burn stablecoins, provided that this new supply is properly backed in one way or another, and doesn't affect the peg of the stablecoin. 

### AMO on lending markets

One type of such operations could be an AMO on lending market. In this case, a contract mints an amount of stablecoins, in our case an agToken, and deposits them on a lending market such as Aave or Euler. Then, these stablecoins can be borrowed by people having a sufficient amount collateral in the lending protocol. Once borrowed, the minted stablecoins are finally on the open market. At this point, they are backed by the collateral deposited in the lending protocol by the borrowers. As such, the agTokens originally minted by the protocol contract and deposited in the lending market are over-collateralized when being released in the market. 

This mechanism has several effects, among which an expansion of the agTokens supply and a lowering of the deposit and borrow APYs in the affected lending market. 

### Pros and cons

The main benefit of these operations is that they allow users of the lending markets to have access to agTokens at a lower borrowing cost, effectively widening the potential user base for Angle and agTokens. However, the direct consequence is that agTokens depositors earn a lower yield on their deposits. 

Another benefit is that it allows the protocol to earn a yield on these deposited tokens, to further fund its operations. 

{% hint style="succes" %} 
Borrowed stablecoins are fully backed by the borrowers' deposits in the lending market. 
{% endhint %}

## Angle AMOs on lending markets

Angle governance already approved two proposals to perform these operations and mint 1M agEUR to deposit on [Aave](https://app.aave.com/reserve-overview/?underlyingAsset=0xe0b52e49357fd4daf2c15e02058dce6bc0057db4&marketName=proto_polygon_v3) (Polygon) and [Euler](https://app.euler.finance/market/0x1a7e4e63778b4f12a199c062f3efdd288afcbce8) (mainnet). 

You can find the two governance votes on Snapshot: 
- [Vote to ming 1M agEUR to deposit on Euler (mainnet)](https://snapshot.org/#/anglegovernance.eth/proposal/0x638081b3e21f6fee55927be543097811f192da9a6ee9fe754bd9c8309b4bd798)
- [Vote to mint 1M agEUR to deposit on Aave V3 (Polygon)](https://snapshot.org/#/anglegovernance.eth/proposal/0xbcc1c41a0225446b41fc86870e01356f89d672fb4c6d7214beba90b1138f410d)




