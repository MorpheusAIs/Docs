# Morpheus Bug Bounty Program ($100,000)

**Version 2 — effective 2026-08-07. Supersedes all prior versions.**

Calling all independent security researchers.

## Synopsis

The Morpheus community cares about strong property rights. The Morpheus smart contracts have undergone a multi-tiered audit and mitigation process, but they operate in a dynamic environment that may still contain undiscovered vulnerabilities.

This program pays for **one thing**: a reproducible exploit against deployed Morpheus smart contract bytecode that causes a measurable loss of funds. Nothing else. Read the Scope and Submission Requirements sections in full before submitting — reports that do not meet them are closed without review and without response.

---

## 1. Scope

### 1.1 In scope

**Only the contract addresses listed in Appendix A are in scope.** Scope is defined by deployed address and chain, not by repository. If an address is not in Appendix A, it is out of scope, regardless of whether it is part of Morpheus, referenced in our documentation, or deployed by the Morpheus multisig.

Where a listed address is a proxy or an EIP-2535 diamond, scope includes the implementation or facet code it currently delegates to, reached **through the listed address**. Report against the proxy; an implementation or facet address that is not reachable through a listed proxy is out of scope.

Your report must target the **deployed bytecode** at the listed address. Findings that exist only in a GitHub repository, in an unreleased branch, or in a version that is not currently deployed are **not eligible**, even if the code is labelled "Morpheus".

### 1.2 Out of scope — non-exhaustive, and read it anyway

The following are **categorically ineligible**. Submitting them does not start a discussion; the report is closed.

**Not smart contracts:**

- The Morpheus web interface, dashboard, any website, DNS, email, or hosting infrastructure
- APIs, RPC endpoints, subgraphs, indexers, relayers, or any off-chain service
- MORagents, local agent software, and any client-side application
- Documentation, marketing material, social media accounts, Discord, or community infrastructure
- Testnets (Sepolia, Arbitrum Sepolia, Base Sepolia) and staging deployments, unless the identical bug is demonstrated against a mainnet address in Appendix A
- Third-party contracts built on top of Morpheus (agents, wallets, integrations) that are not in Appendix A

**Not a vulnerability:**

