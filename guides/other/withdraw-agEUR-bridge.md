---
description: Exchange your lz-agEUR for agEUR
---

# Withdraw agEUR from the lz-agEUR bridge contract

When bridging from a network to another, it's possible that you hit the hourly or global bridge limits. In this case, you receive lz-agEUR tokens in your wallet that can be used to redeem canonical agEUR later, when the limits reset.

## How to redeem agEUR from the lz-agEUR bridge contract

On each network where agEUR can be bridged, there is a lz-agEUR contract. You can find their addresses on the [smart contracts addresses](https://developers.angle.money/overview/smart-contracts) page.

If you hit a bridge limit, you should have received lz-agEUR tokens in your wallet. In this case, you can go to the token contract ([example on Optimism](https://optimistic.etherscan.io/address/0x840b25c87b626a259ca5ac32124fa752f0230a72#writeProxyContract)).

![Receive lz-agEUR](/.gitbook/assets/receive-lz-ageur.png)

Then follow these steps:

1. Click on `Write as Proxy`
2. Connect your wallet to Etherscan by clicking on the `Connect to Web3` button.
3. Scroll down to function `22. withdraw()`
4. Enter the amount of lz-agEUR you want to exchange for agEUR, and your wallet address.
5. And send the transaction!

[Example of a withdraw transaction](https://optimistic.etherscan.io/tx/0x20799daf2e30ccf2ec4cf1f66b85f01273b3fc26bc786ad25d7b187eb810f721)

![Connect lz-agEUR](/.gitbook/assets/connect-lzageur.png)

![Send tx Etherscan](/.gitbook/assets/send-tx-etherscan.png)

If the limits are empty, it's possible that the tx will revert. You can check the current limits on the app [bridge page](https://app.angle.money/#/bridges-agEUR).
