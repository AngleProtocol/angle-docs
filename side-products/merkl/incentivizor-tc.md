---
description: Please be aware of the following before depositing an incentive on Merkl
---

# 🖋 Incentivizor Disclaimer

1. Merkl is experimental software provided as is, use it at your own discretion. There may notably be delays in the on-chain Merkle root updates and there may be flaws in the script or in the infrastructure used to update results on-chain. In that regard, everyone can permissionlessly dispute the rewards which are posted on-chain, and when creating a distribution, you are responsible for checking the results and eventually dispute them.
2. If you are specifying an invalid pool address or a pool from an AMM that is not marked as supported, your rewards will not be taken into account and you will not be able to recover them.
3. If you are adding a liquidity position manager address corresponding to a solution that is not supported by Merkl, it will not be taken into account by the script.
4. Fees apply to incentives deposited on Merkl, unless the pools incentivized contain a whitelisted token (e.g an Angle Protocol stablecoin).
5. By interacting with the Merkl smart contract to deposit an incentive for a pool, you are exposed to smart contract risk and to the off-chain mechanism used to compute reward distribution.
6. If the rewards you are sending are too small in value, or if you are sending rewards using a token that is not approved for it, your rewards will not be handled by the script, and they will be lost.
7. If you mistakenly send too much rewards compared with what you wanted to send, you will not be able to call them back. You will also not be able to prematurely end a reward distribution once created.
8. The script handling reward distribution for a pool may not look at all the swaps occuring on the pool during the time for which you are incentivizing, but just at a subset of it to gain in efficiency. Overall, if you distribute incentives using Merkl, it means that you are aware of how the script works, of the approximations it makes and of the behaviors it may trigger (e.g. just in time liquidity).
9. Rewards corresponding to incentives distributed through Merkl do not compound block by block, but are regularly made available (through a Merkle root update) at a frequency which depends on the chain.
