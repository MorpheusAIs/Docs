# Protocol-owned Liquidity Generation Events (POLG)

## Smart Contracts:
### Ethereum:
- **Ethereum Morpheus Distribution contract:** [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)
- **Morpheus Ethereum** [**Multisignature**](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Multisignature%20Account.md) **wallet**: [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://etherscan.io/address/0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E)
 
### Arbitrum:
- **MOR token contract:** [0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86](https://arbiscan.io/token/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)
- **L2TokenReceiverV2 contract:** [0x47176b2af9885dc6c4575d4efd63895f7aaa4790](https://arbiscan.io/address/0x47176b2af9885dc6c4575d4efd63895f7aaa4790)
- **Morpheus Arbitrum** [**Multisignature**](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Multisignature%20Account.md) **wallet**: [0x151c2b49CdEC10B150B2763dF3d1C00D70C90956](https://arbiscan.io/address/0x151c2b49CdEC10B150B2763dF3d1C00D70C90956)
- **Uniswap Arbitrum liquidity pool:** [0xE5Cf22EE4988d54141B77050967E1052Bd9c7F7A](https://app.uniswap.org/explore/pools/arbitrum/0xE5Cf22EE4988d54141B77050967E1052Bd9c7F7A)

### Base
- **MOR token:** [0x7431ada8a591c955a994a21710752ef9b882b8e3](https://basescan.org/address/0x7431ada8a591c955a994a21710752ef9b882b8e3)
- **Multisig Base:** [0xf3ef00168dd40eae68a7e670d56c7b8724e0c183](https://basescan.org/address/0xf3ef00168dd40eae68a7e670d56c7b8724e0c183)

## PoL Generation Mechanics
### Pre-launch Bootstrapping Phase
Morpheus’ Fair Launch kicked off on February 8, 2024 at 12:00 UTC with the beginning of the liquidity Bootstrapping phase. The goal of this phase is to generate yield for Morpheus via the [Techno Capital Machine (TCM) model](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers%2C%20MOR20%2C%20TCM/Techno%20Capital%20Machine%20(TCM).md). 

Throughout this phase, Capital Providers were tasked with allocating their stETH yield towards Morpheus, contributing to the ecosystem's growth and stability. In return, Capital Providers were rewarded with 24% of the daily MOR emissions. 
Protection Fund reserves its allocated 4% of MOR emissions from the 90-day Liquidity Bootstrapping Phase for initializing the AMM Liquidity Pool.

### AMM Initiation Phase
On May 8th, 52% of the yield earned by Morpheus from Capital Providers by Day 88 was successfully paired with MOR tokens acquired by the Protection Fund at Uniswap Arbitrum chain. This strategic pairing optimized liquidity provisioning in line with long-term goals, taking into account the actual circulating supply as of Day 90.

The remaining 48% of the stETH yield and additional MOR from the Protection Fund were allocated to Uniswap V3 liquidity ranges. These ranges were adjusted weekly to support market activity by reducing price impact. This phase lasted for 30 days, after which the liquidity strategy transitioned to a broader range, enhancing overall market stability and liquidity.

Throughout this period, the yield generated was periodically added to the liquidity pool, supporting fair price discovery. Following the AMM Initiation Phase, 50% of the stETH yield was used to purchase MOR tokens, which, along with the remaining stETH (converted to wETH), was locked into the AMM as Protocol Owned Liquidity, in accordance with the guidelines set forth in Morpheus's Whitepaper.

### Long-term PoL 
During the bootstrapping phase, providing liquidity with both ETH and MOR made sense. However, with a significant amount of MOR now available for trading, a more refined Protocol Owned Liquidity (POL) pattern is proposed with [MRC 43](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC43.md):
   - stETH is swapped to wETH.
   - 75% of the resulting wETH is used to buy MOR from the Uniswap pool.
   - The remaining 25% of wETH is paired with 25% of MOR as full-range liquidity on Uniswap.
   - The other 50% of MOR purchased is burned and locked for 16 years to support Epoch 2 Tail Emissions in equal parts.

Initially, 50% of the MOR was used to deepen liquidity during the bootstrap phase. As liquidity solidifies, the focus shifts to buying 75% MOR to drive demand and scarcity. Eventually, the strategy could move to 100% MOR buyback when liquidity is deemed sufficient, prioritizing demand and scarcity.

## Conclusion
This approach aligns with the original design and whitepaper, ensuring liquidity for MOR sellers in the short and long term. By holding and periodically burning MOR, the token becomes increasingly scarce, reinforcing demand and deepening POL over time.
