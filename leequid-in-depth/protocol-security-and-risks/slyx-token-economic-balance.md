# sLYX token: economic balance

#### Description

Even if sLYX is backed 1:1 by LYX, its exchange value can still go below one LYX, as users swapping in the liquidity pool naturally alter the sLYX to LYX ratio, thus impacting the price. The peg of sLYX to LYX, which we can define as the attachment of the sLYX price to 1 LYX, is not a protocolized mechanism. Instead, it relies on market forces driving external actors in order to be maintained. A more thorough explanation on the economic factors driving the peg can be found in the [sLYX token section](../the-slyx-token/1-1-ratio-with-lyx.md#market-forces-that-drive-the-1-1-price-ratio-in-the-slyx-lyx-pair). When these market forces behave unexpectedly, whether it be motivated by generic FUD (Fear, Uncertainty and Doubt), software bugs, hacks, or just the appearance of new forces that upset the current equilibrium, the 1:1 ratio in the pool might skew considerably and take longer to recover.&#x20;

Nothing happens to liquid stakers if there is an unpeg, unless there is a huge surge in withdrawal requests and sLYX to LYX swaps in the liquidity pool. In this scenario, because the sLYX is now undercollateralized (there's more sLYX than LYX), some users will face problems of lack of liquidity, being temporarily unable to withdraw their LYX.

#### Prevention mechanisms

* Allocate a part of the team's funds to provide liquidity in the liquidity pool. The higher the liquidity, the harder it will be for the price to move due to the volume of swaps (an event called slippage). The impact of single trades will be minimized, allowing a bigger timeframe for the natural restoration of balance due to protocol use, or for arbitrageurs to come through and take a small profit to balance the ratios in the pool.
* Provide incentives to liquidity providers. If there is a good APR for providing liquidity, mainly coming from trading fees and liquidity mining programs, more liquidity can be drawn into the protocol, reducing slippage in swaps.&#x20;
* Act quickly in the event of protocol losses. If the protocol experiences any kind of error, even without any loss being accounted, general FUD (fear, uncertainty and doubt) might trigger a cascade of withdrawal requests and sLYX to LYX swaps that will be responsible for a temporarily lack of liquidity in the protocol.
