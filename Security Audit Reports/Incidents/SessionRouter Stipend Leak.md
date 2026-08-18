# SessionRouter stipend leak — intra-day stake recycle

**Status:** Patched on BASE mainnet (2026-07-31). This file is the Protection Fund incident record for a bounty. It is not a request for a new fix.

**Payout:** first installment **$3,000 USDC sent** 2026-08-18 (Arbitrum). Remaining **$12,000** over four monthly payments. Protection Fund reimbursed the paying address (three txs below).

## Summary

`SessionRouter._rewardUserAfterClose` treated a **late close** (`closedAt >= endsAt`) as a full immediate refund of the consumer stake. A session that expired and was then closed returned the used stipend in the same transaction. The same MOR could open another session in the same UTC day and draw stipend again.

That is the stipend leak / intra-day recycle. It is a compute-contract bug. It is in scope for the Protection Fund (bug disclosed against a live Morpheus compute contract) and for Bug Bounty Program v2 (deployed bytecode, measurable over-issuance of rewards).

## Target

| Field | Value |
|---|---|
| Contract | SessionRouter facet, reached through the Inference Diamond |
| Chain | Base mainnet |
| Diamond | `0x6aBE1d282f72B474E54527D93b979A4f64d3030a` |
| Owner (cut) | Gnosis Safe 5-of-9 `0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` |
| Invariant that broke | Used consumer stake cannot be recycled inside the same UTC day to draw another stipend against the same MOR |
| Preconditions | Anyone who can open a funded session. No admin key. Gas is the only friction. |

## Attack (as the shipped docs now name it)

1. Open a funded session.
2. Let it expire (`endsAt` pass).
3. Call `closeSession` after `endsAt` (the consumer node does this ~1 minute later).
4. Pre-fix: full stake returned in that tx. Open another session the same day. Repeat.

Post-fix: unused stake still returns on close. **Used stipend day-locks** until the next UTC day (`userStakesOnHold`, claim via `withdrawUserStakes`). Anchor is `min(closedAt, endsAt)`, not the close-tx timestamp.

## Fix that already shipped

