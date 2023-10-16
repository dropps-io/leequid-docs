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

# Slashing and unexpected validator behaviour

Validators can get slashed and lose part or all of their staked amount. Slashing was created to make it economically infeasible to go against the Proof of Stake protocol. For that reason, if the validators are honest, slashing is very, very rare and can only occur due to a critical error in the client software that runs the validators or a very unfortunate error in the configuration of the nodes, which can be prevented or minimized with careful monitoring and testing.

The underlying structure of validators that generate rewards for the protocol can, theoretically, get slashed. If that happens, some LYX will be taken from the pool and the sLYX token might lose some of its value _temporarily_. The solution is the reinjection of LYX directly in the protocol to compensate for the one burnt in the slashing event.&#x20;

Nothing happens to liquid stakers in the event of slashing, unless there is a huge surge in withdrawal requests and sLYX to LYX swaps in the liquidity pool. In this scenario, because the sLYX is now undercollateralized (there's more sLYX than LYX), some users will face problems of lack of liquidity, being temporarily unable to withdraw their LYX.

In the history of Ethereum's PoS, only once has a staking provider suffered a [slashing event](https://cointelegraph.com/news/expensive-lesson-75-eth2-validators-slashed-for-introducing-potential-chain-split-bug). This was February 2021, the very beginning of the staking era. Since then, hundreds of thousands of validators operating for staking pools have been online for years without a single problem.

#### Prevention and mitigation mechanisms

* **Monitoring tools like **_**Grafana**_** and **_**Prometheus**_ provide a very useful overview of both the consensus and execution client statuses of node operators. Parameters such as participation rate, online time, connected peers, and CPU usage are constantly monitored and have alerts configured for threshold values.
* A **secure cloud environment** helps prevent slashing due to intentional tampering with the nodes by a malicious actor taking control.&#x20;
* A **mechanism to inject the LYX back into the protocol** without minting sLYX is in place. This allows the 1:1 ratio in sLYX to LYX to be restored by injecting rescue capital into the protocol.
