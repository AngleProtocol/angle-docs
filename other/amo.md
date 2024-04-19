---
cover: ../.gitbook/assets/Angle-AMO-cover.jpg
coverY: -42
---

# ⚙️ Algorithmic Market Operations

Algorithmic market operations (or AMOs), also referred to as direct deposit modules, are operations performed by contracts to mint or burn stablecoins without collateral immediately backing these stablecoins. Stablecoins minted by AMOs are still controlled by the protocol, and if other people start controlling these stablecoins, then this new supply should be properly backed in one way or another.

AMOs are conceived not to affect the peg of the stablecoin.

## Example

Algorithmic market operations are well suited for lending markets. In this case, the way an AMO looks like is that a contract mints an amount of stablecoins (using no collateral and hence not interacting with any other protocol module) and deposits them on a lending market such as Aave or Morpho.

These minted stablecoins can then be borrowed by people having a sufficient amount of backing collateral in the lending protocol. It is only when they're borrowed that the minted stablecoins can really be considered to be on the open market. At this point, they are backed by the collateral deposited in the lending protocol by the borrowers. As such, the stablecoins originally minted by the protocol's contract and deposited in the lending market are over-collateralized when being released in the market. And a lending AMO is a way to delegate the borrowing facility of Angle stablecoins to another protocol.

## Angle AMOs

While we described above an example of a lending AMO, the Angle Protocol can support different types of AMOs. Before being put in production, each AMO needs to be proposed on Angle governance forum and voted.

Management of AMOs across different chains differs depending on their type. Some of them are managed by [the governance or guardian multisig](../governance/angle-dao.md#🗳-voting) on the corresponding chain. Others are managed fully automatically via trustless smart contracts or directly via the Timelock of the protocol on the corresponding chain.

{% hint style="info" %}
The state and size of Angle AMOs for all its stablecoins can be tracked in real-time on [Angle Analytics dashboard](https://analytics.angle.money/collaterals).
{% endhint %}

In terms of lending AMOs, the protocol uses Morpho to delegate its borrowing facility on Ethereum and invests USDA on a vault which risk is managed by Gauntlet. The protocol also has a 100k EURA AMO on Aave V3 on Polygon.

### Liquidity AMOs

Angle also uses liquidity AMOs to seed some pools with EURA and/or USDA liquidity. The idea is to either match some of the protocol's reserves with EURA/USDA minted from AMOs or to mint both EURA and USDA to provide liquidity.

In this last case, EURA ends up being backed by USDA when people swap USDA to EURA and conversely, and the balance sheets of the two stablecoins become correlated up to the size of this AMO.

While liquidity AMOs expose the protocol to a potential divergence loss + loss versus rebalancing risk, they also help bootstrapping Angle stablecoins liquidity without relying on individual LPs from start. Their size and balances are in any monitored in real-time to make sure that the potential loss or bad debt never grows beyond an acceptable size with respect to the protocol equity.

## Implications of AMOs

By making Angle stablecoins more easily accessible on some protocols, AMOs widen the user base of the protocol. They can also be an interesting source of revenue for the protocol (from lending yield or transaction fees).

It's important to note though that AMOs are not completely neutral on the protocols on which they are taking place. On a lending market for instance, having an AMO reduces both the deposit and borrow APYs hence reducing yield opportunities for lenders while making it easier for borrowers.

Another issue as well is that having AMOs on a protocol (like Aave or Morpho) means that the risk of Angle becomes to some extent the risk of the underlying protocol. If Angle lends 1m EURA on Aave and Aave gets hacked, then the Angle protocol also makes a loss.

As such, AMOs are a powerful tool to expand Angle stablecoins use cases in DeFi as well as protocol revenue, but they do not come without any risk, and every new AMO type is carefully calibered by Angle governance to control systemic risk before being put in place.
