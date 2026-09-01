# Morpheus — the problem sets, and the parameters that constrain any solution

**Status:** DRAFT source of truth for contributors and maintainers. Not a mechanism RFC. No parameter values, no code changes proposed here.

**Evidence:** founding whitepaper (2 September 2023) · `SessionRouter.sol`, `Marketplace.sol`, `ProviderRegistry.sol`, `BidStorage.sol` · capital-protocol contracts · published commitments and live decisions.

**Held:** no characterization of any specific participant’s on-chain activity. Issue public; actors only in trusted venues.


---

**Mission, as stated in the whitepaper (2 September 2023):**

> Morpheus is a decentralized protocol designed to power a new generation of personal AI agents — “Smart Agents” — that can interact with Web3, execute smart contracts, and act on behalf of users. The vision is to make open, user-controlled AI as accessible and transformative as the web browser or search engine was for the early internet.

> As easy to use as Google, as open as Linux, as permissionless as Ethereum.

The compute marketplace is infrastructure serving that. It is not the mission. Tokenomics is downstream.

---

**Problem set Zero** sits above the compute-contract problems. It is **product-market fit**, and demand **outside circular-flow capital**: not treasury-funded sessions, not yield paid in MOR, not usage by addresses that are themselves emission earners. A retained **external** dollar. The structure must be one **both a willing consumer and a willing supplier will participate in** — a buyer who pays, and a provider who offers hardware at a market ask, not donated below-market compute from early contributors. Every problem set below is scored against whether it moves that, or only rearranges the circle.

---

## Problem set Zero — product-market fit, outside circular-flow capital

**The problem:** no product has a retained paying niche whose money did not come from MOR emissions. Token design cannot manufacture that. The agent layer cannot be the excuse for no dollar. The hosted API cannot *become* the mission because it is the only surface taking money today.

**Circular-flow capital** is any “demand” that is the protocol paying itself: treasury-funded sessions, staking yield in MOR, volume from addresses that earn emissions. It can look like usage. It is not product-market fit.

**This phase’s score:** one niche, one external dollar, then tens of thousands a month from paying clients. Floor already in use: on the order of **$10–15 thousand a month** from paying clients; tighter, **three paying clients**, one node with fit then three. Fit is judged on **specific products**. Settled by **external dollars that survive an incentive cut**, not by a call.

The compute-contract problem sets below are how the **marketplace** is made honest enough that those dollars, if they arrive, are not extraction. They do not replace Problem set Zero.

---

## Problem sets as related to the compute contract

**One sentence.** A single undifferentiated flow of MOR lets the treasury stand in for a buyer, so nothing downstream — attestation, delivery measurement, or the inflation cap — can distinguish payment from subsidy or service from extraction. **The payer default must be settled before any mechanism debate can converge.**

Four distinct problems have been argued as one. They have a strict dependency order. Solving them out of order produces mechanisms that are individually defensible and jointly useless.

**The reviewer ask is the ordering**, not watermark formulas, windows, or thresholds.

Fixing attestation, delivery, or the cap while the treasury still funds sessions by default is buying locks for a door held open from the inside.

| Order | Problem | What it decides |
|---|---|---|
| 1 | **Who pays** | Whether extraction pays at all |
| 2 | **Who attests** | Who may speak to what happened |
| 3 | **What was delivered** | Whether anything was said about the work |
| 4 | **What bounds a claim on inflation** | How large that claim may be |

### Who pays — in pursuit (dominant)

A single flow of MOR serves two incompatible purposes — **subsidy** (bootstrap) and **payment** (delivered compute) — with no marker separating them.

Where the **counterparty** funds a session, self-dealing is a wash. Where the **treasury** funds it, self-dealing is a transfer from all holders to one. **The payer determines whether extraction is possible at all.**

The rail already exists: `session.isDirectPaymentFromUser` is a first-class flag at `openSession` and is branched on at payout. **It is off by default.** The question is why it is not the default, and what the residual subsidised lane is for — with a sunset and a graduation criterion.

### Who attests — in pursuit as a constraint; full client is later

