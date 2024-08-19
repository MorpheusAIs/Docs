<img src="/Graphics/MOR gradient logo.png" width=100% height=100%>

# Morpheus
## A Network For Powering Smart Agents
### Authored by Morpheus, Trinity, & Neo
Published - September 2nd 2023

---
## Introduction 
The Smart Agent concept of connecting LLMs and AI Agents to wallets, Dapps, & smart contracts promises to open the world of Web3 to everyone. Chatting in normal language with your Smart Agent and having it understand the question or task, is similar to how Google's search engine opened the early internet up to the general public.

To make Smart Agents accessible to everyone and increase decentralization we propose a network & fairly launched token for incentivizing all four of the key contributors to their operation. Namely, the community of users, coders contributing to the Morpheus software / agents, capital providers funding development / operations and those supplying computation, storage and bandwidth. It has been well shown by the history of Bitcoin and Ethereum that free & open competition for scarce digital tokens can provide scalable infrastructure for a public blockchain over long periods of time.

---
## Smart Agent Development Principles:
- **Agents cannot execute decisions.**  
Agents can only construct transaction payloads for a user's approval.

- **Local installation.**   
 Agents should run on the user's laptop, typically with 8-16 GB of RAM. This allows for faster execution and better performance.

- **No private keys.**    
Agents must not have access to private keys or be able to execute transactions independently. User's cryptographic approval is essential for any transaction.

---
## Morpheus Local Smart Agent Features v.0.0.9
### Current
- Fetch price, market cap, and TVL of coins and tokens supported on CoinGecko.
- Web interface (Сhrome, Brave)
- Wallet integrations for your existing wallets in-browser:
   - MetaMask
   - Rainbow
   - Coinbase Wallet
   - WalletConnect
- Web3 swap agent.
- Chat with local PDF files

