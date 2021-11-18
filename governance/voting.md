---
description: Voting to adjust ANGLE Liquidity Mining weights across different pools
---

# 🏋️ Liquidity Mining Weights

The Angle system allows ANGLE holders to vote how ANGLE Liquidity Mining rewards are distributed by assigning weights to the different pools and protocols.

## Voting Rules and Information

* Voting will be done via [Snapshot](https://snapshot.org/#/anglegovernance.eth/)
* There will be weekly weight votes, starting Fridays at 10 am CET and ending on Tuesdays at 10 am CET. Liquidity mining weights are updated every Wednesday at 5pm CET. Other propositions may be addressed as they arrive.
* Weight votes have no quorum
* Individual ANGLE holders may spread their votes among multiple pools in weight votes
* Each pool must receive at least 0.5% of the votes before weight is assigned
* In some occasions, pools will be proposed in Snapshot votes in anticipation of their future creation by an external actor (like for instance an incentivized Curve pool). In these situations, it is possible that the pool is not ready in time for the start of the reward distribution on Wednesday. In this case, weights from these pools will be distributed to other pools in proportion of their vote weight.
* On the same page, during the week, and as it's still the early days of the protocol, it is possible that a pool that was not foreseen by community at the start of the week ends up requiring a strategic importance for the protocol and thus needs to be incentivized rapidly. In such a rare situation, the Core Team will try to adapt weights following community and voters feedback about it.
* New pools (that are not directly pools related to the Angle protocol like stablecoins pools, sanTokens pools or HA pools) may be proposed through Snapshot votes.

{% hint style="info" %}
An Angle Protocol governance tokens multi-sig is still required to reflect the outcomes of Angle Snapshot votes. This multi-sig is for the moment controlled by members of the Angle Core Team. In almost all cases, the multi-sig will make sure to reflect what ANGLE holders voted for. However, proposals considered to be blatant attacks against Angle or another protocol are not going to be signed for.
{% endhint %}

{% hint style="info" %}
When implementing the results of the weights votes, there may be rounding errors due to how distributed amounts to staking contracts are computed. These are time-dependent and depending on when the transaction is passed the amount distributed may not be the exact amount voted by ANGLE owners. Angle Protocol multi-sig will however make sure to remain as close as possible to votes.
{% endhint %}