The whitepaper puts the **user** in the attester seat. The contract puts the **provider** there: `_isValidProviderReceipt` returns true when the signer is the provider or their delegate, and that satisfies `noDispute_`.

**Payee-controlled evidence may qualify a payment; it may never size one.**

No human signs a per-session receipt. Consumer attestation lives in client software that does not yet exist. That cost is real. The first client slice (later in this document) is the eventual answer. It is not this week’s RFC.

### What was delivered — in pursuit for the cheap half

- **Payment ignores work.** `_getProviderRewards` = `(sessionEnd − openedAt) × bid.pricePerSecond`. Delivery appears nowhere. Throughput and time-to-first-token **are decoded at close and routed only to stats.**
- **The listing makes no claim.** A bid is `{provider, modelId, pricePerSecond, nonce, createdAt}`. No hardware class, no throughput commitment, no warranty. Advertising an A100 and serving a T4 breaches nothing on-chain.

`pricePerSecond` is provider-set, bounded only by an owner-set global min/max. One administrative number is the ceiling on time-based extraction.

**In pursuit now:** gate on already-decoded throughput / latency; add a claim field to the listing (cheap, unenforceable until sampled).  
**Later:** model-fidelity fingerprinting (`MorpheusAIs/HideNSeek` exists and is unused).

### What bounds a claim on inflation — in pursuit (rescope)

A provider may earn at most their own stake per year (`SessionRouter`: claim limit = stake − period earned; period = 365 days). Withdrawal is capped the same way to stop withdraw-and-restake from a new address.

**Two defects, opposite directions:**

1. The cap also applies to **user-funded** sessions, where no holder is diluted. It throttles honest providers on real demand.
2. Removing the cap removes the **rotation guard**. They are one mechanism. Any relaxation must say so and name the replacement.

The `a(1−a)` bound underneath is self-damping, not Sybil-proof. Weak point: a mid-sized holder, not an address swarm.

### Identity on this contract (deadlock, not a vote)

Permissionless participation is mission-bound. “Anything gameable and profitable will be gamed” is economics-bound. **Neither can be voted away.** Engineer: costly to *abuse*, cheap to *enter*. Two lanes — free entry to **serve paying users**; cost to **claim issuance**.

Identity cost is **not** upstream of the payment default. A wash trade extracts nothing unless a third party pays. Identity cost protects the residual subsidised lane and the reputation layer.

### Who will supply — stake-to-list has divorced ask from demand

A market requires **both** a willing consumer **and** a willing supplier. Problem set Zero covers the consumer. This is the supplier half on the compute contract.

**The situation:** listing compute currently requires staking MOR. That requirement has **nerfed** providers who have excess hardware and would sell it at a market ask. They will not lock token inventory in order to plug a GPU into the network. Remaining supply is largely **donated** by early contributors, **not compensated at market prices** for the hardware they run.

**What that divorces:** the **ask** — the price a compute provider would charge for their hardware — from **demand** — what a paying user would buy. Staking-to-supply is not a price. It is a ticket to stand in the room. When the ticket is MOR, the people with spare capacity stay outside, and the people already inside subsidise the network with underpriced compute.

This is not an argument that provider stake must go to zero on the **issuance** lane (that still hits the earnings-cap / rotation-guard / security-budget collision). It is an argument that **stake as a condition of offering hardware into a paying market** fails the both-willing test. Two lanes again: free enough to **sell compute to a paying user** at an ask; costly to **claim emissions**.

### What is asked of reviewers — and what is not

1. Is the ordering right? Does any proposed mechanism survive the payer default staying wrong?
2. User-funded by default — what breaks, who is harmed? What is the residual subsidised lane **for**, and what is its sunset?
3. Does any live proposal to relax the earnings cap acknowledge that it also removes the rotation guard? What replaces the guard?
4. Any objection to gating on already-decoded throughput / latency, other than sequencing?
5. Should a listing carry a hardware or performance claim? Cheap to add; unenforceable until sampled.
6. Does staking MOR as a condition of **supplying** compute fail the both-willing test — i.e. does it keep excess-capacity providers out and leave only donated, below-market supply? If stake remains on the paying lane, what is the replacement path for a provider who will sell hardware at an ask but will not lock token?

