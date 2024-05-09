## Code Provider - Proof of Contribution Table Snapshot 2. 
### February 8th to March 8th 2024

This table is historical for Snapshot 2.  
Please direct all new pull requests to the latest Snapshot document in the folder.

> [!IMPORTANT]  
> **Before adding a pull request to this table please read [The Best Practices Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Contributor%20Best%20Practices.md)**
&
**[The Code Contributors Weights Guide](https://github.com/MorpheusAIs/Docs/blob/main/Guides/Code%20Contributor%20Weights%20Guide.md)**.

## Snapshot Timelines and Implied Value of a Weight
**Snapshot 1.** September 2nd 2023 to February 8th 2024  
Theoretical Implied Value of a Weight = $0.025 USD per Weight (price is unknown 1MOR = 1MOR).  
 
**Snapshot 2.** February 8th to March 8th 2024  
Theoretical Implied Value of a Weight = $0.2 USD per Weight (price is unknown 1MOR = 1MOR).  

> [!NOTE]
> **Weights are being rebased by 2,000 X at Snapshot 3 to create more granularity as fractions of weights are not supported in the Smart Contract. For more details check [MRC14](https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC14.md)**


## Structuring your Code Contributions

All Code Contributions should include the following five elements:

1. The Ethereum wallet address to be rewarded.
2. Link to the Code Contribution (this may be a commit or PR).
3. Number of [weights](https://github.com/MorpheusAIs/Docs/blob/main/Guides/Code%20Contributor%20Weights%20Guide.md) requested (as a number – do not include the word "weights").
4. Description of Contributions.

Example fields below:  

`|               Wallet Address               |     Link to Work    | Weights Requested (weights) | Description of Contribution |`  
`| 0x98eFf980C57c9D333340b3856481bF7B8698987c | Link to Commit #127 | 50                          | Integration of ollama       |`

Please include the "pipe" `|` symbol correctly as seen above so your contribution will format with the table.

> [!NOTE]
> - Create a pull request and add a row to the following table.
> - If you are submitting multiple contributions, please create multiple pull requests - one pull request per contribution.
> - Only add your link at the bottom, and do not alter any other rows.
> - Detail the work you are contributing to Morpheus. You must include a link to the work for the work to be considered. Examples of proof include links to pull requests, github issues, or other easily verifyable information.
> - It is your responsibility to make the proof easily verifiable. Don't assume reviewers of this table have an understanding of your code. Explain it simply. Limit your descriptions to 250 words.
> - You need a wallet like Metamask that can receive Ethereum based tokens. MOR is an ERC-20 type token. Also must support Arbitrum.

## Code Contributions for Snapshot 2

| Wallet Address | Link to Work | Weight of Value Contributed (Weights) | Description of Contribution                                                                                                                                                                                                                           |
| -------------- | ------------ |----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0x76c22534B60B5dbbe16e9Fc0325435fd68550Bf3 | [Proof of Capital Dune Dashboard](https://dune.com/syncracy/morpheus) | 1 | A Dune dashboard to track the progress of Morpheus fair launch |
| 0x63e55D70e546Bf5276F13888058160a5583D2BD1 | [Overview of Morpheus Fair Launch Dune Dashboard](https://dune.com/binarybuddha/morpheus-fair-launch) | 1 | A dashboard that gives an overview of the stETH stakers on Morpheus Protocol, giving an insight of the protocol's fair launch traction. The metrics include number of unique depositors, withdrawers, net stakers and their corresponding amount in stETH and USD |
| 0xCC5e733cB2E7a59EFC5463575EfC3584D5922486 | https://github.com/MorpheusAIs/Morpheus/tree/0.0.5, https://github.com/MorpheusAIs/Morpheus/blob/006-alpha-fix-2/Contributions/Code%20-%20Proof_Of_Contribution.md | 860 | 0.0.5 build, test, package, sign, publish, diagramming, instructions, 0.0.6-alpha-fix-2 |
| 0x80CdcF57f42C6BfB429b245d798ee46b9F71Edea | https://github.com/MorpheusAIs/Morpheus/pull/517 | 70 | First Smart Agent |
| 0xFa126C09DB44851BFa6bD9D70016f499fdc5586D | [https://github.com/MorpheusAIs/Morpheus/pull/522](https://github.com/MorpheusAIs/Morpheus/pull/522) | 8 | UI style adjustments |
| 0xbac0086453F04Abc25539A1d5D90f797419F9842 | https://github.com/MorpheusAIs/Morpheus/pull/486 | 120 | Fixing the local morpheus client, ollama spawning, asar packaging, Electron CSP |
| 0xC16C04dE65E2EBA60B78294E23953f5EB17F9202 | [https://github.com/MorpheusAIs/tree/rag-feature-branch](https://github.com/MorpheusAIs/Morpheus/tree/rag-feature-branch)https://github.com/MorpheusAIs/Morpheus/tree/rag-feature-branch | 80  | LLamaIndex, Langchain and JSON RPC APIs |
| 0x65DF6F7E5897b033CAcF77447f0fe274aa03B156 | https://github.com/MorpheusAIs/Morpheus/blob/main/Asset/Design%20Library.md, (https://github.com/MorpheusAIs/Morpheus/commit/647f110028d99fd6a5a62927cd65114d3336e468)  | 180 | Administration of Socials, Medium, Design elements, Social graphics, infographics, Design of 4C Sigils, FAQ reiterations, Integrations|
| 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | https://github.com/MorpheusAIs/Morpheus/pull/484, https://github.com/MorpheusAIs/Morpheus/pull/518 | 32 | Editing, adding info to EN whitepapper, Yellow paper and TCM Helping questions and answers to FAQ to Oracle, adding FAQ to Github, Alinging UA and RU TCM, WP and Yellowstone model with EN version, Test dashboard + feedback with findings, translated announcements to RU and UA, helping newcomers with questions and navigation, assisting with issues, facilitating conversations, moderating Ukrainian and Russian language channels |
| 0xbc012fae5b08b244ae680b307a1e03f697d337f6 | https://github.com/MorpheusAIs/Morpheus/pull/547 | 8  | Add funds protection doc translations |
| 0x0d2065e3Ed3E36919b2AD12FDA8E428Da91bb28D | https://dune.com/potato6969/morpheus-fair-launch and [https://github.com/MorpheusAIs/Morpheus/pull/587](https://github.com/MorpheusAIs/Morpheus/pull/587) | 20 | Dune Dashboard and Guide for TCM Contracts Data Analysis |
| 0x28D3bDeCE9A0c7F54687F734fA73fBA04ECf5785 | https://github.com/MorpheusAIs/Morpheus/pull/569 | 8 | Translated Yellowpaper into Korean |
| 0xA94b40c53432f0576E64873CE1CEAd1aae62Fc90 |  | 10 | Best Practice #7 |
| 0x3476ee81BA812D56b571bCc2e6122De698084E15 | https://morstats.info and [https://github.com/MorpheusAIs/Morpheus/pull/601](https://github.com/MorpheusAIs/Morpheus/pull/601) | 25 | Capital Provider Dashboard and Guide for stETH and MOR Calculations |
| 0x6b11a53f72503CfE069818c96f2173506E89B2d0 | https://github.com/MorpheusAIs/Morpheus/commit/5318ccda60698a7336ab6412e3813530c8d179ca | 2.5 | Add guide on how to install morpheus on windows |
| 0x9f953211e1C05548B9A4fc8eD3Ea3Ee90B971E5F | https://github.com/MorpheusAIs/Morpheus/commit/2d37b70a02bd4b3abc3f3d716f344764045e301a | 2 | Albanian whitepaper translation |
| 0xd406993dB46F6f415C2DDD1620081A37188d43c9 | https://github.com/MorpheusAIs/Docs/pull/32 | 5 | Expansive Urdu Translations for Enhanced Global Reach |
| 0x4E1ebaf42b37Fa8af7a5544F06E8c4aefe06F0B8 | https://github.com/MorpheusAIs/Morpheus/pull/540 | 1 | Reviewed language etc |
| 0x06fe938d02C4AB732Db5918dA83Eeb712AD453Ad | https://github.com/MorpheusAIs/Docs/pull/49 | 1.5 | Spell check code contribution weight |
| 0xbc012fae5b08b244ae680b307a1e03f697d337f6 | https://github.com/MorpheusAIs/Morpheus/pull/547 | 8 | Add funds protection doc translations |
| 0xaA5CaAcfD7a79A3A3B7d99D0c35DB90AF8C27676 | https://github.com/MorpheusAIs/Morpheus/pull/597 | 2 | Spell check and natural language corrections |
| 0x06fe938d02C4AB732Db5918dA83Eeb712AD453Ad | https://github.com/MorpheusAIs/Morpheus/pull/624 | 2 | French installation guide |
| 0xaA5CaAcfD7a79A3A3B7d99D0c35DB90AF8C27676 | https://github.com/MorpheusAIs/DashBoard/pull/28 | 3 | Pull request for Dashboard repo - Fixes an issue raised by a user https://github.com/MorpheusAIs/DashBoard/issues/14 and update to messages |
| 0xFA47FA4f95110Bce0B7716056f41e5D982BBfBba | https://github.com/MorpheusAIs/Morpheus/pull/317, https://github.com/MorpheusAIs/Morpheus/pull/285 | 25 | Tranlation for Central Asia|
| 0x2567D753e50159EffcCaB3DA32c960148C93e1a5 | https://github.com/MorpheusAIs/Morpheus/pull/628 | 2 | Whitepaper, Yellow paper, Compute model tranlations in Malayalam language for smc.org.in Malayalam computing community|
| 0xe4C6B02b6095A18D4FF867218A31ff7b11C3e828 | https://youtu.be/PiZnvLYvXCI | 5 | Educational materials: explainer vid for the techno capital machine whitepaper |
| 0xe4C6B02b6095A18D4FF867218A31ff7b11C3e828 | https://www.dropbox.com/scl/fi/czsstt88iz2njze2gusek/MTV.ADB.1.25.24.EG-Building-the-future-of-Web3-Space.RL.mp4?rlkey=e6fmhbfxxpmpw5jcqnebiuaj2&dl=0 | 5|  Educational materials: downloadable/reusable vertical micro content on the TCM explainer vid |
| 0xe4C6B02b6095A18D4FF867218A31ff7b11C3e828 | https://www.dropbox.com/scl/fi/jlb5934fcqd4iemeh1a3m/MTV.ADB.1.25.24.EG-Influence-Project-Growth-Revised.mp4?rlkey=596j3zz2pxxoeo6qxca97vb6b&dl=0 | 5 | Educational materials: downloadable/reusable vertical micro content on the TCM explainer vid |
| 0xe4C6B02b6095A18D4FF867218A31ff7b11C3e828 | https://www.youtube.com/playlist?list=PLko1NeTe2LV7rWl49Z34qeuTK7zlrf8DE | 5 | Educational materials: batch of micro content of David Johnston's NABs speech. Downloadable/reusable for marketing/education purposes |
| 0xc97eEB4223D5b33222ced576C8B73F4c81978Dac | https://github.com/MorpheusAIs/Morpheus/pull/506 | 8 | Translated yellowstone whitepaper into Korean |
| 0x502e6D422ea4538aE2AF21564dfeeC39e3068dB8 | https://github.com/MorpheusAIs/Morpheus/pull/595 , https://github.com/MorpheusAIs/Morpheus/pull/594 | 2 | Proofread and corrected typo errors |
| 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | https://github.com/MorpheusAIs/Morpheus/pull/484 , https://github.com/MorpheusAIs/Morpheus/pull/518, https://github.com/MorpheusAIs/Morpheus/pull/589, https://github.com/MorpheusAIs/Morpheus/pull/630 | 155 | Update documentation, WP, Yellowstone, TCM, testing dashboard, mainnet SC deposit guide, Morpheus Meetup Guide, Morpheus Tokenomics doc, financial indicators for MOR, contributing ideas and content to MORstats, administration and moderation of socials, discord tech support |
| 0x14589BDFdbe3044501044df5B6d53be2f47e92e5 | https://github.com/MorpheusAIs/Morpheus/pull/618 | 1  | Check and Use OLLAMA_HOST environment variable |
| 0x31E985b4f7af6B479148d260309B7BcEcEF0fa7B | https://github.com/MorpheusAIs/Morpheus/pull/332 | 15 | Translated the whitepaper from English to Swedish |
| 0x2e84B79dd9773d712f9D20a98C4ee76541B9533D | https://github.com/MorpheusAIs/Morpheus/pull/627 | 8  | Added send button to Morpheus main UI |
| 0x6e48adc8c660b6eb83abfefc918f19604bbcb89a | https://github.com/MorpheusAIs/Node/pull/29 , https://github.com/MorpheusAIs/Node/pull/31 , https://github.com/MorpheusAIs/Node/pull/33 , https://github.com/MorpheusAIs/Node/pull/27 , https://docs.google.com/document/d/18MrUJrxxUqw9CaXNlcgNbRxr1Va4Owzv7kv6p8pKgKo , https://github.com/MorpheusAIs/Node/pull/39 , https://github.com/MorpheusAIs/Node/pull/40 , https://github.com/MorpheusAIs/Node/pull/43 , https://docs.google.com/document/d/1tjsvGwrOzrqPpzhWQxVWmsVnrPz8cNZNAazO285VM3o , https://docs.google.com/document/d/181KlGZ7du2wkg9ie-nQw4f4wHlotZwvA1ICVK2jhorc/edit | 115 | Coding, testing, and collaboration in launching Node 0.0.6. Reviewed PRs. Made SmartAgent V1 tech spec for design and milestoning collaboration. Contributing/continuing to contribute to smart agent / router brainstorming sessions for the direction of both. Implemented UI/UX changes for light node client. Paired on defining MOR-20 template. Research/design/begin development on mor.software v2 |
| 0x62aF7c48Cf412162465A8CaFdE44dFb17bA96038 | https://github.com/MorpheusAIs/Morpheus/pull/646, https://github.com/MorpheusAIs/Morpheus/pull/650, https://github.com/MorpheusAIs/Docs/pull/8, https://github.com/MorpheusAIs/Docs/pull/11, https://github.com/MorpheusAIs/Docs/pull/12, https://github.com/MorpheusAIs/Docs/pull/14, https://github.com/MorpheusAIs/Docs/pull/15, https://github.com/MorpheusAIs/Docs/pull/24, https://github.com/MorpheusAIs/Docs/pull/45 | 113 | Reorganisation of the /Docs repository, including moving files, restructuring folders structure, fixing links; keeping documentation up to date; research for anti-MEV solutions; contributions to fair price discovery doc; administration and moderation of socials, discord tech support; holding an AMA with David Johnston on Discord |
| 0x5160E91cD5D6b8c3cb5103bE4C470eaC6f123f03 | https://github.com/MorpheusAIs/Morpheus/pull/634/commits/18ca822b43e114204a57ea8b2efadca2552bda1e , https://github.com/MorpheusAIs/Docs/pull/58/commits/7ed191ed04d3ee121cdcd5d7f8d1c95ba6c62b39 | 50 | Integrations, dashboard |
| 0x8b194B58B47ff0008ac89a99e54cFdB3ca2f4a5F | https://github.com/MorpheusAIs/Morpheus/pull/30 | 1  | Fully translated Whitepaper to Vietnamese - intending to keep updated |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | https://drive.google.com/file/d/14a43HQu7Da33xRtrtlBUbJIM8e2gJ8Ss/view?usp=sharing | 150 | Morpheus node architecture |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | https://drive.google.com/file/d/1wRYjtIzVgYQkvuo6SsUZrkat83W2MF7v/view?usp=sharing | 40 | Morpheus wallet UI design |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | https://drive.google.com/file/d/1wRYjtIzVgYQkvuo6SsUZrkat83W2MF7v/view?usp=sharing | 50 | Morpheus provider marketplace UI design |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | https://drive.google.com/file/d/1cDVXvzYaRnDArzh9QPE4W-KDG1obUzyC/view?usp=sharing | 50 | Router architecture and logic flows |
| 0x0D56bAF5Ec33E9EA364BD1e1Ce7AffBF2d457Ec8 | https://docs.google.com/document/d/1_3JAxTBsrUXM6wkyLGZx58FlPYj1cbWv1yS8PhLV4s4/edit?usp=sharing | 80 | Morpheus Ecosystem Smart Contract |
| 0x478aC52c212d5e98EdF0e5877f50AfF38f1f647E | https://github.com/MorpheusAIs/Docs/issues/6| 2 | Discovered bug: 7 day withdrawal lock resets after staking more stETH for total stETH contributed |
| 0x50c7455004f331258E1Acb0a8D526176a1e60980 | https://github.com/MorpheusAIs/Morpheus/pull/632 | 19 | Setup a test suite and wrote test suite for ollama integration of electron application, all apis of ollama are now covered with success and failure unit tests; added error checking for response stream, fixed variable scope issue in ollama integration, added code coverage calculation, jest configurations; added editor specific files from gitignore |
| 0x8ed1221d896a32a1a37a4c6b67577e7eaa67b2d3 | https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md | 3 | Helped construct tokenomics and mechanism design for Morpheus |
| 0x3476ee81BA812D56b571bCc2e6122De698084E15 | https://github.com/MorpheusAIs/Docs/pull/19 , https://github.com/MorpheusAIs/Docs/pull/22 , https://github.com/MorpheusAIs/MRC , https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Fair%20Price%20Discovery.md , https://docs.google.com/document/d/1uMvRT_WA1KqJAkoHbs7fxDkMtYrcdprXrbOmssEXtGg/edit , MorStats.info| 52 | Updated MorStats.info with stETH withdrawals, yield, resources, and price analytics. Proofread, collaborated, and contributed to the following documents: Fair Price Discovery, Fair Launch Process, Waterloo Community Model, Code Contributor Weights Guide|
| 0x65DF6F7E5897b033CAcF77447f0fe274aa03B156 | https://github.com/MorpheusAIs/Docs/blob/main/Asset/Design%20Library.md, [(https://github.com/MorpheusAIs/Morpheus/commit/647f110028d99fd6a5a62927cd65114d3336e468)](https://morpheus-dashboard.vercel.app/)|80|	Administration of Socials, Design elements, Decemination of Morpheus materials, infographics, FAQ reiterations, Integrations, Alpha Dashboard, Testing of morstats, ideations of AMM, testing of 0.0.6 implementation. |
| 0x5694baAEaCa2C419306c9Bf5dbfdAC7F92c7704c | https://github.com/MorpheusAIs/Docs/blob/main/Asset/Design%20Library.md | 10 |  AnonG updated Design Element Collections and Creation of Assets  |
| 0xe4D28FE30829A825B7379EF28d5d91174436C899 |   https://github.com/MorpheusAIs/Docs/blob/main/Asset/Design%20Library.md, (https://morpheus-dashboard.vercel.app/) | 20 | AnonP Major Design work for Sigils, Posters Design, Sticker Design, Dashboard Designs, Logos and new updated infographics|
| 0x0Ba7a85Af6323686a1fE29423bd72c2ce81Fe923 | @TigerBuidl | 8 | Building FAQ for Morpheus community. |
| 0x3476ee81BA812D56b571bCc2e6122De698084E15 | Morstats.info , https://github.com/MorpheusAIs/Docs/pull/51 , https://github.com/MorpheusAIs/Docs/pull/52 , https://docs.google.com/document/d/1PYeWnu3KpQdExwwuKFgGbRl9eajc6oP1poEQZmf7S2w/edit , https://docs.google.com/document/d/1TfnIJXGCJWVPNFrXnbHvoZBs2KOauZQZz6GOhAeTCcI/edit#heading=h.rqskt7b9rus2 , https://docs.google.com/document/d/1uMvRT_WA1KqJAkoHbs7fxDkMtYrcdprXrbOmssEXtGg/edit?usp=sharing , https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Fair%20Price%20Discovery.md , https://docs.google.com/document/d/15d9VkMinNykq0i9LCxjqb9Dz_p8E73GRkV8GPFjp1aA/edit | 43  | Morstats.info code weights table, calculators, MOR market cap analytics, and updated for community feedback. Collaborated, developed analytics for, and helped to create and test the following concepts: Fair Price Discovery and AMM Launch, Protection Fund Diversification, Waterloo Community Model, Code Contributor Weights Guide, Dev Morpheus U3 aka Signaling Fair Launch|
| 0x8d7D04B3679074ff3FBE64f92b24aDB31a602b35 | https://github.com/MorpheusAIs/Node, https://mor.software, https://github.com/MorpheusAIs/Docs | 138 | Morpheus 0.0.6, mor.software, repo management, setup of liet client from node and morpheus lumerin node |
| 0x8d7D04B3679074ff3FBE64f92b24aDB31a602b35 | https://github.com/MorpheusAIs/Node, https://github.com/MorpheusAIs/Docs | 138 | Morpheus 0.0.6, mor.software, repo management, setup of liet client from node and morpheus lumerin node |
| 0x14589BDFdbe3044501044df5B6d53be2f47e92e5 | https://github.com/MorpheusAIs/Docs/pull/13 | 2 | Translated whitepaper and yellowpaper to Traditional Chinese |
| 0xC54d82BD1255a7C7b605f5D6c56823Fd3188ADb9 | https://github.com/MorpheusAIs/Docs/pull/9 | 1 | Translation of Polish paper |
| 0x8e027FCf704c0881aA52c9AFe161b45B6E14c2Da | https://github.com/MorpheusAIs/Morpheus/pull/658 https://github.com/MorpheusAIs/Node/pull/44 | 8 | UI improvement and API integration for listing locally installed models |
| 0xBb7eF56b6efC4a93Df7c1258Ac994fcE297EAe6B | https://github.com/MorpheusAIs/Docs/commit/97dc32f3fe0cb5834b3b6c2fa8e760b461aaa766 https://github.com/MorpheusAIs/Docs/commit/172749c1ecfad6a47efc876f0dc3728d14285eff | 1  |	Translation white/yellowpaper to Bengali | 
| 0x8eecf398819b87547cb178daaef9ecde3597bfab | https://github.com/MorpheusAIs/MRC | 80 | Assisted in research and development for the creation of the "Building the Foundation: Phased AMM Deployment in Morpheus" document. Conducted scenario analysis on various initiation possibilities. Collaborated with other community members to explore alternative launch mechanisms |
| 0xe70Ac2bAFdcD047B34dfB4B056bFDb941b91b0c9 | https://github.com/MorpheusAIs/Node/pull/48 , https://github.com/MorpheusAIs/Node/pull/48/commits/7eb5f9aff2264981d9c59338040927bb5f3ddbc3 | 2 | improvement of user journey and UX/UI |
| 0x478aC52c212d5e98EdF0e5877f50AfF38f1f647E | https://youtu.be/BevLkb-m1fs?si=Qtzi0vd_oZXFL70O | 5 | Guide to provide capital |
| 0x478aC52c212d5e98EdF0e5877f50AfF38f1f647E | https://youtu.be/UdhbLkJA3pA?si=qTf4xQWTQOSZHVuQ | 5 | How to use dashboards | 
| 0x90B77ba59889A1EC737B4eBC8C78B69f7578BB46 | https://github.com/MorpheusAIs/Morpheus/issues/106 , https://github.com/MorpheusAIs/Morpheus/issues/294 | 20 | Testing and troubleshooting models for each version from 0.0.1 - 0.0.6 consisting of UI and UX issue/bug identification and resolution, documention |
| 0x8ed1221d896a32a1a37a4c6b67577e7eaa67b2d3 | https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md | 3 | Helped construct tokenomics and mechanism design for Morpheus |
| 0x3476ee81BA812D56b571bCc2e6122De698084E15 | https://github.com/MorpheusAIs/Docs/pull/19 , https://github.com/MorpheusAIs/Docs/pull/22 , https://github.com/MorpheusAIs/MRC , https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Fair%20Price%20Discovery.md , https://docs.google.com/document/d/1uMvRT_WA1KqJAkoHbs7fxDkMtYrcdprXrbOmssEXtGg/edit , MorStats.info| 52 | Updated MorStats.info with stETH withdrawals, yield, resources, and price analytics. Proofread, collaborated, and contributed to the following documents: Fair Price Discovery, Fair Launch Process, Waterloo Community Model, Code Contributor Weights Guide|
| 0x8d7D04B3679074ff3FBE64f92b24aDB31a602b35 | https://mor.software, https://github.com/MorpheusAIs/Morpheus/issues/106, https://github.com/MorpheusAIs/Morpheus/issues/633, https://github.com/MorpheusAIs/Morpheus/pull/606, https://github.com/MorpheusAIs/Morpheus/pull/576, https://github.com/MorpheusAIs/Morpheus/pull/618, https://github.com/MorpheusAIs/Morpheus/pull/527  | 163 | mor.software MVP, issues and pull requests, onbarding |

**Snapshot 2 contributions are added to the contract with [transaction1](https://etherscan.io/tx/0x28b11f5e3d05daba8c7c4fd2bc1fdad35f46294b876553dc595490a856c7a794) and [transaction2](https://etherscan.io/tx/0x5c554afc10497b17b434860103650415b826c2c4ff572c156c24b3fa7bb9e8ec)**


> [!IMPORTANT]  
> ### This table is closed for adding entries. Contributions added here won't be rewarded.


