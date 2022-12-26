# ⚙️ Angle Algorithmic Market Operations

## ⁉️ About Algorithmic Market Operations (AMOs)

Algorithmic market operations (or AMOs), also referred to as direct deposit modules, are operations performed by contracts to mint or burn stablecoins without collateral immediately backing these stablecoins. The idea is that stablecoins minted by AMOs are still controlled by the protocol, and if other people start controlling these stablecoins, then this new supply should be properly backed in one way or another.

AMOs are conceived not to affect the peg of the stablecoin.

### Example

Algorithmic market operations are perfectly suited for lending markets. In this case, the way an AMO would look like is that a contract mints an amount of stablecoins (using no collateral and hence not interacting with the protocol's Core or Borrowing module) and deposits them on a lending market such as Aave or Euler.

These minted stablecoins can then be borrowed by people having a sufficient amount of backing collateral in the lending protocol. It is only when they're borrowed that the minted stablecoins can really be considered to be on the open market. At this point, they are backed by the collateral deposited in the lending protocol by the borrowers. As such, the agTokens originally minted by the protocol's contract and deposited in the lending market are over-collateralized when being released in the market.

### Implications of AMOs

Algorithmic market operations on a lending market like in the example above have several effects among which an expansion of the agTokens supply and a lowering of the deposit and borrow APYs in the affected lending market.

While this widens the potential user base for borrowers of agTokens, this also reduces the opportunities for agToken lenders and depositors. Note though that in the process, the Angle protocol makes a revenue on the lending yield.

In this specific AMO, borrowed stablecoins are over-collateralized by the borrowers' deposits in the lending market, and as such agTokens remain fully backed.

One issue here, and it's common to almost all AMOs is that, the risk of the agTokens in circulation also becomes the risk of the underlying protocols used (in the example Euler or Aave). If the lending market is Aave and Aave gets hacked, then the Angle protocol also makes a loss.

On top of that, if too many agTokens end up being in circulation through this medium there may not be enough reserves in Angle Core module to maintain convertibility between stablecoins and collateral if everyone comes to burn the stablecoins.

As such, AMOs are a powerful tool to expand agTokens use cases in DeFi as well as protocol revenue, but they do not come without any risk, and every new AMO type should be carefully calibered by Angle governance to eliminate systemic risk.

## Angle AMOs

While we described above an example of a lending AMO, the Angle Protocol supports different types of AMOs. Each AMO is previously proposed on Angle governance forum and voted [on Snapshot](https://snapshot.org/#/anglegovernance.eth) before being put in production.

Management of AMOs across different chains differs depending on their type. Some of them are managed by [the governance multisig](/governance/angle-dao.md#🗳-voting) on the corresponding chain. Others are managed fully automatically via trustless smart contracts.

{% hint style="info" %}
For the most up-to-date info on Angle AMOs managed by the governance multisig, you can check [this document](https://docs.google.com/spreadsheets/d/1RM2wvtGT1B8sGZ5NbKFry-DJMTgZBNvJYE963xZqL7A/edit?usp=sharing).
{% endhint %}

### Curve AMO

This AMO is the only one that is so far automatically and trustlessly managed by smart contracts. It consists in minting agEUR in the Curve agEUR-EUROC when there are more EUROC than agEUR and burning agEUR from the pool when there are more agEUR than EUROC.

This AMO acts as a sort of price stability module for the protocol, as detailed in [this governance proposal](https://gov.angle.money/t/aip-27-deploy-amo-on-the-curve-ageur-euroc-pool/473).

Addresses and code for the smart contracts responsible for the execution of this AMO can be found [here](https://developers.angle.money/overview/smart-contracts/mainnet-contracts#algorithmic-market-operations).

### Lending AMOs

Lending AMOs correspond to the example described above where the protocol mints agTokens (only agEUR so far) and lends it on lending protocols. agTokens minted into such AMOs do not enter in circulation unless they are overcollateralized by a borrower through the concerned money market.

#### Current Protocol Lending AMO Positions

Angle supports so far several different lending AMOs on different chains:

- On [Aave](https://app.aave.com/reserve-overview/?underlyingAsset=0xe0b52e49357fd4daf2c15e02058dce6bc0057db4&marketName=proto_polygon_v3) on Polygon: 1m agEUR are invested in this AMO
- On [Euler](https://app.euler.finance/market/0x1a7e4e63778b4f12a199c062f3efdd288afcbce8) on Ethereum mainnet with ~3.6m agEUR invested as well.
- On [Atlendis](https://app.atlendis.io/pools/0x712a20869e4630d50c37ba0dde9918676224f819b47e8e76eb46ab223056146a/deposit) on Polygon with, as of September 2022, 200k agEUR invested in the AMO.

### Liquidity as a service

Another type of AMO is called liquidity as a service. It consists in lending for a pre-determined agTokens to be deposited in a pool and returned with an interest rate. It can be leveraged by any DAO which is looking to create cheap liquidity for its token.

Risks for the protocol are reduced because the partner DAO is taking the impermanent loss in this case.

So far, Angle has worked with Ondo to offer such services, as presented in [this](https://gov.angle.money/t/proposal-angle-ondo-liquidity-as-a-service-program/320) governance discussion.

#### Current Protocol LaaS AMO Positions

The first liquidity as a service operation has been approved with Paladin as detailed [here](https://gov.angle.money/t/liquidity-as-a-service-partnership-with-paladin/322), to provide 500,000 agEUR as liquidity to PAL through Ondo contracts.

### Protocol-owned Liquidity

Angle also started to use AMOs to seed some pools with agEUR liquidity. The idea is to use some of the protocol reserves and match it with agEUR minted from AMOs to provide liquidity. This has many benefits for Angle, among which bootstrapping agEUR liquidity without relying on individual LPs from the start. The size and balances of these AMOs need to be monitored to make sure that the potential loss or bad debt from providing liquidity is never too big for the protocol.

#### Current Protocol LP AMO Positions

- Optimism: Uniswap 50/50 agEUR/USDC pool, seeded with 200K USDC from surplus and a corresponding amount of agEUR at mint.
- Arbitrum: Uniswap 50/50 agEUR/USDC pool, seeded with 200K USDC from protocol surplus and a corresponding amount of agEUR at mint.
- Ethereum: Curve 50/50 agEUR/EUROC pool, seeded with 200K USDC from the protocol and then swapped to EUROC, and a corresponding amount of agEUR at mint.
- Avalanche: Trader Joe 50/50 agEUR/USDC pool, seeded with 100k USDC from the protocol surplus and a corresponding amount of agEUR at mint.

More details on the pros and cons these AMOs can be found on [this governance post](https://gov.angle.money/t/aip-14-seed-univ3-ageur-usdc-pools-on-optimism-and-arbitrum-using-protocol-surplus-and-amos/396).
