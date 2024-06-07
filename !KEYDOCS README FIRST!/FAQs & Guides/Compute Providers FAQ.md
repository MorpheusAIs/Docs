# Frequently Asked Questions about Morpheus Compute

### What do compute providers do?
The main role of compute providers is to provide a vital AI resource for inference, which is computation.

### How can I get involved with Morpheus as a computer provider? 
You can’t yet as Compute part is in active development.

### How will code providers be rewarded?
Morpheus network pays compute providers only for compute actually provided through a competitive bid process.

### Is Morpheus Compute Node the same node other blockchains have?
No, Morpheus node is not that type of node that runs blockchain and processes transactions.

### When will the Compute testnet be launched?
The first Compute testnet launched in May. Next version is scheduled to be launched in June 2024 and run through July 2024.

### What is the purpose of the Compute testnet?
The Compute testnet aims to test the network’s infrastructure under various conditions, validate the performance and reliability of compute providers, ensure all compensation and incentive systems are working correctly, and ensure the proper functioning of the Compute Contract and proxy Router.

### How long will the Compute testnet last?
The Compute testnet will last approximately 6-8 weeks but could last longer if any fixes or adjustments need to be implemented. A big dependency is on smart contract auditing turn around time and the amount of fixes that need to be addressed in each audit.

### Who can participate in the Compute testnet?
The Compute testnet will be open to select community partners initially and then open to the general public for the last couple weeks.

### Can users of Smart Agents participate in the Compute testnet or is it only for Compute providers?
Compute providers and general users are both welcome to participate although performance and reliability of the testnet providers will be highly variable.

### On which network will the Compute testnet be conducted?
The Compute testnet will be deployed and tested on Arbitrum Sepolia.

### Will there be any rewards for participating in the Compute testnet?
No, participants of the Compute testnet are not entitled to any rewards or compensation.

### When will the Compute mainnet be launched?
Compute mainnet is estimated to launch in Q3 2024 once the testnet audits are fully cleared and core node software is ready for a stable production deployment.

### What is the whitelist for?
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

### How much can I earn as a Compute provider?
Depends on what types of models you offer and how many concurrent sessions your hardware can serve.

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

### I don’t have deep technical knowledge, can I still be a Compute provider?
Yes, but you will probably need to wait for future iterations of the UI that obfuscate a lot of the technical lift.

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
- [Morpheus Lumerin Model](https://github.com/antonbosss/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Morpheus%20Lumerin%20Model.md)

### Where can I get support and ask questions?
Community members would love to assist you in [**#tech-support**](https://discord.com/channels/1151741790408429580/1183666837460897832) discord channel.

### If you did not find the answer to your question, you can add it through this [form.](https://forms.gle/6yt5ps3kAfUfkF4N8) 

> [!WARNING]  
> Beware of scams, anyone who message you with proposal to help is likely scammer. 
