# Frequently Asked Questions about Morpheus Compute

## Testnet

### What do compute providers do?
The main role of compute providers is to provide computation, a vital AI resource for inference, in decentralized way.

### Is the Compute testnet launched?
Yes, it started in June 2024 on Arbitrum Sepolia.

### What is the purpose of the Compute testnet?
The Compute testnet aims to test the network’s infrastructure under various conditions, validate the performance and reliability of compute providers, ensure all compensation and incentive systems are working correctly, and ensure the proper functioning of the Compute Contract and proxy Router.

### At what stage is the compute testnet right now? What’s the status?
The developers and community are actively working to bring the documentation up to speed so everyone with appropriate hardware can participate. The backend server and front end UI are functional and the pieces are in place. The testnet grows as more providers sign on by providing their private compute AI engines. There are already some hosted models running now that consumers running the UI or API can connect to by staking and using Sepoia Testnet tokens (saMOR and saETH which you can get via https://morfaucet.xyz/ and the Arbitrum Sapolia faucet links) to purchase bids and run inference.

### How long will the Compute testnet last?
As long as necessary to get a robust testnet ecosystem in place where primary aspects of the provider and consumer software are running as expected. Some version of the testnet will likely live on in the future after mainnet to test new features.

### Are there any restrictions (like whitelists) to join testnet?
As of right now, anyone can connect to the smart contract running on Arbiturm Sepolia testnet which is currently 0x8e19288d908b2d9f8d7c539c74c899808ac3de45.  
More information are in [Morpheus-Lumerin-Node repository.](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)

### I have no technical knowledge, how can I participate? What steps do I need to take to become a Compute provider?
At this stage, you may be better off waiting until the developers and early adopter technicians have worked through the early technical challenges to provide you a better user experience in the future that requires minimal technical know-how.

### Can I be a compute provider in the testnet from my laptop?
In the beginning, most likely not. Being a computer provider implies that you have a significant investment in hardware, GPU and development for your own models that you want to distribute on Morpheus.  If you have that, then you probably have the technical know-how to run the proxy-router.

### Can users of Smart Agents participate in the Compute testnet or is it only for Compute providers?
In the future, the various smart agents and chat UI will interact with decentralized compute and there will likely be options to connect to mainnet or testnet compute.

### Will there be any rewards for participating in the Compute testnet?
No, participants of the Compute testnet are not entitled to any rewards or compensation.

## Mainnet
### What will the process look like when the compute goes live? / Will I need to just download and install the node and click one button to share compute power of my PC?
In the beginning, compute will likely be provided by serious hardware providers with dedicated servers. Over time, as staking and reputation systems develop to ensure quality of service, anyone will ideally be able to download the software and both consume and provide models which are compatible with their computer resources. The client will be an all-in-one UI for providing and consuming models via decentralized nodes communicating peer-to-peer offering up and consuming bids for compute models.

### I want to consume Morpheus` decentralized compute in the future. What do I need for this?
In the future, the Morpheus Ai tools will have both local and remote options for interacting with your own locally hosted models or connecting to the decentralized network of nodes via peer to peer routing using reputation and staking which involves offers and bids for compute of various models. The providers will be rewarded for their contributions by the network and the consumers will lock their MOR to open a session with the providers, unlocking their MOR at the end of the session.

### How will compute providers be rewarded?
Morpheus network pays compute providers only for compute actually provided through a competitive bid process.

### How much can I earn as compute provider?
Depends on what types of models you offer and how many concurrent sessions your hardware can serve.

### Is Morpheus Compute Node the same node other blockchains have?
No, Morpheus node is not that type of node that runs blockchain and processes transactions.

### When will the Compute mainnet be launched?
Compute mainnet is estimated to launch in Q3 2024 once the testnet audits are fully cleared and core node software is ready for a stable production deployment.

### What is the whitelist in mainnet for?
The whitelist is a temporary mechanism to ensure good actors seed the provider pool. Once seeded the whitelist will be removed and the MOR stake mechanism will take over to ensure economic alignment.

### How can I get on the whitelist?
Post an introduction message in the Compute provider [discord channel](https://discord.com/channels/1151741790408429580/1167520834139738289) and you will be connected with devs working on compute.

### What MOR stake is required to get whitelisted?
Whitelisting is not based on stake amount. Whitelisting is based on known good actors with verifiable stable compute. Once the whitelist is turned off, the MOR stake requirement will be set at an appropriate level chosen by members of the Morpheus community to ensure economic alignment by providers.

### Do I obtain higher credibility as a Compute provider by holding more MOR than needed to get whitelisted?
Holding MOR is not required to be whitelisted. Although, staked MOR may be included in the reputation algorithm.

### Is the Compute provider stake locked, or can it be slashed?
Compute provider stake is only locked. There are no current plans for a slashing mechanism anywhere in the Morpheus ecosystem.

### What is a reputation system?
The reputation system is an on-chain algorithm used for sorting providers according to user needs.

### How does the reputation system work?
The reputation system will take into account metrics such as response performance, connection speed/lag, number of completed sessions, number of canceled sessions, total earnings, and marketplace bid amounts. These metrics will be used to sort and recommend providers to users when a new session is created.

### What penalties are in place for bad actors?
Bad actor penalties are currently constrained to degraded reputation scores.

### Will the launch of the Compute mainnet lead to a large influx of tokens into the market and a possible dump?
No, that won't happen. Since the budget is 1% of the previous day's Сompute contract balance.

### What is the Compute Contract?
Compute Contract is the smart contract that has a MOR address, receives all emitted MOR allocated to the Compute bucket, tracks amounts owed to eligible Providers, and pays MOR to eligible Providers when Providers request payment.

### What is the Compute Proxy Router?
Compute Route is the software application that has a MOR address and negotiates the 2-sided market between Users and Providers. The Router registers and tracks Provider addresses and bids, processes Requests from Users and instructs the Compute Contract to credit eligible Providers for payment in MOR.

### I have a powerful gaming computer, can I be a Compute provider?
Yes, absolutely, but keep in mind if you are providing compute it is important to have your system online and stable otherwise you will hurt your reputation. 

### What is the minimum and recommended hardware configuration to be a Compute provider?
Hardware recommendations greatly depend on the models you are offering. Hardware benchmarking reports would be the best source of information for this. 

### How can I choose which model to serve, and which is optimal for my hardware configuration?
If you are unsure about your system performance with different models it would be best to download and run them locally for a while to see what your local user experience is like. This experience will be fairly close to the same experience remote users will have. 

### I plan to buy a GPU, please advise one the best suited for serving Smart Agents?
Morpheus Smart Agents will be incredibly light weight and not need specialized hardware, but once again this greatly depends on the tasks that the agent is asked to accomplish.

### Can I provide computation with ASICs?
No

### What steps do I need to take to become a Compute provider?
1. Run a Morpheus node on a computer and make sure your ports are configured for inbound traffic. 
2. Download and configure the model you want to provide
3. Register as a provider in the on-chain provider registry.
4. Claim rewards periodically from the session router contract. 

### [Travis Lake's document](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Lake%20Travis%20Decentralized%20AI%20Inference%20System.md) states: “Model and Agent builders would receive a fraction of the compute bucket emissions and rewards proportional to usage as well as payment from direct usage.” Where will these rewards come from?
The session router contract disperses these funds to compute providers. 

### The whitepaper mentions Filecoin as storage. Is that information outdated?
Filecoin storage has not been implemented or planned currently. If community members wish to expand the system and implement it they are welcome to do so. 

### Can I train LLM models with Morpheus Compute?
Not for v1, but we are hoping to achieve this with key partnerships.

### Is it correct to assume that Compute providers will not only need to run model inference but also the agent code itself?
Agent code can run from anywhere as long as it has access to the resources it needs to achieve its objectives.

### Where can I get more information?
- [Yellowstone Compute Model](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Yellowstone%20Compute%20Model.md)
- [Lake Travis - Decentralized AI Inference System](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Lake%20Travis%20Decentralized%20AI%20Inference%20System.md)
- [Morpheus Lumerin Model document](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Morpheus%20Lumerin%20Model.md)
- [Compute Node Repository](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)

### Where can I get support and ask questions?
Community members would love to assist you in [**#tech-support**](https://discord.com/channels/1151741790408429580/1183666837460897832) discord channel.

### If you did not find the answer to your question, you can add it through this [form.](https://forms.gle/6yt5ps3kAfUfkF4N8) 

> [!WARNING]  
> Beware of scams, anyone who message you with proposal to help is likely scammer. 
