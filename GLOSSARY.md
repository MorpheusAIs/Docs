# Morpheus Glossary

## Quick Navigation
[A](#a) • [B](#b) • [C](#c) • [E](#e) • [F](#f) • [I](#i) • [L](#l) • [M](#m) • [P](#p) • [S](#s) • [T](#t)

## A

**Agent Proof**
- A verification process performed by coders to audit agents, ensuring their stated functions are as presented and contain no malicious code.
- Related: *Smart Agent*, *Coder*

**AgentRank Algorithm**
- A system for curating specialized agents based on their effectiveness in executing actions for users.
- Related: *Smart Agent*, *PromptRank Algorithm*, *SmartContractRank Algorithm*

**Automated Market Maker (AMM)**
- A decentralized trading protocol that enables automatic trading of cryptocurrencies and tokens.
- Related: *Protocol-owned Liquidity*, *Liquidity Position*

## B

**Block Rewards**
- Initial daily reward of 14,400 MOR tokens distributed to network participants:
  - 24% Community
  - 24% Capital
  - 24% Compute
  - 24% Code
  - 4% Protection Fund
- Related: *MOR Token*, *Tail Emission*

**Burn Function**
- A mechanism for permanently removing MOR tokens from circulation through a dedicated burn address (0x000000000000000000000000000000000000dead) to increase token scarcity.
- Related: *MOR Token*, *Tail Emission*

## C

**Capital Provider**
- An entity that provides stETH to generate yield for the Morpheus network, contributing to Protocol-owned Liquidity (PoL).
- Must lock deposits for minimum 7-day period
- Receives MOR rewards proportional to contribution
- Related: *Protocol-owned Liquidity*, *TCM*

**Coder**
- A contributor who runs the Morpheus full node and develops agents, smart contracts, or other software for the Morpheus Network.
- Must register with cryptographic signatures and version metadata
- Competes in free market for development opportunities
- Related: *Full Node*, *Smart Agent*

**Community Builder**
- An entity that runs the Morpheus full node and uses the Morpheus API to provide user front ends & developer tools.
- Creates specialized agents and applications
- Earns rewards based on MOR transaction fees burned
- Related: *Full Node*, *Morpheus API Gateway*

**Compute Budget**
- A daily allocation of compute resources that MOR token holders can access proportional to their holdings.
- Related: *Compute Marketplace*, *MOR Token*

**Compute Marketplace**
- A decentralized marketplace where AI Inference Providers can offer compute hardware and Consumers can utilize AI services through prompts and other interactions.
- Related: *Compute Node*, *Compute Provider*, *Morpheus Router*

**Compute Node**
- Developer software that enables advanced access to the Morpheus Compute Marketplace, used by both advanced Consumers and Marketplace Providers.
- Related: *Compute Marketplace*, *Compute Provider*

**Compute Provider**
- An entity running a full node that provides compute resources and offers IPS (inferences per second) bids through the Router.
- Must hold MOR tokens to participate
- Competes in free market for compute provision
- Related: *Compute Marketplace*, *IPS*, *Morpheus Router*

## E

**Epoch**
- A defined period in the Morpheus token distribution schedule, with the first epoch lasting 5,833 days (approximately 16 years).
- Related: *Block Rewards*, *Tail Emission*

## F

**Fair Launch**
- The launch model of Morpheus with no pre-mine, no early token sale, and equal opportunity for all participants to earn MOR tokens through contribution.
- Related: *MOR Token*

**Full Node**
- A complete installation of the Morpheus software that includes wallet functionality and the ability to run Smart Agents.
- Related: *Smart Agent*

**Full Time Equivalent (FTE)**
- A measure used to calculate coder contributions based on the value of work contributed rather than time spent.
- Related: *Coder*

## I

**IPS (Inferences Per Second)**
- The atomic unit of inference in AI, used to measure compute resource usage.
- Related: *Compute Provider*, *Compute Marketplace*

## L

**Liquidity Position**
- A stake in an AMM liquidity pool, specifically referring to the full-range positions owned by the Morpheus protocol.
- Related: *Protocol-owned Liquidity*, *TCM*

## M

**MOR Token**
- The native token of the Morpheus network with a maximum supply of 42 million tokens.
- Key features:
  - Fixed supply cap of 42 million tokens
  - 16-year initial distribution period
  - Burning mechanism for increased scarcity
  - 256-year tail emission schedule
- Related: *Block Rewards*, *Burn Function*, *Tail Emission*

**Morpheus**
- A network designed to power Smart Agents, integrating LLMs, Agents, and Web3 technologies.
- Built on principles of:
  - Individual sovereignty
  - Voluntary markets
  - Free market competition
  - Decentralized governance
- Related: *Smart Agent*, *Smart Agent Protocol*

**Morpheus API Gateway**
- Front-end API infrastructure that provides simplified access for consumers to utilize the Morpheus Compute Marketplace.
- Related: *Compute Marketplace*, *Morpheus Router*

**Morpheus Router**
- The underlying smart contract infrastructure that powers the Morpheus Compute Marketplace, managing the negotiation between Users and Providers for compute resource allocation.
- Responsibilities include:
  - Processing compute requests
  - Managing provider bids
  - Recording performance metrics
  - Facilitating reward distribution
- Related: *Compute Marketplace*, *Compute Provider*

## P

**Protocol-owned Liquidity (PoL)**
- Liquidity owned by the protocol itself, generated from stETH yield and used to ensure stable trading of the MOR token.
- Created through:
  - 50% of ETH yield used to buy MOR
  - Remaining ETH paired with purchased MOR
  - Added to full-range liquidity positions
- Related: *TCM*, *Liquidity Position*

**Prompt Proof**
- A verification generated during user interaction that confirms the expressed intent matches the smart contract selection and transaction values.
- Related: *Smart Agent*, *PromptRank Algorithm*

**PromptRank Algorithm**
- A system for curating prompts based on projected user intent and action.
- Related: *AgentRank Algorithm*, *SmartContractRank Algorithm*

**Protection Fund**
- 4% of MOR resources reserved for security measures
- Covers predefined failure scenarios
- Managed by developer community
- Includes bug bounties and security measures
- Related: *Block Rewards*

## S

**Smart Agent**
- An AI-powered agent capable of executing Smart Contracts on behalf of a user, with user approval required for all transactions.
- Key principles:
  - Cannot execute decisions independently
  - No access to private keys
  - Local installation preferred
  - User approval required for transactions
- Related: *Smart Agent Protocol*, *Agent Proof*

**Smart Agent Protocol**
- The underlying protocol that enables Smart Agents to interact with Web3 infrastructure.
- Related: *Smart Agent*, *Morpheus*

**SmartContractRank Algorithm**
- A system for scoring and recommending Smart Contracts based on user intent.
- Related: *AgentRank Algorithm*, *PromptRank Algorithm*

## T

**Tail Emission**
- A long-term token distribution mechanism that:
  - Begins after the initial 5,833-day period
  - Set to 50% of burned MOR tokens from previous period
  - Capped at 16% of circulating MOR supply
  - Extends for 256 years
- Related: *Block Rewards*, *MOR Token*, *Burn Function*

**TCM (Techno-Capital Machine)**
- The process of yield contribution, token swapping, and liquidity addition that powers the Morpheus network's capital provision system.
- Key components:
  - Yield generation from stETH
  - Automated MOR token purchases
  - Protocol-owned liquidity creation
- Related: *Protocol-owned Liquidity*, *Capital Provider* 