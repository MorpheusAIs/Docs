## Code Provider - Proof of Contribution Table Snapshot #7
### July 1th to July 31th 2024

This table is for code contributions in Snapshot 6.  
[Snapshot 1](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot1.md) | [Snapshot 2](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot2.md) | [Snapshot 3](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot3.md) | [Snapshot 4](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot4.md) | [Snapshot 5](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot5.md) | [Snapshot 6](https://github.com/MorpheusAIs/Docs/blob/main/Contributions/Code%20-%20Proof_Of_ContributionSnapshot6.md)

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
**Snapshot 6:** $0.6 USD per Weight  
**Snapshot 7:** $0.27 USD per Weight (average price of July is $22.2 USD).

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
8. Weight Time (in months). The number of snapshots for which the weights will be considered in emissions.
9. Stake Time (in months). The time of code contributor MOR rewards staking to get Power Factor multiplier. More details in [MRC38.](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC38.md)
   

<p align="center">Example fields</p>
<b>Snapshot | MRI | Wallet Address | GitHub Handle | Description of Contribution | Proof | Weights Requested | Weight Time | Stake Time </b>
<br><br>
<p align="center">Input example</p>
<b>5 | 3 | 0xf93de9fb07f5762a1e3db9a5c687595111928d77 | my GH name | "code does: this" | "http:// Link to proof" | 1250 | 6 | 48 </b>
<br><br>

> [!IMPORTANT]
>
> - Create a pull request and add a row to the following table.
> - Only one MRI per entry.
> - If you are submitting multiple contributions, please create multiple pull requests - one pull request per contribution.
> - Only add your link at the bottom, and do not alter any other rows.
> - Detail the work you are contributing to Morpheus. You must include a link to the work for the work to be considered. Examples of proof include links to pull requests, github issues, or other easily verifyable information.
> - It is your responsibility to make the proof easily verifiable. Don't assume reviewers of this table have an understanding of your code. Explain it simply. Limit your descriptions to 200 words.
> - You need a wallet like Metamask that can receive Ethereum based tokens. MOR is an ERC-20 type token. Also must support Arbitrum.

## Code Contributions for Snapshot 7

| **Snapshot** | **MRI** | **Wallet Address**                         | **GitHub Handle** | **Description of Contribution**        | **Proof of Contribution**   | **Weights Requested** | **Weight Time** | **Stake Time**
| ---------- | ----- | ------------------------------------------ | ----------------- | ---------------------------------- | --------------------------- | ------------- | -------- | ------ |
| 7            | 8       | 0x0000000000000000000000000000000example | contributor  | Description of Contribution  | Proof of contribution links | 1250  | 3 | 48 |
| 7            | 8       | 0x22E0225540ccf80aB3C4F029F3dE75dB785754A3 | NirmaanAI  | Developed a claiming application/dashboard that enables capital and code contributors to connect their wallets and easily claim their rewards. The application features a simple, effective UI and follows a three-step process. First, users connect their wallets to load their accrued rewards. Second, they claim these rewards to an Arbitrum receiver address of their choice. In the final step, a timer and current balance are displayed, updating in real-time when the tokens arrive, and a confirmation card shows the updated balance and the amount of reward sent to the Arbitrum wallet. Additionally, the application includes a separate page where users can track their MOR token holdings on Arbitrum without needing to connect their wallets. This application is built directly on top of the distribution contract, ensuring direct interaction with the contract through our efficient and aesthetically pleasing UI. The streamlined claim process guarantees complete security while providing a seamless user experience. | [MOR Rewards Claim App](https://testing-2nm.pages.dev/) | 14000  | 11 | 0 |
| 7            | 2       | 0xC3B82270Db1b77B4bE28a83d0963e02c38A9d13f | artfuljars | Create 0.0.9 mac + windows build, create continuous integration (CI) pipeline for automatic Windows build creation  | https://github.com/MorpheusAIs/moragents/pull/46, https://github.com/MorpheusAIs/moragents/pull/43 | 132000 | | | 
| 7 | 9 | 0x62af7c48cf412162465a8cafde44dfb17ba96038 | antonb | Setup Morpheus Gitbook, pay for premium, fill with basic content that will be extended over time | [Morpheus Gitbook](https://morpheusai.gitbook.io/docs) | 35000  | 12 | 57 |
| 1 | 9 | 0x62af7c48cf412162465a8cafde44dfb17ba96038 | antonb | Support of MOR rewards staking launch, contract and dashboard testing and providing feedback, creating of testnet and mainnet guides and FAQ | [Testnet Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Testnet/MOR%20Rewards%20Staking%20Testnet%20Contract%20Guide.md), [Mainnet Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20Rewards%20Staking%20Mainnet%20Contract%20Guide.md), [FAQ](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/MOR%20Rewards%20Staking%20FAQ.md) | 15000  | 4 | 57 |
