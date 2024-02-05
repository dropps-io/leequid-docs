# Security overview

Once LYX moves from a user's wallet into the LEEQUID protocol, staking is handled in a predictable, programmed, non-custodial manner. Deposited LYX coins will move through the staking contracts and into LUKSO’s deposit contract, where they will remain until an unstake request triggers their withdrawal, returning to the protocol, and ultimately, redeeming to the user wallet. The flow of LYX within LEEQUID is explained in detail in [this section](../../navigating-leequid/staking/deposited-lyx-lifecycle.md).

The [code in the protocol](https://github.com/dropps-io/leequid-contracts) is open source and has been audited by [Consensys](https://consensys.io/diligence/), one of the most reputable auditors in the web3 space.

Staking pools represent one of the safest types of DeFi protocols available. This is because user funds are stored in a smart contract developed over many years and extensively tested by the Ethereum team, known as the _Deposit Contract_.&#x20;

Once LYX enters the Proof of Stake consensus network, only a violation of the consensus rules can impact that LYX.&#x20;

There is no mechanism for the staking pool developers or admins to take control over user funds, making a "rug pull" or protocol takeover impossible by definition. Our liquid staking token, called _StakedLYX_ (sLYX), has no initial distribution, no treasury, and no share for the marketing, executive, or development teams. Its supply adheres to the simplest of all rules:

> The amount of sLYX minted is equal to the LYX that enters the protocol. The amount of sLYX burned is equal to the LYX that exits the protocol. LYX enters and exits the protocol through staking and unstaking, respectively.

So, what is there to lose when staking through a staking pool? Practically speaking, nothing. In theory, LEEQUID, along with its node operator partners, operates an infrastructure of validators. When a user stakes, they trust LEEQUID to perform its job properly and ensure that the validators adhere to the rules of the consensus mechanism. Otherwise, as mentioned above, a violation of consensus rules results in sanctions against staked LYX.

LEEQUID has taken careful steps in assembling its validator infrastructure and selecting its node operator partners, in compliance with industry standards. The inspiration for these decisions comes from major staking players in the market such as LIDO and Stakewise. Security in LEEQUID is on par with these million-dollar protocols, which have smoothly sailed through all the upgrades in Proof of Stake without incidents.

Below is a table detailing the theoretical possible risks of a staking protocol for user consideration. Because preventive measures are in place, such risks have never resulted in incidents in any major staking platform in the market.&#x20;

<figure><img src="../../.gitbook/assets/risks_overview (1).png" alt=""><figcaption><p>Summary of the risks to consider when staking through a staking provider like LEEQUID</p></figcaption></figure>
