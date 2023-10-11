# Potential wait times while staking

## Dilution queue

When there is a quick surge in the number of users trying to stake through the staking pool, onboarding stakers might be placed in a queue, which will delay the minting of new sLYX. This cap protects already-established stakers, whose stake is effectively generating rewards, from reward dilution due to yet-to-be-activated stake by onboarding users. Currently, the protocol mints sLYX until it has 10% of the total staked value in a pre-activation state. When it reaches this threshold, sLYX will be minted at the rate validators are activated, and the stake starts generating rewards.

The activation time in the Proof of Stake protocol spans from when the deposit is accepted by the official contract to when the new validator starts validating, thus collecting rewards. This can range from a few hours to a few days, depending on how many new validators are trying to register on LUKSO at the same time. See [activation queue](potential-wait-times-while-staking.md#activation-queue) for more details.

To LEEQUID users, this timespan translates into a gap between the moment the user presses the stake button and the moment sLYX tokens can be minted for him. For this reason, in a time of congestion, a user might need to check the platform at a later date to claim his sLYX and start accruing rewards. There are some factors that improve the chance of being added to the dilution queue:

* The amount being staked is considerably high in relation to the pool’s total
* There is currently a surge in the number of users staking through LEEQUID at roughly the same time
* There is currently a lack of users trying to exit LEEQUID
* There is currently a long activation queue in the LUKSO Proof of Stake protocol

If there is an amount equivalent to more than 10% of the total active stake waiting in line to become activated, then new stakers won’t get sLYX immediately but instead will have to wait until their sLYX is available to claim and send a second transaction. This way, the impact of new stakers receiving rewards while their stake doesn’t get activated is minimized.

## Activation queue

The activation queue happens at the LUKSO Proof of Stake protocol level and depends on the number of new validators trying to join the Proof of Stake consensus at the same time. Validators can’t simply be switched “on” and “off”; they go through a number of different states in their activation process and also in their exit process. In the beginning, the protocol needs to onboard new validators and assign them a position in the consensus algorithm. For that, a minimum of 8 hours will pass until the validators transition from the deposited to the active state.

However, there is a limit to how many validators can join consensus in a certain time frame. This limit is called the _churn limit_ and starts at 4 validators per epoch (6.4 minutes), increasing with the total number of validators in the protocol, up to a maximum of 10. When the limit is reached, new validators are put in a first-in/first-out queue, waiting for their turn to become active and collect rewards. This queue can last for a few days.

As a LEEQUID user, you will not feel the impact of the activation queue directly. Most of the time, staking will be a seamless experience and you will start accruing rewards straight away. That's because the LEEQUID protocol has a certain capacity to mint sLYX, even if some of the new stake is not yet active in validators. This generates what is called "reward dilution" and can affect established stakers. For that reason, there is a threshold to how much the protocol can take of "unactivated" LYX. See [dilution queue](potential-wait-times-while-staking.md#dilution-queue) for more details.

It might happen that due to the size of the activation queue, incoming stake requests take longer to activate, which in turn might result in the establishment of a dilution queue. In this scenario, the minting of new sLYX is delayed and you will have to return to the platform at a later time to claim your staked tokens.&#x20;