- Anything requiring an admin key, owner role, multisig signature, or privileged role. Centralization risk, admin key compromise, "the owner could rug", governance capture, and timelock design are **out of scope in all forms**. If your attack starts with "assume the owner is malicious", stop. **Narrow exception:** a bug that lets an *unprivileged* address acquire a privileged role, bypass an access-control check, or hijack a proxy is in scope and is Critical — because it does not assume a malicious owner, it creates one. This requires a PoC in which the attacker starts with no special permissions.
- Gas optimization, code style, naming, missing events, missing NatSpec, missing zero-address checks, floating pragma, unused variables, or any finding whose impact is readability or gas
- Raw output from static analyzers (Slither, Mythril, Aderyn, Semgrep, etc.) or from any automated tool, submitted without an exploit
- Theoretical, speculative, or "could become exploitable if X changes" issues
- Best-practice deviations, missing input validation, and design opinions with no demonstrated loss
- Known issues: anything already known to us at the time of your submission. This covers findings from any prior audit or security review of Morpheus, anything publicly disclosed anywhere, and anything an earlier researcher has already reported (first valid report wins). If we close your report as known, we will say which of these it falls under. The audits [here](https://github.com/MorpheusAIs/Docs/tree/main/Security%20Audit%20Reports) are a starting point for your own de-duplication, not the complete list.
- Attacks requiring a compromised user (phishing, malware, leaked private keys, malicious token approvals granted by the user)
- Attacks requiring control of block production, validator collusion, chain reorganization, or a >51% attack
- Front-running and MEV, unless the PoC demonstrates a loss to the protocol or to third-party users that is not merely ordering priority
- Griefing and denial-of-service that does not result in permanent loss or permanent lock of funds.
- Bugs in third-party protocols we integrate with (Aave, Uniswap, LayerZero, Chainlink, etc.), unless the flaw is in **Morpheus's own use** of that integration and the PoC demonstrates it against a Morpheus address
- Rounding, precision loss, and dust. **Exception:** if your PoC demonstrates that the rounding error compounds through a shared invariant (share rate, yield accounting, price-per-token) into a material drain, it is in scope and will be treated as High or Critical. The exception requires the PoC, not the argument.
- A condition that clears on its own, because an oracle round lands, a lock expires, a period rolls over or a permissionless call can be repeated,
is not a freeze, whatever the value sitting behind it. If your finding is that a transaction reverts and succeeds on retry, it is out of scope and
the size of the balance it touches does not change that.

**Not a submission:**

- Reports without a working proof of concept (see Section 2)
- Reports generated by an AI system and submitted without human verification (see Section 5)

---

## 2. Submission requirements — mandatory

A submission that does not contain **every item below** is closed on sight. This is not a formality; it is the filter.

### 2.1 Required: a working proof of concept

Your PoC must:

1. Be a **Foundry test** (`forge test`). Hardhat is accepted; nothing else is.
2. Run against a **mainnet fork pinned to a specific block** (`vm.createSelectFork(RPC, BLOCK)`), targeting the deployed address from Appendix A.
3. Run to a passing result with **one command**, from a clean clone, with no manual setup beyond an RPC URL.
4. **Assert the loss**: the test must contain an assertion on the attacker's balance before and after, or on the protocol invariant that breaks. A test that merely reverts, or that prints a suspicious value, is not a PoC.
5. Use **no privileged accounts**. No `vm.prank` as owner, admin, or multisig. The attacker must be an address that anyone can control.
6. Be delivered as a **public GitHub repository or gist**, linked in the report, not as an attachment, screenshot, or code block in an email.
7. If your PoC advances time on a fork (`vm.warp`), it must not rely on state that would have moved on live chain. Oracles, rebasing balances and streaming accruals are frozen in a fork, so warping past a heartbeat makes every feed stale by construction and proves nothing about how often that happens in production. Where frequency is part of your claim, measure it against chain history and show the measurement.

We run your test. If it does not pass on our machine, the report is closed.

### 2.2 Required: the report itself — maximum one page

Use exactly these headings:

```
TARGET:      <contract name> @ <address> on <chain>, block <N>
INVARIANT:   <the one protocol property that breaks, in one sentence>
IMPACT:      <amount at risk, in tokens AND USD at time of writing, with the
              arithmetic that produces the number>
PRECONDITIONS: <what must be true on-chain for the attack to work; state
              honestly if it requires capital, timing, or a specific state>
ATTACK:      <numbered steps, maximum 10 lines>
POC:         <link to public repo/gist>
FIX:         <one sentence or a diff>
```

Reports longer than one page, or that do not follow this structure, are closed unread. Length is not evidence of rigor.

### 2.3 The impact number

Every submission must state a specific, defensible amount at risk. "Potentially significant", "could lead to loss of funds", and "an attacker may be able to" are not impact statements. If you cannot compute the number, you have not finished the research.

If the amount at risk is bounded by a parameter (a cap, a balance, an allowance), state the current on-chain value of that parameter and the block at which you read it.

For any finding whose impact is that funds are unavailable rather than lost, the impact number is a **duration**, not a balance. State how long the condition lasts, how you measured it and what ends it. An amount of TVL sitting behind a temporary revert is not an amount at risk and a report that
leads with one will be assessed on the duration it failed to state. 

---

## 3. Severity and rewards

Rewards are paid from the Protection Fund, in proportion to demonstrated impact, at the Morpheus community's sole discretion. **Every tier requires a passing PoC and a quantified impact number.** Severity is assigned by us, based on the demonstrated effect — not by the reporter.

| Severity | Definition — all require a working PoC | Reward |
|---|---|---|
| **Critical** | Direct theft of user funds or treasury assets; unauthorized minting of MOR; permanent freeze of funds at protocol scale; drain that scales with TVL or with treasury balance | **Up to $100,000**, capped at 10% of demonstrated funds at risk |
| **High** | Theft or permanent lock of a bounded but material amount of funds; measurable over-issuance of rewards; loss requiring realistic preconditions the attacker can create | **Up to $50,000** |
| **Medium** | Freeze of funds that persists until a privileged action or an external repair, which your PoC must show lasting at least 24 hours without one; quantified loss to a subset of users; griefing with a demonstrated, measurable cost borne by others | **Up to $10,000** |
| **Low** | Quantified loss below $10,000 total, with a working PoC | **Up to $2,500** |

**The amounts above are indicative, not a price list.** They describe the range we expect a tier to land in. The actual reward is set case by case on the demonstrated impact, the quality of the report and PoC, and the state of the Protection Fund — it may fall below or, for an exceptional finding, above the stated range.

**Notes:**

- A finding whose maximum extractable value is bounded and small is Low, no matter how elegant the exploit or how easy it is to execute. Scale determines reward, not cleverness.
- Where impact depends on a changeable on-chain value (an allowance, a balance, a TVL), the reward is assessed against the value at the time of the report, and we may re-assess if that value is materially different at the time of the fix.
- The first researcher to submit a valid report on a unique issue is the only one eligible. Duplicates receive no reward.
- **Rewards are subject to available Protection Fund liquidity.** Amounts are denominated in USD and paid in MOR or another asset held by the Fund, valued at the time of payout. Where the Fund's liquid balance is below the assessed reward, we will pay what is available and agree a schedule for the remainder; the tiers above are ceilings, not a guaranteed cash reserve.

---

## 4. Disclosure process

Submit to **devs@mor.org** with the subject line:

```
[BOUNTY] <Contract name> — <one-line impact>
```

**What happens next:**

1. **Format check (automatic, within 3 business days).** Missing PoC link, missing impact number, out-of-scope target, or a report that ignores the Section 2.2 template → closed with a single-line reason. No appeal, no discussion.
2. **Reproduction.** We run your PoC. If it passes, we confirm receipt and begin assessment.
3. **Assessment and reward decision** within 14 business days of a passing PoC.

We respond in substance only to submissions that pass step 1. We will not explain why an out-of-scope or PoC-less report was rejected beyond the one-line reason, and we will not review revised versions of a report that was closed for scope.

---

## 5. AI-assisted submissions

You may use any tooling you like, including LLMs and AI agents, to **find** vulnerabilities. We do not care how you found it.

You may not use them to **write and send** a report you have not verified yourself. Concretely:

- Every submission must include a PoC you personally ran to a passing result.
- Submitting findings you have not reproduced yourself falls outside the good-faith terms of this program. Such reports are closed without review and are not eligible for a reward.
- Sending unverified, machine-generated reports in volume is not security research, and we may decline to review further submissions from that source.

The PoC requirement in Section 2 exists precisely so that this rule enforces itself. If your finding is real, producing the test is a small additional step. If producing the test is impossible, you do not have a finding.

---

## 6. Terms and conditions

To be eligible for reward consideration, you must:

- Identify an original, previously unreported, non-public vulnerability within the scope defined in Section 1
- Meet every submission requirement in Section 2
- Report promptly upon discovery

To distinguish good-faith research from malicious activity, you must:

- Act in good faith under the terms of this program and any other relevant agreement. Where there is any inconsistency between this program and another agreement, a good-faith determination will be made.
- Avoid violating the privacy of others, disrupting our systems, destroying data, or harming user experience
- Use only devs@mor.org to discuss vulnerabilities with us
- Keep the details of any discovered vulnerability confidential until it is fixed and we have confirmed you may disclose
- Test only against forks and testnets. Do not execute an exploit against mainnet contracts.
- Interact only with accounts you own or have explicit permission to use
- Not engage in blackmail, extortion, or any other unlawful conduct

When you work with us under this program, you can expect us to:

- Pay rewards for eligible discoveries based on demonstrated severity and impact, at the Morpheus community's sole discretion
- Extend **Safe Harbor** for research related to this program: we will not threaten or bring legal action against anyone making a good-faith effort to comply with it
- Work with you to understand and validate a report that meets the submission requirements, with a timely initial response
- Remediate confirmed vulnerabilities in a timely manner
- Publicly recognize your contribution if you are the first to report a unique issue and your report triggers a code or configuration change

---

## TL;DR

- Up to **$100,000** from the Protection Fund, capped at 10% of demonstrated funds at risk and subject to available Fund liquidity
- **Smart contracts only.** Only the addresses in Appendix A. Frontend, APIs, agents, testnets, and infrastructure are out of scope.
- **No PoC, no submission.** Foundry test, mainnet fork, pinned block, passing assertion on the loss, public link.
- **No admin-key, centralization, gas, style, or theoretical findings.** Ever.
- One page, fixed template, quantified impact in tokens and USD
- Send to devs@mor.org. Non-conforming reports are closed without review.
- Do not disclose publicly before the fix is live

---

## Appendix A — In-scope contract addresses

**Last updated: 2026-08-07.** All addresses below were read from chain on that date. Report against the address in the "Address" column; where that address is a proxy or a diamond, its current implementation or facet code is in scope through it.

### Ethereum Mainnet — Capital

| Contract | Address | Type |
|---|---|---|
| MOR token | `0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0` | token |
| DepositPool (stETH) | `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790` | ERC1967 proxy |
| DepositPool (wETH) | `0x9380d72aBbD6e0Cc45095A2Ef8c2CA87d77Cb384` | ERC1967 proxy |
| DepositPool (wBTC) | `0xdE283F8309Fd1AA46c95d299f6B8310716277A42` | ERC1967 proxy |
| DepositPool (USDC) | `0x6cCE082851Add4c535352f596662521B4De4750E` | ERC1967 proxy |
| DepositPool (USDT) | `0x3B51989212BEdaB926794D6bf8e9E991218cf116` | ERC1967 proxy |
| Distributor | `0xDf1AC1AC255d91F5f4B1E3B4Aef57c5350F64C7A` | ERC1967 proxy |
| RewardPool | `0xb7994dE339AEe515C9b2792831CD83f3C9D8df87` | ERC1967 proxy |
| ChainLinkDataConsumer | `0xd182263D06Fdc463c96190005d6359Cc3d3BbC5E` | ERC1967 proxy |
| L1SenderV2 | `0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84` | ERC1967 proxy |

All five DepositPool proxies currently share implementation `0xdB10dAEF167eA2233Ba6811457dD24D676FbD670`.

### Arbitrum One — cross-chain

| Contract | Address | Type |
|---|---|---|
| MOR token | `0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86` | token |
| L2MessageReceiver | `0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427` | ERC1967 proxy |
| L2TokenReceiverV2 | `0x47176b2af9885dc6c4575d4efd63895f7aaa4790` | ERC1967 proxy |

### Base — token

| Contract | Address | Type |
|---|---|---|
| MOR token (MOROFT) | `0x7431aDa8a591C955a994a21710752EF9b882b8e3` | token, non-upgradeable |

### Base — Builders

| Contract | Address | Type |
|---|---|---|
| BuildersV4 | `0x42BB446eAE6dca7723a9eBdb81EA88aFe77eF4B9` | ERC1967 proxy |
| BuildersTreasuryV2 | `0x9eba628581896ce086cb8f1A513ea6097A8FC561` | ERC1967 proxy |
| RewardPool (Builders) | `0xDC99a8596e395E52aba2BD08C623E1e428Dc3980` | ERC1967 proxy |
| FeeConfig | `0x845FBB4B3e2207BF03087b8B94D2430AB11088eE` | ERC1967 proxy |
| LinearDistributionIntervalDecrease | `0x2265ae4127a49218c1C562Cb16822971f295Ed50` | external library |

### Base — Inference marketplace

| Contract | Address | Type |
|---|---|---|
| LumerinDiamond | `0x6aBE1d282f72B474E54527D93b979A4f64d3030a` | EIP-2535 diamond |

All marketplace logic is reached through the diamond. Its five facets as of 2026-08-07 — ProviderRegistry `0xE30279b79392AEfF7fDf1883C23d52eBA9D88A75`, ModelRegistry `0xb7994dE339AEe515C9b2792831CD83f3C9D8df87`, Marketplace `0x5B660aB78f3AC743953F9E68630A2D66e7b45F64`, Delegation `0x345B8B23c38F70f1d77560C60493Bb583f012Cb0`, SessionRouter `0x3a3952f0E57b343F00b31F7dA039eF16389B7260` — are in scope through the diamond, not as standalone targets. Facets may be replaced by upgrade; pin your fork block and state which facet set you tested.

**Explicitly not in scope:** multisig wallets (`0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` on all chains), the deployer EOA (`0x040EF6Fb6592A70291954E2a6a1a8F320FF10626`), the funding account (`0x5160C0311A95E0A1072FA85Df23712A7BA1cD4b1`), the burn address, the lock address, the DelegateFactory / ProvidersDelegate contracts (not initialised, zero TVL), and any contract not listed above.

---

## Resources

- [Protection Fund Details](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
