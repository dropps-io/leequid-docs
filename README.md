# 👋 Welcome

In this documentation you will find details on the inner workings of the LEEQUID protocol, along with some fundamental concepts related to liquid staking. The information herein contained will help you understand how the platform operates, as well as the smart contract logic that ensures the non-custodial processing of staked LYX and the liquidity of the liquid staking derivative token, sLYX.

_Our documentation is under continuous improvement. We encourage you to send us your suggestions through our public channels or by submitting a pull request to the official_ [_GitHub repository_](https://github.com/dropps-io/leequid-docs)_._

## About LEEQUID

LEEQUID is a non-custodial liquid staking protocol for the LUKSO blockchain. The protocol emerged as a fork of [Stakewise V2](https://github.com/stakewise/contracts/tree/master/contracts/pool), a liquid staking pool available for the Ethereum blockchain, pre-Shapella upgrade. The LEEQUID protocol, deployed on the LUKSO blockchain, results from numerous upgrades to the Stakewise V2 protocol, advancing it to a pos-Shapella state, where withdrawals are enabled.

&#x20;Progress over Stakewise V2 includes:

* A full unstaking system, which effectively exits validators, recovering staked LYX and burning sLYX in the process. Exiting validators and withdrawing rewards became available for EVM blockchains like LUKSO after the [Shapella upgrade](https://blog.ethereum.org/2023/03/28/shapella-mainnet-announcement), on April 12th, 2023.
* The possibility to withdraw rewards to one's wallet. This means not only accruing them in the liquid staking token, but effectively transfer them as LYX, anytime, to a user controlled Universal Profile or Externally Owned Address.
* A stake/unstake buffer to match incoming deposits with outgoing withdrawals. This buffer can transform waiting periods of days into minutes.&#x20;
* Adjustment to the LSP7 token standard, making LEEQUID the first LUKSO native DeFi protocol.
* Update of solidity code to the newest version, benefiting from increased security and efficiency.&#x20;

LEEQUID users can deposit and withdraw LYX at any time, accruing rewards through the protocol’s interest-bearing token, sLYX.&#x20;

The rewards, which are distributed evenly to all stakers according to their share of the pool, come from the work of Proof of Stake validators, registered automatically in the LUKSO blockchain by the LEEQUID protocol. By running its own node infrastructure, LEEQUID ensures maximum validator performance, closely monitoring validator metrics, and providing staking as a service in the LUKSO blockchain for the first time.

There is no upfront cost for users staking through LEEQUID. Instead, the protocol takes a 10% fee on accumulated rewards. See the section on [reward distribution](navigating-leequid/collecting-rewards/reward-distribution-in-the-leequid-protocol.md) for more details.

The diagram below is a graphical representation of the interactions between LEEQUID's oracles, the smart contracts in the protocol, and user actions. The information in the diagram is complemented by this documentation as well as the official [GitHub repository](https://github.com/dropps-io/leequid-contracts) of the protocol.

<figure><img src=".gitbook/assets/contracts_infra_leequid.png" alt=""><figcaption><p>The LEEQUID protocol overview</p></figcaption></figure>

### Securing the LEEQUID protocol

Once LYX moves from the user's wallet into the LEEQUID protocol, staking is handled in a predictable, programmed, non-custodial way. Deposited LYX coins will move through the staking contracts and into LUKSO’s deposit contract, where they will sit until an unstake request activates their withdrawal, return to the protocol, and finally, redemption to the user wallet. The flow of LYX inside LEEQUID is explained in detail in [this section](navigating-leequid/staking/deposited-lyx-lifecycle.md).

The [code in the protocol](https://github.com/dropps-io/leequid-contracts) is open source and has been audited by [Consensys](https://consensys.io/diligence/), one of the most reputable auditors in the web3 space.

Nonetheless (and akin to all staking protocols) there are risks to consider. You can read more about them in the [Security section](leequid-in-depth/protocol-security-and-risks/) of the documentation.





