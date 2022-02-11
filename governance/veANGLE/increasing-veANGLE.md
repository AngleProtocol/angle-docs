---
description: Details about adding ANGLE to your lock
---

# 🔓 Increasing your veANGLE balance

There are two ways to increase an address balance of veANGLE:

- extend the lock expiration date
- add ANGLE to the lock

Increasing veANGLE balance has three impacts:

- increase voting power
- **potentially** increase boost
- increase weekly interest distribution

## Voting Power

When increasing the veANGLE balance of an address, its voting power increases accordingly. However, if the voting power was already allocated, users will have to apply it again.

**Let’s look at it from an example:**

Let’s say that Carol locks 90 ANGLE for 4 years, giving her a balance of 90 veANGLE, and allocates only 50% of her votes to Gauge A. This will take into account 45 veANGLE to allocate to Gauge A.

A year later, Carol’s veANGLE balance will have decreased by 25% as the lock expiration gets closer. She will have 0.75\*90 = 67.5 veANGLE. The voting power allocated to Gauge A is currently 33.75 veANGLE.

Now, Carol decides to push back her lock’s expiration to 4 years later again, which gives her back her original balance of 90veANGLE. She also adds 10 ANGLE to the lock, such that she has a 100 veANGLE balance.

Her voting power is now 100 veANGLE. **However,** only 33.75 of her total veANGLE balance is currently allocated to Gauge A. She needs to re-apply her votes for the balance increase to take effect.

If she want to put 50% of her 100 veANGLE balance on Gauge A, she needs to do another voting transaction, allocating 50% to Gauge A. This new voting tx will take into account the new 100 veANGLE balance, and allocate half to this gauge.

If she had allocated all her voting power on multiple gauges, she would have to re-apply all of these votes with the new weights she wants to allocate.

#### Conclusion

As we can see, increasing one’s veANGLE balance provides more voting power, but comes at the cost of having to apply all votes again.

## Boost

One might think that increasing veANGLE balance simply increase your boost. However, this is more complicated than that.

As detailed in the boost page, a user’s boost depends on their share of veANGLE in total, compared to their share of liquidity in the pool at the moment they apply their boost. The more someone has liquidity in a pool, the higher share of veANGLE they need to have the max boost.

A user’ boost in a pool doesn’t decrease continuously as their veANGLE balance does, but updates only on two specific occasions when:

- They deposit, withdraw, or call the user_checkpoint() function from the liquidity gauge contract.
- Other users call the kick() function on another address, if this address has an expired lock, or if it extended or added to it and should have a lower boost.

**Let’s look at another example**

Bob had originally locked 90 ANGLE for four years like Carol. One year later, he has the same 67.5 veANGLE balance than Carol. Bob is not interested by his voting power, but only by his boost. He wants to extend his lock to four years again, and add 10 ANGLE to get to 100 veANGLE and increase his boost.

However, other external factors, such as the total veANGLE supply or the pool liquidity might have changed. It might be possible that updating his boost will actually decrease it (see the boost page details).

Because of that, Bob should actually use the calculator at ... to make sure that he would meet the necessary veANGLE balance he needs for his deposit to get the specific boost he wants. Otherwise, he would have locked ANGLE for nothing, and other users could call the kick() function and reduce his boost.

#### Conclusion

Increasing one’s veANGLE balance doesn’t necessarily increase its boost. Always make sure to verify in the calculator the veANGLE balance needed to get the max boost depending on the amount of tokens you are staking on the gauge.

## Weekly Interest Distribution

The weekly interest distribution happens every week on Thursday (European Time). At the beginning of the week on the previous Thursday, a snapshot of all veANGLE holders with their balances is recorded to process the interest distribution accordingly.

As such, an increase in veANGLE balance is directly linked to an increase in the share of interest an address will receive.
