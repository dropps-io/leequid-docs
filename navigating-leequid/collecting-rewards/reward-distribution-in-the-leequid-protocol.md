# Reward distribution in the LEEQUID protocol

In the LEEQUID protocol, **rewards are updated every 12 hours**. For this reason, you will see your _reward balance_ in the LEEQUID web app change twice a day. The amount of rewards collected in each reward round will depend on the current APR as well as some slight variations every period, due to the way Proof of Stake works. The LEEQUID protocol takes **a fee of** **10% on the rewards accrued**. For example, in a situation where the current APR is 14%, 12.6% is collected by the user and 1.4% (corresponding to 10% of 14) is collected by the protocol.

{% hint style="info" %}
The 10% protocol fee from LEEQUID is deduced from the rewards accrued every 12 hours. When a user withdraws or unstakes, no fee is applied.
{% endhint %}

The rewards displayed in the "Rewards" tab of the web app dashboard are held non-custodially on the LEEQUID protocol’s [Rewards contract](../../leequid-in-depth/smart-contracts/rewards.md). They do not generate further rewards. To enable this, users can toggle the **auto-compound** feature, and the protocol will automatically re-stake the rewards for the user on a daily basis.&#x20;

Manual compounding is also an option in the "Rewards" tab of the LEEQUID web app, providing users with control over whether he wants to withdraw or re-stake their rewards. This action will reintroduce the rewards into the staking pool as a new stake request and, consequently, it might be delayed by [staking queues](../staking/potential-wait-times-while-staking.md).
