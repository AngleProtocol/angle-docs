---
description: Guide to integrate Merkl in your app
---

# 📒 Integration Guide

Data about all Merkl incentivized pools across all supported chains can be found by calling our API endpoint: `https://api.angle.money/v1/merkl`.

When calling this payload, you must specify the `chainId` and a `user` address. If you're not interested in fetching info for a specific user, you can specify a random user address.

A typical query then looks like: [`https://api.angle.money/v1/merkl?chainId=10&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185`](https://api.angle.money/v1/merkl?chainId=10&user=0xfdA462548Ce04282f4B6D6619823a7C64Fdc0185).

## List incentivized pools

The API returns when called for a chain in a `pools` object a mapping between pool addresses (like Uniswap V3 pool addresses) and for each details on the APRs for providing liquidity in the pool.

On the APR, note that on concentrated liquidity AMMs, because of the way the script works, two LPs with different APRs, may earn drastically different returns. As such, APRs given here are average measures of the returns a LP could earn. You may want to build the APR indicators tailored to your use cases.

The `pools` object also has for each pool that has ever been incentivized details about the different distributions: their start and end dates, the parameters set for this distribution, the amount of incentives.

You can then filter from there to display the pools of your choice (for instance pools with tokens in a subset and with an active distribution).

## Display user rewards

The API lets you get for a user through the `rewardsPerToken` object how much of rewards can be claimed for a specific pool.

This object maps each reward token to the total amount of rewards accumulated on the pool (it is also inclusive of the rewards that have already been claimed) as well as to the amount of unclaimed tokens on the pool. It also details where these tokens have been earned (Uniswap V3, Gamma, ...).

## Claim user rewards

The API can be used to build the payload of a claim transaction of a user which accumulated rewards. When called for a specific user, it returns in a `transactionData` payload the list of tokens with for each the amount that can be claimed, and the Merkle proof to use to claim the rewards.

Rewards are claimable per token: meaning that if you have accumulated rewards of several tokens, you may choose to only claim your rewards of one token type, but you may also choose to claim all your token rewards at once.

The contract on which rewards should be claimed is the `Distributor` contract which address can be found on [this docs](helpers.md#🧑‍💻-smart-contracts), or on the [Angle SDK](https://github.com/AngleProtocol/sdk).

Here is [a script](https://gist.github.com/Picodes/306bcaef48e68ef4999d49a155cf9cec) you may use to claim all the token rewards for a user on a chain.