**Not asked:** watermark formulas, window lengths, thresholds, new-provider grace. Those follow the ordering.

**Non-goals:** no parameter values; no loss magnitudes; no named participant activity; no governance action requested. Mechanism RFCs follow this.

---

## Parameters: situational and universal constraints

**Universal** constraints bind every solution, every year. A vote cannot repeal them.  
**Situational** constraints are this contract, this phase, this default — they bind *how we engage the problem set now*. They can move when the situation moves; they are not optional while it lasts.

A proposal that satisfies every universal law and ignores the situation (treasury still the default payer) has failed the compute problem set.

### Universal constraints

Sorted by who can relax them.

| Class | Derives from | Who can relax it | “We’ll fix it later”? | Violation means |
|---|---|---|---|---|
| **ECONOMIC** | Arithmetic; self-interested parties; token flows | **Nobody** | **Never** | You fail. The loss occurs whether or not anyone agreed |
| **TECHNICAL** | What the code and stack can currently do | **Engineers**, with time and money | **Yes** — the only class where it is | Nothing is owed; it is not built yet |
| **MISSION** | The whitepaper tagline above | Only by **becoming a different project** | Only if you accept the identity change | It may still work. **It is no longer Morpheus** |
| **PROMISE** | Published commitments and ratified decisions | **The parties owed**, by open renegotiation | Only if renegotiated openly | Quiet lapse is the only unrecoverable move |
| **CUSTODIAL** | Who can change emission, stake, or allowance parameters, and after what delay | **Whoever holds the key**, unless a delay exists | **Never** for “no delay” | The other four become theatre. A key can ignore economic law; it does not repeal it |

**Precedence:** economics binds regardless → custodial delay decides whether anyone can ignore that this week → technical bounds what can ship *now* → mission decides whether the result is still Morpheus → promises decide who is owed an explanation.

**Two expensive misfilings:** economic filed as technical → you fund detectors forever. Technical filed as economic → you concede a fight you would have won (“we can’t measure delivery” while throughput is already decoded and discarded).

**DeFi Education / Iguana feedback** (Iguana is one of the two people behind DeFi Education; the slice that is uniquely his is **revenue quality** — who pays, and whether those payers are themselves subsidised). These are universal economic constraints. They are not a second scoring system.

- **Master question.** Is this token likely to have more net demand or more net sellers? Tokenomics only unlocks value that already exists. Anything that can be sold will be sold.
- **Net structural demand** must be runnable: external buybacks + sticky organic demand − emissions − unlocks − forced selling. Session counts do not substitute.
- **Emissions as a share of external net revenue must trend down.** External = dollars (or hard assets) that did not come from MOR. If the ratio cannot be computed, the design is not underwritable. Fatal-mismatch shape: mechanics do not matter if emissions in dollars dwarf external revenue.
- **If the protocol fails, the token should fail.** That coupling is the goal. Treasury-simulated demand that keeps the token looking alive while nobody pays is the anti-pattern.
- **Yield or fee-share paid in the same token is circular** and fragile. It is not structural demand.
- **Utility must force holders structurally long**, not buy-to-spend-and-sell. Staking for inference *access* is currently that long. Do not remove it until an **externally funded** substitute is live and material versus float. “Easy as Google” is distribution; structural long is a token constraint — do not collapse them.
- **Unlocks are forced selling on a calendar** (payday loans: the protocol borrowed from the future). They enter the net-demand equation on the unlock date. A subsidy sunset can be drowned by an unmodelled unlock.
- **Impossible triangle.** You cannot have good tokenomics, profitable customer acquisition, and sustainable growth at once. Something is always subsidised. Name which two this phase picks (Problem set Zero picks acquisition on one product).
- **Revenue quality (Iguana).** Who pays the fees? Are those payers themselves emission earners? Would dollar revenue survive a 50% cut in incentives? Usage paid by subsidised participants is priority-fee equivalent, not base demand. Pair the user-funded **session** ratio with a user-funded **dollar** ratio that **excludes emission-earning payers**. Capture it **before** the next emissions step-down.
- **Six numbers, none of which exist as a standing series:** (1) annualized emissions in dollars, price assumption written down; (2) annualized external net revenue; (3) emissions ÷ external net revenue; (4) emissions ÷ circulating market cap; (5) unlock calendar, 24 months, by holder class; (6) share of sessions whose payer is not an emission earner, in dollars and in counts.
- **Admin keys without a delay.** Parameter changes with no timelock make the protocol effectively custodial. Unknown delay **reads as fail now**. A key can ignore economic law; it does not repeal it.
- **New units enrich whoever stands at the injection point.** Ask who stands there, and what standing there costs.

