# Opening Leveraged Positions on Angle

## Opening

1. To open a position on Angle, you first need to select a collateral/stablecoin pair.
2. Then, you need the select the position size of your choice that is the amount of collateral from the protocol for which you are exposed to the volatility
3. Then, similarly to an isolated-margin exchange, you need to select the amount of collateral you want to lock in Angle as margin for your position or the leverage for it. Leverage in Angle is computed as $$(margin + position Size)/margin$$.
4. The collateral/stablecoin exchange rate and fee are displayed.
5. You then need to approve your collateral.
6. If you want to get protected from variations of prices or of transaction fees between the moment where you send your transaction and the moment at which it is executed, there is an expert mode available on the top right hand corner.
7. Clicking the `Open position` button will send the margin to the protocol and open the leveraged position.

{% hint style="warning" %}
Be careful, when opening a position, updating and closing will be locked for an hour. More info [here](app-faq.md).
{% endhint %}

## Updating

If you have some open positions, you might want to add or remove margin to some of them. Doing so will update your leverage and change your liquidation price. There is no fee for updating margin.

1. On the HA positions page, click on the `Update` button.
2. Enter an amount of collateral to add or remove from your position, or change its leverage. You can remove collateral up to reaching the max leverage on your position (x10).
3. You will find current and updated info about your position.
4. Then, just confirm the transaction and it will send/withdraw the amount of collateral that was specified.
5. After the transaction is confirmed, you can go back to the Positions page to see your updated position.

## Closing

1. To close a position, click on the `Close` button of the positions you would like to close.
2. Your position opening and current prices, as well as the total cash out amount are displayed.
3. Click on the `Close` button to confirm the transaction and receive the cash out amount (margin ± PnL).

{% hint style="info" %} Upon closing a position, there is also an expert mode to protect for important slippage in price or in fees.
{% endhint %}
