---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Smart contract code correctness

#### Description

Even though a series of measures are taken to ensure code correctness, such as:

* Careful development using battle-tested libraries like Open Zeppelin
* Extensive and thorough testing
* Audit by the best experts in solidity and blockchain technology

The intricacies of protocols such as LEEQUID are such that sometimes bugs can appear in the most unexpected interactions. For that reason, further prevention and handling mechanisms are put in place.&#x20;

#### Prevention mechanisms

* LEEQUID's contracts are _**pausable**_. This means that, in the event of a flaw, the protocol can be stopped immediately, freezing all deposits and withdrawals. The pause action can be executed by an address with the role of _owner_. This address can either be controlled manually by a person (or team), or by a smart contract (for example a _Multisig_ or a DAO).&#x20;
* LEEQUID's contracts are _**upgradeable**_. If a flaw is discovered, the protocol can be paused, the flaw corrected and the faulty contract upgraded. Upgrading a smart contract means switching it with a new one. This change doesn't affect the protocol or the user, all the data will be preserved and the user-facing surface of the protocol will remain unaltered. Think about it as replacing a malfunctioning battery in a car.&#x20;
* LEEQUID's contracts **were audited**. A professional team with high expertise in blockchain security and specialized in solidity and the Ethereum Virtual Machine (EVM) has performed a careful [audit](https://consensys.io/diligence/audits/2023/09/leequid-staking/#no-protection-of-uninitialized-implementation-contracts-from-attacker) of the protocol's smart contracts, stating no security vulnerabilities.
* LEEQUID's contracts are **an evolution of Stakewise V2**. The protocol has been live on Ethereum since November 2020, with a total value locked of more than 85000 ETH (more than 100 million dollars in 2023), and a proven history of robustness and reliability. The changes introduced by LEEQUID allowed the portability of Stakewise V2 to LUKSO's blockchain standards (like LSP7 tokens), and introduced a major upgrade to accommodate the withdrawal of validators, which were locked until the Shapella upgrade in April 2023.&#x20;
