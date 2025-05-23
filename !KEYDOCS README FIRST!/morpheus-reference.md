# Morpheus Reference

## Tokenomics
- Token Symbol: MOR
- Supply Cap: 42,000,000 MOR
- Initial Emission: 14,400 MOR/day, declining by 2.468994701 MOR/day
- Distribution: 24% each to community, capital, compute, code; 4% to protection funds

## Emission Schedule
- Block reward starts at 14,400 MOR per day and declines daily until reaching 0 on day 5,833 (about 16 years).
- After 5,833 days, tail emissions begin: 50% of burned MOR in the previous period, capped at 16% of circulating supply per period.
- See diagrams for emission curves and supply projections.

## MOR Token Utility
- MOR is used for on-chain accounting, paying compute providers, purchasing specialized agents, and rewarding users for training data.
- Fees for compute, code, capital, and community are paid in MOR, creating demand as usage grows.

## Smart Contract Details
- MOR token is implemented as an ERC20 contract on Ethereum mainnet and Arbitrum L2.
- Capital Provider, Coder, Compute, and Community Builder contracts manage registration and rewards.
- Deposits and claims are made via smart contracts; stETH is used for capital provision.

## Tech Stack
- Ethereum mainnet and Arbitrum L2 for smart contracts and rewards.
- IPFS and Filecoin for decentralized storage.
- Zero-knowledge proofs and FHE for privacy and scalability (future roadmap).

## Security Model
- 4% of MOR emissions reserved for protection fund to compensate users in case of bugs or failures.
- Community-driven oracle to recognize and address economic effects of bugs.
- Potential integration with decentralized protection networks (e.g., Nexus Mutual).

## Diagrams
- Emission curves, supply projections, and user flow diagrams are available in the original WhitePaper and graphics directory. 