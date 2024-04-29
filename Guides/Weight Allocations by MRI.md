# Weight Allocations by MRI

## Introduction
The GitHub repository maintainer rewards contributions with weights, a crucial component of the protocol development. Weights play a pivotal role in motivating ongoing development and collaboration, serving as an incentive mechanism that underpins the operational expansion of the protocol.

As Morpheus began its bootstrapping, weights were distributed from a single pool as most early activities were interconnected and easily comparable in terms of the level of impact that they had. As Morpheus has evolved and expanded, there is an increasing need to isolate buckets of weights by Morpheus Reference Implementations (MRIs) to better align the overall goals of Morpheus along with doing the best possible job of putting GitHub repository maintainers in a position to accurately evaluate contributions via a narrower scope.

## Morpheus Reference Implementations (MRIs)
The key document can for MRIs can be found at https://github.com/MorpheusAIs/Docs/blob/9d3c789c2ed7511d04d07e1b5411d33edb55d5e7/!KEYDOCS%20README%20FIRST!/Reference%20Implementations.md#morpheus-reference-implementations-mrisds which goes into detail regarding the MRI system and design.

In summary, there are currently 10 existing MRIs:
- Smart Contracts
- Smart Agent Tools & Examples
- Morpheus Local Desktop / Mobile
- TCM / MOR20
- Protection Fund
- Capital Proofs Extending
- Compute Proofs MOR / Lumerin
- Code Proofs & Dashboards
- Frontend Proofs & Examples
- Interoperability

As Morpheus evolves, so will these MRIs. Some may accomplish their goals and fade away to maintenance roles, others may shift based on the overall changes to the ecosystem, and more will come into the fold as there are new opportunities and obstacles that develop for Morpheus. This is to be expected and should continue to foster an environment of healthy competition - furthering the point that weights are valuable and highly sought after. As Morpheus transitions into that period, these guides will expand on documentation in order to define the steps taking for MRIs to be added and/or removed entirely.

## Allocation by MRI
As each MRI focuses on a different level of technical expertise, knowledge, and impact to Morpheus, it would be difficult for any particular GitHub maintainer to be able to compare contributions related to one MRI against another. In that situation, you complicate the process by often getting apples to oranges comparisons. Therefore, allocating weights by MRI has the following main benefits:

- GitHub maintainers get to focus on their area of expertise and compare apples to apples
- Each MRI can distribute their monthly weights how they view as the most impactful to Morpheus
- No MRI can distribute above their monthly cap - they cannot give a disproportionate amount of weights to contributors
- Generates a healthy level of competition among MRIs, both existing and new ones, to demonstrate and deliver the highest value to Morpheus

## Allocation Methodology
As detailed in the Code Contributor Weights Guide, https://github.com/MorpheusAIs/Docs/blob/9d3c789c2ed7511d04d07e1b5411d33edb55d5e7/Guides/Code%20Contributor%20Weights%20Guide.md, the maximum number of weights available for distribution varies monthly in Year 1, and then hits a consistent distribution starting in Year 2 - with this amount being adjusted each year. It is important to establish a fair and transparent process that will manage how weights are allocated among MRIs.

**Allocation Procedures** - The first month where the weights are allocated by MRI will have a default of an even distribution among each MRI. Subsequent months will use the default of the prior month percentage allocations. This will create smoother adjustments across MRIs as the prior month is most likely to resemble the upcoming month compared to any other data point. 

For any given month, the allocations can stray away from the default values. This may occur for a variety of reasons: MRIs could wind down or not have much activity expected in an upcoming month, there could be a strong push required to ramp up aspects of an MRI before a major launch or release, an MRI might naturally require more resources, or any other number of reasons.

