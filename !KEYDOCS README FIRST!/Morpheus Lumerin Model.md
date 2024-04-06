# Morpheus Lumerin Model
### Ryan Condron
### March 16th 2024

## Summary

The Morpheus Lumerin Model utilizes the Lumerin protocol routing pattern to create a peer-to-peer, decentralized, and anonymous ecosystem for connecting AI users with AI model and agent compute providers. This model seeks to incorporate aspects of the original Morpheus white paper and yellow paper as well as core concepts from the [Yellowstone Compute Model](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Yellowstone%20Compute%20Model.md) and Lake Travis System.

The following proposal will explain the key design principles that have been incorporated as well as outline each part of the on-chain ecosystem model, client-side node, and underlying protocol.

## Design Principles

In order to ensure the scalability, security, and censorship resistant ethos of the Morpheus vision, the following design principles will be used in the design and development of each part of the ecosystem.

#### 1. No SPOFs (single points of failure)

Centralized servers, data stores, and even routers or relays often pose significant risk in a decentralized architecture, mainly by creating single points of failure (SPOFs). When vital functions or data are centralized, the entire system's reliability is jeopardized if those servers or services fail or are compromised. To mitigate these risks, the architecture emphasizes the importance of decentralization at multiple levels: servers, data stores, and routing mechanisms. This approach ensures no single component's failure can bring down the entire system, thereby enhancing its resilience and security.

#### 2. One Software Solution

A single codebase for both providers and users streamlines maintenance, versioning, and upgrades significantly. This approach means that any update or fix is universally applicable, eliminating the need for parallel development tracks or compatibility checks between different client versions. It simplifies the deployment process, as there's only one software version to distribute and update. For open-source projects, this enhances collaboration and contribution efficiency, as developers can focus on a single code repository, making it easier to track changes, manage issues, and merge contributions. This unified framework fosters a more cohesive development environment, reducing fragmentation and ensuring that improvements benefit the entire ecosystem simultaneously.

#### 3. Minimal Blockchain Transactions

Blockchain technology categorizes transactions into inexpensive reads and costly, slow writes. Reading data from a blockchain is efficient and cheap, ideal for applications needing frequent data access. Writing data, however, demands consensus, uses more resources, and incurs higher fees. Applications that limit on-chain writes can cut costs and improve performance, making the technology more viable for various uses. This highlights the value for designing the Morpheus protocol with a minimal amount of costly write operations, optimizing for both economic and computational efficiency.

#### 4. Blockchain Agnostic

The ability to deploy smart contract code on any Ethereum Virtual Machine (EVM) compatible blockchain is paramount for ensuring maximum interoperability and flexibility. By designing smart contracts to be blockchain agnostic, developers can leverage the unique advantages of different blockchains while maintaining a consistent and seamless experience for users. This approach not only broadens the potential user base but also enhances the robustness of applications by integrating with multiple ecosystems, significantly improving the overall resilience and scalability of the deployed solutions.

#### 5. Model Agnostic

Being AI model agnostic is crucial for the Morpheus network to efficiently process and handle a wide array of data models. This versatility ensures that the network can seamlessly integrate with different AI technologies, regardless of their underlying architecture or design principles. By fostering an environment that accommodates any type of AI model, the network enhances its adaptability, enabling it to quickly respond to evolving technological trends and user needs. This AI model agnosticism not only future-proofs the network but also significantly broadens its applicability across various industries, ensuring it can meet diverse data processing requirements with precision and efficiency.

#### 6. Prompt & Inference Privacy

Ensuring that the prompt and inference data stream seamlessly between the user and provider, without intermediaries, is a cornerstone of the Morpheus privacy strategy. This direct transmission guarantees that sensitive information remains confidential, significantly reducing the risk of data breaches. By circumventing the need to publicly expose any private data, we maintain a high level of security and confidentiality for all users and providers. This approach not only reinforces good decentralized system design patterns but also keeps the data transmitted through a public blockchain as anonymous and private as possible.

#### 7. Node Security

For providers, protecting their IP address or URL endpoint is paramount to maintaining the integrity and security of the Morpheus network. Utilizing proxies, load balancers, VPNs, or other obfuscation methods helps shield their digital footprint, making it significantly more challenging for malicious actors to target or exploit the system. Similarly, ensuring user nodes are only visible to providers during active sessions enhances privacy and security for all users. This layer of anonymity is crucial; it prevents potential attackers from easily mapping the network or identifying vulnerable points for attacks. Together, these strategies form a robust defense mechanism, bolstering the network's resilience against cyber threats and preserving the confidentiality and integrity of the data flowing through it.




