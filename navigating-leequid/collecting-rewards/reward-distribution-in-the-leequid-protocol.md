# Reward distribution in the LEEQUID protocol

In the LEEQUID protocol, **rewards are updated every 12 hours**. For this reason, you will see your _reward balance_ in the LEEQUID web app change twice a day. The amount of rewards collected in each reward round will depend on the current APR as well as some slight variations every period, due to the way Proof of Stake works. The LEEQUID protocol takes **a fee of** **10% on the rewards accrued**. For example, in a situation where the current APR is 14%, 12.6% is collected by the user and 1.4% (corresponding to 10% of 14) is collected by the protocol.

{% hint style="info" %}
The 10% protocol fee from LEEQUID is deduced from the rewards accrued every 12 hours. When a user withdraws or unstakes, no fee is applied.
{% endhint %}

The rewards displayed in the _reward balance_ section of the dashboard are sitting non-custodially on the LEEQUID protocol’s [Rewards contract](../../leequid-in-depth/smart-contracts/rewards.md). They are not generating further rewards, or, in other words, they don't auto-compound. For compounding, a user will need to press the “Stake Rewards” button and sign the transaction. This will reintroduce the rewards in the staking pool as a new stake request and, as such, it might be delayed by [staking queues](../staking/potential-wait-times-while-staking.md).