### Pending
- [FeedBuzz](https://github.com/yeagerai/feedbuzz-contracts) - AI filtered logging system to surface user demand and failure modes for new functionality
- [Delegating agent](https://github.com/MorpheusAIs/moragents/pull/45) which can maintain user's persona/interests as well as coordinating to task agents and tools.
- X/Twitter Posting Agent - an agent which generates spicy tweets with an X integration for one-click posting.

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

<img src="/Graphics/Docs%20Graphics/English/README/Data%20agent.png" width=50% height=50%>

![image](https://github.com/user-attachments/assets/48b7f04d-df86-4bad-8017-4c8ba83666d0)


For the **Swap Smart Agent**, a typical flow looks like this:

- A user requests a swap, e.g "I want to swap ETH for WBTC".

- The agent requests any missing information, e.g. in this case the amount is missing.

- Once all the information has been collected, the agent looks up the assets on the current chain, retrieves contract addresses and generates a quote if available.

- The quote is shown to the user, who may either proceed or cancel.

- If the user accepts the quote, the swap may proceed. The back-end will generate transactions which will be sent to the front-end to be signed by the user's wallet.

- If the allowance for the token being sold is too low, an approval transaction will be generated first.

<img src="/Graphics/Docs%20Graphics/English/README/agent_clarify3.png" width=80% height=80%>
<img src="/Graphics/Docs%20Graphics/English/README/wallet_integration1.png" width=90% height=90%>
<img src="/Graphics/Docs%20Graphics/English/README/successful_swap2.png" width=90% height=90%>



> [!WARNING]
> Review all transactions before approving them. The LLM makes mistakes, you have human wisdom.  
>
> Seriously, double check all actions in your wallet interface before sending money. 
> 
> This is an experimental release and the ETH Smart Agent may try and send your money into a black hole.  
>
> Gas costs are high on Ethereum. Consider testing out 0.0.8 using the Sepolia testnet or Arbitrum.


---
## Installs
### Mac OS M1/2/3 etc. (arm64)
>[!Note]
> Minimum 16GB RAM is required

**1.** Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
   
**2.** Follow default settings, can skip surveys, then leave docker desktop running. You can minimize it.
   
**3.** Download and install [MORagents009.pkg](https://drive.proton.me/urls/762Z6QFNH4#68MKubcGeDtf) 
   
**4.** Open ZIP, and copy MORagents.app to your Applications folder.  
   > SHA256 5200350bba351a40cfac5552476bad1bb67d32ff069a4d9ebc0b3556367673b7  MORagents009.pkg

**5.** Wait several minutes for background files to download and then your browser should automatically open to **http://localhost:3333**
   
> [!Note]
> After installation is complete, the MORagents app icon will bounce for several minutes on your dock, and then stop. This is normal behavior as it's downloading a large 9GB file in the background. You can open "Activity Monitor" and in the Network tab see that it's downloading
   
**6.** Open the "MORagents" app from Mac search bar.
 
> [!TIP]
>  For easier access: Right-click MORagents icon on dock -> Options -> Keep in Dock

#### Troubleshooting
If the app shows connections errors in connecting to agents. Please ensure Docker Desktop is running, then close and reopen **MORagents** from desktop.

---
### macOS Intel (x86_64)
*coming soon*

---
### Windows (x86_64)
>[!Note]
> Minimum 16GB RAM is required

 1. Use Chrome to download [MORagentsSetupWindows009.zip](https://drive.proton.me/urls/8X58WAH80G#ib5r3K4WalDA)
    > SHA256 6b8bd78571df2f5e8c6e516102aa05b1121d0214fdfb75a2be16146c22e0d2c52 MORagentsSetupWindows009.zip

2. Go to downloaded **MORagentsSetupWindows009(.zip)** file and double click to open

3. Double click **MORagentsSetup.exe**  
   - You may need to click "More info" -> "Run anyway"
   - If that still doesn't work, try temporarily disabling your antivirus and open the *.exe again

4. Click and Run **MORagentsSetup.exe** to auto-install Docker Desktop dependency.

5. Open **MORagents** from Desktop.

6. Wait for Docker engine to start...

7. Open **MORagents** App from Desktop
   First time installation requires some extra time to load agent's image.  
   

#### Troubleshooting
If anything hangs for >10min, please try opening the MORagents app again from the Desktop.

---------
### Linux
*coming soon*

---------
### Build It Yourself
1. [MacOS](https://github.com/MorpheusAIs/Docs/blob/main/Guides/README_MACOS_DEV_BUILD.md)
2. [Windows](https://github.com/MorpheusAIs/Docs/blob/main/Guides/README_WINDOWS_DEV_BUILD.md)

---------
## Key Documents List:
- [Morpheus Fundamentals](https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Fundamentals)
- [Capital Providers](https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers)
- [Compute Providers](https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers)
- [Code Providers](https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/Code%20Providers)
- [FAQs](https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/FAQs)
- [White Paper](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md)
- [Yellow Paper](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/YellowPaper.md)
- [Techno Capital Machine](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers%2C%20MOR20%2C%20TCM/Techno%20Capital%20Machine%20(TCM).md)
- [Morpheus Launch Phases](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Launch%20Phases.md)
- [Morpheus Multisig Account](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Multisignature%20Account.md)
- [Protection Fund Details](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md)
- [Morpheus Testing Plan](https://github.com/MorpheusAIs/Docs/blob/main/Security%20Audit%20Reports/Morpheus%20Testing%20Plan.md)
- [Bug Bounty Program](https://github.com/MorpheusAIs/Docs/blob/main/Security%20Audit%20Reports/Bug%20Bounty%20Program.md)
- [Morpheus Meetup Guide](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/Morpheus%20Meetup%20Guide.md)

---
## Code:
-	Morpheus Smart Agent Local Install: https://github.com/MorpheusAIs/moragents
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

---
## Morpheus Network Diagram
<img src="/Graphics/MOR network diagram.png" width=100% height=100%>