## Ecosystem Model

The Morpheus ecosystem will consist of several on-chain and off-chain systems. On-chain systems can be divided into two categories: capital systems and compute systems. Capital systems are deployed on blockchains for the purpose of locking up capital in exchange for minted MOR tokens while compute systems are deployed on blockchains for the purposes of creating an AI model and agent market.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Lumerin%20Model/figure1.png">
<i>Figure 1. On-chain ecosystem</i>

### Layer 1 Contracts

#### **Ecosystem Registry**
The ecosystem registry is a reference list of all official Morpherus contracts deployed on that blockchain as well as a list of ecosystem registries deployed on other blockchains.

##### Variables

| Name | Type | Description |
|---|---|---|
| Pointer | struct | Complex object containing pointer variables.<br>{ <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) Name, <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) Address, <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) AddedBy, <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) AddedTimestamp <br>} |
| PointerIds | string[] | Array of pointer names. |
| Pointers | mapping | Mapping of pointers by name. (string => Pointer) |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| getPointer | Name (string) | Returns a Pointer object with the given name. |
| getPointers | none | Returns an array of pointer objects. |
| getPointerIds | none | Returns an array of pointer names. |
| addPointer | Addr (address),<br>Name (string) | Adds new pointer to Pointers and PointerIds |
| updatePointer | Name (string),<br>OldAddr (address),<br>NewAddr (address) | Updates pointer record with new address. |
| deletePointer | Name (string) | Removes pointer from Pointers and PointerIds. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

#### **Token Distributor**
The token distribution contract is responsible for attributing MOR to the different tokenomic model tranches.


<i>"Distribution.sol is the core contract of the [Techno Capital Machine](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md). It allows Capital Providers to stake stETH (Lido Staked ETH) on Ethereum and claim MOR rewards to Arbitrum.

Distribution utilizes [L1Sender](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L1Sender.md) to bridge stETH yield and relay MOR claims to Arbitrum. [LinearDistributionIntervalDecrease](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/LinearDistributionIntervalDecrease.md) is used to calculate pool rewards."</i> <sup>1</sup> 
 
[https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/Distribution.sol](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/Distribution.sol) \
[https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)

At the time of this writing there are five pools setup in the distribution contract.

1. Capital Tranche (Pool 0) \
 \
