# Deployment of the Liquidity Pool

Below is a quick outline of the steps to be taken in the coming days as Morpheus heads into the Token launch. 

The first phase will be the conversion of stETH (Mainnet) to wETH (on Arbitrum)
The second phase will be the creation of the pool on May 8 and the liquidity range. 


## Phase 1: Conversion of stETH (on Ethereum Mainnet) to wETH (on Arbitrum)
When: Will be completed prior to May 6th by the multi-sig

### Step 1: The multi-sig will convert stETH to wETH using Option A

- Option A: Use Dex Aggregatior  [Cow Swap](https://swap.cow.fi/#/1/swap/WETH)
        - This results in slippage of approximately .5 eth 
        - The net negative impact to Mor Price at the creation of the pool will be $.01 lower due to the slippage

- Option B: Unstake with Lido 
        - Slippage: None
        - Time to Receive Fund: Up to 5 Days, Dependent on validator queue. ([Source](https://stake.lido.fi/wrap))
        - Impact to MOR price when the pool is established is $.01 higher due to less slippage
        - Note: This option declined to avoid any risk of delay in receiving funds.

### Step 2: Bridge wETH from Eth Mainnet to Arbitrum using the main bridge

([Link](https://bridge.arbitrum.io))


## Phase 2: Creation of the Liquidity Pool on May 8th. 12:00PM UTC

- Step 1: Create the MOR/wETH Pool.
      - 52% of the wETH (converted from the stETH accumulated during the bootstrapping phase via Phase 1 process above) will be paired with 50,309 MOR tokens on Uniswap
      - The pool fee will be set to 0.3%
      - Position will be created adopting a 'full range' liquidity position 
      - This will naturally create the initiation ratio, aka launch price
- Step 2: Create second liquidity position in MOR/wETH Pool
      - Single-sided concentrated liquidity position comprised of the remaining 48% wETH (converted from the stETH accumulated during the bootstrapping phase via Phase 1 process above)
      - As detailed in MRC09, concentrated position is strategically set from 0 to the initiation ratio

Note: The Morpheus multi-sig will establish the main pool on Arbitrum. All liquidity from capital providers will be concentrated there. Presumably, other market participants will create additional liquidity pools elsewhere.

Beware of pools with low liquidity which may result in significant slippage. 

BEWARE of Fake Token Pools and SCAMS. The pool address will be posted on all Morpheus channels once it has been established. 

**Resources:**

[Phased AMM Deployment | Fair Price Discorvery Proposal](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Phased%20AMM%20Deployment%20and%20Fair%20Price%20Discovery.md) 

[UniswapV3: How to Add Liquidity](https://support.uniswap.org/hc/en-us/articles/7423194619661-How-to-add-liquidity-to-Uniswap-v3) 

[Lido Staking and Redemption Process](https://stake.lido.fi/wrap)

[Lido Validator Queue](https://www.validatorqueue.com/ )
