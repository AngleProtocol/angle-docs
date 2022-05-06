---
description: Minting agTokens from specific tokens
---

# 🛩 Token Reactors

Thanks to its ability to whitelist addresses and to accept specific risky collateral types with tailored parameters, Angle Borrowing module can be used to mint agTokens from a long tail of volatile/risky assets.
In these cases, and to further reduce risk, the protocol offers a reactor mode in which the agTokens borrowed are not technically controlled by the addresses depositing the collateral but by a protocol contract which invests the agTokens in yield strategies. Yield obtained can then be shared between depositors of the collateral and the protocol.

## Reducing risk through protocol control

In the reactor mode, the fact that the contract controls the agTokens makes it less risky for the protocol to use volatile collateral assets. The protocol can indeed pull the agTokens before a liquidation happens if the price of the collateral decreased by too much. In fact, the collateral ratio of the vault is programatically managed by the underlying strategy to reduce the chances of getting liquidated and worse to accrue bad debt.

## Offering yield on any tokens

As yield from strategies implemented by the protocol is shared between depositors and the protocol, this reactor mode effectively creates staking pools for volatile assets.

Users depositing their tokens in a token reactor can earn yield in agTokens on volatile assets, that potentially increase in value themselves. This gives additional utility to a long tail of unused assets in DeFi, and more generally **open the gates for any DAO to get yield on idle treasury assets.**

## Increasing agTokens liquidity

On top of offering a native yield on volatile tokens, Angle Token Reactors also allow to increase agTokens liquidity across DeFi, making them much better stablecoins for users.
