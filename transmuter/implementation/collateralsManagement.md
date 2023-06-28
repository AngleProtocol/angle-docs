---
description: How Transmuter can adjust its mechanisms for some specific collateral assets
---

# 📄 Collateral Assets Management and Whitelist

## 🤝 Collateral Whitelist

Transmuter is compatible with assets for which holders may be permissionned. There is the option to make some specific collateral assets whitelisted, in the sense that only some addresses are eligible to burn for this asset or receive it during a redemption. This can typically apply to the case of security tokens which cannot be permissionlessly sent to any address.

The consequence of having such whitelisted assets in the system is that the full expressivity and fairness of Transmuter is only available to addresses who are whitelisted.

If there is a whitelisted collateral in the system representing 20% of the reserves and the protocol is collateralized at 100%, then a non whitelisted address will only be able to get 80% of the value of the stablecoin during a redemption (as it is not be eligible to receive the whitelisted token), while a whitelisted address will get 100% of it. Note that non-whitelisted addresses can still burn in this case for collateral assets that do not require the whitelist.

As the redemption feature is mostly designed for advanced market makers and arbitrageurs who should be whitelisted anyway, having whitelisted collateral assets in the system induces more friction in the redemption process but does not impact the Transmuter's ability to get the stablecoin priced at the fair value of its reserves on the secondary market.

Depending on the assets, different types of whitelists may apply and the management of whitelists is delegated to the protocol governance or to external trusted systems.

{% hint style="info" %}
The state of whether whitelisted collateral assets are supported for agEUR can be found in [Angle Analytics](https://analytics.angle.money).
{% endhint %}

## 🌾 Collateral Management

While collateral assets in Transmuter remain by default idle in the contract, the system supports the possibility to plug manager contracts or strategies to generate a yield on the assets in the backing.

{% hint style="info" %}
While possible, this feature is not activated so far for any of the agEUR collateral assets. It could be activated on a per asset level by the protocol governance.
{% endhint %}

Investing a portion of the reserves of Transmuter in yield strategies can enable it to get over-collateralized over time and to build a safety buffer for future depegs of assets in the system. If the protocol gets badly collateralized, this kind of mechanism may also help the protocol slowly re-collateralize itself.

This comes with an extra composability risk if the underlying protocols in which the strategies invest get hacked or if the strategies make a loss. To maintain the invariant about redemptions and eliminate bank run effects in case of a loss in a strategy, such manager contracts must send the underlying tokens they are controlling during a redemption. The oracles for assets which are invested in yield strategies should also take into account the state of the strategies in which they are invested.

For instance if $$\texttt{EUR}_A$$ is invested on Aave, the protocol will control $$a\texttt{EUR}_A$$. During a redemption, the protocol should send users a basket of $$\texttt{EUR}_A$$ and $$a\texttt{EUR}_A$$ based on what is invested. If Aave gets hacked, this guarantees that first users will not be getting more than the ones coming afterwards. The deviation value in the oracle for $$\texttt{EUR}_A$$ would also need to take into account the fact that the system does not only have $$\texttt{EUR}_A$$ but also $$a\texttt{EUR}_A$$ which decreased in value.