Behavior change in `_rewardUserAfterClose` ([#833](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/833), from [@rcondron](https://github.com/rcondron) [#830](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/830)):

```solidity
uint128 sessionEnd_ = uint128(session.closedAt.min(session.endsAt));
uint128 startOfEndDay_ = startOfTheDay(sessionEnd_);
uint128 releaseAt_ = startOfEndDay_ + 1 days;

if (block.timestamp < releaseAt_) {
    // lock used stipend in userStakesOnHold
}
```

| Step | PR | Merged |
|---|---|---|
| Original patch | [#830](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/830) [@rcondron](https://github.com/rcondron) (superseded — wrong base) | closed 2026-07-30 |
| Contract + tests + runbook + nodedocs | [#833](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/833) `0x18f6…6b9C` → `dev` | 2026-07-29 |
| Promote | [#834](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/834) `0x18f6…6b9C` `dev`→`test` | 2026-07-29 |
| Promote | [#835](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/835) `0x18f6…6b9C` `test`→`main` | 2026-07-29 |
| Deploy note | [@nomadicrogue](https://github.com/nomadicrogue) on #830: contract update instructions sent for testnet and mainnet | 2026-07-30 |
| Mainnet `diamondCut` | runbook two-step: EOA deploys facet, Safe signs one cut | 2026-07-31 |

Docs already state the new rule: *“You can reuse the same MOR many times in one day by letting sessions expire”* is false after the day-lock.

## Impact

While the hole was open, network-wide extraction was bounded by the compute treasury’s **~1% daily draw**, about **25,000 MOR/day**, declining as the treasury shrank. The recycle was unbounded *per stake*; the daily draw was the ceiling on damage.

This is **over-issuance of compute stipend** from the protocol funding account, not a lock of user deposits and not a capital-pool drain. Bug Bounty v2 maps “measurable over-issuance of rewards” to **High ($10,000–$50,000)**. The assessed award is inside that band.

## Submitter

`0x18f61d9C2b3303d2C6cEafBEF81302c1016C6b9C` (`0x18f6…6b9C`)

First valid report on this unique issue. Under Bug Bounty Program v2, the first address to submit a valid report is the only one eligible. Patch authors listed above are not additional bounty claimants.

## Protection Fund payment requested

| Field | Value |
|---|---|
| Type | Pre-defined Protection Fund payment #1 — bug discovered and disclosed |
| Program | [Bug Bounty Program v2](../Bug%20Bounty%20Program.md) (effective 2026-08-07); [Protection Fund Details](../../!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md) |
| Submitter / payee | `0x18f61d9C2b3303d2C6cEafBEF81302c1016C6b9C` |
| Amount | **$15,000 USD** |
| Asset | **USDC** |
| Schedule | **5 monthly payments of $3,000 USDC** |
| Paid by (on behalf of the Protection Fund) | `0x65485DEECeAF608C8304978CA0FCA1C49f5308aE` |
| Paid to | `0x18f61d9C2b3303d2C6cEafBEF81302c1016C6b9C` |

Code Providers: signal TRUE/FALSE on this record within 7 days of merge. If a majority of participating weight validates TRUE, authorize the remaining schedule. Each monthly transfer is recorded below by tx hash.

## Payout log

Chain: **Arbitrum One**. Native USDC `0xaf88d065e77c8cC2239327C5EDb3A432268e5831`.

### Protection Fund reimbursement (to the paying address)

These three transfers reimbursed `0x65485DEECeAF608C8304978CA0FCA1C49f5308aE` for paying the submitter.

| When (UTC) | Amount | From | To | Tx |
|---|---:|---|---|---|
| 2026-08-18 18:33 | 2,000 MOR | mint / claim (`execute302`) | `0x6548…308aE` | [`0x8289acf2…054720`](https://arbiscan.io/tx/0x8289acf2e7c05c4a7c760c23581b0b7e88b3a348ff821980b2c6486586054720) |
| 2026-08-18 19:11 | 1 MOR | `0xb19B3b7B23fA14F6A5fCFD1B9A03a4105E242169` | `0x6548…308aE` | [`0x22dea25d…4bb1cf`](https://arbiscan.io/tx/0x22dea25d55b1183e791d24b4c4ac477a316370d0a37da162b62c5d8e2d4bb1cf) |
| 2026-08-18 19:15 | 1,999 MOR | `0xb19B3b7B23fA14F6A5fCFD1B9A03a4105E242169` | `0x6548…308aE` | [`0xd5e461ce…c5cf05`](https://arbiscan.io/tx/0xd5e461ceb3257cf49da7d049e2465c9e123e4d667ea5cd30f931c98340c5cf05) |

### Installment 1 of 5 — $3,000 USDC to submitter (sent)

| When (UTC) | Amount | From | To | Tx |
|---|---:|---|---|---|
| 2026-08-18 18:57 | 10 USDC | `0x6548…308aE` | `0x18f6…6b9C` | [`0x69bd1f65…103580`](https://arbiscan.io/tx/0x69bd1f65fc9dd119abb7374e6ad101dfb95da3a9ad90191790205d1970103580) |
| 2026-08-18 19:27 | 2,990 USDC | `0x6548…308aE` | `0x18f6…6b9C` | [`0x0000e9b0…217087`](https://arbiscan.io/tx/0x0000e9b0072808144d920afc420baed0924dcac11fb52afc25736c1515217087) |
| **Total** | **3,000 USDC** | | | |

Remaining: **4 × $3,000 USDC**.

## Addendum — Arbiscan URLs (for approval)

Arbitrum One. Submitted for `@DavidAJohnston` to approve as the on-chain record of installment 1 and the Protection Fund reimbursement.

**Protection Fund reimbursement (MOR → paying address `0x6548…308aE`):**

1. https://arbiscan.io/tx/0x8289acf2e7c05c4a7c760c23581b0b7e88b3a348ff821980b2c6486586054720
2. https://arbiscan.io/tx/0x22dea25d55b1183e791d24b4c4ac477a316370d0a37da162b62c5d8e2d4bb1cf
3. https://arbiscan.io/tx/0xd5e461ceb3257cf49da7d049e2465c9e123e4d667ea5cd30f931c98340c5cf05

**Installment 1 — $3,000 USDC to submitter `0x18f6…6b9C`:**

4. https://arbiscan.io/tx/0x69bd1f65fc9dd119abb7374e6ad101dfb95da3a9ad90191790205d1970103580
5. https://arbiscan.io/tx/0x0000e9b0072808144d920afc420baed0924dcac11fb52afc25736c1515217087

## What this record is not

- Not [SmartContracts #63](https://github.com/MorpheusAIs/SmartContracts/issues/63) / [#64](https://github.com/MorpheusAIs/SmartContracts/issues/64) ([@Apollyon13X](https://github.com/Apollyon13X)).
- Not a user-error reimbursement.
- Not a request to revert or re-cut SessionRouter.

## Sources

- https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/830
- https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/833
- https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/834
- https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/pull/835
- https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/smart-contracts/docs/session-day-lock-upgrade-runbook.md
- [Protection Fund Details](../../!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
- [Bug Bounty Program](../Bug%20Bounty%20Program.md)