**Economic laws (always)** — including the DeFi Education / Iguana lines above, plus the compute-RFC laws:

1. The payer determines whether extraction is possible at all. A compute RFC that does not say which lane it applies to (user-funded vs subsidised) is incomplete.
2. Payee-controlled evidence may qualify a payment; it may never size one.
3. Anything gameable and profitable will be gamed. Profitability is sufficient; motive need not be shown.
4. Every metric ships with its cost-of-faking, and whether the payer is an emission earner.
5. Emission per unit of burn must be strictly less than the burn, or volume-faking mints money.
6. The pro-rata bound `a(1−a)` is self-damping, not Sybil-proof — maximal at 50% ownership.
7. The earnings cap and the rotation guard are one mechanism. Any cap-relaxation RFC must name the replacement guard on the record.
8. A subsidy without budget, date, and graduation criterion is a leak. The graduation ratio must be instrumented **before** any step-down.
9. Unknown delay on an emission or allowance key reads as fail now.
10. You cannot pay out more **realizable** value than enters. Realizable ≠ spot × quantity.
11. Value is revealed only in exchange between distinct interests.
12. Yield or fee-share paid in the same token is circular — not structural demand.
13. A utility that forces holders structurally long may not be removed until an **externally funded** substitute is live and material versus float.
14. Unlocks are forced selling on a calendar.
15. You cannot have good tokenomics, profitable customer acquisition, and sustainable growth at once. Something is always subsidised. Name it.

16. **Both sides must be willing.** A structure only a consumer will use, or only a supplier will donate into, is not a market. The consumer must choose to buy; the supplier must choose to offer hardware at an **ask**. If either side is there only because of emissions, lockups, or obligation, you have circular-flow capital, not a market.

**Design rules (always)**

1. A listing is a warranty; warranties need sampling.
2. **The structure must be one in which both a willing consumer and a willing supplier will participate.** Test: would a buyer with external money use it, and would a provider with excess capacity plug in **at a market price**, without being an early contributor donating hardware? If either answer is no, the design has failed this rule — even if sessions exist.
3. The protocol does not judge quality. It verifies that a counterparty with something at stake did.
4. Watch the failure that looks like success: rejections to zero, provider count growing, ratings high, governance “responsive.”
5. Renegotiate promises in the open; never let one lapse quietly.
6. Disclosed dilution is capital formation; undisclosed or undelivered dilution is expropriation.
7. No emission-parameter change ships without a written maximum extraction rate available to a participant who contributes nothing.
8. No mechanism that *actually* presumes two distinct interests ships before identity costs something on the lane where that presumption matters.

**Mandates (promises that invalidate rather than merely cost):** providers paid only on demand · rewards only after the software is live · stETH stakers earn emissions until openly renegotiated · global mint-and-burn · fair-launch terms (unretrieved, bind at the broadest reading) · indestructible access.

### Situational constraints

These are the live defaults and this phase’s scoring rule. They constrain *this* engagement with the compute contract. They are not eternal laws.

**This phase’s objective (not a class).** Close zero-to-one on one paying product. BowtiedBluefin: one niche, one dollar paid to resolve the problem — preferably a user set where not resolving has a measurable cost that already weights against other costs they pay — then tens of thousands a month. Rank by what it costs to not fix. David: usage and real revenue; fit judged on specific products. Commercial floor already in use: on the order of **$10–15 thousand a month from paying clients**; tighter, **three paying clients**, one node with fit then three. Token design cannot manufacture this. The agent layer cannot be the excuse for no dollar. The hosted API cannot *become* the mission.

