# Potential wait times while staking

{% hint style="info" %}
**Usually, staking in LEEQUID will be a fluid process with no wait times**. **However, during big surges in staking volume, a dilution queue is in place that will delay the minting of sLYX.** Certain constraints in the Proof of Stake protocol can slow the staking pool capacity to add new validators to the network. In this section, we'll learn more about them and how they interact with LEEQUID.
{% endhint %}

## Can I bypass the queues?

Before delving into the rationale behind the protocol's queues, let's explore an existing alternative: [the liquidity pool.](../swapping/slyx-for-lyx-an-instant-alternative-to-exiting.md) This is a component of the LEEQUID protocol designed to facilitate instant conversions between sLYX and LYX, enabling immediate staking and unstaking.&#x20;

Acquiring sLYX through the liquidity pool yields the same result as staking through the staking pool: a deposit of sLYX into the user's wallet, generating rewards overtime. However, this swap operation incurs a small fixed fee of 0.3% along with a slight loss of capital known as "slippage", which increases proportionally with the amount swapped.&#x20;

Before deciding on the path of staking sLYX, a user should consider the queue length and the potential rewards they might miss out on while queued for activation. During congested periods, it might be more advantageous to swap instead of staking through the staking pool.

## The validator lifecycle

After a LEEQUID user submits a new stake request, the staked LYX will sit in the [Pool contract](../../leequid-in-depth/smart-contracts/pool.md) until the oracles pick it up and send it to the LUKSO Deposit contract, registering new validators. From this point onwards, the validator lifecycle begins:

<figure><img src="../../.gitbook/assets/Validator_states (2).png" alt=""><figcaption><p>source: <a href="https://docs.prylabs.network/docs/how-prysm-works/validator-lifecycle">https://docs.prylabs.network/docs/how-prysm-works/validator-lifecycle</a></p></figcaption></figure>

### State 0: Unknown (deposit transaction pending)

The deposit transaction is created by the oracles after they recognize a user's staking request and is sent through the pool contract. This transaction effectively moves the staked LYX away from the boundaries of the LEEQUID protocol, into the LUKSO deposit contract. In exchange, the LUKSO deposit contract will provide LEEQUID with a validator registration number, which LEEQUID can use to operate validators and collect rewards. \
\
In a matter of minutes the deposit transaction will move from the pending transactions list (called the _mempool_) into a newly minted block.&#x20;

### State 1: Deposited - waiting follow distance

Once the deposit transaction reaches the deposit contract and is verified in a block, a new validator is officially born, but not yet active. The deposit is recognized by the consensus layer but does not yet have a validator index associated to it. It will wait for \~8 hours (2048 epochs) as a strict safety measure to prevent an eventual blockchain reorganization from affecting the process. This wait period is called the `ETH1_FOLLOW_DISTANCE.`

Another \~6.8 hours will pass in the deposited state. This second waiting period in the deposit state is named `EPOCHS_PER_ETH1_VOTING_PERIOD`.&#x20;

### State 2: Pending

After waiting for, approximately 15 hours, the 32 LYX deposit is now recognized as a new validator with and index given and agreed upon by the whole network. This is when the validator joins the activation queue, almost ready to start attesting blocks. If there is no queue, it will be ready in a matter of minutes. The queue can, however, last for hours if not days.&#x20;

### State 3: Active

This is the state in which the validator is performing all its duties, and in here it will remain until it is either exited voluntarily or it gets slashed.&#x20;

## Activation queue

The activation queue happens at the LUKSO Proof of Stake protocol level, when the validator is in the _Pending_ state, of the validator lifecycle explained above.&#x20;

Validators can’t simply be switched “on” and “off”. There's a limit to how many validators can join or exit consensus in a certain time frame. This limit is called the _churn limit_ and ranges between 4 and 10 validators per epoch (6.4 minutes), according to the total number of validators in the protocol. New validators are put in a first-in/first-out queue, waiting for their turn to become active and collect rewards. This queue can last for a few days.

As a LEEQUID user, you will not feel the impact of the activation queue directly. Most of the time, staking will be a seamless experience and you will start accruing rewards straight away. That's because the LEEQUID protocol has a certain capacity to mint sLYX, even if some of the new stake is not yet active in validators. However, that minting creates "reward dilution", which affects established stakers. For that reason, there is a threshold to how much the protocol tolerates of "unactivated" LYX. If too many staking requests are incoming but their activation rate is slow, a [dilution queue](potential-wait-times-while-staking.md#dilution-queue) will settle. In this scenario, the minting of new sLYX is delayed and you will have to return to the platform at a later time to claim your staked tokens.&#x20;

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