In order to ensure transparency of the process, the following will be the general steps taken:
1) Prior month percentage allocations are rolled forward to current month
2) Any adjustments to number of weights are made (i.e. if MRI 1 has 10% and the total weights for the month drop from 2,500,000 to 2,000,000, then MRI 1 goes from 250,000 weights to 200,000 weights)
3) Any MRI owner can submit their request for an adjustment in weights. The owner should specify the number of weights they would like to change as well as if there is a particular MRI they think those weights should come from, or if they are requesting an even spread across the other MRI owners.
  - I.e. MRI owner 1 wants to request 50,000 additional weights for Month 4. They request that these additional weights come as 34,000 from MRI 2 and then 2,000 from MRIs 3 through 10.
  - Or… MRI owner 1 wants to request 50,000 additional weights for Month 4. They don’t identify a specific MRI that the weights will come from so the implied result would be that the other 9 MRIs all give up 5,556 weights.
4) Discussions take place among MRI owners and the community. These discussions will talk through the reasoning behind increases/decreases in weights for an MRI. It will give everyone a forum to raise questions, comments, and concerns, as perhaps a community member was planning a big contribution in an upcoming month that was previously unknown.
5) If a general consensus is reached, then the weights will be adjusted as agreed upon.
6) If no general consensus can be reached, then the default of the prior month remains in place.
7) The GitHub maintainer reserves the right to make final decisions if there are varying viewpoints on the weight allocations.

**Atomic Governance** - This document outlines the standard procedures to be followed in the ordinary course of operations. The goal is to create a transparent process that accurately allocates MRIs with weights according to need. However, there might be situations where a general consensus is not reached, but it is in Morpheus’ best interest to make an adjustment to the allocations nonetheless. In these types of situations, the GitHub Maintainer reserves the right to change weight allocations as they deem appropriate.

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
|Total | Total | n/a | 2,250,000|

## Additional Considerations
**Unused Monthly Weights** - If an MRI owner does not distribute all of the weights allocated to their MRI for a particular month, those weights stay with the MRI owner to distribute in a later month. This encourages each MRI owner to use their weights responsibly, without pressure to spend all their weights in a given month which may result in inefficient and unnecessary distributions. The expectation is that each MRI owner will run their MRI as a ‘business.’ They are trying to get the most value out of their allocated weights on behalf of their MRI as well as Morpheus as a broader ecosystem.

**Contributor Weight Submissions to MRI Maintainers** - Each MRI maintainer is in control of their budget, to use how they see fit. Their goal is to utilize weights related to their MRI to accomplish the objectives as laid out via the Code Contributor Weights guide. With that said, to help promote transparency and consistency across all the MRIs, and Morpheus as a whole, the following outline is offered as a suggestion on how to manage monthly weights by MRI. 

Statistics broken down by MRI that captures:
- Monthly available weights
- Weights assigned/distributed
- Weights in progress
- Remaining weights
- Estimated current value of each weight - so USD value is easily identifiable
**Note:** The exact format for this information is still a work in progress. It could be maintained via a snapshot in GitHub, or could become a page on the upcoming Code Contributor site that is being prepared by the community.

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

**Note**: There will be some instances where contributions may require quicker turnaround and not go through the full formalized process. In those situations, it is still highly recommended for contributors to contact the MRI maintainer as early as possible. Completion of work does not guarantee the allocation of any weights - it is fully at the discretion of the MRI maintainer. Thus, the more active the communication can be, the less likely efforts will be completed and ultimately not rewarded.

**Deprecated Weights** - MRC31 also encompasses the process for deprecating weights when a contributor fails to conduct proper maintenance. There is still the outstanding question of what happens with those weights - do they get "burned,” do they go to a new contributor offering to provide the maintenance, do they go to Epoch 2, or some other approach. This Weight Allocation by MRI also comes into play as it’ll determine whether deprecated weights go to a broader pool or if they stay with a particular MRI. The authors of this paper plan to explore this idea and put forward further suggestions in a future paper.

**Maintenance** - As noted in the paper above, MRIs will likely change over time. This will likely be alongside new MRI maintainers that will review what impact potential changes could have on the currently defined process. To the extent that any roadblocks or issues are raised, the MRC authors will collaborate with the community to determine potential solutions, ideally before any problems ever arrive. 

## Conclusion
Allocating weights by MRI will allow the maintainers to better distribute weights in an efficient manner than provides the most value back for Morpheus. It ensures that weights are distributed by the maintainers that are closest to the efforts and encourages ongoing communication between the community, contributors, and MRI maintainers. 