Pool 0 started February 8th, 2024 at midnight GMT.  \
It mints 3,456 MOR every 24 hours to the capital tranche. \
Minting amount decreases by [0.59255872824](https://etherscan.io/unitconverter?wei=592558728240000000) MOR every 24 hours. \
Users accrue MOR daily in ratio to their deposit against total deposits. \
User accrued MOR is available to claim after May 8th, 2024 at midnight GMT. \
Staked Ethereum deposited in this contract cannot be withdrawn for 7 days. \
Staked Ethereum deposited in this contract has a withdrawal hold time of 7 days.

2. Code Tranche (Pool 1) \
 \
Pool 1 started February 8th, 2024 at midnight GMT.  \
It mints 3,456 MOR every 24 hours to the code tranche. \
Minting amount decreases by [0.59255872824](https://etherscan.io/unitconverter?wei=592558728240000000) MOR every 24 hours. \
Users accrue MOR daily in ratio to their weights against total attributed weight. \
User accrued MOR is available to claim after May 8th, 2024 at midnight GMT. \

3. Community Tranche (Pool 2) \
 \
Pool 2 started February 8th, 2024 at midnight GMT.  \
It mints 3,456 MOR every 24 hours to the community tranche. \
Minting amount decreases by [0.59255872824](https://etherscan.io/unitconverter?wei=592558728240000000) MOR every 24 hours. \
Users accrue MOR daily in ratio to their weights against total attributed weight. \
User accrued MOR is available to claim after May 8th, 2024 at midnight GMT. \


4. Compute Tranche (Pool 3) \
 \
Pool 3 started February 8th, 2024 at midnight GMT.  \
It mints 3,456 MOR every 24 hours to the compute tranche. \
Minting amount decreases by [0.59255872824](https://etherscan.io/unitconverter?wei=592558728240000000) MOR every 24 hours. \
Providers can claim up to 1% of the compute tranche every 24 hours starting after May 8th, 2024 at midnight GMT. \


5. Protection Tranche (Pool 4) \
 \
Pool 4 started February 8th, 2024 at midnight GMT.  \
It mints 576 MOR every 24 hours to the protection tranche. \
Minting amount decreases by [0.09875978804](https://etherscan.io/unitconverter?wei=98759788040000000) MOR every 24 hours. \
Tokens in this pool are claimable after May 6th, 2024 at midnight GMT.

#### Layer 1 Sender

The layer 1 sender contract facilitates the bridging of tokens and messages to the layer 2 receiver contracts.

<i>"L1Sender.sol is responsible for sending tokens and messages from Ethereum to Arbitrum. It is called by [Distribution](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/Distribution.md) to:

- Wrap and send the deposit token (stETH) to Arbitrum via the native Arbitrum bridge

- Send instructions to mint MOR to Arbitrum via LayerZero"</i> <sup>2</sup>

[https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L1Sender.sol](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L1Sender.sol) \
[https://etherscan.io/address/0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://etherscan.io/address/0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84)

### Layer 2 Contracts

#### **Ecosystem Registry**
Same as the layer 1 ecosystem registry, the layer 2 ecosystem registry is a reference list of all official Morpherus contracts deployed on that blockchain as well as a list of ecosystem registries deployed on other blockchains.

#### **Layer 2 Minter**
The layer 2 minter contract owns the Morpheus Token (MOR) contract and is responsible for receiving messages from the layer 1 sender contract and executing the minting of MOR based on those messages.

<i>"L2MessageReceiver.sol is an implementation of the [ILayerZeroReceiver](https://layerzero.gitbook.io/docs/evm-guides/evm-solidity-interfaces/ilayerzeroreceiver) interface used to receive messages via LayerZero. It receives instructions to mint MOR tokens (e.g. to Capital Providers) from [L1Sender](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L1Sender.md) on Ethereum."</i> <sup>3</sup>

[https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2MessageReceiver.sol](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2MessageReceiver.sol) \
[https://arbiscan.io/address/0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427](https://arbiscan.io/address/0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427)

#### **Morpheus Token (MOR)**
The MOR contract is a standard ERC20 token contract deployed on Arbitrum.

<i>"MOR.sol, the Morpheus token, is an OpenZeppelin ERC20 implementation that extends the ERC20Capped and ERC20Burnable extensions.

New tokens can only be minted by the contract owner – [L2MessageReceiver](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L2MessageReceiver.md) – up to the immutable cap of 42,000,000 tokens."</i><sup>4</sup>

[https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/MOR.sol](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/MOR.sol) \
[https://arbiscan.io/address/0x7431ada8a591c955a994a21710752ef9b882b8e3](https://arbiscan.io/address/0x7431ada8a591c955a994a21710752ef9b882b8e3)

#### **Layer 2 Capital**

The layer 2 capital contract is the receiver of the capital yield earned by tokens locked in the distribution contract and sent by the layer 1 sender contract.

<i>"L2TokenReceiver.sol is a component of the Techno Capital Machine. It is responsible for receiving wstETH yield from [L1Sender](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L1Sender.md) via the native Arbitrum bridge and managing Protocol-Owned Liquidity.

All functions on L2TokenReceiver can only be called by the contract owner – the Morpheus multisig."</i> <sup>5</sup>

[https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2TokenReceiver.sol](https://github.com/MorpheusAIs/SmartContracts/blob/main/contracts/L2TokenReceiver.sol) \
[https://arbiscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://arbiscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)

#### **Provider Registry**

The provider registry contract is a list of providers and their designated TCP/IP endpoints. Providers will be required to stake a minimum amount of MOR to be added to the registry. If the provider stakes more than the required amount of MOR the additional stake will be counted towards the provider’s reputation weight in the marketplace.

##### Variables

| Name | Type | Description |
|---|---|---|
| Provider | struct | Complex object containing provider variables.<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;string) Endpoint,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) Port,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) Stake,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) RegTimestamp<br>} |
| ProviderIds | address[] | Array of registered provider addresses. |
| Providers | mapping | Mapping of registered providers. (address => Provider) |
| Stake | uint256  | Minimum required stake to register a new provider. |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| getProvider | address | Returns a Provider object from Providers mapping. |
| getProviderIds | none | Returns an array of registered provider addresses. |
| getProviderList | none | Returns an array of registered providers. |
| getStakeReq | none | Returns an uint256 of required MOR stake to register. |
| registerProvider | IP (string),<br>Port (uint) | Receives the stake & adds a provider to the registry lists. |
| unregisterProvider | none | Sends the stake & removes a provider from registry lists. |
| updateProvider | IP (string),<br>Port (uint) | Updates the mapped provider objects with new values. |
| setProviderStakeReq | uint256 | Updates the minimum stake requirement. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

#### Model Registry

The model registry contract is a list of LLM models available on the Morpheus network and their corresponding IPFS locations.

##### Variables

| Name | Type | Description |
|---|---|---|
| Model | struct | Complex object containing model variables.<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) Owner,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) UUID,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) Name,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) IPFS,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string[]) Tags,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) RoyaltyFee,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) Stake,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) RegTimestamp<br>} |
| ModelIds | string[] | A string array of model UUIDs. |
| Models | mapping | Mapping of registered models by UUID. (string => Model) |
| Tags | string[] | A string array of available tags. |
| Stake | uint256 | Minimum required stake to register a new model. |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| getModel | UUID (string) | Returns a Model object from Models mapping. |
| getModelIds | none | Returns an array of registered model UUIDs. |
| getModels | none | Returns an array of registered models. |
| getModelTypes | none | Returns a string array of model types. |
| getModelsByOwner | Owner (address) | Returns an array of Model objects filtered by given owner. |
| getModelsByType | Type (string) | Returns an array of Model objects filtered by given type. |
| getStakeReq | none | Returns an uint256 of required MOR stake to register. |
| registerModel | UUID (string),<br>Name (string),<br>IPFS (string),<br>Tags (string[]),<br>RoyaltyFee (uint256) | Receives the stake & adds a model to the registry lists. |
| unregisterModel | none | Sends the stake & removes a model from registry lists. |
| updateModel | UUID (string),<br>Name (string),<br>IPFS (string),<br>Tags (string[]),<br>RoyaltyFee (uint256) | Updates the mapped model objects with new values. |
| setModelStakeReq | uint256 | Updates the minimum stake requirement. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

