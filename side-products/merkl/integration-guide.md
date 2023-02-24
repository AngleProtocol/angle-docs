---
description: Guide to integrate Merkl in your app
---

# 📒 Integration Guide

Data about all Merkl incentivized pools across all supported chains can be found by calling our API endpoint: `https://api.angle.money/v1/merkl`.

When calling this payload, you must specify the `chainId` address. You may also specify a \`user\` address if you want additional information related to one user (like claimable amounts, liquidity in the pools, ...)

A typical query looks like: [`https://api.angle.money/v1/merkl?chainId=10&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185`](https://api.angle.money/v1/merkl?chainId=10\&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185).

## List incentivized pools

When called for a specific chain, the API returns in a `pools` object a mapping between pool addresses of this chain (like Uniswap V3 pool addresses) and for each pool details on the APRs for providing liquidity in it.

On the APR, note that on concentrated liquidity AMMs, because of the way the script works, two LPs with different APRs may earn drastically different returns. As such, APRs given here are average measures of the returns a LP could earn. If you are to integrate Merkl in your app, you may want to build the APR indicators tailored to your use cases.

The `pools` object also has for each incentivized pool details about the different distributions that occurred on it: their start and end dates, the parameters set or the amount of incentives for each distribution.

You can filter from the \`pools\` object to only display the pools of your choice (for instance pools with tokens in a subset and with an active distribution).

## Display user rewards

The API lets you get for a user through the `rewardsPerToken` object how much of rewards can be claimed for a specific pool.

This object maps each reward token to the total amount of rewards accumulated on the pool (it is also inclusive of the rewards that have already been claimed) as well as to the amount of unclaimed tokens on the pool. It also details where these tokens have been earned (Uniswap V3, Gamma, ...).

## Claim user rewards

On top of displaying how much has been earned by a specific address, the API can also be used to build the payload of a claim transaction of a user which accumulated rewards.&#x20;

When called for a specific user, it returns in a `transactionData` payload the list of tokens with for each a Merkle proof to use to claim the associated rewards.

Rewards are claimable per token: meaning that if you have accumulated rewards of several tokens, you may choose to only claim your rewards of one token type, but you may also choose to claim all your token rewards at once.

The contract on which rewards should be claimed is the `Distributor` contract which address can be found on [this docs](helpers.md#🧑‍💻-smart-contracts), or on the [Angle SDK](https://github.com/AngleProtocol/sdk).

Here is a script you may use to claim all the token rewards for a user on a chain.

```typescript
import { Distributor__factory, MerklAPIData, registry } from '@angleprotocol/sdk';
import { JsonRpcSigner } from '@ethersproject/providers';
import axios from 'axios';

export const claim = async (chainId: number, signer: JsonRpcSigner) => {
  let data: MerklAPIData['transactionData'];
  try {
    data = (
      await axios.get(`https://api.angle.money/v1/merkl?chainId=${chainId}&user=${signer._address}`, {
        timeout: 5000,
      })
    ).data.transactionData;
  } catch {
    throw 'Angle API not responding';
  }
  const tokens = Object.keys(data).filter((k) => data[k].proof !== undefined);
  const claims = tokens.map((t) => data[t].claim);
  const proofs = tokens.map((t) => data[t].proof);

  const contractAddress = registry(chainId)?.Merkl?.Distributor;
  if (!contractAddress) throw 'Chain not supported';
  const contract = Distributor__factory.connect(contractAddress, signer);
  await (
    await contract.claim(
      tokens.map((t) => signer._address),
      tokens,
      claims,
      proofs as string[][]
    )
  ).wait();
};
```
