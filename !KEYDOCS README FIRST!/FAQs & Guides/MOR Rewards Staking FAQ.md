# MOR Rewards Staking (MRS) Reference

---

## Overview & Purpose
MOR Rewards Staking (MRS) is a mechanism that allows Morpheus contributors to stake their future MOR reward claims for a defined period. In return, contributors receive a "Power Factor" multiplier that amplifies their MOR rewards. MRS is designed to:
- Incentivize long-term commitment
- Distinguish real contributors from short-term opportunists
- Close the negative feedback loop in the capital providers bucket

---

## Eligibility & Participation
- All four types of Morpheus contributors (Code, Capital, Compute, Community/Builders) are eligible for MRS.
- Capital and Code staking are live first; Compute and Builder staking will follow.
- Only future MOR reward claims can be staked (not MOR already in your wallet).
- Staking is optional, but only staked rewards receive the Power Factor multiplier.

---

## Power Factor & Staking Mechanics
- The Power Factor is a multiplier applied to staked MOR rewards, increasing with longer staking periods.
- The Power Factor mirrors the dilution rate due to daily emissions contributors experience while staking.
- The maximum Power Factor is 10.7x for a 6-year stake.
- The Power Factor equation is defined in [MRC42](https://github.com/antonbosss/MRC/blob/main/IN%20PROGRESS/MRC42.md#the-time-power-factor-shortened-power).

| Staking Period      | Power Factor Multiplier |
|---------------------|------------------------|
| 6 months            | 1x                     |
| 6 years             | 10.7x                  |
| (interpolated)      | (grows with time)      |

- The Power Factor starts at 1x after six months and increases up to 10.7x at six years. There is no upper limit, but the reasonable range is 6 months to 6 years.

---

## Staking Periods & Multipliers
- Staking periods can only be increased, not decreased.
- Rewards cannot be withdrawn until the end of the staking period.
- The staking period is set at the time of staking and is locked in.

---

## Claiming & Withdrawal Rules
- Only future MOR reward claims are eligible for staking.
- Staked rewards cannot be withdrawn early.
- For capital contributors, stETH can be withdrawn at any time (subject to the normal 7-day lock), but MOR rewards will stop accruing if stETH is withdrawn.

---

## Technical Details & Contract Behavior
- Not every transaction triggers Power Factor recalculation—only those interacting with the Distribution contract (e.g., depositing/withdrawing stETH, increasing/decreasing code weights).
- Buying or selling MOR from the wallet where rewards are staked does not affect the Power Factor unless it interacts with the Distribution contract.
- MRS does not impact daily MOR emissions, but staking reduces the amount of MOR entering circulation.

---

## Impact on Emissions & Circulation
- Staking does not change the total daily MOR emissions.
- Staked rewards are locked, reducing the circulating supply of MOR during the staking period.

---

## References & Support
- Full proposal: [MRC42](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC42.md)
- [Morpheus Dashboard – Staking Interface](#) *(placeholder for dashboard link)*
- For questions, use the [#capital-providers](https://discord.com/channels/1151741790408429580/1167520881908666569) or [#code-providers](https://discord.com/channels/1151741790408429580/1167520984849469530) channels on Discord.

---

## [Placeholder: Add contract addresses and dashboard links as available]

