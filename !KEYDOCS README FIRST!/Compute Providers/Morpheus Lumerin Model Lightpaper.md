### The document provides an overview of the Morpheus node architecture and design principles based on Ryan Condron's insightful presentation at the Decentralize AI Day in Denver on February 28, 2024

# Introduction:
Ryan founded Lumerin as a response to Bitcoin's centralization issue in mining, aiming to create a decentralized hashpower routing system. The architecture of Lumerin, which emphasizes decentralization, transparency, and efficiency, serves as a solid foundation for the Morpheus node. By adopting the principles and design patterns established in Lumerin, Morpheus inherits the benefits of decentralization, such as increased security, reduced risk of manipulation or censorship, and improved scalability.

# Design Principles
## Core Principles
### No SPOF (Single Points of Failure):
- No centralized servers.
- No centralized data stores.
- No centralized routers or relays.

### Single Software Solution / Code Base:
- Provider Node = User Node.
- Any user can be a provider, and any provider can be a user.

### Minimal On-chain Transactions:
- Reads are inexpensive.
- Writes are costly.

### Agnostic as Possible:
- Supports multiple blockchains (EVM).
- Model type agnostic.

## Privacy and Security
### Prompt / Inference:
- Prompts and inferences are kept private.
- No prompt or inference data is written to the blockchain.

### Node Locations:
- Providers register their IP or URL on-chain.
- User nodes are visible only to providers during sessions.
- Recommended use of proxy, load balancer, VPN, or obfuscation method.

# Morpheus Node Architecture
The Morpheus node architecture incorporates significant elements (highlighted in green) that have been tested by Lumerin for the past two and a half years. By leveraging the tested elements from Lumerin, the Morpheus node architecture benefits from proven solutions and robust design principles. 

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Node/%20Architecture.png" width=75% height=75%>

# Morpheus Smart Contracts Structure
The cornerstone of Morpheus' smart contract architecture is the ecosystem registry contract. This contract serves as a versioning mechanism for managing the complexity of operating across multiple blockchain networks. Instead of dealing with the challenges of tracking smart contracts, addresses, and versions separately on each chain, Morpheus simplifies this process by using the ecosystem registry. When deploying on a new blockchain, the first step is deploying the registry contract, which then registers all subsequent contracts deployed on that chain. Developers and users interacting with Morpheus can easily access all relevant contracts by calling the main ecosystem contract for that specific blockchain. This streamlined approach ensures efficient access to the Morpheus functionalities across different chains.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Node/%20Smart%20Contracts%20Structure.png" width=75% height=75%>

## The full list of contracts:
- Ecosystem Registry
- Provider Registry (whitelist)
- Session Router
- Marketplace
- Token Contract
- Capital Contract
- Model Registry (whitelist)
- Agent Registry (whitelist)

## Smart Contracts Whitelists
In the initial stages Morpheus will rely on whitelists as a trust mechanism. This involves placing trust in reputable actors within the Provider Registry, authenticated LLM (Model Registry) models, and trustworthy agents (Agent Registry). The reason for this cautious approach is the novelty of the technical solutions and the potential unknown hazards it may pose. As the ecosystem evolves and technology advances to enable proof of inference, proof of models, and proof of agents, the reliance on whitelists will gradually diminish. Reputation systems will be developed for providers and models, allowing for a more open and decentralized environment once trust can be verified through these mechanisms.

# Morpheus Session Flow
The basic pattern is adopted from Lumerin node structure

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Node/%20Session%20Flow.png" width=75% height=75%>

## The full session cycles includes six stages:
**1. Get Providers**  
User selects a model and receives endpoints from the router.  
**2. Select Provider**  
User node pings endpoints to determine the best provider and requests a session.  
**3. Open Session**  
If the provider accepts a session request, the user submits an "open session" transaction to the router.  
**4. Send Prompts**  
User communicates prompts to the provider through an open socket.  
**5. Close Session**  
Upon completion, the user requests a receipt from the provider and submits it, along with a report, to the router for session closure.  
**6. Pay Provider**  
The provider claims payment from the router.  

# Conclusions
- Avoid centralization points
- Prioritize privacy where possible
- Use portable code for a seamless user/provider experience
- Adopt the proven Lumerin pattern for efficiency and reliability
- Ensure deterministic interactions for transparent transactions
- Start with whitelists for trust and gradually move towards proofs
- Time is of the essence to safeguard models from interference

---------------------

For detailed technical information, refer to the full documentation and resources available on the provided links:
- [Github](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)
- [Full Model Documentation](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Morpheus%20Lumerin%20Model.md)
- [Presentation](https://drive.google.com/file/d/1Tute7WQD8djn1S5ZAQEgCTCDnDMOG3Em/view?usp=sharing)
- [Video](https://youtu.be/l83Zq12tCpg?si=owcmcqLYzhoEFvht) 

-------------------

**Ryan’s contacts:**
- Telegram: [@rkcondron](https://t.me/rkcondron)
- X/Twitter: [@ryankcondron](https://twitter.com/ryankcondron)
- Email: ryan@titan.io
 
