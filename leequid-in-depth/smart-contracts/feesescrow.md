---
description: '0x9658B1Ff55597303EF2Ed963A9E8Aadb7E3E135e'
---

# FeesEscrow

The _FeesEscrow_ contract is a very short contract that has only one function: to temporarily store execution layer rewards.&#x20;

Each time one of the validators in the LEEQUID protocol proposes a block, it benefits from transaction ordering tips, also called MEV or execution layer rewards. It does so by prioritizing transactions that offer a tip, which goes to an address called the "fee recipient". This address is set in _fee\_recipient_ attribute of the block's header and, expectedly, the LEEQUID protocol's validators are configured to set it to the _FeesEscrow_ contract's address on mainnet. You can learn more about the block structure of EVM based blockchains in the [Ethereum official docs](https://ethereum.org/en/developers/docs/blocks/).

Each time the [Oracles ](oracles.md)in LEEQUID update the reward balance of the protocol (which happens roughly twice a day) they sweep the fees accumulated in the _FeesEscrow_ contract and transfer them to the Rewards contract. That's the purpose of the _transferToRewards_ function as seen below:

```solidity
// SPDX-License-Identifier: AGPL-3.0-only

pragma solidity ^0.8.20;

import {IFeesEscrow} from "../interfaces/IFeesEscrow.sol";

/**
 * @title FeesEscrow
 *
 * @dev FeesEscrow contract is used to receive tips from validators and transfer
 * them to the Rewards contract via a call to the transferToRewards method by the Rewards contract.
 */
contract FeesEscrow is IFeesEscrow {
    // @dev Rewards contract's address.
    address payable private immutable rewards;

    constructor(address _rewards) {
        rewards = payable(_rewards);
    }

    /**
     * @dev See {IFeesEscrow-transferToRewards}.
     */
    function transferToRewards() external override returns (uint256) {
        require(msg.sender == rewards, "FeesEscrow: invalid caller");

        uint256 balance = address(this).balance;

        if (balance == 0) {
            return balance;
        }

        rewards.transfer(balance);

        emit FeesTransferred(balance);

        return balance;
    }

    /**
     * @dev Allows FeesEscrow contract to receive execution layer tips. Later these rewards will be transferred
     * to the `Rewards` contract by `FeesEscrow.transferToRewards` method which is called by the `Rewards` contract.
     */
    receive() external payable {}
}
```