**Current posture (revisable):** the network is the objective; the API gateway is a **node** (signup can convert while renewal churn runs 80–95% — node retention, not a protocol verdict). Pay follows results; 30-day paid-pilot gate. Capacity in hours, not per-token. Builders emissions walking down is an **unmeasured** quality experiment. Staking MOR for inference access is still the live utility door — do not demote it before an external-dollar path exists.

**Stake-to-supply (this contract):** requiring MOR stake to list compute has kept providers with **excess capacity** off the network. They will not lock token to sell hardware. What remains is largely **donated** by early contributors, **below market price**. That divorces the provider’s **ask** (price of the hardware) from **demand** (what a paying user would buy). Fails the both-willing rule on the supply side. Distinct from staking-for-**access** (consumer utility). Distinct from stake-to-**claim issuance** (emissions lane).

**Live disagreement:** one principal reads early fit into open-weight models; others read no fit because people do not stay and pay. Settled by **external dollars that survive an incentive cut**.

**Now vs later (this contract)**

**Now** if: written into immutable state · mints entitlements a constituency will defend · defines identity/namespace others index on. Time spent not deciding is not neutral.

| Now | Later |
|---|---|
| User-funded **default** (mints reliance daily) | Fee-share *mechanism*, once **externally** funded |
| Pre-register subsidy graduation + sunset | Router/rating rebuild |
| Earnings-cap **scope** (and the rotation guard it carries) | Identity *mechanism* (registry design) |
| Identity *direction* on the record: free entry to **sell compute to a paying user** at an ask; cost to **claim issuance** — stake-to-list on the paying lane is the live failure | Agent and model registries |
| Delivery gate on already-decoded throughput / time-to-first-token | Model-fidelity fingerprinting |
| Claim field on a listing | Onboarding polish |
| User-funded session ratio **in dollars**, excluding emission-earning payers | |
| Emissions ÷ external net revenue (price assumption written down) | |
| Unlock calendar, 24 months, by holder class | |
| Delay — or explicit none — on emission and allowance keys | Challenge bonds |

**Two hard deadlines:** the user-funded ratio and the dollar/emission ratio must exist **before** the next subsidy step-down. The unlock calendar must exist **before** anyone calls a sunset a success.

**Live misfilings on this contract**

| Claim | Argued as | Actually |
|---|---|---|
| “We can’t verify compute was delivered” | Technical | **Split.** Empty-session detection is nearly free. Model fidelity is hard |
| “Consumer attestation needs no new attesters” | Technical, cheap | Technical, **expensive** — the attester is client software that does not exist |
| “Zero minimum provider stake reduces friction” | Mission | Mission vs economic; also deletes the rotation guard |
| “The builders reduction cuts emissions ~50%” | Promise | **Technical** — mint-and-burn is unshipped |
| “A large lock multiplier rewards long-term alignment” | Economic (incentive) | **Economic, inverted** |

**Compute-relevant collisions (this situation)**

| Trade-off | Settle by |
|---|---|
| Costly identity vs permissionless entry | Design, not a vote. Two lanes. Identity tax is not required on the paying lane |
| Staking as access vs easy as Google | Split the instrument. Do not remove access-as-**long** until an external-dollar fee is live |
| Subsidy-to-fee transition vs no dial | Build the dial or renegotiate the promise openly |
| Annual return cap vs paying demand | Rescope the cap off the paying lane. Name the replacement rotation guard **before** the cap moves |
| **Stake-to-supply vs both-willing market** | Requiring MOR stake to list compute is Sybil defence / security budget. | Providers with excess capacity will not lock token to sell hardware at an ask. Remaining supply is donated by early contributors below market price. Ask and demand are divorced. | Stake-to-list is not a price. It is a ticket. The people with spare GPUs stay outside. Zero stake on the **issuance** lane still hits the cap/rotation-guard collision. | Two lanes: offer hardware into a **paying** market at an ask without buying the ticket in MOR; stake (or equivalent cost) to **claim emissions**. Measure: would a non-contributor with idle capacity plug in at a posted ask? |

**Design and sequencing trade-offs**

