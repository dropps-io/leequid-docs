# Potential unpeg of sLYX from LYX

The fundamental assumption that makes sLYX a liquid substitute of LYX is that the amount of sLYX in circulation will always be less than or equal to the amount of LYX staked in the LEEQUID protocol.&#x20;

$$
sLYXCirculation <= LYXlocked
$$

There are, however, theoretical scenarios where such assumption might not hold. Validators can get slashed resulting in some of the LYX in the LEEQUID protocol being burned. On the other hand, an incorrect reading of all the oracles that provide the rewards for a period, i.e., an overestimation of the total rewards, can result in more rewards being available for withdraw than those actually accrued by the protocol.

Because the peg relies on external actors, real world events such as the ones stated in the previous paragraph might (or might not) affect the price of sLYX. In fact, there are even other forces at play, not related to protocol failures but to economic factors, that can drive the price of sLYX away from LYX:

1. **Lack of arbitrageur competition:** Because LUKSO is a new blockchain, it will take a while until the market grows and attracts a healthy ecosystem of participants and protocols.&#x20;
2. **Low liquidity in the pool:** In this scenario, a substantial trade might skew the price so much that it will trigger alert reactions in all the users and protocols tied to the sLYX token. On developed markets, this could trigger stop loss actions and initiate a cascade of events that would delay the returning of the peg to normal. Furthermore, a new, more profitable DeFi protocol might appear that will attract the capital once used to provide liquidity. You can read more about mechanisms to deal with this scenario in the [protocol security](../protocol-security-and-risks/slyx-token-economic-balance.md) section.
3. **Fear, uncertainty and doubt (FUD):** Any rumor can cause FUD. However, let's analyse a theoretically possible situation instead: if LEEQUID validators get slashed, the 1:1 ratio no longer holds at the protocol level, as it now owns less LYX than the total sLYX in circulation. This is because LYX was burned in the slashing event, but no sLYX could be burnt to account for the loss. In this event, we can say that sLYX is now in an undercollateralized situation, which can only be restored by manually increasing the protocol’s reserves of LYX. Such scenario can generate a fearful sentiment in the market, which will cascade a series of events that will lead to the unpeg of sLYX; fear triggers a surge in withdrawals and a halt in deposits; withdrawals skew the ratio in the liquidity pool; liquidity providers remove liquidity due to fear of losses; the ratio skews even more due to lower liquidity; the price of sLYX will fall until it is at par with market sentiment. However, there is now a huge arbitrage opportunity and as soon as FUD dissipates, the peg will quickly be restored.&#x20;
