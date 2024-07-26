---
description: What are the risks for using Angle stablecoins?
---

# ⚠️ Risks

Angle develops stablecoins. While all the protocol smart contracts are built so that the system's stablecoins keep their peg, there is no risk zero. And like any DeFi product, there are risks associated with interacting with Angle and/or holding Angle stablecoins.

When you're holding a stablecoin you are not only exposed to the underlying technological stack on which the stablecoin is built but also on the economic principles designed to guarantee that there are always more assets in reserves than stablecoins in circulation.

Even though Angle Protocol contributors have security as a top priority and work tirelessly to mitigate these risks and have the safest platform to deploy capital, it's critical that the risks induced with the protocol remain transparently known by all its stakeholders.

{% hint style="warning" %}
This list is obviously a non-exhaustive list of the risks entailed with Angle Protocol. We invite everyone to do its own research before interacting with Angle smart contracts.
{% endhint %}

## Smart Contract Risk

Angle is built on smart contracts. While these are undergoing [regular audits](resources/audits/), there may be a fatal error or a vulnerability out there that would leave a portion or all the funds of the protocol to be hacked.

## Blockchain Risk

There is also an inherent risk with having smart contracts operating on blockchains which may not be bullet proof. Angle is deployed across multiple chains. If one of the underlying chains gets exploited, or if one of the bridge systems that the protocol leverages is manipulated, then the protocol could be left with a loss and get undercollateralized.

The protocol has a [unique security system](other/cross-chain.md) to mitigate this risk and reduce the relative exposure to a bridge or blockchain hack, but this may not always be enough.

## Oracle Risk

Angle is dependent on oracles (Chainlink, Redstone, Pyth among others) to assess the price of the assets it has in its reserves. Even though there are [important safeguards](transmuter/mintBurn.md#📈-target-price-and-deviation) in place, the failure of some of the oracles on which the protocol relies may lure the protocol into giving away its assets at a deflated value thus leaving the protocol under-collateralized.

## Collateral Risk

Angle stablecoins are backed by collateral assets. Within [the Transmuter](transmuter/) for instance, these should be denominated in the same currency as that of the stablecoin. For instance, EURA has in its reserves bC3M a tokenized representation of [a Euro ETF](https://www.amundietf.fr/fr/professionnels/produits/fixed-income/amundi-etf-govies-06-months-euro-investment-grade-ucits-etf-dr/fr0010754200).

The failure of one of the assets in the reserves or a drastic loss in value of one of these assets may leave the protocol badly collateralized. Every collateral of a protocol's stablecoin may pose some relative risk.

## Counterparty Risk

Some of the collateral assets of the protocol (EURC, USDC for instance) are controlled by centralized entities. There is therefore a counterparty risk related to these entities. Bankruptcy remoteness and the ability to claim the underlying assets of the supported collaterals is an important aspect of the collateral selection process.

As part of its [direct deposit modules](other/amo.md), the protocol invests stablecoins and a portion of its treasury into other protocols (Uniswap, Aave, Morpho for instance). The hack or a failure of any of these underlying protocols may lead the protocol to lose funds. So far for EURA, the protocol has invested less than 20% of its equity in direct deposit modules.

## Bad Liquidation Risk

The protocol, in [its borrowing module](borrowing-module/), comes with mechanisms to deal with the price decrease of the collateral assets of the module, like liquidations. Yet, a rapid price decrease or poorly set risk and liquidation parameters may prevent liquidations from happening in time leaving the protocol with bad debt.

## Governance Risk

Angle is a decentralized protocol controlled by a DAO. A manipulation of the governance systems of the protocol, a majority attack not caught up by the protocol emergency multisig could lead the protocol to lose a portion if not all its funds.

## Failure of the underlying mechanisms

More globally, the systems on which the protocol relies are based on economic and game-theoretic mechanisms exposed in [the whitepapers](whitepapers.md). The failure of the mechanisms to work as intended in some situations may lead the stablecoins of the protocol to lose their peg.

## Higher fees or lower than expected returns

The fees at stake in different places of the protocol may be variable (for instance in the borrowing module the rate may be modified by governance or within the Transmuter the minting and burning fees are dynamic based on the system's exposure to its collateral assets). The costs associated with getting or burning EURA may therefore vary and increase without notice.

Similarly, on Angle Savings contracts, the rate that is paid to stablecoin holders may vary, leading to lower than expected returns.