#### Agent Registry

The agent registry contract is a list of registered AI agents available for use on the Morpheus network and their corresponding IPFS location.

##### Variables

| Name | Type | Description |
|---|---|---|
| Agent | struct | Complex object containing Agent variables.<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) Owner,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) UUID,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) Name,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) IPFS,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string[]) Tags,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) RoyaltyFee,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) Stake,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) RegTimestamp<br>} |
| AgentIds | string[] | A string array of agent UUIDs. |
| Agents | mapping | Mapping of registered agents by UUID. (string => Agent) |
| Tags | string[] | A string array of available tags. |
| Stake | uint256 | Minimum required stake to register a new agent. |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| getAgent | UUID (string) | Returns an Agent object from Agents mapping. |
| getAgentIds | none | Returns an array of registered agent UUIDs. |
| getAgents | none | Returns an array of registered agents. |
| getAgentTypes | none | Returns a string array of agent types. |
| getAgentsByOwner | Owner (address) | Returns an array of Agent objects filtered by given owner. |
| getAgentsByType | Type (string) | Returns an array of Agent objects filtered by given type. |
| getStakeReq | none | Returns an uint256 of required MOR stake to register. |
| registerAgent | UUID (string),<br>Name (string),<br>IPFS (string),<br>Tags (string[]),<br>RoyaltyFee (uint256) | Receives the stake & adds an agent to the registry lists. |
| unregisterAgent | none | Sends the stake & removes an agent from registry lists. |
| updateAgent | UUID (string),<br>Name (string),<br>IPFS (string),<br>Tags (string[]),<br>RoyaltyFee (uint256) | Updates the mapped agent objects with new values. |
| setAgentStakeReq | uint256 | Updates the minimum stake requirement. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

#### Marketplace

The marketplace contract collects model price information from providers and acts as the Morpheus ecosystem’s open order book. The marketplace contract imports data from the Provider Registry, Model Registry, and Agent Registry. The nonce in each bid is used to track bid history and prevent mid-session price changes.

##### Variables

