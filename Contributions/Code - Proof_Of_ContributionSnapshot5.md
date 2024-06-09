## Code Provider - Proof of Contribution Table Snapshot #5
### May 8th to June 8th 2024

This table is for code contributions in Snapshot 5.  
[Snapshot 4](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot4.md)  
[Snapshot 3](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot3.md)  
[Snapshot 2](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot2.md)  
[Snapshot 1](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot1.md)  

> [!IMPORTANT]  
> If you would like to make a pull reqest please submit to latest snapshot after reading   
> [The Best Practices Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Best%20Practices.md)
> [The Code Contributors Weights Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md)

## Snapshot Timelines and Implied Value of a Weight
**Snapshot 1.** September 2nd 2023 to February 8th 2024  
Theoretical Implied Value of a Weight = $0.025 USD per Weight (price is unknown 1MOR = 1MOR).   

**Snapshot 2.** February 8th to March 8th 2024  
Theoretical Implied Value of a Weight = $0.2 USD per Weight (price is unknown 1MOR = 1MOR).
  
**Snapshot 3.** March 8th to April 8th 2024  
Theoretical Implied Value of a Weight = $0.407 USD per Weight (price is unknown 1MOR = 1MOR).  

**Snapshot 4.** April 8th 2024 to May 8th 2024   
Theoretical Implied Value of a Weight = $0.783 USD per Weight (price is unknown 1MOR = 1MOR).  

**Snapshot 5.** May 8th 2024 to June 8th 2024   

