# StakedLyxToken

The _StakedLyxToken_ is a smart contract designed to facilitate staking and unstaking operations. The contract follows the LSP7 token standard (LUKSO Standard Proposal number 7) and is built with Solidity, making it compatible with the Ethereum blockchain. This is the contract that mints and saves the balances of sLYX tokens, representing the staked amount of every user in the protocol. It is used both in the staking and the unstaking process, and is consulted by the _Rewards_ contract to calculate the reward balance of each account.&#x20;

#### Key features

**Staking**

The contract enables users to keep track of their staked tokens by minting 1 sLYX token for each LYX token staked on the `Pool` contract. The staking process starts with a transaction addressed to the _Pool_ contract, which will call the _StakedLyxToken_ mint function:

```solidity
function mint(
        address to,
        uint256 amount,
        bool allowNonLSP1Recipient,
        bytes memory data
) external override {
        require(msg.sender == address(pool), "StakedLyxToken: access denied");

        // start calculating account rewards with updated deposit amount
        bool rewardsDisabled = rewards.updateRewardCheckpoint(to);
        if (rewardsDisabled) {
            // update merkle distributor principal if account has disabled rewards
            distributorPrincipal = distributorPrincipal + amount;
        }

        _mint(to, amount, allowNonLSP1Recipient, data);
    }
```

**Unstaking**

The contract includes a comprehensive unstaking mechanism, allowing users to request unstaking of their tokens. Unstaking requests are stored in the `_unstakeRequests` mapping and can be retrieved using the `unstakeRequest` function.&#x20;

```solidity
//@dev Unstake Request - Mapping containing all the unstake request requests in chronological order, the uint256 key being used as an index.
    mapping(uint256 => UnstakeRequest) internal _unstakeRequests;
```

The `unstake` function can be used to initiate an unstake request, which will subtract the unstaked amount from the user's deposit and increase the total pending unstake.

```solidity
function unstake(uint256 amount) external override nonReentrant whenNotPaused {
```

The unstake function also increments the unstake request count and emits a _NewUnstakeRequest_ event, so that the oracles can pick up the request and process it later on. &#x20;

#### Token transfer

The contract allows for the transfer of staked tokens between addresses. When transferring sLYX tokens, checkpoints are created for both addresses on the `Rewards` contract, to save the current rewards states. Indeed, when transferring sLYX, it's the new owner of the tokens that will get the next associated rewards.

#### Authorization

The contract includes a functionality for authorizing operators to manage token operations on behalf of the token owner. The `authorizeOperator` and `revokeOperator` functions allow token owners to respectively grant and revoke operator rights.

#### Rewards

The `toggleRewards` function allows the admin to enable or disable rewards for a specific user.

#### Pausable and ownable

The contract follows the Ownable and Pausable patterns, providing security mechanisms to pause contract functionalities and restrict contract management to authorized addresses.

#### Upgradeable

The contract can be upgraded, ensuring that it can be improved and expanded upon in the future without affecting the current state and functionality.
