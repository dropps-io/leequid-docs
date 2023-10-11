# 1:1 ratio with LYX

## The sLYX peg to LYX

Every single sLYX represents a share in the staking pool, i.e., the right to redeem 1 LYX from the pool at any time. The LEEQUID protocol has no way of spending the LYX that goes through it and no sLYX can be minted beyond the LYX ever received. For this reason, we say that sLYX is a Liquid Staking Derivative token (LSD token), backed one-to-one by LYX within LUKSO’s official deposit contract.

When the sLYX is returned to the protocol (by unstaking) it is burned and the corresponding amount of LYX is given in exchange. No sLYX can be taken out of circulation without the same amount of LYX exiting the protocol, otherwise, the 1:1 ratio in the pool would be broken.

## Market forces that drive the 1:1 price ratio in the sLYX / LYX pair

Because the protocol ensures that every unit of sLYX is backed by a unit of LYX (as seen [above](1-1-ratio-with-lyx.md#the-slyx-peg-to-lyx)), it guarantees that a user will always be able to trade between the two at this fixed ratio. To do this, a user must stake or unstake through the staking pool and not through the liquidity pool.

There is no protocol-enforced mechanism to maintain the 1:1 price ratio in the sLYX / LYX pair. The balances of the tokens in the liquidity pool depend on the trading activity; should there be considerable trade movement towards one side, the price of the sLYX token will move away from 1 LYX.

This situation of imbalance creates an opportunity for arbitrage, as arbitrageurs can always either obtain LYX or sLYX at the fixed ratio of 1:1 by going through the staking pool. Arbitrageurs, especially automated ones, might constantly monitor the liquidity pool for opportunities to make small profits, and every time they do an arbitrage trade, they correct the price back to the initial 1:1 ratio. This market force is the pegging mechanism that binds sLYX to LYX outside the staking pool and creates reliable conditions (price stability and liquidity) for the usage of sLYX in other DeFi protocols, or even as a currency.

