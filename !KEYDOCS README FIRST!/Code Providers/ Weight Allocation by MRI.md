# Weight Allocations by MRI

## Introduction
The GitHub repository maintainer rewards contributions with weights, a crucial component of the protocol development. Weights play a pivotal role in motivating ongoing development and collaboration, serving as an incentive mechanism that underpins the operational expansion of the protocol.

As Morpheus began its bootstrapping, weights were distributed from a single pool as most early activities were interconnected and easily comparable in terms of the level of impact that they had. As Morpheus has evolved and expanded, there is an increasing need to isolate buckets of weights by Morpheus Reference Implementations (MRIs) to better align the overall goals of Morpheus along with doing the best possible job of putting GitHub repository maintainers in a position to accurately evaluate contributions via a narrower scope.

## Morpheus Reference Implementations (MRIs)
The key document which goes into detail regarding the MRI system and design can be found [here.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Morpheus%20Reference%20Implementations%20(MRC).md)

In summary, there are currently 10 existing MRIs last updated October 15th 2024:

- 1  	MOR Distribution Smart Contracts
- 2  	Smart Agents
- 3  	UI/UX (Local, Web, & Mobile)
- 4  	MOR20
- 5  	Protection Fund
- 6  	Capital Tools
- 7  	Routing Node & Compute Market
- 8  	Code Tools
- 9  	Builder Tools
- 10  MOR Interoperability


As Morpheus evolves, so will these MRIs. Some may accomplish their goals and fade away to maintenance roles, others may shift based on the overall changes to the ecosystem, and more will come into the fold as there are new opportunities and obstacles that develop for Morpheus. This is to be expected and should continue to foster an environment of healthy competition - furthering the point that weights are valuable and highly sought after. As Morpheus transitions into that period, these guides will expand on documentation in order to define the steps taking for MRIs to be added and/or removed entirely.

## Allocation by MRI
As each MRI focuses on a different level of technical expertise, knowledge, and impact to Morpheus, it would be difficult for any particular GitHub maintainer to be able to compare contributions related to one MRI against another. In that situation, you complicate the process by often getting apples to oranges comparisons. 

Therefore, allocating weights by MRI has the following main benefits:
- GitHub maintainers get to focus on their area of expertise and compare apples to apples.
- Each MRI can distribute their monthly weights how they view as the most impactful to Morpheus.
- No MRI can distribute above their monthly cap - they cannot give a disproportionate amount of weights to contributors.
- Generates a healthy level of competition among MRIs, both existing and new ones, to demonstrate and deliver the highest value to Morpheus.

## Allocation Methodology
As detailed in the [Code Contributor Weights Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Code%20Contributor%20Weights%20Guide.md), a maximum number of weights available for distribution has been determined based on an emission schedule. While the maximum amounts have been calculated and set, it is important to establish a fair and transparent process that will manage how weights are allocated among MRIs.

### Allocation Procedures
These allocation procedures are noted as the long-term steady state for allocation of weights. This will likely take several months to get fully up and running. In the meantime, the process will continue as it has via Atomic Governance. With that said, the following procedures are noted for the future state. 

Allocations to each MRI will ultimately be determined by staking of the Morpheus token (“MOR”). This will further the goals of decentralization as everyone is equally free to obtain or sell MOR tokens as they see fit.

In order to ensure transparency of the process, the below list will be the general steps taken.  
As technical development continues, this list will be continuously updated to reflect any changes.
1) Anyone can buy or sell MOR tokens throughout the snapshot period.
2) During the snapshot period, MOR token holders can stake their MOR to any MRI of their choosing.
3) Staked MOR is used to direct the subsequent snapshot period. I.e. If you stake during the snapshot ending June 8, 2024, the results will direct the weight allocations for the snapshot ending July 8, 2024.
4) Any staked tokens will be locked until the snapshot period ends.
5) At the completion of the snapshot period, each MRI will be allocated the percent of the total monthly weights equal to the percent of MOR that was staked.

For example, let's say 1,000,000 MOR was staked across all MRI's during the snapshot period ending June 8, 2024. If MRI 3 had 200,000 MOR staked, it would be allocated 20% of the weights (400,000 weights) for the upcoming snapshot period (ending July 8, 2024), as 2,000,000 total weights are available for that subsequent period.

## Allocation Snapshot
Similar to the Code Contributors Weights Snapshot used to track weights on a snapshot-by-snapshot basis. This will be updated each snapshot with the results posted to provide clear and transparent information to the community. When necessary, there will also be a small discussion section to highlight any particular notes - such as if there is a big need for weights in a specific MRI one month as a result of major developments.

