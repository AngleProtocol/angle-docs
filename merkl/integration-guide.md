---
description: Guide to integrate Merkl in your app for your incentives distribution
---

# 📒 Integrate Merkl in your App

You can integrate Merkl pools in your app but you don't have to. All pools are listed on the [Merkl App](https://merkl.angle.money/), and users can claim their tokens from there. This doc will guide you through the different options to integrate Merkl in your app.

![Merkl front integration diagram](../../.gitbook/assets/docs-merkl-front-integration.jpg)

Data about all Merkl incentivized pools across all supported chains can be found by calling our API endpoint: `https://api.angle.money/v2/merkl`.

When calling this payload, you may specify a list of `chainIds` to query or a list of `AMMs` on which you specifically want some information. You may also specify a `user` address if you want additional information related to one user (like claimable amounts, liquidity in the pools, ...).

A typical query looks like: [`https://api.angle.money/v2/merkl?chainIds[]=1&AMMs[]=uniswapv3&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185`](https://api.angle.money/v2/merkl?chainIds[]=1&AMMs[]=uniswapv3&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185).

{% hint style="info" %}
The schema and docs for the Merkl API endpoint can be found [here](https://api.angle.money/api-docs/#/Merkl/get_v2_merkl).
{% endhint %}

## Listing incentivized pools

When called for a specific chain, the API returns in a `pools` object a mapping between pool addresses of this chain (like Uniswap V3 pool addresses) and details on the APRs for providing liquidity.

Note that because how concentrated liquidity AMMs and the way the script works, two LPs with different positions may earn drastically different returns. As such, APRs displayed here are average measures of the returns LPs can earn. If you are to integrate Merkl in your app, you may want to build the APR indicators tailored to your use cases.

The `pools` object also has details about the past distributions for each incentivized pool: their start and end dates, the parameters set and the amount of incentives for each distribution.

You can filter from the `pools` object to only display the pools of your choice (for instance pools with tokens in a subset and with an active distribution).

## Displaying user rewards

The `rewardsPerToken` object lets you get how much rewards of a specific token can be claimed by a user for a specific pool.

This object maps each reward token to the total amount of rewards accumulated on the pool for a user. It includes the rewards that have already been claimed as well as to the amount of unclaimed tokens on the pool. It also details where these tokens have been earned (Uniswap V3, Gamma, ...).

## Claiming user rewards

On top of displaying how much has been earned by a specific address, the API can also be used to build the payload of a claim transaction for a user which accumulated rewards.

When called for a specific user, it returns in a `transactionData` payload with the list of `tokens` to claim, the `amounts`, and a Merkle `proof` required to claim each of them.

_Rewards are claimable per token: meaning that if you have accumulated rewards of several tokens, you may choose to only claim your rewards of one token type, but you may also choose to claim all your token rewards at once._

The contract on which rewards should be claimed is the `Distributor` contract which address can be found on [this docs](./supported-chains-amms.md).

You have two options to do that:

- Rely on Angle's API: we build the claim transaction payload for you and the associated proof, and you just call our API. This is the example shown below.
- Build the proof yourself and join it to the transaction data from the API. You can find a Github repository below showing how to do that.

{% hint style="info" %}
In any case, if a call is made to the correct `Distributor` contract and the `token` or `amount` doesn't match the `proof`, the transaction will revert.
{% endhint %}

Here is a script you may use to claim all the token rewards for a user on a chain.

```typescript
import { JsonRpcSigner } from "@ethersproject/providers";
import { ethers } from "hardhat";
import axios from "axios";

export const claim = async (chainId: number, signer: JsonRpcSigner) => {
  try {
    data = (
      await axios.get(
        `https://api.angle.money/v2/merkl?chainIds[]=${chainId}&user=${signer._address}`,
        {
          timeout: 5000,
        }
      )
    ).data[chainId].transactionData;
  } catch {
    throw "Angle API not responding";
  }
  // Distributor address is the same across different chains
  const contractAddress = "0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae";
  const tokens = Object.keys(data).filter((k) => data[k].proof !== undefined);
  const claims = tokens.map((t) => data[t].claim);
  const proofs = tokens.map((t) => data[t].proof);

  const contractAddress = registry(chainId)?.Merkl?.Distributor;
  const distributorInterface = new ethers.utils.Interface([
    "function claim(address[] calldata users, address[] calldata tokens, uint256[] calldata amounts, bytes32[][] calldata proofs) external",
  ]);

  const contract = new ethers.Contract(
    contractAddress,
    distributorInterface,
    signer
  );

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

## Tracking user rewards without the API

The [merkl-rewards](https://merkl-rewards.angle.money/) website contains the history of rewards given across all distributions across all pools of all supported AMMs. If you want to see which addresses earned the most from a distribution, or if the biggest LPs in the pool you're incentivizing are also active in other Merkl-incentivized pools, you may want to check this repo.

## Featuring Merkl in your app

If you have integrated Merkl pools in your app, you can showcase it by showing the following logo:

![Powered by Merkl](/.gitbook/assets/powered-by-merkl-dark.png)

![Powered by Merkl](/.gitbook/assets/powered-by-merkl-light.png)

Please add a link on the images redirecting to [merkl.angle.money](https://merkl.angle.money)

### Other logos

Here are other Merkl logos you can use for communication:

![Merkl full logo dark](/.gitbook/assets/angle-merkl-logo-dark.png)

![Merkl logo dark](/.gitbook/assets/merkl-logo-dark.png)

#### SVG

![Merkl logo light](/.gitbook/assets/merkl-landscape.png)

![Merkl icon](/.gitbook/assets/merkl-logo-icon.png)

#### Banner

![Merkl sharing visual](/.gitbook/assets/angle-merkl-sharing-visual.png)
