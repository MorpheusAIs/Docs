## Code Provider - Proof of Contribution Table Snapshot 
### April 8th to May 8th 2024

This table is for code contributions in Snapshot 4.  
[Snapshot 3](https://github.com/MorpheusAIs/Docs/blob/main/Code%20Contributions/Code%20Contributions%20Snapshot%203.md)
[Snapshot 2](https://github.com/MorpheusAIs/Docs/blob/main/Code%20Contributions/Code%20Contributions%20Snapshot%202.md)
[Snapshot 1](https://github.com/MorpheusAIs/Docs/blob/main/Code%20Contributions/Code%20Contributions%20Snapshot%201.md)

> [!IMPORTANT]  
> **Before adding a pull request to this table please read [The Best Practices Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Contributor%20Best%20Practices.md)**
&
**[The Code Contributors Weights Guide](https://github.com/MorpheusAIs/Docs/blob/main/Guides/Code%20Contributor%20Weights%20Guide.md)**..

## Snapshot Timelines and Implied Value of a Weight
**Snapshot 1.** September 2nd 2023 to February 8th 2024  
Theoretical Implied Value of a Weight = $0.025 USD per Weight (price is unknown 1MOR = 1MOR).   

**Snapshot 2.** February 8th to March 8th 2024  
Theoretical Implied Value of a Weight = $0.2 USD per Weight (price is unknown 1MOR = 1MOR).
  
**Snapshot 3.** March 8th to April 8th 2024  
Theoretical Implied Value of a Weight = $0.407 USD per Weight (price is unknown 1MOR = 1MOR).  

**Snapshot 4.** 
April 8th 2024 to May 8th 2024  
Theoretical Implied Value of a Weight = $*.** (to be calculated at the end of the month) USD per Weight (price is unknown 1MOR = 1MOR). 

> [!NOTE]
> **Weights were rebased by 2,000 X at Snapshot 3 to create more granularity as fractions of weights are not supported in the Smart Contract. For more details check [MRC14](https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC14.md)**

## Structuring your Code Contributions

All Code Contributions should include the following five elements:

1. The Ethereum wallet address to be rewarded.
2. Link to the Code Contribution (this may be a commit or PR).
3. Number of [weights](https://github.com/MorpheusAIs/Docs/blob/main/Guides/Code%20Contributor%20Weights%20Guide.md) requested (as a number – do not include the word "weights").
4. Description of Contributions.

Example fields below:  

`|               Wallet Address             |  MRI   |   Link to Work    | Weights Requested (weights) | Description of Contribution |`  
`| 0x98eFf980C57c9D333340b36481bF7B8698987c | MRI #3 | Link to Commit #127 | 50                        | Integration of ollama       |`

Please include the "pipe" `|` symbol correctly as seen above so your contribution will format with the table.

> [!IMPORTANT]  
> There is new a new MRI column added where the contributor should specify which MRI the contribution is related to. 

- **MRI Number 1:** [Smart Contracts on Ethereum / Arbitrum](https://github.com/MorpheusAIs/SmartContracts)  
  - **Maintainer's GitHub Handle:** [DavidAJohnston](https://github.com/DavidAJohnston) 
- **MRI Number 2:** [Smart Agents Tools & Examples](https://github.com/MorpheusAIs/SmartAgents)
  - **Maintainer's GitHub Handle:** [LachsBagel](https://github.com/LachsBagel)
- **MRI Number 3:** [Morpheus Local Install Desktop / Mobile](https://github.com/MorpheusAIs/Morpheus)
  - **Maintainer's GitHub Handle:** [betterbrand](https://github.com/betterbrand)
- **MRI Number 4**: [TCM / MOR20 Token Standard for Fair Launches](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md)
  - **Maintainer's GitHub Handle:** [EnergyHound](https://github.com/EnergyHound)
- **MRI Number 5**: [Protection Fund](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
  - **Maintainer's GitHub Handle:** [EnergyHound](https://github.com/EnergyHound)
- **MRI Number 6:** [Capital Proofs Extended beyond Lido stETH](https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC15.md)
  - **Maintainer's GitHub Handle:** [DavidAJohnston](https://github.com/DavidAJohnston)
- **MRI Number 7:** [Compute Proofs Morpheus / Lumerin](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)
  - **Maintainer's GitHub Handle:** [rcondron](https://github.com/rcondron)
- **MRI Number 8:** [Code Proofs & Dashboards](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Coder%20Guide.md)
  - **Maintainer's GitHub Handle:** [betterbrand](https://github.com/betterbrand)
- **MRI Number 9:** [Frontend Proofs & Examples](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC08.md)
  - **Maintainer's GitHub Handle:** [ErikVoorhees](https://github.com/ErikVoorhees)
- **MRI Number 10:** [Interoperability](https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC16.md)
  - **Maintainer's GitHub Handle:** [RuslanProgrammer](https://github.com/RuslanProgrammer) / [DavidAJohnston](https://github.com/DavidAJohnston)



> [!NOTE]
> - Create a pull request and add a row to the following table.
> - If you are submitting multiple contributions, please create multiple pull requests - one pull request per contribution.
> - Only add your link at the bottom, and do not alter any other rows.
> - Detail the work you are contributing to Morpheus. You must include a link to the work for the work to be considered. Examples of proof include links to pull requests, github issues, or other easily verifyable information.
> - It is your responsibility to make the proof easily verifiable. Don't assume reviewers of this table have an understanding of your code. Explain it simply. Limit your descriptions to 250 words.
> - You need a wallet like Metamask that can receive Ethereum based tokens. MOR is an ERC-20 type token. Also must support Arbitrum.

## Code Contributions for Snapshot 4

| Wallet Address | MRI | Link to Work | Weight of Value Contributed (Weights) | Description of Contribution |
| -------------- | ------- | ------------ |----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0xA6D60da9ed25509092bA912b523F812E109F3C9c | 3 | [PWA]https://github.com/MorpheusAIs/pwa/pull/3 | 20,000 | PWA: new pages and chat integration |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | 9 | [MORLORD](https://morlord.com) | 100,000 | Public API endpoints for MOR.org, Marketplace UI prep for beta, community leaderboard |
| 0x8bfA2307C282f114F4F3384FE88957EB4ED47588 | 7 | [Morpheus-Lumerin-Node Proxy Router](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/tree/main/proxy-router) | 200,000 | Proxy API for localhost UIs, Wallet Refactoring from Electron to GO, Node multithread testing, AI engine integrations |
| 0x8bfA2307C282f114F4F3384FE88957EB4ED47588 | 3 | [Morpheus-Lumerin-Node Electron Desktop UI](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/tree/main/ui-desktop) | 150,000 | Chat interface for electron front end, provider & model registry UI for electron front end |
| 0x8bfA2307C282f114F4F3384FE88957EB4ED47588 | 1 | [Morpheus-Lumerin-Node Smart Contracts](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/tree/main/smart-contracts) | 100,000 | Smart contract development and deployment for provider registry, model registry, agent registry, MOR staking and compute sessions |
| 0xae855e324087A34E96bB9127d2e17c1A12873020 | 8 | [MRC31 Thread](https://discord.com/channels/1151741790408429580/1228539984844165140) | 5,000 | Proposals and discussions on the MRC31 |
| 0xa13984862467DCaa12c47b849C5Da4cB3a8d0915 | 1 | [Morpheus Architecture Guidance Doc](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Lumerin%20Model.md)| 100,000 | Session router smart contract design updates, node architecture updates, smart contract updates to handle new compute tranche migration strategy |
| 0xC3B82270Db1b77B4bE28a83d0963e02c38A9d13f | 8 | https://docs.google.com/document/d/196-ew97-Z436c9xWBtNuWC6ngnaYs6QOfxoGRulLYrY/edit | 20000 | Drafting, development, discussions, design considerations around d-git and morsoftware |
| 0xe36B28c72C1F7f8a4D87cA5d64B63233875173a4 | 3 | https://docs.google.com/document/d/179Hfe_CUICLBBUY00WnlJu1KSmggkclH_5XEeQDphM0/edit | 10,000 | CI/CD development workflow - Describes the development and release process across multiple concurrent feature branches for project applications |
| 0x80AC5d6B29EC148cb1f71a18C2A4F0A0c7DEddF0 | 8 | https://mor.codes, https://github.com/mor-codes/morcodes-ui | 10000 | Developing mor.codes, a code contribution dashboard system that simplifies the proof of contribution on GitHub with basic search and filter functionalities |
| 0xa1c5a906B69A3B149836753e5705ee06057D51eF | 1 | https://github.com/MorpheusAIs/MRC/blob/main/MRC34.md, https://github.com/MorpheusAIs/MRC/pull/52 | 65,000 | Draft MRC34, beginning of research and discussion of Smart Agent Domains implementation with the team. Fixes in other MRCs. And some helpful comments in PRs/Issues |
