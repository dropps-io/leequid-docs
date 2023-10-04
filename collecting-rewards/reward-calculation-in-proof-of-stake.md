# Reward calculation in Proof of Stake

Rewards earned by validators come mainly from their attesting duties in the consensus protocol. These are called consensus layer rewards and they are minted every single slot (the basic time unit of the Proof of Stake algorithm) in the LUKSO blockchain. This means that new LYX is being minted every slot.

On the other hand, users pay gas fees to have the network execute their transactions. In Proof of Stake, the gas paid by users doesn't go to the validators. Instead, it is burned. This means that LYX is being burned every slot.&#x20;

It is possible for users to send an extra tip, on top of gas paid, to the validator chosen as the block proposer in a given slot. This tip is what makes up execution layer rewards, famously known as MEV (Maximal extractable value).&#x20;

#### Consensus layer rewards

The new LYX minted each slot makes up the total consensus layer rewards for that slot and accrues directly in the participating validators' balances. Slowly, the validator balance will start surpassing 32 LYX, but it will never go way beyond because rewards are periodically processed by the network and withdrawn into the validator's withdrawal address. This withdrawal is called a _partial withdrawal_, in contrast with exiting the validator and withdrawing the 32 LYX, which is called a _full withdrawal_.

> A _partial_ withdrawal will be performed automatically, in a regular period, for the validators whose balance is above 32 ETH (due to their rewards). The exceeding amount of ETH will be transferred to the Ethereum account they have declared in the transaction they submitted to the Deposit Contract (in the field `eth1_withdrawal_address`) - [Nethermind-eth blog](https://medium.com/nethermind-eth/bls-signatures-withdrawals-bbf38658c242#2be3)

The Ethereum account specified as the _withdrawal address_ for all validators operated by LEEQUID is the address of the _Rewards_ contract. There is a constant flow of LYX into this contract and periodically the Oracles calculate the amount of _partial withdrawals_ collected and update the&#x20;

The rewards accrued by validators come from the duties they perform for the blockchain. Among them we count:

* Attestations. Every time a validator “validates” a block, it verifies if such block respects the chain rules to choose its parent block and also that its content is correct (no double spending). This is the most steady source of rewards and will amount to the majority of the income. A validator does one attestation every epoch (6.4 minutes).
* Block proposer rewards. Occasionally a validator might be chosen to propose a new valid block for the blockchain. When this happens, the validator gets a hefty reward, much bigger than attestation rewards. However, this event happens to one validator, on average, once per week, and this likelihood decreases as the number of total validators increases.
* Sync Committee. 512 validators are randomly selected once every 256 epochs (27.3 hours).  For any given validator this will happen rarely; with 500,000 validators, the expected interval between being chosen for sync committee duty is around 37 months. However, during the 27-hour period of participation the rewards are considerably increased. While a validator is part of the currently active sync committee, it is expected to continually sign the block header that is the new head of the chain at each slot. The purpose of the sync committee is to allow **light clients** to keep track of the chain of block headers. Sync committee participants receive a reward for every slot that they correctly perform their duties.&#x20;

#### Execution layer rewards

Besides these 3 types of rewards awarded to correct participants in Proof of Stake consensus, there is a special type of reward for block proposers. In other words, when a validator is chosen to become a block proposer (using an algorithm called RANDAO for pseudo-randomness), it has the opportunity to explore what is called MEV, i.e., Maximal Extractable value. This income does not spring from the protocol itself, but instead from the transaction fees paid by users who want to have their transactions included in a block. For this reason, MEV is usually called an execution layer reward, in contrast with the consensus layer rewards we mentioned above. Payments from MEV can be very generous, but they vary considerably, according to network congestion. Because blocks are basically put in an auction system where whoever pays more gets their transaction included, sometimes you have great competition and the prices go higher, and sometimes you have lower transaction fees. The validator client software has scarce control over this.
