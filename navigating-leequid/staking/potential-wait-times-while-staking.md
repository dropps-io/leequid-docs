# Potential wait times while staking

**Usually, staking in LEEQUID will be a fluid process with no wait times**. However, there are constraints in the Proof of Stake protocol than can affect the staking pool. In this section, we'll learn more about them and how they interact with LEEQUID.

## State transitions in the staking process

Before proceeding, keep in mind that none of the timespans mentioned in the sections below apply to the regular staking flow of LEEQUID. This is relevant in the exceptional cases where "unactivated" stake in the LEEQUID staking pool reaches 10% of total stake. In that scenario, the dilution mechanisms come into play, and indeed they interact with the waiting times in the Proof of Stake protocol.&#x20;

With this said, below is a diagram of the validator lifecycle inside the Proof of Stake protocol:&#x20;

<figure><img src="../../.gitbook/assets/Validator_states (2).png" alt=""><figcaption><p>source: <a href="https://docs.prylabs.network/docs/how-prysm-works/validator-lifecycle">https://docs.prylabs.network/docs/how-prysm-works/validator-lifecycle</a></p></figcaption></figure>

Every time a multiple of 32 LYX is sitting in the LEEQUID staking pool for while, the protocol will pick it up and deposit that LYX in LUKSO's official deposit contract, thus triggering the activation of new validators. &#x20;

If the volume of deposits is high, this activation process takes longer, as the new validators start to queue in the _pending_ state. This queue is emptied at a rate of 4 validators per epoch.

In the diagram above, the Staker is actually LEEQUID's pool contract.&#x20;

### State 0: Unknown (deposit transaction pending)

The deposit transaction is created by the oracles and sent through the pool contract. This transaction will sit in the pending transactions list (called the mempool) for some minutes, before it is included in a block.&#x20;

### State 1: Deposited - waiting follow distance

Once the deposit transaction reaches the deposit contract and is verified, a new validator is officially born, but not yet active. The deposit is recognized by the consensus layer but does not yet have a validator index associated to it. It will wait for \~8 hours (2048 epochs) as a strict safety measure to prevent an eventual blockchain reorganization from affecting the process. This wait period is called the `ETH1_FOLLOW_DISTANCE.`

Another \~6.8 hours will pass in the deposited state. This second waiting period in the deposit state is named `EPOCHS_PER_ETH1_VOTING_PERIOD` in the Proof of Stake specification.&#x20;

### State 2: Pending

After waiting for, approximately 15 hours, the 32 LYX deposit is now recognized as a new validator with and index given and agreed upon by the whole network. This is when the validator joins the activation queue, almost ready to start attesting blocks. If there is no queue, it will be ready in a matter of minutes. The queue can, however, last for hours if not days.&#x20;

### State3: Active

This is the state in which the validator is performing all its duties, and in here it will remain until it is either exited voluntarily or it gets slashed.&#x20;

## Activation queue

The activation queue happens at the LUKSO Proof of Stake protocol level and depends on the number of new validators trying to join the Proof of Stake consensus at the same time. Validators can’t simply be switched “on” and “off”; they go through a number of different states in their activation process and also in their exit process. In the beginning, the protocol needs to onboard new validators and assign them a position in the consensus algorithm. For that, a minimum of 8 hours will pass until the validators transition from the deposited to the active state.

However, there's a limit to how many validators can join consensus in a certain time frame. This limit is called the _churn limit_ and starts at 4 validators per epoch (6.4 minutes), increasing with the total number of validators in the protocol, up to a maximum of 10. When the limit is reached, new validators are put in a first-in/first-out queue, waiting for their turn to become active and collect rewards. This queue can last for a few days.

As a LEEQUID user, you will not feel the impact of the activation queue directly. Most of the time, staking will be a seamless experience and you will start accruing rewards straight away. That's because the LEEQUID protocol has a certain capacity to mint sLYX, even if some of the new stake is not yet active in validators. This generates what is called "reward dilution" and can affect established stakers. For that reason, there is a threshold to how much the protocol can take of "unactivated" LYX. See [dilution queue](potential-wait-times-while-staking.md#dilution-queue) for more details.

It might happen that due to the size of the activation queue, incoming stake requests take longer to activate, which in turn might result in the establishment of a dilution queue. In this scenario, the minting of new sLYX is delayed and you will have to return to the platform at a later time to claim your staked tokens.&#x20;

## Dilution queue

When there's a quick surge in the number of users trying to stake through the staking pool, onboarding stakers might be placed in a queue, which delays the minting of new sLYX. This cap protects already-established stakers, whose stake is effectively generating rewards, from reward dilution due to yet-to-be-activated stake by onboarding users.&#x20;

Currently, the protocol mints sLYX until it has 10% of the total staked value in a pre-activation state. When it reaches this threshold, sLYX will be minted at the rate validators are activated, and the stake starts generating rewards.

The activation time in the Proof of Stake protocol spans from when the deposit is accepted by the official contract to when the new validator starts validating, thus collecting rewards. This can range from a few hours to a few days, depending on how many new validators are trying to register on LUKSO at the same time. See [activation queue](potential-wait-times-while-staking.md#activation-queue) for more details.

To LEEQUID users, this timespan translates into a gap between the moment the user presses the stake button and the moment sLYX tokens can be minted for him. For this reason, in times of congestion, users might need to check the platform at a later date to claim their sLYX and start accruing rewards. There are some factors that improve the chances of being added to the dilution queue:

* The amount being staked is considerably high in relation to the pool’s total
* There is currently a surge in the number of users staking through LEEQUID at roughly the same time
* There is currently a lack of users trying to exit LEEQUID
* There is currently a long activation queue in the LUKSO Proof of Stake protocol

If there is an amount equivalent to more than 10% of the total active stake waiting in line to become activated, then new stakers won’t get sLYX immediately but instead will have to wait until their sLYX is available to claim and send a second transaction. This way, the impact of new stakers receiving rewards while their stake doesn’t get activated is minimized.
