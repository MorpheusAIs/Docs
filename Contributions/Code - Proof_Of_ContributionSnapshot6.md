## Code Provider - Proof of Contribution Table Snapshot #6
### June 1th to June 30th 2024

This table is for code contributions in Snapshot 6.  
[Snapshot 1](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot1.md) | [Snapshot 2](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot2.md) | [Snapshot 3](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot3.md) | [Snapshot 4](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot4.md) | [Snapshot 5](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot5.md)  

> [!IMPORTANT]  
> If this is your first pull request please read these documents first:
> 
> [**Coder Guide**](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Coder%20Guide.md)
>  
> [**The Best Practices Guide**](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Best%20Practices.md)
> 
> [**The Code Contributors Weights Guide**](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md)
>   
> [**MRC:37 Weight Time**](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC37.md)

## Code Contribution Bidding Schedule

![Monthly Dev Bid - Monthly](https://github.com/MorpheusAIs/MRC/assets/76454555/b4c42782-ca45-4a87-9583-12357cab2e85)

- By the 7th - Maintainers judge contributions from the previous month
- By the ~8th - Morpheus smart contract updated with new weights
- By the 9th - Contributors submit new bids by filling out the Bid for Weights form (see forms) 
- By the 15th - Maintainers will accept or reject new bidsSub
- By the 31st - Contributors submit a Proof of Contribution (see forms) describing a delivered contribution add the normal information on Github to the [snapshot file](https://github.com/MorpheusAIs/Docs/tree/main/Contributions) for that month.

### Forms
1. Bid for Weights: https://forms.gle/ZBmPXq4jZ3L6qwqR8
2. Proof of Contribution: https://forms.gle/51Bsd4QWoURAXEc7A

## Theoretical Implied Value of a Weight per Snapshot
**Snapshot 1:** $0.025 USD per Weight  
**Snapshot 2:** $0.2 USD per Weight  
**Snapshot 3:** $0.407 USD per Weight  
**Snapshot 4:** $0.783 USD per Weight  
**Snapshot 5:** $0.783 USD per Weight  
**Snapshot 5:** $0.6 USD per Weight (average price of June is $49.5 USD).

The weight calculation method explained [here](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md#calculating-the-implied-value-of-weights).

## Structuring of Code Contributions

All Code Contributions to include the following elements:

1. Snapshot number.
2. Morpheus Referrence Implementation a contributios falls under. The MRIs list is [here](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Morpheus%20Reference%20Implementations%20(MRI).md)
3. The Ethereum wallet address to be rewarded.
4. Handle of a contributor GitHub.
5. Full description of a contribution.
6. Proof of the Code Contribution (this may be a commit or PR).
7. Amount of [weights](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md#calculating-the-implied-value-of-weights) requested (as a number – do not include the word "weights").
8. Weight Time. The number of snapshots for which the weights will be considered in emissions.

<p align="center">Example fields</p>
<b>Snapshot | MRI | Wallet Address | GitHub Handle | Description of Contribution | Proof | Weights Requested | Weight Time</b>
<br><br>
<p align="center">Input example</p>
<b>5 | 3 | 0xf93de9fb07f5762a1e3db9a5c687595111928d77 | my GH name | "code does: this" | "http:// Link to proof" | 1250 | 6</b>
<br><br>

> [!IMPORTANT]
>
> - Create a pull request and add a row to the following table.
> - Only one MRI per entry.
> - If you are submitting multiple contributions, please create multiple pull requests - one pull request per contribution.
> - Only add your link at the bottom, and do not alter any other rows.
> - Detail the work you are contributing to Morpheus. You must include a link to the work for the work to be considered. Examples of proof include links to pull requests, github issues, or other easily verifyable information.
> - It is your responsibility to make the proof easily verifiable. Don't assume reviewers of this table have an understanding of your code. Explain it simply. Limit your descriptions to 250 words.
> - You need a wallet like Metamask that can receive Ethereum based tokens. MOR is an ERC-20 type token. Also must support Arbitrum.

## Code Contributions for Snapshot 6

| **Snapshot** | **MRI** | **Wallet Address**                         | **GitHub Handle** | **Description of Contribution** | **Proof of Contribution**   | **Weights Requested** | **Weight Time** |
| ---------- | ----- | ------------------------------------------ | ----------------- | ---------------------------------- | --------------------------- | ------------- | -------- |
| 6            | 8       | 0x2e84B79dd9773d712f9D20a98C4ee76541B9533D | dannweeeee   | Description of Contribution     | Proof of contribution links | 1250  | 3  |
| 6 | 2 | 0xA84471C5bAbC4Edd9f59cB4eC180a178AAdCEDac | object335 | RAG agent - final version, back-end & front-end, adapted to use ollama | https://github.com/MorpheusAIs/moragents/pull/34 | 100000 |  |
| 6            | 2       | 0xBdCfeB717DeAaae0aEAA1D4c80c4E46C9231063f | MuncleUscles   | FeedBuzz - Intelligent Log Aggregation   | https://github.com/yeagerai/feedbuzz-contracts | 50000  |   |
| 6            | 2       | 0x096904182208dFAeD937361ae83d45De5A1f4c9C                     | IoDmitri          | Model verification algorithm to detect bad actors on the network                    | https://github.com/MorpheusAIs/HideNSeek       | 150000       |          |
| 6            | 2      | 0x48d0EAc727A7e478f792F16527012452a000f2bd  | lachsbagel  | Pioneering Work in Model Verification | https://github.com/MorpheusAIs/HideNSeek | 50000 | |
| 6 | 2 | 0xC3B82270Db1b77B4bE28a83d0963e02c38A9d13f | artfuljars | ollama in wizards + unit testing framework for moragents under the guidance of Lachsbagel | https://github.com/MorpheusAIs/moragents/pull/35, https://github.com/MorpheusAIs/moragents/pull/36 | 80000 | |
| 6 | 2 | 0x48d0EAc727A7e478f792F16527012452a000f2bd | lachsbagel | coordination and architecture | https://github.com/MorpheusAIs/moragents/blob/main/AGENTABILITIES.md | 50000 | |
| 6            | 7       | 0x22E0225540ccf80aB3C4F029F3dE75dB785754A3 | NirmaanAI   | Full Frontend, UI and Backend Development for Morpheus Lumerin Node Dashboard: We've incorporated the suggestions from the last issue and successfully developed a fully functional dashboard that integrates information from the Lumerin Node Contracts. To achieve this, we forked, deployed, and verified the official Lumerin contracts, creating a 1:1 replica. This forked version was populated with on-chain data to register providers, models, bids, and open/close sessions. We revamped the UI and frontend to align with the official Morpheus design and developed a new backend to fetch on-chain data for models, providers, bids, and sessions. To optimize performance, we implemented a state-of-the-art caching mechanism that updates every few minutes, ensuring a smooth user experience. Key features added include: A graph tracking average daily IPS across all sessions, A marketplace table comparing models, best bids, number of providers, and active sessions, A comprehensive models page listing all available models and a graph comparing the number of sessions opened daily versus active sessions, Provider comparison tables showing total sessions completed, sessions for specific models, average IPS, and bid price per second. | https://nirmaan-morpheous-dashboard.pages.dev/, https://nirmaan-morpheous-dashboard.pages.dev/model, https://nirmaan-morpheous-dashboard.pages.dev/provider?address=0x23ECAd7A98CE5EC6cCaac8Bc01ae8d3bD07Dd7A6 | 35000 | 11 |
| 6 | 6 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Detailed guide on how to claim MOR from the dashboard website as there were several requests from community members who are not familiar with Arbitrum chain. This guide will also be placed on the capital claim mor.org page. Maintenance and updates over time weight period | https://github.com/MorpheusAIs/Docs/pull/333 | 2500  | 7 |
| 6 | 1 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Technical specification and providing assistance to a developer for a dashboard to track and collect statistics for balances/sales/claims/transfers and liquidity of Morpheus contributors. Full maintenance and updates over time weight period | https://parsec.fi/layout/BT/brknrAI5 | 3500 | 12 |
| 6 | 9 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Collect, prepare and review with maintainers information about Morpheus achievements, developments and progress starting from the May 8th for Morpheus digest that will be published at the mor.org website. The digest will be compiled every month until Jan 2025 | https://docs.google.com/document/d/1jZfNqAMW5qxvjR4vQti_xArnZXvl1UFGKTrOxZw7tdg/edit?usp=sharing | 21000  | 7 |
| 6 | 9 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Develop connectors to provide updated Morpheus data and new metrics to Defillama, one of the biggest dapps aggregators (history data for TVL, MOR supply, Protocol owned Liquidity, Mcap, MOR price, trading volume). Full maintenance and updates over time weight period | https://github.com/DefiLlama/DefiLlama-Adapters/pull/10817, https://github.com/DefiLlama/defillama-server/pull/7399 | 5000  | 12 |
| 6 | 8 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Morpheus GitHub repositories review, content generation and update, structure optimization, link fixes, cross-linking and formatting| https://github.com/MorpheusAIs/MRC/pull/70, https://github.com/MorpheusAIs/Docs/pull/329, https://github.com/MorpheusAIs/Docs/pull/324, https://github.com/MorpheusAIs/MOR20/pull/12, https://github.com/MorpheusAIs/MRC/pull/65, https://github.com/MorpheusAIs/Docs/pull/315, https://github.com/MorpheusAIs/Docs/pull/292, https://github.com/MorpheusAIs/Morpheus/pull/666, https://github.com/MorpheusAIs/MorpheusLinux/pull/4 | 35000  | 7 |
| 6 | 10 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonboss | Extensive testing of MOR bridge contracts using OFT LayerZero standard and creating users’ guide. Full maintenance and updates over time weight period | https://github.com/antonbosss/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20OFT%20Bridge%20Guide.md | 7000  | 12 |

