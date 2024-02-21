# MOR Liquidity Bootstrapping on Uniswap via Arbitrum
The two primary objectives of the bootstrapping period are to: 

#1. Enable fair and transparent price discovery for the MOR token. Avoiding the typical price spike on the first day of listing the token on the AMM.

#2. Implement best practices to avoid MEV or other attacks that would extract the Protocol Owned Liquidity added to the AMM by the protocol.

## Estimates for MOR Token Day 90
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
**1) Why 88 days?**
- This is 2 days earlier than all other MOR become claimable, so that the MOR tokens can be deposited into the Uniswap pool and avoid someone snipping the pool on the first block.

**2) Why 7.522%?**
- 7.522% of the initial bootstrapping yield equals 1 to 1 the same amount of MOR in the Protection Fund (as compared to the total MOR emitted the first 90 days) 50,344 of 668,778 MOR in circulation.

**3) Where did you get 50,344 MOR from?**
- The Protection Fund gets 4% of the daily emissions (576 MOR per day (minus the decay rate). 50,344 are the MOR that will be avilable to the Protection Fund day 90.

**4) When will the pool be set?**
- Just before day 90 when the rest of the MOR become claimable.

**5) How much bootstrapping yield will be added?**
- This number is unknown until closer to the end of the 90 day Bootstrapping period.
- However you can calculate a rough estimate based on the amount of stETH deposited in the Morpheus Smart Contract.
- 100,000 stETH would equal 3,300 stETH of yield per year or 825 stETH in a 90 day period.

**6) How to add MOR to AMM?**
- The Multisig address will deposit MOR into the AMM before all MOR are released.
- Once MOR are claimable by everyone on day 90 anyone will be free to deposit their MOR in the AMM.

**7) Can everyone add liquidity?**
- Yes, after day 90 when the MOR become claimable, every MOR holder will be free to add their MOR to the Uniswap pool.

**8) What if no one deposit MOR into the LP?**
- The pool will begin based on the Protection Fund MOR even if no one else has deposited yet.

**9) What's the MOR price on day 90 (the first day on Uniswap)?**
- This depends on many variables such as: 
- A. How much stETH is deposited in the Morpheus Smart Contract.
- B. How many MOR will be claimed and then deposited in the Uniswap pool on day 90.
  
However using the numbers from above (100,000 stETH staked on average over the 90 days) we can calcuate an example. If 825 wETH is available on day 90 as the "bootstrapping yield" and 7.522% of that is deposited in the AMM to start, then there would be 62 wETH on one side of the order book and 50,344 MOR on the other side of the order book. A price of 0.00123 wETH per 1 MOR.

If wETH has a dollar price of $3,000 USD in May, then that would imply a price of $3.69 USD per 1 MOR. 

Of course this will change as soon as others begin depositing additional MOR in the Uniswap pool or buying MOR with wETH.
Given the other 92.478% of the bootstrapping yield (763 wETH) will be added to the Uniswap pool in proportion as MOR deposits increase, there is effectively the same 0.00123 wETH per 1 MOR ($3.69 USD per MOR) implied price until all the bootstrapping yield has been deployed. 

Then the market price will freely float based on the daily yield added to the Protocol Owned Liquidity and whatever the natural buy / sell pressure for MOR is that day.

**10) How will you prevent MEV bots attack in the first block? (buy cheap)**
- The price should be set by the implied amount of stETH vs MOR when both are deposited in the first block.
- Suggestions to avoid attacks are welcome and several experts have been asked.

## Exploring Methods For Fair Price Discovery
Current Notes On Fair Price Discovery Methods Available:

### Option #1. Balancer Example
The Liquidity Bootstrapping Pool method used by some projects, where the purchaser does know the price. The price falls on a known curve until a user feels it’s worth buying. See example details here: https://docs.balancer.fi/concepts/pools/liquidity-bootstrapping.html

### Option #2. Camelot Example
“A 'liquidity bootstrap' would be a way to establish a fair Day 90 price and limit the wild swings that could be otherwise experienced. 

There could do a phased bootstrap approach: 

- (Phase 1) 24 hour period where anyone who wants to commit their MOR to the pool can do so. Deposit only. This could be bolstered by a seed amount from the Protection Fund to ensure there is at least some MOR allocated 

- (Phase 2) 24 period where users contribute ETH to the other side, once again being a deposit only period. 

- (Phase 3) the ending balances on both sides are what set the starting price and total liquidity is moved from the locked contract and into the actual pool. Both sides of the contributions are given their relative piece of the pool, i.e. a user who contributes MOR would have half their MOR swapped for the relative price of ETH.

Limiting the deposits to a single side at a time and only executing the pool at the end of Phase 2 removes the live trading of anyone trying to scalp the market and focuses it as an investment versus a wild trading day of price discovery. I've seen several good roll-outs of this, Camelot ($GRAIL) on Arbitrum was one I thought that had a very smooth and successful execution.

### Option #3. Signaling Example
Uniswap V3 supports one-sided liquidity which in nature is a limited order.
It would be difficult to have users add one-sided liquidity themselves as it could turn out to be very complex as the users need specific knowledge of the process and liquidity has to be put in a "specific range".

Instead there is a proposal to have a "signaling period", where a user has to provide approval to the Smart Contract (needs to be developed) and thus say: "Hey, I want to take place in a fair price discovery." Which means his MOR (amount indicated by the user) will be used to create liquidity and he will get wETH in exchange.

All these actions will take place BEFORE liquidity is created, meaning that pool will be rebalanced before it live on mainnet as Smart Contract will withdraw users' MOR and credit them wETH directly from the bootstrapping yield. Thus the risk of possible MEV attack tricks are mitigated and greatly decrease complexity of Smart Contract development.

Pre-launch price discovery period could lasts for week or days and people could see the outcome of their actions/decision and  "AMM listing price" fluctuations in real time and can making thoughtful decisions and reach natural price equilibrium based on free market approach.

## Post Bootstrapping

stETH yield added to the Protocol Owned Liquidity will be converted to wETH, 50% buying MOR and the other 50% being added as an LP of the pool. This will continue into the future as long as the Capital Provider rewards providing yield to the Protocol Owned Liquidity (256 years).

Longer term as additional staked asset yield from Bitcoin, USDT, Solana, gets added as a source of Capital to Morpheus then other AMMs on other chains can be added for MOR trading pairs. Then the yield from those assets will be directed toward those pools in proportion to the total locked value held in those pools vs the total TVM across all MOR AMM pools.