| Name | Type | Description |
|---|---|---|
| Bid | struct | Complex object containing bid variables.<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) Provider,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) UUID,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) Nonce,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) BidAmount,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) CreatedTimestamp<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint) DeletedTimestamp<br>} |
| Bids | mapping | A mapping of Bid arrays by Provider + UUID + Nonce. (string => Bid[]) |
| Providers | mapping | A mapping of Provider arrays by UUID. (string => Address[]) |
| ProviderModels | mapping | A mapping of Model UUIDs by Provider. (address => string[]) |
| ProviderAgents | mapping | A mapping of Agent UUIDs by Provider. (address => string[]) |
| ModelFee | uint256 | Marketplace bid fee to post a new model. |
| AgentFee | uint256 | Marketplace bid fee to post a new agent. |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| getBids | UUID (string) | Returns list of Bid objects. |
| getModelsByProvider | Addr (address) | Returns a list of model bids filtered by provider address. |
| getAgentsByProvider | Addr (address) | Returns a list of agent bids filtered by provider address. |
| postModelBid | UUID (string),<br>BidAmount (uint256),<br>Nonce (uint256) | Adds new Bid object to Bids mapping.<br>Adds new UUID to ProviderModels provider mapping. |
| postAgentBid | UUID (string),<br>BidAmount (uint256),<br>Nonce (uint256) | Adds new Bid object to Bids mapping.<br>Adds new UUID to ProviderAgents provider mapping. |
| deleteModelBid | UUID (string),<br>Nonce (uint256) | Removes Bid object from Bids mapping.<br>Removes UUID from ProviderModels provider mapping. |
| deleteAgentBid | UUID (string),<br>Nonce (uint256) | Removes Bid object from Bids mapping.<br>Removes UUID from ProviderAgents provider mapping. |
| updateModelBid | UUID (string),<br>BidAmount (uint256),<br>Nonce (uint256) | Runs deleteModelBid with UUID.<br>Runs addModelBid with UUID, BidAmount, & Nonce. |
| updateAgentBid | UUID (string),<br>BidAmount (uint256),<br>Nonce (uint256) | Runs deleteAgentBid with UUID.<br>Runs addAgentBid with UUID, BidAmount, & Nonce. |
| setModelBidFee | uint256 | Update the fee for posting a new model bid. |
| setAgentBidFee | uint256 | Update the fee for posting a new agent bid. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

#### **Session Router**

The session router contract is responsible for maintaining an active log of current of past user sessions. Session closeout data can be used to generate a reputation score for a provider, model, and agent. Imports data from Provider Registry, Model Registry, Agent Registry, and MOR Token contracts.

##### Variables

| Name | Type | Description |
|---|---|---|
| Session | struct | Complex object containing session variables.<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) SessionId,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) User,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(address) Provider,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) UUID,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) Budget,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) Refund,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) Stake,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(string) CloseoutReceipt,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) CloseoutType,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) OpenTimestamp,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(uint256) CloseTimestamp<br>} |
| Sessions | mapping | A mapping of Sessions by SessionId. (string => Session) |
| ProviderSessions | mapping | A mapping of SessionIds by Provider. (address => string[]) |
| UserSessions | mapping | A mapping of SessionIds by User. (address => string[]) |
| StakeDelay | uint256 | Number of seconds to delay the stake return when a user closes out a session using a user signed receipt. |
| Owner | address | The owner of the contract. |

##### Functions

| Name | Parameters | Description |
|---|---|---|
| openSession | Provider (address),<br>UUID (string),<br>Budget (uint256) | Receives the session stake and creates a Session object.<br>Returns SessionId string. |
| closeSession | SessionId (string),<br>Receipt (string),<br>Signature (string) | Processes session closeout and returns session stake.<br>Add MOR payout to the provider’s claimable balance.<br>Return unused budget (refund) to the user balance.<br>Uses signature to determine if the "CloseoutType" is a provider signed or user signed report. |
| getClaimBalance | Addr (address) | Returns claimable balance by provider address. |
| getSpendBalance | Addr (address) | Returns spendable balance by user address. |
| getTodaysBudget | none | Returns today's MOR  budget. |
| getComputeTranche | none | Returns total MOR in Compute Tranche |
| claimAmount | Amt (uint256) | Withdraws MOR from the provider’s claimable balance. |
| deleteHistory | SessionId (string),<br>Index (uint) | Removes SessionId from UserSessions array.<br>Clears User address field in Session record. |
| updateStakeDelay | StakeDelay (uint256) | Updates the number of seconds a stake is delayed when a user closes out a session using a user signed receipt. |
| transferOwnership | address | Transfers the ownership of the contract to a new address. |
| getOwner | none | Returns the current owner of the contract. |

Receipt strings will be a signed message from either provider or user and consist of session metrics and bid data. A message signed by the provider will return the user’s stake immediately. A message signed by the user will trigger a delay in the stake return. This mechanic is designed to incentivize users to close out sessions with receipts they receive from providers, but provides a path to reclaim stake if a provider is a bad actor.