These bind *order of work*, not a vote on physics. A proposal that does not say which side it takes, and what it pays, is incomplete.

| Trade-off | Side A | Side B | What is already true | What settles it |
|---|---|---|---|---|
| **Slow and terminating vs fast and recurring** | Building the agent layer (the buyer) is quarters of work. | Patching marketplace contracts ships in weeks. | Patching a simulated demand side does not converge. Months of unexecuted emissions reductions is the evidence. | Choose terminating work. Marketplace patches that assume a treasury-funded session are the recurring kind. |
| **Bootstrap subsidy vs leak** | Agents need providers; providers need agents to be paid. Some subsidy is unavoidable while the buyer is being built. | A subsidy with no budget, date, or graduation line is a leak. | This is the one place a subsidy is justified — only if the sunset is written first. | A tranche: budget, date, graduation = share of sessions a user actually paid for, in **dollars**, excluding emission earners. Instrument **before** any step-down. |
| **Agent-signed receipts vs provider-signed receipts** | The whitepaper put the user in the attester seat. An agent can sign, because it is software. | Client software can lie. A malicious agent can collude with a provider. | Provider self-attestation has no victim inside the transaction. Agent misattestation burns the principal’s money. Better, not perfect. | Ship the budgeted client. Do not wait for perfect attestation. Payee evidence may qualify a payment, never size one. |
| **Sovereignty vs easy as Google** | User-owned keys, self-custodied budgets, revocable delegated authority. | First value without a token purchase, a stake, a bridge, or a seed-phrase ceremony. | These *are* the friction the mission also forbids. No owner. | Named owner. Known directions: account abstraction, session keys, custodial-by-default with an exit. None is free. |
| **Permissionless listing vs verifiable quality** | Free entry to serve. | Unverifiable quality is a lemons market, including on the paying lane. | Throughput and time-to-first-token are decoded and discarded. HideNSeek exists and is unused. | A listing is a warranty. Warranties need sampling. |
| **More providers vs the binding constraint** | Permissionless entry and cold-start capacity. | If existing providers are idle, additional providers have zero marginal value. | Provider count is the number that moves when demand does not. Utilization is **unmeasured**. | Measure utilization. If the existing set is idle, “more providers” is not a goal. |
| **Where the next subsidy dollar goes** | Demand side — supply is already long. | Neither: let prices clear. Or a staged tranche with a kill switch. | Until identity costs something on the subsidised lane, a demand-side subsidy is farmable. Changing the **payer** zeroes the wash-trade payoff. | User-funded-by-default first. Do not rotate the subsidy onto a new farmable surface. |
| **Should the protocol assess quality?** | Never — verify a staked exchange only. | Without warranty and sampling, the paying lane collapses on its own. | Ratings are already “price price price.” | If churn on the honest paying lane stays extreme, sampling of listing claims is the reconciliation, not a quality court. |
| **Zero minimum provider stake** | Lowers entry friction. | Stake is the compute-side security budget **and** the earnings-cap denominator. Stake of zero is security budget zero, and as coded the claim limit is also zero — including on paying sessions. | Elasticity of honest, demand-serving providers versus the current minimum is unmeasured. | If almost none of those providers are deterred by the current minimum, the friction cost is imaginary and the security cost is not. |
| **Remove friction now vs reversible work first** | Shipping zero-stake / minimal provider friction is the fast path to scale. | That move mints entitlements a constituency will defend. | Time spent not deciding is not neutral. Once live and farmed, walking it back is an expropriation fight. | Reversible items now. Irreversible entry-rule changes last, and only after the paying lane exists. |
| **Better detection vs change the payer** | Watermarks and gates will stop extraction. | No detector survives a profitable target. Treasury-in-the-path **is** the payoff. | Filing this as technical funds detectors forever. | Change who pays. Detection may raise the cost of faking on the residual subsidised lane; it does not size payment. |
| **Open record vs protocol moat** | Keep settlement and grading open. | The durable asset is the exchange, the grading standard, and the settlement layer — not the GPUs. | Everything except that record is commodity. | Keep the record open and still own the network effect. |
| **Agent layer vs work people already own** | The mission layer is the product and the fix. | Promoting it demotes marketplace work people have owned for years. | Saying this only after the reordering is how trust breaks. | Say it out loud. Assign an owner to the first client slice. |
| **Pro-rata inflation vs lock multipliers** | Compute-side earnings bounded per provider. | A large claim-lock multiplier on the capital side can let one staker reduce another’s share of a fixed pool. | If that inverse is real, compute and capital implement opposite principles. Unverified against live params. | Confirm on-chain. If confirmed, it is an economic inversion, not an alignment feature. |
| **Honest marketplace vs net token flows** | Fix who pays, who attests, what identity costs. | The token can still have more sellers than buyers. | Session-count “demand” is not the net-demand equation. | Instrument the six numbers (DeFi Education / Iguana list). Do not ship a cleaner marketplace as if that were product-market fit. |
| **Zero-to-one on one product vs the full agent mission** | Problem set Zero: one niche, one external dollar. | Wait for the agent runtime, registries, Google-easy onboarding. | Tokenomics cannot manufacture the dollar. The agent layer cannot be the excuse for no dollar. The gateway cannot be the mission. | Sequence: measure the first **external** dollar **and** build the client slice. Do not substitute either for the other. |
| **No delay on admin keys vs “decentralized contracts”** | Parameter toggles ship faster. | No delay on emission or allowance changes = effectively custodial. | Emission rates are adjustable, not a hard-coded schedule. | State the delay, or state that there is none. That is Now. |

