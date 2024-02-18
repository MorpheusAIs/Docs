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

## FAQs

- **1) Why 88 days?**
- This is 2 days earlier than all other MOR become claimable, so that the MOR tokens can be deposited into the Uniswap pool and avoid someone snipping the pool on the first block.

- **2) Why 7.522%?**
- 7.522% of the initial bootstrapping yield equals 1 to 1 the same amount of MOR in the Protection Fund (as compared to the total MOR emitted the first 90 days).

- **3) Where did you get 50,344 MOR from?**
- The Protection Fund gets 4% of the daily emissions (576 MOR per day (minus the decay rate). 50,344 are the MOR that will be avilable to the Protection Fund day 90.

- **4) When will the pool be set?**
- Just before day 90 when the rest of the MOR become claimable.

- **5) How much bootstrapping yield will be added?**
- This number is unknown until closer to the end of the 90 day Bootstrapping period.
- However you can calculate a rough estimate based on the amount of stETH deposited in the Morpheus Smart Contract.
- 100,000 stETH would equal 3,300 stETH of yield per year or 825 stETH in a 90 day period.

- **6) How to add MOR to AMM?**
- The Multisig address will deposit MOR into the AMM before all MOR are released.
- Once MOR are claimable by everyone on day 90 anyone will be free to deposit their MOR in the AMM.

- **7) Can everyone add liquidity?**
- Yes, after day 90 when the MOR become claimable, every MOR holder will be free to add their MOR to the Uniswap pool.

- **8) What if no one deposit MOR into the LP?**
- The pool will begin based on the Protection Fund MOR even if no one else has deposited yet.

- **9) What's the MOR price on day 90 (the first day on Uniswap)?**
- This depends on many variables such as: 
- A. How much stETH is deposited in the Morpheus Smart Contract.
- B. How many MOR will be claimed and then deposited in the Uniswap pool on day 90.
  
- Using the numbers from the example above if 825 stETH is available on day 90 as the "initial yield", and 7.522% of that is deposited in the AMM to start, then there would be 62 stETH on one side of the order book and 50,344 MOR on the other side of the order book. If ETH has a dollar price of $3,000 USD in May, then that would imply a per MOR price of $3.69 USD per MOR. 

Of course this will change as soon as others begin depositing addtional MOR in the Uniswap pool or buying MOR with wETH.
Given the other 92.478% of the initial yield (763 wETH) will be added to the Uniswap pool in proportion as MOR deposits increase, there is effectively a $3.69 USD per MOR floor price until all the initial yield has been deployed. Then the market price will freely float based on the daily yield added to the Protocol Owned Liquidity and whatever the natural buy / sell pressure for MOR is that day.

- **10) How will you prevent MEV bots attack in the first block? (buy cheap)**
- The price should be set by the implied amount of stETH vs MOR when both are deposited in the first block.
- Suggestions to avoid attacks are welcome and several experts have been asked.

## Post Bootstrapping

stETH yield added to the Protocol Owned Liquidity will be converted to wETH, 50% buying MOR and the other 50% being added as an LP of the pool. This will continue into the future as long as the Capital Provider rewards providing yield to the Protocol Owned Liquidity (256 years).

Longer term as additional staked asset yield from Bitcoin, USDT, Solana, gets added as a source of Capital to Morpheus then other AMMs on other chains can be added for MOR trading pairs. Then the yield from those assets will be directed toward those pools in proportion to the total locked value held in those pools vs the total TVM across all MOR AMM pools.
