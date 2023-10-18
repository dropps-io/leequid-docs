---
description: '0x5D48F7FC221ABcAC5386c374eF723a56AD03D4B4'
---

# Rewards

The Rewards contract is a key piece in the liquid staking application, providing a way to distribute rewards to protocol participants, handling protocol fees, and managing checkpoints for efficient reward calculation. This contract is also the withdrawal address of the protocol's validators: where all the rewards and unstakes from the protocol's validators get sent to.&#x20;

The _Rewards_ contract interacts with various other contracts including:

1. [_StakedLyxToken_](merkle-distributor.md): Tracks the staked tokens.
2. [_Oracles_](oracles.md): Responsible for updating the total rewards in the Rewards contract.
3. [_MerkleDistributor_](merkle-distributor.md)_:_ Distributes the rewards to the protocol's participants.
4. [_FeesEscrow_](feesescrow.md): Handles the protocol's execution layer fees.
5. [_Pool_](pool.md)_:_ Handles incoming LYX.

### Key features

The _Rewards_ contract tracks the total rewards earned by the staking protocol and the total amount that has been cashed out. It also calculates the reward per token for user reward calculation.

#### **Checkpointing**

To optimize gas usage and enhance scalability, the contract uses a checkpoint system that keeps track of an account's rewards at a particular point in time. The reward per token is stored in each checkpoint, along with the reward value, in a single memory slot. This allows the Rewards contract to calculate the user's reward.

```solidity
struct Checkpoint {
    uint128 reward;
    uint128 rewardPerToken;
}
```

#### **Fee Handling**

The contract calculates protocol fees and handles the distribution of these fees. It allows the protocol's admin to set the fee recipient address and fee percentage.

#### **Oracles**

An oracle system is in place that updates the total rewards in the Rewards contract.

#### **Reward disabling**

The contract provides an option to disable rewards for an account. The state is toggled by calling the `setRewardsDisabled` function. Rewards of addresses with rewards disabled accrue in the distributor principal, the balance of the [Merkle Distributor contract](merkle-distributor.md), responsible for the token distribution of rewards calculated off-chain.

