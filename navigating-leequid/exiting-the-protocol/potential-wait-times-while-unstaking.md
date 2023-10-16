# Potential wait times while unstaking

## Stake matching window

When an unstake request is issued by a user, a 24-hour time frame is started, in an attempt to match the unstake request to new capital flowing into the protocol. The concept is simple: a user entering inherits the position of a user exiting. The end result is exactly the same as going through the complete process on both sides, except that it can be much, much faster while dodging any queues.

This time frame is part of the flow and can only be cut short if a total match occurs. Otherwise, after the 24-hour wait, the exiting of validators will be triggered and the control of the unstake process will be transferred to the LUKSO Proof of Stake protocol, where it will pass through the exit queue.

## The exit queue

Unless a staking participant chooses to [swap their sLYX for LYX ](../swapping/slyx-for-lyx-an-instant-alternative-to-exiting.md)through the liquidity pool, exiting the protocol is a process with several steps that can take from a few hours up to a few days.

The exit queue, which happens at the Proof of Stake protocol level, is usually empty. However, unlikely events (like a big depositor exiting all his funds at once) can fill the exit queue temporarily, making other users experience unusually long queue times.

The best case scenario is when the total value in the unstake request is matched to an onboarding user, depositing LYX. In that case, the waiting time can be a matter of hours, if not minutes. The worst-case scenario is when no match occurs and there is an exit queue.
