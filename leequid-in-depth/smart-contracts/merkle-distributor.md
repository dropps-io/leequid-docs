# Merkle Distributor

The _MerkleDistributor_ smart contract is part of a liquid staking application, designed to distribute rewards based on off-chain calculations to users who have contributed their sLYX tokens to liquidity pools like the LEEQUID swap.

This contract is beneficial in situations where rewards cannot be directly given to liquidity providers, since liquidity pools are addresses with disabled rewards. Instead, the rewards are calculated off-chain and distributed using a Merkle tree.

This contract plays a crucial role in the rewards distribution system, enabling a secure, transparent and efficient mechanism for distributing rewards to liquidity providers.

#### Key features

**Merkle root management**

This contract maintains a Merkle Root (`merkleRoot`) that helps in proving rewards ownership. This can be updated by the oracle through `setMerkleRoot` function.

**Claim mechanism**

Users can claim their rewards through the `claim` function by providing the Merkle proof. The function verifies the proof and distributes the reward if the proof is valid.

**Periodic distribution**

The contract allows periodic distribution of tokens through the `distributePeriodically` function. The distribution period is defined in terms of block numbers.

**One-time distribution**

For one-off distributions, the `distributeOneTime` function is used. It transfers tokens to the contract and triggers a one-time distribution event.

**Claim status**

It provides the `isClaimed` function to check if a particular reward has been claimed or not.

**Upgradeability**

The contract allows updating the Oracles addresses. This operation can be done only when the contract is paused and only by the admin, as ensured by the `upgrade` function.

**Pausing**

The contract inherits from `OwnablePausableUpgradeable`, which allows the admin to pause the contract in case of anomalies. Certain functions like `upgrade`, `distributePeriodically`, `distributeOneTime`, and `claim` are affected by the pause status of the contract.

**Auditable events**

The contract emits specific events like `MerkleRootUpdated`, `PeriodicDistributionAdded`, `OneTimeDistributionAdded`, and `Claimed` to keep a transparent and verifiable record of significant actions.
