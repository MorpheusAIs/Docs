<p align="center"> <img src="https://github.com/user-attachments/assets/1acd0683-cc00-4034-bb50-2b3568278d95" width=70% height=70%>

# Morpheus
## A Network For Powering Smart Agents
### Authored by Morpheus, Trinity, & Neo

---
## Introduction 
On September 2nd, 2023, a group of anonymous authors who identified themselves as Morpheus, Trinity, and Neo published [a groundbreaking paper](/!KEYDOCS%20README%20FIRST!/MOR%20-%20Network%20For%20Powering%20Smart%20Agents.pdf), marking the inception of the Morpheus, **"A Network For Powering Smart Agents"**.

With Morpheus, everyone will have access to a powerful personal AI, capable of thinking alongside them and taking actions that serve their best interests. Just as personal computers and search engines once empowered individuals, today we have the same opportunity with personal AIs. Morpheus integrates an ideal blend of technologies LLMs, Agents, and Web3 into a public network designed to accelerate the widespread distribution and use of Smart Agents. Communicating naturally with your Smart Agent, which understands your tasks and queries, mirrors how Google’s search engine made the early internet accessible to the general public. Now, Morpheus is opening up Web3 to billions of users.

---
## Smart Agent Development Principles:
1. **Agents cannot execute decisions**: Agents should not be given private keys or allowed to make transactions on their own. They can only construct transaction 
payloads for a user's approval. This is due to the limitations of current LLMs in understanding complex transactions and the risk of [gaslighting](https://arxiv.org/abs/2311.04235).

2. **Local installation**: Agents should run on the user's laptop, typically with 8-16 GB of RAM. This allows for faster execution and better performance.
   
3. **No private keys**: Agents must not have access to private keys or be able to execute transactions independently. User's cryptographic approval is essential for any 
transaction.

---
## Morpheus Local Smart Agent Releases
The latest release can be found at https://github.com/MorpheusAIs/moragents/releases. 

Releases built with built with the friendliest of dev tooling. Python for AI Agents, JS for UI. Runs in your favorite browser. Made possible by Docker. Fully Extensible, devs can add their own agents and have them automatically invoked based on user intent.

### Features
- [Delegating agent](https://github.com/MorpheusAIs/moragents/pull/45) which can maintain user's persona/interests as well as coordinating to task agents and tools.
- Fetch price, market cap, and TVL of coins and tokens supported on CoinGecko.
- Web interface (Сhrome, Brave)
- Wallet integrations for your existing wallets in-browser.
- Web3 swap agent.
- Chat with local PDF files
- [FeedBuzz](https://github.com/yeagerai/feedbuzz-contracts) - AI filtered logging system to surface user demand and failure modes for new functionality
- X/Twitter posting agent - an agent which generates spicy tweets with an X integration for one-click posting.
- Crypto news agent
- Check MOR rewards 

### Example queries
After connecting Morpheus with your web3 wallet, you can test the **Data Smart Agent** with prompts such as:  

- What is my balance?
  
- What is my address?
  
- Send ETH to [Ethereum Address]
  
- What is the price of Ethereum / Price of ETH (or other token listed on Coingecko)
  
- What is the market cap of DOGE / MC of DOGE (or other token listed on Coingecko)
  
- What is the fully diluted valuation of Solana / FDV SOL (or other token listed on Coingecko)
  
- What is the total value locked in Uniswap / TVL of Uniswap (or other token listed on Coingecko)

- Can you give me a short summary of the PDF? *after uploading the document

<img src="https://github.com/MorpheusAIs/moragents/blob/main/images/mor_rewards.png" width=80% height=80%>
<img src="https://github.com/MorpheusAIs/moragents/blob/main/images/real-time-info.png" width=80% height=80%>
<img src="https://github.com/MorpheusAIs/moragents/blob/main/images/tweet_sizzler.png" width=80% height=80%>
<img src="https://github.com/MorpheusAIs/moragents/blob/main/images/price-fetcher-realtime-news.png" width=80% height=80%>
<img src="/Graphics/Docs%20Graphics/English/README/agent_clarify3.png" width=80% height=80%>
<img src="/Graphics/Docs%20Graphics/English/README/wallet_integration1.png" width=90% height=90%>
<img src="/Graphics/Docs%20Graphics/English/README/successful_swap2.png" width=90% height=90%>


> [!WARNING]
> Review all transactions before approving them. The LLM makes mistakes, you have human wisdom.  
> 
> This is an experimental release and the ETH Smart Agent may try and send your money into a black hole.  
>
> Gas costs are high on Ethereum. Consider testing using the Ethereum Sepolia or Arbitrum Sepolia testnets.

---
## Links List:
### Documentation: 
- [Key documents folder](/!KEYDOCS%20README%20FIRST!)
- [FAQs](/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides)
- [White Paper](/!KEYDOCS%20README%20FIRST!/WhitePaper.md)
- [Morpheus Launch Phases](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Launch%20Phases.md)
- [Morpheus Multisig Account](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Multisignature%20Account.md)
- [Protection Fund Details](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
- [Bug Bounty Program](https://github.com/MorpheusAIs/Docs/blob/main/Security%20Audit%20Reports/Bug%20Bounty%20Program.md)
- [Morpheus Meetup Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/Morpheus%20Meetup%20Guide.md)

---
### Repositories:
-	MORagents Local Install: https://github.com/MorpheusAIs/moragents
-	Smart Contracts: https://github.com/MorpheusAIs/SmartContracts
-	Frontend Dashboard: https://github.com/MorpheusAIs/DashBoard
- Technical Documentation https://github.com/MorpheusAIs/Docs
- Morpheus Request for Comments: https://github.com/MorpheusAIs/MRC
- Morpheus Lumerin (Compute) Node: https://github.com/MorpheusAIs/Morpheus-Lumerin-Node
- Morpheus MOR20 Contracts: https://github.com/MorpheusAIs/MOR20  

---
## Morpheus Smart Contract addresses:
**Ethereum:**
- MOR token: [0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0](https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0)
- Distribution: [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)
- L1Sender: [0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://etherscan.io/address/0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84)
- Multisig Ethereum: [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://etherscan.io/address/0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E)
- Multisig ENS: [MOR.ETH](https://etherscan.io/name-lookup-search?id=mor.eth)
  
**Arbitrum:**
- MOR token: [0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)
- L2TokenReceiverV2: [0x47176b2af9885dc6c4575d4efd63895f7aaa4790](https://arbiscan.io/address/0x47176b2af9885dc6c4575d4efd63895f7aaa4790)
- L2MessageReceiver: [0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427](https://arbiscan.io/address/0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427)
- Multisig  Arbitrum: [0x151c2b49CdEC10B150B2763dF3d1C00D70C90956](https://arbiscan.io/address/0x151c2b49CdEC10B150B2763dF3d1C00D70C90956)
- MOR burn address: [0x000000000000000000000000000000000000dead](https://arbiscan.io/token/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86?a=0x000000000000000000000000000000000000dead)

**Base:**
- MOR token: [0x7431ada8a591c955a994a21710752ef9b882b8e3](https://basescan.org/address/0x7431ada8a591c955a994a21710752ef9b882b8e3)
- Multisig Base: [0xf3ef00168dd40eae68a7e670d56c7b8724e0c183](https://basescan.org/address/0xf3ef00168dd40eae68a7e670d56c7b8724e0c183)


