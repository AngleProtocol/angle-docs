---
cover: ../.gitbook/assets/Angle-AMO-cover.jpg
coverY: -42
---

# ⚙️ Algorithmic Market Operations

Algorithmic market operations (or AMOs), also referred to as direct deposit modules, are operations performed by contracts to mint or burn stablecoins without collateral immediately backing these stablecoins. Stablecoins minted by AMOs are still controlled by the protocol, and if other people start controlling these stablecoins, then this new supply should be properly backed in one way or another.

AMOs are conceived not to affect the peg of the stablecoin.

## Example

Algorithmic market operations are well suited for lending markets. In this case, the way an AMO would look like is that a contract mints an amount of stablecoins (using no collateral and hence not interacting with any other protocol module) and deposits them on a lending market such as Aave.

These minted stablecoins can then be borrowed by people having a sufficient amount of backing collateral in the lending protocol. It is only when they're borrowed that the minted stablecoins can really be considered to be on the open market. At this point, they are backed by the collateral deposited in the lending protocol by the borrowers. As such, the agTokens originally minted by the protocol's contract and deposited in the lending market are over-collateralized when being released in the market.

## Angle AMOs

While we described above an example of a lending AMO, the Angle Protocol can support different types of AMOs. Before being put in production, each AMO needs to be proposed on Angle governance forum and voted [on Snapshot](https://snapshot.org/#/anglegovernance.eth).

Management of AMOs across different chains differs depending on their type. Some of them are managed by [the governance multisig](../governance/angle-dao.md#🗳-voting) on the corresponding chain. Others are managed fully automatically via trustless smart contracts.

{% hint style="info" %}
As of August 2023, Angle only supports a single lending AMO on Aave V3 with 100k minted agEUR and some protocol-owned liquidity AMOs.
{% endhint %}

### Protocol-owned Liquidity

Angle uses protocol-owned liquidity AMOs to seed some pools with agEUR liquidity. The idea is to match some of the protocol's reserves with agEUR minted from AMOs to provide liquidity. This has many benefits for Angle, among which bootstrapping agEUR liquidity without relying on individual LPs from the start. The size and balances of these AMOs need to be monitored to make sure that the potential loss or bad debt from providing liquidity is never too big for the protocol.

#### Current Protocol LP AMO Positions

- Optimism: Uniswap V3 agEUR/USDC pool (0.05%), seeded with 200K USDC from surplus and a corresponding amount of agEUR at mint.
- Arbitrum: Uniswap V3 agEUR/USDC pool (0.05%), seeded with 300k USDC from protocol surplus and a corresponding amount of agEUR at mint.
- BNB Chain: PancakeSwap V3 agEUR/USDC pool (0.05%), seeded with 150k USDT from protocol surplus and a corresponding amount of agEUR at mint.

## Implications of AMOs

By making agTokens more easily accessible on some protocols, AMOs widen the user base of the protocol. They can also be an interesting source of revenue for the protocol (from lending yield or transaction fees).

It's important to note though that AMOs are not completely neutral on the protocols on which they are taking place. On a lending market for instance, having an AMO reduces both the deposit and borrow APYs hence reducing yield opportunities for lenders while making it easier for borrowers.

Another issue as well is that having AMOs on a protocol (like Aave) means that the risk of Angle becomes to some extent the risk of the underlying protocol. If Angle lends 1m agEUR on Aave and Aave gets hacked, then the Angle protocol also makes a loss.

As such, AMOs are a powerful tool to expand agTokens use cases in DeFi as well as protocol revenue, but they do not come without any risk, and every new AMO type should be carefully calibered by Angle governance to control systemic risk.
