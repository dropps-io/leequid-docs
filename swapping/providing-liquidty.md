# Providing liquidty

## Being a liquidity provider

Swapping through liquidity pools is only possible because there are people willing to take any side of the trade, in exchange for a small fee. These actors are called “liquidity providers” and they are crucial in automated market making protocols. Liquidity providers deposit their capital in a smart contract called a liquidity pool, which will automatically and instantly complete incoming trade orders by taking the opposite side. The price is established mathematically, according to the formula **x \* y = k**, where **x** and **y** are the quantities of each token in the pool.

In order to provide liquidity, a user needs to deposit both “x” and “y” tokens in the pool in proportion to the already existing ratio, respecting the established value of “k” in the formula above. The calculation of these values is done automatically by the liquidity pool smart contract.

After providing liquidity, a special token called an LP (Liquidity Provider) token will be minted to the provider’s account. This token is equivalent to shares of the pool, which can be redeemed at any time yielding an amount equivalent to the quantities initially deposited, but now in proportion to the current ratio between the pair (x, y).

A pool with large reserves of capital deposited in it is considered highly liquid and it is capable of handling large swap requests without skewing the price significantly. On the other hand, when the pool has low liquidity, a reasonable swap size will tilt the pool too much, and the swap will incur in a loss called _slippage_. Due to the tilting of the price during the swap, the ratio will “slip” against the swapper, making him pay a higher price for his tokens than what was initially calculated, at the current ratio. This is the reason why high liquidity is a good indicator of protocol health.

The bigger the trade volume a pool sustains every day, the higher the returns for the liquidity providers, who earn a part of their income through trading fees. In each trade, the fee is taken from the trader and deposited into the pool, increasing the worth of each share held by the liquidity providers, consequently making LP tokens more valuable.

## How to provide liquidity through the LEEQUID platform

Head over to “Swap” in the main menu and then to the “Liquidity Pool” tab. Here you will have the option to either add or remove liquidity. Before adding liquidity, make sure you have enough sLYX and LYX in your wallet. The interface will tell you the exact quantities for the current ratio. Submit the necessary transactions and you're done. From now on, you can check the total amount of fees you have accrued in the liquidity pool dashboard with your wallet connected.

## Collecting staking rewards while providing liquidity

When a user provides liquidity, he doesn’t miss incoming rewards on his sLYX tokens. In fact, the protocol will accrue both staking rewards and liquidity provider rewards to his address. However, it’s important to note that, in order to exit the staking pool, a liquidity provider will first need to remove the liquidity and afterwards initiate an unstake request.
