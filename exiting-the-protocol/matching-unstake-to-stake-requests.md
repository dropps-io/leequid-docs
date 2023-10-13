# Matching unstake to stake requests

At the beginning of the exit process, the LEEQUID protocol opens a 24-hour window in which the unstake request can be matched to stake requests of new/onboarding users, cutting short the exit process and delivering reduced waiting times. During this period, one of three things can happen:

1. No stake is matched
2. Only a portion of the unstake value is matched
3. The unstake request is fully matched by incoming stake

Both scenarios 1 and 2 result in the unstake request advancing to the next stage, where validators are exited from the Proof of Stake protocol and withdrawn LYX returns from the LUKSO deposit contract to the LEEQUID protocol. The amount withdrawn will cover all the unmatched value and the unstake will be available to be claimed in a single action. This represents the longest path to unstaking in the LEEQUID platform:



<figure><img src="../.gitbook/assets/unstake_flowchart.png" alt=""><figcaption><p>The unstake process. Notice the separation of flows after the "Match found" condition.</p></figcaption></figure>



Alternatively, scenario 3 can happen, where stake from users trying to enter the LEEQUID protocol ends up covering the amount another user was trying to unstake. In such scenario, there is a full match and the process terminates earlier, without the exit of any validators from the Proof of Stake protocol. The LYX will be available earlier and it can be claimed by the user in a single action. Scenarios like this represent the shortest path in the diagram above, which bypasses all the exit procedures in the Proof of Stake protocol.
