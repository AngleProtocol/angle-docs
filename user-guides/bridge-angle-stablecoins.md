---
description: Bridge USDA, EURA or ANGLE tokens across 12+ chains
---

# 🌉 Bridge Angle stablecoins

The Angle app leverages the protocol's [cross-chain bridge setup](https://docs.angle.money/side-modules/cross-chain) built on LayerZero to enable bridging its stablecoins and ANGLE tokens between 12+ EVM-compatible networks such as Ethereum, Optimism, Arbitrum, Base, BNB, Polygon, Avalanche, Celo and more.

{% hint style="info" %}
Before bridging assets, make sure you having enough funds on the origin chain to pay for transaction fees for both the origin and the destination chains.

For example, if you bridge tokens from Polygon to Ethereum, you will need MATIC tokens to pay for gas fees on Polygon AND on Ethereum.

If you do not have enough funds, the transaction might revert or you could get an `internal JSON RPC` error displayed on the Angle app.
{% endhint %}

<figure><img src="../.gitbook/assets/‎bridge user guide.‎001.jpeg" alt=""><figcaption><p>Bridge Angle stablecoins from one chain to another</p></figcaption></figure>

1. Open the Angle and connect your wallet
2. Go to the [`Bridge`](https://app.angle.money/bridge/) section
3. Select the token you want to bridge among USDA, EURA and ANGLE
4. Select the chain of origin, on which you have funds
5. Select the chain of destination
6. Enter the amount (pay attention to the bridge volume limit mentioned at the bottom of the bridge interface)
7. Click on the `Bridge` button and confirm the transaction in your wallet

{% hint style="info" %}
it might take up to 20 minutes to receive your freshly bridged assets.
{% endhint %}

{% hint style="info" %}
If you don't know whether you have received funds in your wallet after a bridge transaction, you can check on [LayerZeroScan](https://layerzeroscan.com/) with the hash of the bridge transaction from the origin network.

If the transaction on the destination chain is confirmed but you don't have the tokens in your wallet, you can read the paragraph below about how to get back stablecoins from lz tokens.
{% endhint %}

### Bridge limits

For security reasons, Angle's bridge system implements total and hourly limits for the amounts that can be bridged to a chain. These limits are specific to each asset (USDA, EURA or ANGLE tokens) and to each chain.

If the limits are reached when processing a bridge transaction, you won’t receive Angle stablecoins or ANGLE tokens on the destination chain. Instead, you will receive lz tokens in your wallet that can be used to redeem USDA, EURA or ANGLE later, when the limits reset.

### R**edeem lz tokens**

If you hit a bridge limit, you should have receive **lz-USDA, lz-EURA, or lz-ANGLE** tokens in your wallet.

You can redeem these lz-tokens for USDA, EURA or ANGLE tokens by interacting directly with the [smart contracts](https://developers.angle.money/overview/smart-contracts) of the lz tokens.

1. Go on the explorer of the network on which you own lz tokens (e.g. Etherscan for Ethereum, Arbiscan for Arbitrum, etc)
2. Enter the token contract of the lz token you want to redeem in the search bar.\
   E.g of the lz-USDA smart contract address on Ethereum: [0xEc0B13b2271E212E1a74D55D51932BD52A002961](https://etherscan.io/address/0xEc0B13b2271E212E1a74D55D51932BD52A002961)
3. Click on the “Contract” tab
4. Click on `Write as Proxy`
5. Connect your wallet to Etherscan by clicking on the `Connect to Web3` button.&#x20;
6. Scroll down to the function `withdraw()`
7. Enter the amount of lz tokens you want to redeem, and your wallet address. The amount input needs to be in the correct decimals format: you need to multiply the amount by _`10^18`_. For example, to exchange _`123`_ lz-EURA, you need to input _`123000000000000000000`._
8. Click on the `Write` button and validate the transaction