Theoretical Implied Value of a Weight = $1.186 USD per Weight (average price from the 8th to the 27th of May: $97.07 USD).  
The weight calculation method explained [here](https://github.com/MorpheusAIs/Docs/blob/main/Guides/Code%20Contributor%20Weights%20Guide.md#year-1-weights-schedule).

## Structuring of Code Contributions

All Code Contributions to include the following elements:

1. Snapshot number.
2. Morpheus Referrence Implementation a contributios falls under.
3. The Ethereum wallet address to be rewarded.
4. Handle of a contributor GitHub.
5. Full description of a contribution.
6. Proof of the Code Contribution (this may be a commit or PR).
7. Amount of [weights](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md#calculating-the-implied-value-of-weights) requested (as a number – do not include the word "weights").

Example fields below:  

`Snapshot | MRI | Wallet Address | GitHub Handle | Description of Contribution | Proof of Contribution | Weights Requested`  

`5 | 3 |0xf93de9fb07f5762a1e3db9a5c687595111928d77 | mordeveloper | Integration of ollama | Link to Commit #127 | 1250`  

Please include the "pipe" `|` symbol correctly as seen above so your contribution will format with the table.

> [!IMPORTANT]  
> There is new a new MRI column added where the contributor should specify which MRI the contribution is related to.
>  
> One MRI = one entry.
> 
> Don't combine multiple MRIs in a single line. Break out contributions into their own line in the table.  

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
> - Only one MRI per entry.
> - If you are submitting multiple contributions, please create multiple pull requests - one pull request per contribution.
> - Only add your link at the bottom, and do not alter any other rows.
> - Detail the work you are contributing to Morpheus. You must include a link to the work for the work to be considered. Examples of proof include links to pull requests, github issues, or other easily verifyable information.
> - It is your responsibility to make the proof easily verifiable. Don't assume reviewers of this table have an understanding of your code. Explain it simply. Limit your descriptions to 250 words.
> - You need a wallet like Metamask that can receive Ethereum based tokens. MOR is an ERC-20 type token. Also must support Arbitrum.

## Code Contributions for Snapshot 5


 **Snapshot** | **MRI** | **Wallet Address** | **GitHub Handle** | **Description of Contribution** |  **Proof of Contribution** | **Weights Requested**  
---|---|---|---|---|---|---
 5 | 3 | 0xf93de9fb07f5762a1e3db9a5c687595111928d77 | mordeveloper | Description of Contribution | Proof of contribution links | 1250 | 
 5 | 4 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonbosss | MOR launch support, coordination and tech assistance, implementation of extra the anti-spam and anti-scam measures on launch, daily monitoring of fake MOR tokens; added information about MOR token to Geckoterminal; applied and paid for MOR listing at Dexscreener and Dappradar; MOR20 Dashboard testing and feedback; assisterr MOR20 onboarding and assistance | https://dexscreener.com/arbitrum/0xe5cf22ee4988d54141b77050967e1052bd9c7f7a, https://www.geckoterminal.com/arbitrum/pools/0xe5cf22ee4988d54141b77050967e1052bd9c7f7a, https://www.loom.com/share/13e055ab70694184a79e37a72cba7d00?sid=917ee6a1-7ef1-458e-ba52-f6bc5ef101be, https://dappradar.com/dapp/morpheus  | 12000 
 5 | 1 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonbosss | bought and sent to multisig MOR.ARB handle to prevent squatting | https://arbiscan.io//tx/0x296d3676741cee699761fd19071236321949fb6269bd9ab9288a2ae58147f015 | 900
 5 | 8 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonbosss | MOR.Software terms of reference review and feedback | https://mor.software/ | 400
 5 | 9 | 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | antonbosss | Re-work of the General, Capital, Code, MOR token and PoL FAQs; compute test launch FAQ; new README for 0.0.8 release doc; Github structure optimization, update of links and content; administration and moderation of socials, tech assistance, facilitation of discussions, sharing and coordination of the information exchange; organization and managing of the Discord AMA and events; added, setup and paid for telegram Combot premium subscription; integration of new MOR token data for Discord and Telegram info bot. | https://github.com/MorpheusAIs/Morpheus/pull/666, https://github.com/MorpheusAIs/MorpheusLinux/pull/4, https://github.com/MorpheusAIs/Docs/pull/292, https://github.com/MorpheusAIs/Docs/pull/261, https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/FAQs | 17000 
 5 | 3 |0xf93de9fb07f5762a1e3db9a5c687595111928d77 | mordeveloper | Description of Contribution | Proof of contribution links | 1250 | 
 5 | 8 |0xEb4E7939C3bCC0635b8531e3C0a6bD42de95cfeF | Stan909 | MRC22 - Staking for community rewards collaboration. Supporting document to expanding on analysis, guidance, frameworks, templates, and considerations relevant to staking procedures and the Community emissions | https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC22.md , https://docs.google.com/document/d/1CvDcZn2lfjYPvWZc4QvqZXrU26nyax0HfW6tOTq9ndE/edit | 25000 | 
 5 | 8 |0x03aa1e85487a5c3c509bc584ad9490a41d248011 | Nebuchadnezzar Crew 2 - Anon | MRC22 - Staking for community rewards collaboration. Supporting document to expanding on analysis, guidance, frameworks, templates, and considerations relevant to staking procedures and the Community emissions | https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC22.md , https://docs.google.com/document/d/1CvDcZn2lfjYPvWZc4QvqZXrU26nyax0HfW6tOTq9ndE/edit | 25000 | 
 5 | 2 | 0x63AE77cCa59BbEdCbEe3F88C51231056e7f9929C | LachsBagel | local install 0.0.8 | https://github.com/MorpheusAIs/moragents/pull/14 | 20000 |
 5 | 2 | 0x622805409A2632b7Ca58c970925e009555567891 | object335 | Rag Agent - local install example agent | https://github.com/object335/morpheus_rag_agent | 100000
 5 | 2 | 0xC3B82270Db1b77B4bE28a83d0963e02c38A9d13f | artfuljars | Windows and MacOS moragents builds and packaging | [moragents builds project](https://github.com/LachsBagel/moragents/blob/e499b416e2b3612f3779ae2bdb31d5b925d277e5/AGENTABILITIES.md?plain=1#L30) | 50000 |
 5 | 2 | 0x5CD4C60f0e566dCa1Ae8456C36a63bc7A8D803de | polupoker | Discord & Telegram Bots development | https://discord\.com/oauth2/authorize?client\_id=1225160336144076980&permissions=292058032192&scope=bot, https://t.me/morpheus_ai_info_bot | 1500 |
 5 | 9 | 0xE4708c48B2E1FDee9DD60A08F3E89aee45B93906 | Tigerbuidl | This month its been a lot of integrations work (events such as Consensus). On boarding contributors to the ecosystem (via Discord). Support for engagement with developers (DeAI Day related work). And Posting Talks and speeches at events on Youtube (@morpheusintern) |  | 29000 |
 5 | 8 | 0xe36B28c72C1F7f8a4D87cA5d64B63233875173a4 | xfactor | azure terraform | https://github.com/indrgun/terraform-azure-linux-vm/tree/mv-azure/azure | 15000 | 8 |
 5 | 1 |0xEb4E7939C3bCC0635b8531e3C0a6bD42de95cfeF | Stan909 | (Nebuchadnezzar Crew #1) Per MRC31, creation of the framework for weight allocation by MRI. Document outlines the allocation methodology, snapshot procedures, and additional considerations for framework | https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/%20Weight%20Allocation%20by%20MRI.md , https://github.com/MorpheusAIs/Docs/pull/259 | 19000 | 
 5 | 8 |0xEb4E7939C3bCC0635b8531e3C0a6bD42de95cfeF | Stan909 | (Nebuchadnezzar Crew #1) Per MRC31, creation of the framework for weight allocation by MRI. Document outlines the allocation methodology, snapshot procedures, and additional considerations for framework | https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/%20Weight%20Allocation%20by%20MRI.md , https://github.com/MorpheusAIs/Docs/pull/259 | 1000 | 
 5 | 2 | 0x4317C2A305857eD8A9Bc2Db3190083584C916bd2 | dorianjanezic | Helping with the development of MORAgents local build install; identifying and providing a correct command for installing smart agent docker image | https://discord.com/channels/1151741790408429580/1220404152165994648/1239497522846896210, https://discord.com/channels/1151741790408429580/1167520984849469530/1242529458339057684 | 2000
 5 | 3 |0xf93de9fb07f5762a1e3db9a5c687595111928d77 | rcondron | Description of Contribution | Proof of contribution links | 1250 | 
 5 | 9 | 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | rcondron | \[MORLORD\]\(https://morlord\.com\) updates, testnet API endpoints, Marketplace UI for testnet, Provider registry for testnet | \[MORLORD\]\(https://morlord\.com\) | 100000 | 
 5 | 7, 3, 1 | 0x8bfA2307C282f114F4F3384FE88957EB4ED47588 | rcondron | Testnet launch!, UI updates, QA checks for user <> provider connection | \(https://github\.com/MorpheusAIs/Morpheus\-Lumerin\-Node/tree/main/proxy\-router\), \[Morpheus\-Lumerin\-Node Electron Desktop UI\]\(https://github\.com/MorpheusAIs/Morpheus\-Lumerin\-Node/tree/main/ui\-desktop\), \[Morpheus\-Lumerin\-Node Smart Contracts\]\(https://github\.com/MorpheusAIs/Morpheus\-Lumerin\-Node/tree/main/smart\-contracts\), \[Morpheus Architecture Guidance Doc\]\(https://github\.com/MorpheusAIs/Docs/blob/main/\!KEYDOCS%20README%20FIRST\!/Morpheus%20Lumerin%20Model\.md\) | 450000 | 
 5 | 1 | 0x3386Ab7D6AfaE6cEaBE0213ae35b46036C1E67ac | rcondron | Node design updates, session router design updates for evergreen sessions, new provider report schema, new smart contract structures | \[Morpheus Architecture Guidance Doc\]\(https://github\.com/MorpheusAIs/Docs/blob/main/\!KEYDOCS%20README%20FIRST\!/Morpheus%20Lumerin%20Model\.md\) | 150000 |
 5 | 8 |0xefc7d0a88AA9AA7c161CF93B78dAD64f86d9358d | rethereum1 | Creation of a MOR ERC20 token dashboard. The dashboard connects directly to the blockchain and pulls information on: MOR Transfers, MOR claimed, MOR token accumulation, the liquidity orderbook of all MOR univ2 & uniV3 LPs, detailed breakdown of each LP, MOR live trade tracker & trades by size, MOR token holders treemap & list. A full guide is included | (https://parsec.fi/layout/BT/brknrAI5 and https://docs.google.com/document/d/1f3g_qZ51ogWxOqrH9gkPdkXVFSMeX54SNyReT-Ca5jw/edit?usp=sharing) | 13,000 |
 5 | 8 |0x256cfAE8091aeF65EF77089CF717571D3309ae0a |	Betterbrand |	https://github.com/MorpheusAIs: MRC, LC/Node |	MRI 8, NFA, MRC, GH |  25,000 |   
 5 | 8 |0x0d00486197600e94876C3D4542dDe6703a9018E4	| joeyzengazi | AI Day	| event | 2,500 |
 5	| 8 |0x478aC52c212d5e98EdF0e5877f50AfF38f1f647E	| Taddy Mason | AI Day	| event | 2,500 |
