# 👋 Welcome

In the pages of this Docs you will find details on the inner workings of the LEEQUID protocol, along with fundamental concepts related to liquid staking.&#x20;

[Status page](https://status.leequid.info/): check if everything is online. [🚥](https://emojipedia.org/horizontal-traffic-light)

[Metrics page](https://metrics.leequid.io): insights about protocol usage and evolution. 📈&#x20;

[Medium](https://medium.com/leequid): detailed explanations about protocol features and the world of liquid staking. 👩‍🏫

[Audit](https://consensys.io/diligence/audits/2023/09/leequid-staking/): by Consensys Diligence [🔒](https://emojidb.org/security-emojis)

_Our documentation is under continuous improvement. We encourage you to send us your suggestions through our public channels or by submitting a pull request to the official_ [_GitHub repository_](https://github.com/dropps-io/leequid-docs)_._

## About LEEQUID

LEEQUID is a non-custodial liquid staking protocol for the LUKSO blockchain. It emerged as a fork of [Stakewise V2](https://github.com/stakewise/contracts/tree/master/contracts/pool), a liquid staking pool available for the Ethereum blockchain, pre-Shapella upgrade. The LEEQUID protocol was the first to ever be deployed on the LUKSO blockchain and is the result of [numerous upgrades](leequid-in-depth/upgrades-over-stakewise-v2.md) to the Stakewise V2 protocol, advancing it to a pos-Shapella state, where withdrawals are enabled.&#x20;

Being a liquid staking protocol, LEEQUID enables its users to deposit and withdraw LYX at any time, accruing rewards through the protocol’s interest-bearing token, sLYX. The rewards, which are distributed evenly to all stakers according to their share of the pool, come from the work of Proof of Stake validators, registered automatically in the LUKSO blockchain by the LEEQUID protocol.

LEEQUID distributes its validator load independently between its own infrastructure and 3rd party node operators, guaranteeing a high degree of fidelity and decentralization. By closely monitoring the performance of all validator in its network, LEEQUID ensures high efficiency and participation rates, which translate into maximal reward APY and resource optimization.

There is no upfront cost for users staking through LEEQUID. Instead, the protocol takes a 10% fee on accumulated rewards. See the section on [reward distribution](navigating-leequid/collecting-rewards/reward-distribution-in-the-leequid-protocol.md) for more details.

The diagram below is a graphical representation of the interactions between LEEQUID's oracles, the smart contracts in the protocol, and user actions. The information in the diagram is complemented by this documentation as well as the official [GitHub repository](https://github.com/dropps-io/leequid-contracts) of the protocol.

<figure><img src=".gitbook/assets/contracts_infra_leequid.png" alt=""><figcaption><p>The LEEQUID protocol overview</p></figcaption></figure>





