---
description: Common questions about getting and exchanging the Ppotocol's stablecoins
---

# FAQ - Stable Seekers and Holders

## Could I use the protocol as a decentralized exchange?

Angle can be used as a decentralized exchange where there is no slippage for swapping.

If Angle's agUSD is backed by wETH and wBTC, a user wishing to swap wETH against wBTC with no slippage can choose to come to Angle, swap wETH against agUSD, and then use these agUSD to redeem wBTC.

## What happens if I ask to get a collateral that is not present in sufficient quantity against my stablecoins?

Angle leaves the choice to its users as for the collateral type they can get when burning their stablecoins.

It is however possible that there is an imbalance between the value of the different collateral pools backing a stablecoin. If 100 agEUR are backed by 10 DAI and 150 USDC, the transaction of a user asking DAI against 100 agEUR will fail because there are not enough DAI in reserves to reimburse the user.

## Do I still own the collateral I bring to the protocol to mint stablecoins?

No. Unlike in Maker's system, Angle's protocol works with swaps from a user perspective, meaning that the collateral brought to get stablecoins does no longer belong to the person who brought it: it belongs to the protocol which keeps it in reserves and uses it to programmatically get some yield on it.

## Are the stablecoins borrowed from the protocol?

No, once the stablecoins are issued, they are not considered as a debt from the person which issued it, and there is no need to reimburse or to pay interests to the protocol on it.

## Can I transfer my stablecoins to other addresses?

Yes, Angle's stablecoins \(which are called **agTokens**\) are standard ERC-20 tokens. They can be exchanged and transferred from one address to another.

This notably means that someone willing to get Angle's stablecoins may buy it on the open market \(like on Uniswap\) and without interacting with the protocol. The same goes for people willing to sell their stablecoins.

Note that having people buying on secondary markets creates an increasing pressure on the market price of the stablecoins, thus incentivizing people to issue new tokens to restore peg.

