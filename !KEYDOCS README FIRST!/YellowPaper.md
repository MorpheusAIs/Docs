# Morpheus Yellow Paper (Technical Reference)

This document provides authoritative technical specifications for the Morpheus full node, smart contracts, and protocol components. For conceptual explanations, see the White Paper. For community and roadmap information, see the Community Guide.

---

## System Downloads & Version Information

| Platform   | Download Link                                                                 | SHA256 Hash                                                         | Version                |
|------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------|------------------------|
| Linux RPM  | https://storage.googleapis.com/get-morpheus/Morpheus-0.0.6-rpm.zip           | fa811b823f80c6afc537b608edff99feb1bc68451c0bba9d22f7abedf5e66c0a    | Morpheus-0.0.6-rpm     |
| Linux DEB  | https://storage.googleapis.com/get-morpheus/Morpheus-0.0.6-deb.zip           | 04044442119e4ab296ffa6c5d3ae297b178197b4855e42dcbd8a4634e2d8d8ad    | Morpheus-0.0.6-deb     |
| Mac x64    | https://storage.googleapis.com/get-morpheus/morpheus-0.0.6-x64.dmg           | 004948f4dcc3702ea41f6050d0d3a86db2198e1ebfd599aca20a9a6cdefcd8e3    | morpheus-0.0.6-x64.dmg |
| Mac ARM64  | https://storage.googleapis.com/get-morpheus/morpheus-0.0.6-arm64.dmg         | 2179c229c8f1acca5b8c3e9a813d75f5a42b971c8aff555ad30f0a8ada9dbb1c    | morpheus-0.0.6-arm64   |
| Windows    | https://storage.googleapis.com/get-morpheus/morpheus-0.0.6_x86_64_win.zip    | 37cb37a7a8443da87541fb1896d9f23112fecff650e3cfc053d51938a1e326a3    | morpheus-0.0.6_x86_64  |

---

## Smart Contract Specifications

### 1. N2 Yield Smart Contract (Arbitrum)
- Lock ETH via Thorchain, donate yield to Coders & Compute Providers.
- Calculate pro-rata ETH donated.

### 2. MOR Token Burn
- Burn address or burn function for MOR tokens.
- Forever provable destruction of MOR.

### 3. MOR ERC20 Template Contract
- Mint MOR tokens daily to Capital & Community (pro-rata to ETH yield donated).
- Mint MOR tokens daily to Coders & Compute Providers (pro-rata to MOR burned via fees).

### 4. Proof of Morpheus
- Publish lists of audited Agents, LLMs, Smart Contracts, and Prompts with Smart Rank scores.

### 5. Protection Funds
- Distribute MOR & ETH in cases of hacks, errors, bugs, or attacks.
- Pre-defined payout scenarios, policies for forking/rollbacks.
- Bug bounty and white hat funds.
- Protection from nation-state actors.

---

## Technical Diagrams & Distribution Tables

### MOR Smart Contract Rewards Distribution
![new-buckets](https://github.com/SmartAgentProtocol/SmartAgents/assets/76454555/cd57bae7-2a56-4a55-bf3e-1f810f3fba9c)

### MOR Token Distribution (Day 1 & Day 2)
![Untitled spreadsheet - Google Sheets 2023-10-15 13-28-08](https://github.com/MorpheusAIs/Morpheus/assets/76454555/6ff7869d-bbd6-46b5-8673-6a59b75906e1)

#### Example Distribution Calculation (ETH Contributor)
- Step 1: ![Diagram1ofETHDontator](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/fead528c-d628-449e-a3a3-2f53904f4a3d)
- Step 2: ![ETHGivenDiagram2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/915020e8-d342-48bc-85ee-367de0325680)
- Step 3: ![Diagram3ForETHGiven](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a3f455af-56de-4c6b-9688-5b9e91673e5a)

#### Example Distribution Calculation (Compute Provider)
- Step 1: ![MORForCompute](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/bef69c69-0420-441f-97f0-7e8195844f57)
- Step 2: ![MORForCompute2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a6f30da5-5441-4f0a-be80-c5798f5920cd)

#### MOR Token Distribution Pie Chart
![mordist](https://github.com/MorpheusAIs/Morpheus/assets/76454555/4157efe7-6abf-404a-87f9-a8dc76cd4799)

---

## Developer Tools & Tech Stack
- Llama2: Open source LLM (local run)
- Ollama: Packaging for Llama2
- LangChain: LLM-to-Vector store/API integration
- LangSmith Editor: Low-code agent builder
- SmartContractRank: Smart contract curation
- AgentRank: Specialized agent curation
- PromptRank: Prompt curation
- Filecoin: Storage & cloud compute
- Akash Network: Open compute for LLMs/agents
- Wallets: Shapeshift, Exodus, open source options

---

## Protocol Interfaces & Audit Process
- Placeholder: Detailed API schemas, protocol message formats, and system requirements to be added.
- Placeholder: Audit process description, certification, and incentives for auditors.
- Placeholder: Technical specifications for ranking algorithms and protocol interfaces.

---

## System Architecture Diagrams
- Morpheus Full Node: ![MorpheusLocalDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a0564914-cddb-42e4-b0f4-8c2310db6a66)
- Morpheus P2P: ![MorpheusP2PDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a7eeb31f-3d38-4233-a45f-e9b91ad84ba2)
- Morpheus Decentralized: ![MorpheusDecentralized](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/1699f2de-cc18-42e8-a05c-32b3307baa20)

---

## Validation & Security
- All downloads must be validated using the provided SHA256 hashes.
- Smart contract addresses and function signatures: [PLACEHOLDER – Add full contract ABIs and addresses]
- Error codes and handling: [PLACEHOLDER – Add error code documentation]
- System requirements: [PLACEHOLDER – Add minimum hardware, OS, and network requirements]

---

## [Community, Dapps, and recruiting information have been moved to the Community Guide.]