---

## The rest

### Promise integrity

- **Builders / Code bucket.** About a quarter of emissions was allocated on the promise that staking there converts into daily inference credits and **directs actual compute**. Stakes yield tokens. No additional compute. The public gateway was built as if that conversion existed. It was never built.
- **Staking for access versus no sacred cows.** A 13 April 2026 decision treats staking MOR for inference access as non-negotiable, with no reversal conditions, never finished as a live decision. A later live decision says there are no sacred cows except solve the client’s problem and keep access indestructible. Those cannot both be true. The second is eating the first without open ratification.
- Fair-launch terms unretrieved. Whitepaper banner-marked ARCHIVED; replacement unfinished.
- April 2026 emissions reduction: arithmetically sound, **never executed**. Mint-and-burn unshipped.

### Unbuilt mission layer (later answer to who attests)

Six missing pieces: agent runtime · delegated-authority rail · personal memory store · agent registry · model registry · onboarding without token/stake/bridge first.

**First slice (not this week’s compute RFC):** a budgeted client that opens a session, pays from the user’s money, measures throughput/latency, and signs the close. Test: one such session with the treasury not in the path.

### Token flows

The marketplace can be honest and the token can still have more sellers than buyers.

Net structural demand = external buybacks + sticky organic demand − emissions − unlocks − forced selling.

Session counts do not substitute for the situational numbers in the Now table.

### Parked (not evaluated)

- A stake vault paying holders pro-rata inflation via builders.
- Move the marketplace toll from per-listing to per-session and burn it (`bidFee` today is per-listing and withdrawn, not burned).

### Still unverified

- Deployed bytecode vs source.
- Whether the capital-side lock multiplier lets one staker reduce another’s share of a fixed pool.
- Canonical bucket allocation table — not on file.
- Community bucket — undefined at every level.

---

## How a contributor is supposed to engage

1. The tagline is the mission. Do not substitute the gateway for it.
2. **Problem set Zero first.** Does this move a retained dollar **outside circular-flow capital**? If it only rearranges treasury-funded volume or MOR-paid yield, it has not scored.
3. Run the proposal against the **compute-contract problem set in order**. If it patches attestation, delivery, or the cap while the treasury still pays by default, it is locks on an open door.
4. Check **universal** constraints, including the DeFi Education / Iguana block. If it fails an economic law or has no delay on a key that can ignore one, stop.
5. Check **situational** constraints and the **design/sequencing** table. Name which side you take.
6. If it revises something someone was told, name who, what replaces it, and tell them before they find it in a diff.
7. Mechanism values (windows, watermarks, stakes) come **after** agreement on that ordering.
