# MOR Liquidity Bootstrapping on Uniswap via Arbitrum
The two primary objectives of the bootstrapping period are to: 

#1. Enable fair and transparent price discovery for the MOR token. Avoiding the typical price spike on the first day of listing the token on the AMM.

#2. Implement best practices to avoid MEV or other attacks that would extract the Protocol Owned Liquidity added to the AMM by the protocol.

## Facts for MOR Token Day 90
- About 50,309 of MOR will become claimable by the Protection Fund on day 88 of the fair launch. This will be used to create the MOR AMM pool on Uniswap.

- There will be 668,778 total MOR tokens in circulation on day 90. Capital + Code + Protection Fund MOR tokens emitted.

## AMM Bootstrapping Details
- The initial yield of stETH will be referred to as the "bootstrapping yield".

- The bootstrapping yield originally in stETH will be converted into wETH (ETH on Arbitrum).

- 7.522% of the "bootstrapping yield" generated during the 90 day bootstrapping period will be paired with these 50,309 MOR from the Protection Fund.

- As additional MOR are deposited into the Uniswap pool (by MOR holders who earned them from providing Capital or Code) additional wETH bootstrapping yield will be deployed into the Uniswap AMM in proportion.

- This formula is total yield from bootstrapping period will be deployed 1 for 1 with total MOR tokens earned & claimable on day 90.

- For Example if 66,877 MOR are deposited of the total 668,778 MOR in circulation (10% of supply), then 10% of the bootstrapping yield will be paired with these tokens. 

- This formula will continue daily until all the bootstrapping yield has been added to the AMM.

Best practices for avoiding MEV and other "snipping" type attacks to be developed.

## Post Bootstrapping

stETH yield added to the Protocol Owned Liquidity will be converted to wETH, 50% buying MOR and the other 50% being added as an LP of the pool. This will continue into the future as long as the Capital Provider rewards providing yield to the Protocol Owned Liquidity (256 years).

Longer term as additional staked asset yield from Bitcoin, USDT, Solana, gets added as a source of Capital to Morpheus then other AMMs on other chains can be added for MOR trading pairs. Then the yield from those assets will be directed toward those pools in proportion to the total locked value held in those pools vs the total TVM across all MOR AMM pools.