<TODO Assign compute budget spend to third party> \
<TODO Create reputation endpoints>

## Node Architecture

The Morpheus core node is a client-side node that connects providers and users together based upon on-chain routing information. The node consists of five core parts which are illustrated in figure 2: Wallet, API, UI, Proxy Router, and AI Engine.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Lumerin%20Model/figure2.png">
<i>Figure 2. High Level Node Block Diagram</i>

#### Wallet & Key Storage

The wallet module is a backend system that is responsible for key generation and restore, signing, and interacting with the blockchain. All EVM ABI data and monitored smart contracts will be stored in the wallet module and made accessible to the other modules through the node API. The key storage element is an encrypted file containing the user’s mnemonic, imported keys, and can be used to store all sensitive wallet related information that shouldn’t be shared through the API.

<TODO Add Key Storage JSON Schema>

#### Application Programming Interface (API) Bus

The Morpheus node API is an internal bus system that allows all of the different modules to interact with each other. Each module will have its own API schema that can be altered as needed to adapt module functionality.

The AI Engine API schema is planned to be in the format of the Open AI developer API.^6^

##### Wallet API

| Endpoint | Method | Parameters | Response |
|---|---|---|---|
| /wallet/addresses | GET | none | {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"addresses": ["0x", "0x"]<br>} |

##### Proxy Router API

| Endpoint | Method | Parameters | Response |
|---|---|---|---|
| /proxy/sockets | GET | none | {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"sockets": ["{guid}", "{guid}"]<br>} |

##### AI Engine API

| Endpoint | Method | Parameters | Response |
|---|---|---|---|
| /ai/models | GET | none | {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"models": ["model1", "model2"]<br>} |

<TODO Add API schema documentation>

#### User Interface (UI)

The default Morpheus UI is a client-side application built using Electron, Node.js, and React. Since the initial Morpheus ecosystem will be deployed on Arbitrum, the Morpheus UI will have dual wallet features for MOR and aETH. A sample mockup of a proposed user interface can be found in figure 3. The UI can be designed and built in a modular fashion for greater flexibility. Different modules can be added as needed to the navigation bar along the left side of the client window.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Lumerin%20Model/figure3.png">
<i>Figure 3. Proposed wallet UI mockup</i>

The Morpherus node API bus exposes a consumable API that any permissioned UI can access. The node may even be run as a daemon service on a central web server to provide Morpheus network access to web and mobile apps.

#### Proxy Router

The Proxy Router is a socket management module that listens on a local port for incoming connections and handles the handshake with remote nodes.

<TODO>

#### AI Engine & AI Models

The AI Engine will initially be a wrapper on llama.cpp

<TODO>

#### Data Storage

The data storage elements

<TODO>


## Morpheus Protocol

The Morpheus Protocol is essentially the language and pattern that the Morpheus nodes use to talk to each other and the on-chain ecosystem. The decision trees of the Morpheus protocol can be categorized into three main areas: Provider node communication, user node communication, and session router contract interactions.

### Provider Node Communication

#### Provider Node to User Node

1. **Provider / User Handshake**
    
    a. Provider’s listening port (default port: 3333) receives an incoming socket connection from a User node.
    
    b. Provider receives a session request from the User node and checks if the message signature is valid. If the signature is not valid the provider returns an "Err: Failed Auth" message and closes the socket.
    
    <i>{ "method": "response.error", "params": { "message": "Failed to authenticate signature.", "timestamp": 1707379200, signature: "# string" }}</i>
    
    | Method | "response.error" | Indicates an error response to a request method. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: error message. |
    | Parameter (uint) | "timestamp" | Timestamp of message. |
    | Parameter (string) | "signature" | Provider signed message.<br>{provider + user + timestamp} |
   
    c. Provider checks the current workload and system constraints to determine if it can service the request. If the provider cannot service the request it returns an "Err: Provider at capacity" message and closes the socket.

    <i>{ "method": "response.error", "params": { "message": "Provider at capacity.", "timestamp": 1707379200, signature: "# string" }}</i>
   
    | Method | "response.error" | Indicates an error response to a request method. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: error message. |
    | Parameter (uint) | "timestamp" | Timestamp of message. |
    | Parameter (string) | "signature" | Provider signed message. <br>{provider + user + timestamp} |
   
    d. Provider sends the User node an accept message which contains the provider’s encryption key. Provider node starts a new session thread with the User node socket and stores the User node’s public key in a thread variable for encrypting the inference responses.
   
    <i>{ "method": "response.success", "params": { "message": "020bdffbf477c8f03affb 9ac006eb2c682a75cd017c9723d028733e083a82d5273", "timestamp": 1707379200, signature: "# string" }}</i>
   
    | Method | "response.success" | Indicates a success or true response to a request method. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: public key. |
    | Parameter (uint) | "timestamp" | Timestamp of message. |
    | Parameter (string) | "signature" | Provider signed message.<br>{provider + user + timestamp} |
   
