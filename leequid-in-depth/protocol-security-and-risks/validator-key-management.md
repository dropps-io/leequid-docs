# Validator key management

A LEEQUID _multisig_ guardian is entitled to a share of the validators' seed phrases used for the LEEQUID protocol. In each node,  validators are generated with a different seedphrase.

Each of these seed phrases is split in 7 shares using the [Shamir Secret Sharing](https://en.wikipedia.org/wiki/Shamir's\_secret\_sharing) algorithm, with a threshold of 4 shares required to recover the seed phrase.

Each of these 7 shares will be encrypted and sent to a different shareholder using his RSA key.