| MRI | MRC | GitHub Maintainer |Snapshot 5: Ending June 8, 2024|
|--- |---|---|---|
| Smart Contracts | Whitepaper | David Johnson | 225,000 |
| Smart Agent Tools & Examples | Whitepaper | LachsBagel | 225,000 |
| Morpheus Local Desktop/Mobile | Yellow Paper | BetterBrand | 225,000 |
| TCM / MOR20 | TCM Paper | Anon 69 | 225,000 |
| Protection Fund | Whitepaper | EnergyHound | 225,000 |
| Capital Proofs Extending | Whitepaper | David Johnson | 225,000 |
| Compute Proofs MOR / Lumerin | Yellowstone | Ryan Condron | 225,000 |
| Code Proofs & Dashboards | Coding Guide  | David Johnson | 225,000 |
| Frontend Proofs & Examples | Waterloo Paper | Erik Voorhees | 225,000 |
| Interoperability | LayerZero | Anon 99 | 225,000 |
|Total | Total | n/a | 2,250,000 |

## Additional Considerations
### Unused Monthly Weights 
If an MRI owner does not distribute all of the weights allocated to their MRI for a particular month, those weights stay with the MRI owner to distribute in a later month. This encourages each MRI owner to use their weights responsibly, without pressure to spend all their weights in a given month which may result in inefficient and unnecessary distributions. The ultimate goal is  to get the most value out of weights for Morpheus and the broader ecosystem.

### MOR Staking
There are ongoing discussions and development in terms of staking the MOR token to direct the Community emissions to smart agents and front-ends. As this work progresses, it will be interconnected with the staking for MRI allocations as well. For example, will a MOR holder have to choose to stake for either MRI allocations or Community rewards or will they be able to stake for both using the same tokens. This will be flushed out in the coming months leading up to when MRI staking and Community staking go live.

### Contributor Weight Submissions to MRI Maintainers
Each MRI maintainer is in control of their budget, to use how they see fit. Their goal is to utilize weights related to their MRI to accomplish the objectives as laid out via the Code Contributor Weights guide. With that said, to help promote transparency and consistency across all the MRIs, and Morpheus as a whole, the following outline is offered as a suggestion on how to manage monthly weights by MRI. 

**Statistics broken down by MRI that captures:**
- Monthly available weights
- Weights assigned/distributed
- Weights in progress
- Remaining weights
- Estimated current value of each weight - so USD value is easily identifiable

> [!Note] 
> The exact format for this information is still a work in progress. It could be maintained via a snapshot in GitHub, or could become a page on the upcoming Code Contributor site that is being prepared by the community.

For contributors interested in requesting weights:
- Contributor submits ‘Preliminary Request’ to MRI Maintainer
  - Brief description
  - Estimated weight / USD range with basis for valuation
  - Brief analysis on value / deliverables / etc
- MRI Maintainer does a preliminary review to determine if:
  - Topic is relevant and needed
  - Weights are in a reasonable range
  - Ample weights are available that month based on expected other open requests
- Contributor and MRI owner discuss any open points and agree on the general topic, weights, deliverables
- Once work is completed, Contributor submits ‘Official Request’ to MRI Maintainer
  - Final description
  - Originally requested weights / USD range
  - Official requested weights / USD
  - Explanation for any changes
  - Deliverables

> [!Note] 
> There will be some instances where contributions may require quicker turnaround and not go through the full formalized process. In those situations, it is still highly recommended for contributors to contact the MRI maintainer as early as possible. Completion of work does not guarantee the allocation of any weights - it is fully at the discretion of the MRI maintainer. Thus, the more active the communication can be, the less likely efforts will be completed and ultimately not rewarded.

### Deprecated Weights
MRC31 also encompasses the process for deprecating weights when a contributor fails to conduct proper maintenance. There is still the outstanding question of what happens with those weights - do they get "burned,” do they go to a new contributor offering to provide the maintenance, do they go to Epoch 2, or some other approach. This Weight Allocation by MRI also comes into play as it’ll determine whether deprecated weights go to a broader pool or if they stay with a particular MRI. The authors of this paper plan to explore this idea and put forward further suggestions in a future paper.

### Maintenance
As noted in the paper above, MRIs will likely change over time. This will likely be alongside new MRI maintainers that will review what impact potential changes could have on the currently defined process. To the extent that any roadblocks or issues are raised, the MRC authors will collaborate with the community to determine potential solutions, ideally before any problems ever arrive. 

## Conclusion
Allocating weights by MRI will allow the maintainers to better distribute weights in an efficient manner than provides the most value back for Morpheus. It ensures that weights are distributed by the maintainers that are closest to the efforts and encourages ongoing communication between the community, contributors, and MRI maintainers. 