2. **User Session**
   
    a. Provider receives a prompt message from the User node and checks to see if the session is still open. If the session is closed or doesn’t exist it returns an "Err: Closed Session" message and closes the socket.
   
    <i>{ "method": "response.error", "params": { "message": "Session is closed.", "timestamp": 1707379200, signature: "# string" }}</i>
    
    | Method | "response.error" | Indicates an error response to a request method. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: error message. |
    | Parameter (uint) | "timestamp" | Timestamp of message. |
    | Parameter (string) | "signature" | Provider signed message.<br>{provider + user + timestamp} |
   
    b. Provider checks to see if the prompt puts the User’s session over its spend limit. If the session is over its spend limit the Provider node returns an "Err: Over spend limit." message but does not close the session.

    <i>{ "method": "response.error", "params": { "message": "Over spend limit.", "timestamp": 1707379200, signature: "# string" }}</i>
    
    | Method | "response.error" | Indicates an error response to a request method. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: error message. |
    | Parameter (uint) | "timestamp" | Timestamp of message. |
    | Parameter (string) | "signature" | Provider signed message.<br>{provider + user + timestamp} |
   
    c. Provider decrypts prompt message and sends prompt to AI engine for processing.

    d. Provider sends inference back to User Node and updates internal session tracking.
   
    { "method": "response.inference", "params": { "message": "Encrypted inference string", "timestamp": 1707379200, signature: "# string"}}
   
    | Method | "response.inference" | Used to send inference from provider node to User node. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: inference encrypted using the User’s public key. |
    | Parameter (uint) | "timestamp" | Timestamp of request. |
    | Parameter (string) | "signature" | Provider signed message.<br>{provider + user + timestamp} |
   
3. **Session Closeout**
    a. Provider receives session close request from User node.
    b. Provider compiles and sends a session report to the User node.

    <i>{ "method": "response.report", "params": { "message": "Report string", "timestamp": 1707379200, signature: "# string"}}</i>
    
    | Method | "response.report" | Used to send a close out report from a Provider node to a User node. |
    |---|---|---|
    | Parameter (string) | "message" | Response payload: session report. |
    | Parameter (uint) | "timestamp" | Timestamp of request. |
    | Parameter (string) | "signature" | Provider signed message. {report} |
   
    The session report will be a summary of the User node session socket activity.<br><br>
    <i>{ "sessionid": "0x…", "start": 1707379200, "end": 1707456732, "prompts": 3, "tokens": 1650, "reqs": [ { "req": 1707379250, "res": 1707379425, "toks": 620 }, { "req": 1707399127, "res": 1707400563, "toks": 426 }, { "req": 1707450734, "res": 1707455732, "toks": 604} ] }</i>
    
    ##### Report Variables

    | Name | Type | Description |
    |---|---|---|
    | "sessionid" | string | User node’s session ID. |
    | "start" | uint | Timestamp marking start of the session socket. |
    | "end" | uint | Timestamp marking end of the session socket. |
    | "prompts" | uint | Number of prompts sent by the User node and received by the Provider node. |
    | "tokens" | uint | Number of language tokens sent from the Provider node to the User node. |
    | "reqs" | array | An array of req objects. |
   
    ##### Req Object Variables
   
    | Name | Type | Description |
    |---|---|---|
    | "req" | unit | Timestamp of prompt request message. |
    | "res" | uint | Timestamp of inference response message. |
    | "toks" | uint | Number of language tokens provided in the inference response. |
   
    c. Provider closes the socket and purges session data from memory.

#### Provider Node to Blockchain

1. **Check Session State**

Provider uses Session ID provided by the User node to check session status in the on-chain Session Router Contract. \

3. **Check Session Balance**

Provider uses Session ID provided by the User node to check session balance in the on-chain Session Router Contract. \

4. **Check User Report**

This method is used if the Provider node wishes to contest a user report. \

5. **Claim Funds**

Provider claims MOR tokens that have been allocated to its wallet address.

