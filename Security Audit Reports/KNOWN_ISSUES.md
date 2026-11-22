# Morpheus Bug Bounty: Known Issues

Reports that match an entry below are closed with a reference to its ID and are not eligible for a reward. Entries are not removed. Some entries are already fixed, others are scheduled for a fix according to priority, and others are by design. If an entry has been fixed and your PoC reproduces it against the current deployment, it is a regression and is treated as a new report.

This list is not exhaustive. Some known issues are still under review or under fix and are not listed. A report that matches no entry here is not automatically new.

Findings in the published audits below count as known issues as well, whether or not an entry is listed here:

- Code4rena: Morpheus Capital V2
- Zenith: Morpheus Capital V2
- Renascence: Morpheus Lumerin (compute) Audit Reports 1, 2 and 3
- Renascence: Distribution V2; Distribution V3 (Capital Staking); Distribution V3 (Code Staking); Distribution V4 (Claim Lock); Distribution V5 (Referral Program)
- Renascence: L2TokenReceiverV2 (Initial and Final)
- Renascence: MOR Dynamic Minter (Wormhole)
- Renascence: MOR20 Contracts
- Trust Security: BuildersV2
- OpenZeppelin: MOR Token Contract
- Community: Distribution V1 Audit
- CodeHawks: Distribution V1 Public Bug Bounty

Scope is defined by the bounty rules (Appendix A and section 1.2), not by this file.

Last updated: 2026-11-22

## Capital (Ethereum)

| ID | Contract | Class |
| --- | --- | --- |
| MOR-KI-001 | DepositPool (all pools) | Expired claim lock carried forward on re-lock |
| MOR-KI-002 | DepositPool (all pools) | Self-referral |
| MOR-KI-003 | DepositPool (USDC, USDT, wBTC) | Referrer tier thresholds stored at wrong decimals |
| MOR-KI-004 | DepositPool / Distributor | Stake placed inside the distribution throttle window shares the pending interval |
| MOR-KI-005 | Distributor | Pool yield measured from aToken balance, donation shifts emission share between pools |
| MOR-KI-006 | Distributor | One stale Chainlink feed reverts the price update for all pools |
| MOR-KI-007 | Distributor | External call before state write in yield withdraw |
| MOR-KI-008 | L1SenderV2 | claim() reverting after LayerZero V1 default send version change |
| MOR-KI-022 | DepositPool (all pools) | Raised reward weight kept after the claim lock ends, until the next stake, withdraw or claim |
| MOR-KI-023 | DepositPool (all pools) | Stake or withdraw on a locked position restarts the claim lock |
| MOR-KI-024 | DepositPool (all pools) | claimFor callable by any address when a claim receiver is set |

## Compute (Base, LumerinDiamond)

| ID | Contract | Class |
| --- | --- | --- |
| MOR-KI-009 | SessionRouter | Provider self-dealing session (Lumerin Audit 1 H-7) |
| MOR-KI-010 | SessionRouter | Session close can revert for some provider contracts; session stakes locked |
| MOR-KI-011 | SessionRouter | Direct-payment close charges the user more than the provider receives |
| MOR-KI-012 | SessionRouter | claimForProvider reverts on same-day late close until next UTC day |
| MOR-KI-013 | SessionRouter | Provider approval not bound to the approved user |
| MOR-KI-014 | SessionRouter | Provider receipt stats not range-checked, stats overflow blocks closes |
| MOR-KI-015 | SessionRouter | Direct payouts counted in providersTotalClaimed |
| MOR-KI-017 | ProviderRegistry | Restake does not reset the provider reward limiter |
| MOR-KI-018 | SessionRouter | Same stake cycled through many sessions per UTC day |
| MOR-KI-025 | SessionRouter | Provider signature expiry not enforced |
| MOR-KI-026 | ModelRegistry | Model cannot be deregistered while another provider's bid on it is active |

## Builders (Base)

| ID | Contract | Class |
| --- | --- | --- |
| MOR-KI-019 | BuildersV4 | Subnet withdraw lock raised after deposits |
| MOR-KI-020 | BuildersV4 | Reward counters restarted at the V2 to V4 upgrade |
| MOR-KI-027 | BuildersV4 | Subnet created with another address as admin |
| MOR-KI-028 | BuildersV4 | No fee charged on claim |
| MOR-KI-029 | BuildersV4 | Subnet name registered first by another address |

## Off-chain

| ID | Component | Class |
| --- | --- | --- |
| MOR-KI-021 | api.mor.org gateway | Billing and usage accounting reports, off-chain, out of scope |
