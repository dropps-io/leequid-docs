---
description: '0xA46d16FB9F228785cF1A7C20415bb5AfC193945A'
---

# Implementation

LEEQUID features a LYX/sLYX pair liquidity pool, alongside its main staking protocol. The liquidity pool logic is handled by the code of [Uniswap V2](https://ethereum.org/en/developers/tutorials/uniswap-v2-annotated-code/), directly deployed on the LUKSO blockchain with no modifications. This is the first decentralized exchange (DEX), deployed on LUKSO's mainnet and it serves the staking pool by adding an instant route to stake or unstake, granting the sLYX token maximum liquidity.

Uniswap V2 is an [EVM compatible](#user-content-fn-1)[^1] smart contract suite, which allows the creation of exchange markets between any two [ERC-20](https://eips.ethereum.org/EIPS/eip-20) tokens. In these exchange markets, the presence of liquidity reserves and AMM[^2] logic ensure instant swaps and settle the price.&#x20;

On LUKSO, the ERC-20 standard is being replaced by the newer [LSP7](https://docs.lukso.tech/standards/nft-2.0/LSP7-Digital-Asset/), which is, nonetheless, fully compatible with ERC-20. However, LUKSO's native coin, LYX, is neither an LSP7, nor an ERC-20 token. Instead, it is a native blockchain currency, and, technically, not a token run by a smart contract. Due to that constraint, LEEQUID also deploys a wrapper around the LYX coin, used internally by the liquidity pool, making LYX ERC-20 compatible. This wrapper uses the unmodified [code of WETH10](https://github.com/WETH10/WETH10), the Ethereum wrapper, deployed on the LUKSO blockchain.&#x20;

[^1]: **EVM compatible** represents code that compatible with any blockchain that uses the Ethereum Virtual Machine computation engine, like LUKSO does.

[^2]: **AMM** stands for automated market-maker, an algorithm based form of trading which relies on a liquidity pool instead of buy/sell orders and settles the price based on the ratio of assets in the pool.   &#x20;