### User Node Communication

#### User Node to Provider Node

1. **Provider / User Handshake** <br><br>
When a User node first establishes a tcp/ip socket connection with a provider node it will initiate the protocol handshake.
    a. User node sends the Provider node a session request.

    <i>{ "method": "session.request", "params": { "provider": "0x…", "user": "0x…", "timestamp": 1707379200, "spend": 0.032, "key": "020bdffbf477c8f03affb9 ac006eb2c682a75cd017c9723d028733e083a82d5273", signature: "# string"}}</i>

    | Method | "session.request" | Used to request permission from provider node to establish a new session socket. |
    |---|---|---|
    | Parameter (string) | "provider" | Provider node wallet address. |
    | Parameter (string) | "user" | User node wallet address. |
    | Parameter (uint) | "timestamp" | Timestamp of request. |
    | Parameter (uint) | "spend’ | Max budget for proposed session. (MOR) |
    | Parameter (string) | "key" | User node’s public encryption key. |
    | Parameter (string) | "signature" | User signed message.<br>{provider + user + timestamp} |

    b. If the session request is accepted the User node will receive an encryption public key back from the Provider node.

    c. The User node submits an on-chain transaction to the Session Router Contract to create a new session. If successful the User node will receive a new Session ID back from the contract method.

3. **User Session**
   
    a. User node sends an encrypted prompt message to the Provider node.
   
    <i>{ "method": "session.prompt", "params": { "sessionid": "0x…", "message": "Encrypted user prompt", "timestamp": 1707379200, signature: "# string"}}</i>

   | Method | "session.prompt" | Used to send a user prompt to the Provider node for processing. |
   |---|---|---|
   | Parameter (string) | "sessionid" | Active session Id. |
   | Parameter (string) | "message" | Request payload: user prompt encrypted using the Provider’s public key. |
   | Parameter (uint) | "timestamp" | Timestamp of prompt. |
   | Parameter (string) | "signature" | User signed message.<br>{provider + user + timestamp} |

    b. User node receives inference response back from Provider node.

4. **Session Closeout**
   
    a. User node requests a close out report from Provider node.
   
    <i>{ "method": "session.close", "params": { "sessionid": "0x…", "timestamp": 1707379200, signature: "# string"}}</i>

   | Method | "session.close" | Used to request a closeout report from the Provider node. |
   |---|---|---|
   | Parameter (string) | "sessionid" | Active session Id. |
   | Parameter (uint) | "timestamp" | Timestamp of request. |
   | Parameter (string) | "signature" | User signed message.<br>{provider + user + timestamp} |

    b. User node receives and audits the closeout report sent from Provider node.

    c. If the User node does not agree with the Provider node’s report it can compile and submit its own report to close the session and reclaim its stake.

#### User Node to Blockchain

1. **Get a list of models.**

   The User node uses this process to retrieve and cache a list of registered models.
   
2. **Get a list of providers and bids for the selected model.**
  
   Once a model is selected by the end user. The User node retrieves a list of providers and bids for the selected model.<br><br>
   The User node then sorts the list of providers by a combination of their endpoint latency, bid, and reputation. (reputation is derived from session closeout data).
   
3. **Create new session transaction**
  
   Once a provider accepts the User node session request, the User node creates an on-chain transaction to open a new session in the Session Router smart contract.

4. **Close session transaction**

   When the User node is done with the session socket. The User node will request a closeout report from the Provider node. If the User node agrees with the received closeout report then the User node will use it in its closeout transaction.<br><br>If the User node does not agree with the received closeout report from the Provider node the User node will submit its own report in the closeout transaction.

## Conclusion

The Morpheus Lumerin Model is a simple yet dynamic architecture that allows for maximum scalability and decentralization. Key attack vectors are mitigated using a combination of staking and reputation mechanics.<br><br>The on-chain architecture can initially be deployed on any EVM chain. Eventually the solidity code will be ported into other ecosystems for greater reach.

#### References

1. [https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/Distribution.md](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/Distribution.md)

2. [https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L1Sender.md](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L1Sender.md)

3. [https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L2MessageReceiver.md](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L2MessageReceiver.md)

4. [https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/MOR.md](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/MOR.md)

5. [https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L2TokenReceiver.md](https://github.com/MorpheusAIs/Docs/blob/main/Smart%20Contracts/L2TokenReceiver.md)

6. [https://platform.openai.com/docs/api-reference/introduction](https://platform.openai.com/docs/api-reference/introduction)
