---
description: Keeper in Angle Protocol
---

# Keepers 在 Angle Protocol 的角色

- Based on:[ 🛡️ Keepers in the Angle Protocol](https://blog.angle.money/%EF%B8%8F-keepers-in-the-angle-protocol-d592f42efad0)
- Last Updated: 2022/1/14
- Author: Aaron Diong#2378
- Reviewed: licrazy#4951
- Assisted: RP#2743

Keepers 这个角色在 DeFi 的世界中，是被遗忘的那一个。他们不仅是需要维护协议并确保其处在一个健康运行的状态，有时自身还必须承受亏损。像其他的协议一样，Angle 需要借助 Keepers 来执行一些无法自动化的任务。这篇文章主要是去解释涉及在协议里头，不同的 Keeper 交易，以及为什么他们需要存在以及如何去操作他们。

![keeper](https://miro.medium.com/max/1400/0*xHjxXRYbX-89c8T3.png)

### Keepers — 去中心化协议

### 什么是 Keepers？

Keepers 通常是以机器人的形式在一些情况下与去中心化协议进行交互，以帮助协议能在安全的状态下运行。最著名的例子当属于在 Maker 以及 Aave 里头的清算机器人，他们会清算（关闭）用户账户中，那些安全指数偏低的贷款（这类情况的贷款，会导致现有的系统受到攻击，因此必须遭到清算。）

想了解更多关于 Aave 清算的内容，请查看[这里](https://docs.aave.com/faq/liquidations)。

### 为什么需要他们？

我们需要 Keepers 这个角色的主要原因是因为区块链本身的设计是一个被动的机制。当交易在需要被执行及验证时，是需要与网络进行访问交互，否则交易将无法完成。因此，为了更新协议在区块链上的数据以及完成一连串的后续动作，我们需要一个来自外部的交易来达成。一些交易是需要协议本身来执行，但却无法自动化地来进行操作，所以这一类的交易一般是交由 Keepers 代为执行操作，Keepers 因此能直接/间接地获得奖励（同时间他们也需要承担成本）。很自然地，一些人就会建立这些机器人(Keepers)来执行操作以最大化地获取这些奖励。

请注意要成为 Keepers 是完全不需要任何的认证许可，任何人都能与以太坊的网络进行交互，然后执行这些操作来获得奖励。

**Keepers 主要涉及在 Angle 协议里头的几个部分。**

### Hedging Agents 清算

在协议里头，Angle 让交易者（在协议里称为 Hedging Agents(HA) )，能够利用自身的资产（资产种类必须是被协议所接受的）作为抵押物，来开启杠杆永续合约的仓位。当仓位开启时，HA 的盈亏表现将根据潜在资产的价格涨跌的结果而定。就像其他的中心化交易所一样，这是协议的工作-确保参与的交易者所放入的抵押物价值超过他在里头如果交易失败的亏损价值，以确保协议能维持健康的偿还能力。还记得我们一开始介绍时所提到关于协议本身是属于被动的一个设计机制，它本身并不知道哪一个交易的仓位应该需要被清算。为了确保那些危险的仓位能在正确的时间内被强行清算，协议将会奖励来自外部的人士，Keepers 等，他们能够执行`PerpetualManagerFront` 合约里头的 Function `liquidatePerpetuals(list of IDs)` 来检查相关的仓位交易是否需要被清算，并执行相关清算活动（如果发现危险的仓位交易），并且获得奖励（如果相关危险仓位有被及时地清算）。

关于 USDC/EUR 和 DAI/EUR 这两个交易对的维持保证金比率是设在 0.625%（更多资料，请查看这里) ，这代表了如果保证金的比率少过整个仓位的 0.625%, 任何的 Keepers 将能够根据正确的 Perpertual ID 来执行`liquidatePerpetuals(list of IDs)`这将会导致该仓位被清算，并且将奖励发送给执行操作的 Keepers。

清算该合约仓位所获得的奖励的设计，用于 USDC 是根据（这个设计跟 FEI 以及 FRAX 的一样）：

![alt text](https://miro.medium.com/max/875/1*JJ03U_2xAgHPCd2VpGBzmA.png)

因此一个 Keeper 在一次交易里清算 n 个仓位合约，将获得：

![alt text](https://miro.medium.com/max/875/0*Tas8Xz18KJ_x--E7.png)

这个清算比率的参数（仓位合约遭清算后所剩下的数额，多少份额将会分给 Keeper），将由社群治理来决定。目前这个参数的设定为 60%（协议里头所有类型的抵押物），你可以在每一个稳定币/抵押物 的交易对所对应的[分析](https://analytics.angle.money/#/DAI/EUR)里找到相关详情。

请注意 Keeper 所获得的奖励数额，将依据该仓位合约遭清算后的数额（对比维持保证金）而定。如果资产价格下跌太多，所清算的数额有可能太微少，这将导致 Keepers 无法在执行清算后，获得任何的奖励。这也意味着 Keepers 必须在仓位合约的价值，还没跌超过维持保证金的比率之前，就事先执行清算的动作。

**摘要：**

- Keepers 执行 PerpetualManagerFront 这个合约里头的 `liquidatePerpetuals([list** of perpIDs])`→ 清算危险的仓位合约，并获得奖励。Keepers 会执行这个动作如果他能从中获利，举例：如果当时执行这个清算动作所需花费的 Gas 成本少于协议给予的清算奖励。

### Hedging Agents 强制关单

另外一个仓位需要被强行关闭的情况就是：当前有太多的仓位合约被开启，这代表协议被过度对冲了。这种情况如何发生以及为什么需要被控制，都有在这个[文章](https://blog.angle.money/angle-research-series-part-4-hedging-agents-positions-force-closing-d5a75bcd68dc)里详细解释。

与执行清算的情况一样，Keepers 执行 `function forceClosePerpetuals(list of IDs`，将根据执行后的结果获得相对应的奖励。为获得奖励，Keepers 必须将协议维持在所设定的对冲比率之下（更多详情，请参考以上提到的资料）。

![alt text](https://miro.medium.com/max/875/0*FYfimfQPPw5kev8-.png)

Estimated Cost of Attack 是指烧毁足够的 agTokens 所需的成本，以获得在仓位执行`forceClosePerpetuals(list of IDs)`的权利并获得奖励。可以参考以下的细节：

![alt text](https://miro.medium.com/max/875/0*s0v6vZ3FtsqDRQ4k.png)

在之前的研究报告有提到，Keepers 确实会被利诱去烧毁稳定币来增加对冲比率（以达到超过所限定的对冲比率的目的），这样让 Keepers 能够从操作关闭仓位合约来获利。因此协议将所能获得的奖励进行设限，以提高进行操纵的成本，来避免有心人士进行操纵。

ClosingFees 是将仓位合约关闭时所需付的费用。当执行`forceClosePerpetuals` Keepers 通常会关闭多个仓位合约。他们将会根据所关闭的仓位合约，其所收到的 closing fees 的总数，来获得相对应的奖励。

Keepers 进行关闭仓位合约的动作，以确保协议所设定的对冲比率维持在健康的比率。因此 KeeperClosingRatio 是个参数，用来决定多少的 Closing Fees 是用来奖励 Keepers 的。

由于 Keepers 能够强行关闭任何的仓位合约，让他们能够最大化获得奖励的策略并不明显。根据以上提到的奖励设计，Keepers 应该尝试去：

- 避免关闭太多的仓位合约因为 Gas 的成本可能过高
- 维持接近在协议所设定的对冲比率，`KeeperClosingRatio` 非常重要
- 关闭那些能提供足够交易手续费的仓位合约（通过仓位数额大小来计算）

**摘要:**

- Keepers 执行这个合约- PerpetualManagerFront 里头的 `forceClosePerpetuals(list of IDs)` → 强制关闭仓位合约并奖励 Keepers。Keepers 如何优化操作行为是个复杂的问题，因此 Keepers 可以选择在奖励高过 Gas 成本时，才执行操作。

**资源：**

- [Developers Doc](https://developers.angle.money/modules/perpetualmanager-hedging-agents-positions#keeper-functions)
- [PerpetualManagerFront contract](https://github.com/AngleProtocol/angle-core/blob/main/contracts/perpetualManager/PerpetualManagerFront.sol)

### Updating Strategies

Angle 将大部分协议的闲置资金投资在利率策略上，这些策略有特定的债务比率，这也代表说每个策略的投资额只能占协议资金的其中一部分。对比一开始协议存入的这些资金，长期而言，这些策略将带来盈余以及更好的资金分配。

像之前所说的，协议本身是处于被动的形式，因此需要依靠 Keepers 来执行协议的更新，例如：债务比率，从不同的策略中存入/提出资金，更新从不同策略里所赚取的盈余资料。

举例：如果最近有许多的资金存入协议中，一些 Keepers 需要在合约中执行 function `harvest()`以让协议里的资金被善用来投资。

目前为止，执行 function `harvest()`没有任何的奖励，是由团队定期地执行 function。如果有需要的话，治理代币能够作为其操作的奖励。

**摘要:**

- Keepers 执行`harvest()` → 更新关于策略的盈亏/债务比率

**资源：**

- [Developer Doc](https://developers.angle.money/side-smart-contract-modules/adapters/strategies#external-functions)
- [BaseStrategy contract](https://github.com/AngleProtocol/angle-core/blob/main/contracts/strategies/BaseStrategy.sol)

**更新质押的分配**

RewardsDistributor 里面的 function `drip(stakingContractAddresses)`能够根据合约里之前设定好的奖励分配，将代币分发给特定的质押合约。条件是这个 function 在指定的时间前（目前是 7 天）,不能执行该 function。

执行这个 function,将会获得 ANGLE 代币作为奖励（目前设定为 100 ANGLE 代币），目前已经计划会更新该奖励的数额。

**摘要：**

- Keepers 执行合约里头的`drip()`function → 奖励将会分配给不同的质押合约。

**资源：**

- [Developers Doc](https://developers.angle.money/side-smart-contract-modules/rewards-distributor-organizing-rewards#external-function-for-keepers)
- [RewardsDistributor contract](https://github.com/AngleProtocol/angle-core/blob/main/contracts/staking/RewardsDistributor.sol)

**根据抵押物比率来调整费用**

在 Angle 协议里头，一些费用调整的机制，能根据协议的抵押物比率来鼓励 用户在协议中进行一些行为。这些机制主要由社区治理提出，费用将根据抵押物的比率来进行调整。

举例：如果协议目前的抵押物比率低过标准水平，SLP 的存币费用可以调低，并且调高提币费用，这就能吸引用户进行存币的动作而不是提币。

在链上计算这些抵押物比率的成本相当高，这导致在协议更新每一笔交易的方法，变得不切实际。因此协议需要依赖 Keepers 这个角色来计算以及更新费用的资料。Keepers 能通过执行这两个 functions - `updateUsersSLP()` , `updateHA()` 来达到。执行这两个 functions 没有任何的奖励。

- Keepers 执行合约里头的 functions `updateUsersSLP()` , `updateHA()` → 关于用户，SLP (Standard Liquidity Providers), HA(Hedging Agents) 的费用调整，将能及时反映协议的抵押物比率的变动。

请注意这个用来调整费用来应付抵押物比率变动的计划还没开始实行，目前只有 SLP 的滑点会根据抵押物比率变动而调整。

**资源**

- [Developers Doc](https://developers.angle.money/side-smart-contract-modules/feemanager-parameters-setting#external-keeper-functions)
- [FeeManager contract](https://github.com/AngleProtocol/angle-core/blob/main/contracts/feeManager/FeeManager.sol)

**Angle keepers and MEV**

对于那些在 Angle 协议贡献的 Keepers，有一点需要强调的就是，你是不需要付出任何的资金，来执行以获得奖励。对比 Maker 这个协议，要获得清算的资格是必须通过一个拍卖的形式，代表说 Keepers 需要付出资金来参与。而在 Angle 的情况是，执行清算的动作只需通知协议说，哪些仓位合约需要被清算就完成了。当然这也会导致一些 Keepers 的交易会被一些套利机器人发现而被 front-ran 的风险。

有一个方法能够规避这个问题，就是采用 RPC 的 flashbot，详情可以参考这个[链接](https://docs.flashbots.net/flashbots-protect/overview/)。

**总结**

Keepers 是一个比较困难去理解的概念，但它不至于到非常复杂。基本上，Keepers 就是用户通过操作机器人，来监督去中心化协议里头的情况。当他们发现一些指定的信号，他们通过执行一些交易来更新以换得奖励。这个需求的诞生也正好是因为区块链本身是一个被动的机制。

在 Angle 协议里头，Keepers 需要做的是：

1. 清算以及强制关闭相关 Hedging Agents 的仓位合约
2. 更新策略的盈余以及债务比率
3. 更新质押的分配
4. 根据抵押物比率的变动来调整费用

关于 functions (2),(3),(4)的奖励还没完全设定完毕，因此这些 functions 目前为团队代为执行。虽然如此，我们欢迎任何用户来执行这些 function，我们计划在未来的几个月内调整这些奖励。

### 想了解更多？加入我们的社群吧！📐

[Twitter](https://twitter.com/AngleDevs) | [Discord](https://discord.gg/9EKFec2MBm) | [Docs](https://docs.angle.money/)
