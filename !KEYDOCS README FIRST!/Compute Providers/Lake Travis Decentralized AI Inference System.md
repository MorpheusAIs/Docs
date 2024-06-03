# Lake Travis Decentralized AI Inference System Proposal: MRC25

### Abstract

In the evolving landscape of decentralized AI, the "Lake Travis Decentralized AI Inference System" introduces significant enhancements to the Morpheus "Yellowstone" Compute Model [1]. This proposal iterates on Erik Voorhees' pioneering work, aiming to refine the distribution of model weights, metering structure and compute incentivization mechanisms on the Morpheus decentralized AI network. This work as well as Voorhees' work are continuations from the original Morpheus white paper [2]. The enhancements detailed below are designed to bolster transparency, efficiency, and security within the network, promoting a more competitive and user-centric ecosystem.

The system known as the Lake Travis Decentralized AI Inference System will be referred to as the "Lake Travis System.”


### Summary of Enhancements

1. **Decentralized Model Registry**:
	- A pivotal feature of the Lake Travis proposal is the establishment of a decentralized model registry. Compute providers will download models from this registry to host model weights and definitions. This not only facilitates compute consumption but also promotes a distributed file-sharing network by allowing providers to act as nodes in an InterPlanetary File System (IPFS) [3], enhancing the ecosystem's robustness and decentralization.
	- Entities like HuggingFace [4] have made significant strides in creating an open model registry accessible to everyone. However, for Morpheus, there's a crucial need for a decentralized model registry. This approach safeguards against adversarial actions that could compromise a vital component of unrestricted AI, ensuring robustness and continuity in the ecosystem.
	- Compute providers provide both inference as well as storage for the wider network.
	- Each time a model or agent is uploaded it must be named with a globally unique name on the Morpheus network. The upload contains all assets necessary (e.g., model weights, definition) to load and invoke a model, given that the compute provider has the relevant hardware and software dependencies. This allows model or agent builders to receive credit regardless of which compute provider downloads and serves up their model or agent. Model variation uploads may be tagged much like Docker [8] images.

2. **Router Transparency and Model Popularity Tracking**:
	- The Lake Travis System borrows the concept of an on-chain router. However, sessions are established off-chain to ensure users' computation privacy from the world. This also allows all requests and responses to operate with the lowest latency possible as they do not rely on on-chain block resolution times.
	- Lake Travis proposes that router requests publicly record, not the content, but the details of which model is being requested and the duration of session times. This critical adjustment ensures the visibility of the most sought-after models, guiding compute providers on which models to prioritize for serving and at competitive pricing offerings.
	- Lake Travis introduces a significant evolution from the Yellowstone model by transitioning the Pass/Fail metric from a user-substantiated decision to an inferred attribute, determined by data analytics rather than manual scoring. This refinement suggests that the active participation of users in scoring performance may not be necessary. Instead, Lake Travis computes analytics to ensure fidelity.  This facilitates the identification of potentially malicious actors through the detection of anomalous session durations with respect to given models or agents, ensuring a more streamlined and efficient quality control process.
	- For complete transparency, reports will be public.
    
3. **Compute Resource Utilization and Pricing**:
	- The Lake Travis system introduces a nuanced approach to measuring the use of compute resources, focusing on the session length relative to a provider's set price per unit of time. Such as MOR/hr, MOR/s, etc. Providers are encouraged to view the router's leaderboard of in-demand models to competitively select their prices and publish their measured inference per second (IPS) or tokens per second (TPS) rate. This mechanism allows users to choose providers based on minimum IPS/TPS speed requirements, ensuring flexibility and fairness.
	- Charging by session duration future-proofs the pricing mechanism:
		- Supports both predetermined (e.g., image classifier) and undetermined output length (e.g., LLM) style inferences
		- Treats the model or agent as a first class citizen. When users request a model they do so with a unique model handle. The model or agent builder is rewarded (described below) regardless of which provider fulfills user requests.
		- Agnostic of inference accelerator used, enabling for the uptake of more novel chips such as LPUs [9], TPUs [10], VPUs [11], analog coprocessors [12], all while still supporting conventional GPUs and CPUs.
		- Eliminates complexity of estimating whether a user has sufficient funds. Compute providers may list minimum connection times. When credits are insufficient and the user cannot or is unwilling to expend their MOR balance, the session can be terminated by the Router.
	
4. **Model and Agent Builder Compensation:**
	- This framework guarantees that model and agent builders can finally receive compensation for their contributions, irrespective of the compute provider that ultimately facilitates access to their innovations. Such an approach directly fosters and supports a culture of appreciation and incentives for ongoing development through the Morpheus network.
	- Model builders would receive a fraction of the compute bucket emissions and rewards proportional to usage as well as payment from direct usage.
	- Agent builders would receive emissions from the community bucket as well as payment from direct usage.

5. **Local and Decentralized AI Inference**:
	- Distinguishing between local AI inference and decentralized inference, the Lake Travis System requires that local node installations come pre-installed with trusted smart contracts. A Retrieval-Augmented Generation (RAG) system [5] will load appropriate reference contracts for custom payload generation during user requests. However, there is an even greater onus on users when engaging with third-party models developed by other smart agent and model developers, emphasizing user responsibility in a decentralized landscape. 
	    
	- All inference will occur on single system image computers (SSI). Where an SSI is one which has all storage, memory, and compute elements (i.e., CPUs and accelerators) to be treated as a single machine. Inference is not to be shared between machines.

6. **Cryptographic Transaction Security**:
	- Reinforcing security measures, all cryptographic transactions initiated by a smart agent or Large Language Model (LLM) require a signature from the user's web3 wallet. This provision ensures that agents or models do not possess private keys or the capability to sign transactions, upholding the network's integrity and users' sovereignty over their digital assets. The Lake Travis System hereby recommends all third-party developers who wish to engage with cryptographic and otherwise high value assets request user confirmation before the execution of any such operation. Preferably the design of the model or agent should preclude the ingestion or observability of any private key, password, passphrase, passcode, or any other special knowledge or object which would otherwise allow an automated system to perform an irrecoverable action.

### Goals
The goals are largely adapted from [1].
- Enable users to have a pro-rata quantity of allocated compute available to them each day before depleting their MOR holdings.
- Achieve efficient, scalable, and sustainable provision of permissionless compute resources for AI inference.
- Incentivize low response time and cost competition among compute providers. All while ensuring providers and agent developers are compensated for consumption.
- Minimize the number of blockchain transactions (whether L2 or otherwise).
- A future proof pricing structure where models and agents can have their prices reliably discovered and competed against.
- Incentivize AI model and agent developers to open source their work.
- Demonstrate an economically sound fundamental demand for MOR.

### Actors
The following is adapted from [1].
- Users / Clients
	- Have requests to be processed
	- Want AI inference for minimal cost and without censorship or surveillance
- Compute Providers
	- Have compute and storage
	- Want compensation (MOR)
- Morpheus Router
	- High throughput processing engine
	- Decentralized
	- Matches users/clients with relevant compute providers
	- Surfaces in-demand models for compute providers
	- Aids in detecting and halting bad faith activity
- Morpheus Model Registry
	- Allows any compute provider to download and serve in-demand models or agents given they have the necessary compute prerequisites
	- Allows model or agent builders to openly publish their work while receiving compensation
	- Decentralized
- Morpheus Compute Contract
	- Permissionless smart contract which receives emissions of MOR, tracks credits and debits to Providers and Model / Agent Builders, and pays Providers and Model / Agent Builders

### Workflow
This is adapted heavily from [2].
1. Users, Providers, and Router all create MOR pub keys (this is their identity, all messages signed as such).
2. If User HODLs any balance of MOR, User may submit a signed Request for Compute “RFC” message to the Router. User specifies model or agent as well as any price or latency preferences.
3. Router prioritizes RFCs based on User’s MOR balance (solves Sybil issue [6])
4. Router selects the most competitively priced Provider serving up the desired model or agent. If a provider exists which meets the user's latency requirements, they will be prioritized for session creation over those who don't.
5. Router sends liveness check to Provider. If Pass, then
6. Router connects User to the Provider over a TCP/IP connection
7. User sends their inference query to Provider
8. Provider computes query, sends Result to User
9. User repeats request submission and response reception as desired...
10. Once the user has finished submitting requests, the user's client will close the session to prevent additional charges
12. Router instructs Compute Contract to credit Provider and Agent / Model Builder with MOR
13. (Some time later) Provider and Agent / Model Builder requests payment of MOR from Compute Contract and Compute Contract sends MOR payment if valid

### Outcome
- Model / Agent Builders:
	- Compensated while open-sourcing their innovations
	- Don't need to be concerned about infrastructure considerations
- Compute Providers:
	- Compensated for providing compute
	- Can download and serve any model / agent
- Users:
	- Resolve their AI requests without constraints on compute availability or overreach 
	- Receive a free daily compute budget proportional to their MOR holdings [1]
		- Can pay for additional compute beyond their budget
- Morpheus Network:
	- Rewards all actors involved in serving up decentralized compute
	- Incentivizes in-demand models / agents to have more compute availability without a central arbiter
	- Has liquidity provided to it by the TCM funding approach [7] and excess demand from Users

### Reconciling Yellowstone with Lake Travis
This proposal seeks not only to introduce these enhancements but also to seamlessly integrate them within the existing Yellowstone framework.

The Lake Travis System delineates between local AI inference — equipped with smart rank features, including trusted contracts and a RAG system [5] — and decentralized inference, where the model registry is open for any model uploads and hosting by compute providers. This distinction aims to balance the openness of decentralized innovation with the reliability and security of trusted, local computation.

### Conclusion and Contributions

The "Lake Travis Decentralized AI Inference System" directly advances upon the Morpheus "Yellowstone" Compute Model's limitations by introducing a nuanced pricing structure that measures compute resources based on session length, ensuring flexibility and fairness.

This system not only guarantees compensation for model and agent builders, fostering a supportive environment for development and contribution, but also simplifies the user experience by eliminating complex balance estimations and transitioning the pass/fail metric from user-determined to an analytics-based inference.

Additionally, Lake Travis innovates with a decentralized model registry, enabling a transparent and efficient distribution of AI models, which further enhances accessibility and incentives for model contribution within the ecosystem.

Through these strategic enhancements, Lake Travis proposes a more robust, competitive, and user-friendly ecosystem, addressing critical shortcomings of current open source and proprietary AI inference arrangements, and setting a new benchmark for decentralized AI network operations.

---
### References

[1] Voorhees, Erik, *Morpheus: “Yellowstone” Compute Model*, 2024. https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Yellowstone%20Compute%20Model.md#workflow

[2] Morpheus, Trinity, and Neo, *Morpheus: A Network For Powering Smart Agents*, Earth, 2023. https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md

[3] J. Benet, *"IPFS - Content Addressed, Versioned, P2P File System,"* https://doi.org/10.48550/arXiv.1407.3561, arXiv:1407.3561 [cs.NI], [July 2014]

[4] T. Wolf, L. Debut, V. Sanh, et al., "Transformers: State-of-the-Art Natural Language Processing," Oct. 2019. [Online]. Available: [https://arxiv.org/pdf/1910.03771.pdf](https://arxiv.org/pdf/1910.03771.pdf).

[5] P. Lewis, E. Perez, A. Piktus, et al., "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks," in _Advances in Neural Information Processing Systems (NeurIPS)_, 2020.

[6] J. R. Douceur, "The Sybil Attack," in Proc. of the 1st International Workshop on Peer-to-Peer Systems (IPTPS), Cambridge, MA, USA, Mar. 2002, pp. 251-260.

[7] Johnston, D. A., *Techno Capital Machine (TCM): Code, Capital, Community, Compute: The Open Source Revolution Starts Here* https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md

[8] Docker, Inc., 'Docker: Empowering App Development for Developers,' Docker, Accessed on [March 2024]. [Online]. Available: [https://www.docker.com/](https://www.docker.com/)

[9] Groq. (2024). Groq LPU Inference Engine Crushes First Public LLM Benchmark. Retrieved from [https://wow.groq.com/groq-lpu-inference-engine-crushes-first-public-llm-benchmark/](https://wow.groq.com/groq-lpu-inference-engine-crushes-first-public-llm-benchmark/)

[10] Jouppi, N. P., Young, C., Patil, N., & others. (2017). In-datacenter performance analysis of a Tensor Processing Unit™. arXiv preprint arXiv:1704.04760. Retrieved from [https://arxiv.org/abs/1704.04760](https://arxiv.org/abs/1704.04760)

[11] Q. Xu, V. Li, and C. D. S. Crews, "Neural Architecture Search for Intel Movidius VPU," arXiv:2305.03739 [cs.NE], May 2023. [Online]. Available: [https://doi.org/10.48550/arXiv.2305.03739](https://doi.org/10.48550/arXiv.2305.03739).

[12] "Taking powerful, efficient inference to the edge," Mythic, February, 2022. [Online]. Available: [https://mythic.ai/wp-content/uploads/2022/02/MythicWhitepaper-2019oct31.pdf](https://mythic.ai/wp-content/uploads/2022/02/MythicWhitepaper-2019oct31.pdf).

---

## Appendix

### A. Mentions

Ryan Condron regarding the router. 
Manveer regarding the decentralized model registry.

### B. Glossary

- **Agent:** Refers to a smart agent, an AI system capable of autonomous actions to achieve objectives and perform tasks.
    
- **Agent builder:** A developer who constructs smart agents, designed to perform autonomous actions and accessible from the Morpheus network.
    
- **AI (Artificial Intelligence):** A field of computer science dedicated to the creation of systems capable of performing tasks that normally require human intelligence, such as visual perception, speech recognition, decision-making, and language translation.
    
- **Compute Provider:** An entity within the Morpheus network that offers computational resources (e.g., processing power and storage) for AI inference and model hosting.
    
- **Inference:** The process of using a trained AI model to make predictions or decisions based on new, unseen data.
    
- **IPS (Inferences Per Second):** A measure of the performance capacity of a system, indicating the number of inference operations it can perform in one second.
    
- **LLM (Large Language Model):** A type of AI model that has been trained on a vast dataset of text to understand and generate human-like text based on the input it receives.
    
- **Model:** In the context of AI, a model is a mathematical representation of what an AI system has learned from the training data. It is used to make predictions or decisions without being explicitly programmed to perform the task.
    
- **Model builder:** A developer who creates and trains AI models, potentially contributing them to the Morpheus network.
    
- **MOR:** The native cryptocurrency or token utilized within the Morpheus network, used for transactions, rewards, and accessing compute resources.
    
- **Morpheus:** A decentralized network designed for powering smart agents and AI inference, facilitating permissionless access to compute resources.
    
- **Predetermined output length:** Refers to AI inferences where the output length is known ahead of time, typically based on the model's design. Examples include classification models that output a fixed set of categories.
    
- **Provider:** See "Compute Provider."
    
- **RFC (Request for Compute):** A message initiated by a user within the Morpheus network to request AI inference services, specifying the model or agent as well as any price or latency preferences. This results in the Router 

- **Router:** A high-throughput processing engine within the Morpheus decentralized AI network. It operates as a decentralized entity responsible for matching users or clients with the most suitable compute providers based on the requested AI inference services. The router plays a critical role in maintaining network efficiency and transparency, leveraging its capabilities to surface in-demand models to providers and ensuring the equitable distribution of computational tasks. The router's functions include prioritizing requests based on users' MOR balance to address potential Sybil attacks, performing liveness checks on compute providers, and facilitating the direct TCP/IP connection between users and providers for session initiation. Additionally, the router records the details of model requests and session durations (without revealing the content of computations) to provide insights into model popularity and guide compute providers on which models to prioritize, enhancing the network's responsiveness and competitive pricing strategies.

- **TPS (Tokens Per Second):** In the context of Large Language Models (LLMs), TPS refers to the number of tokens (pieces of text) that a model can generate or process per second. This metric is used to measure the speed of LLMs in generating text-based outputs.
    
- **Training:** The process of teaching an AI model to make predictions or decisions by feeding it data and letting it learn the patterns within that data.
    
- **Undetermined output length:** Refers to AI inferences where the length of the output is not fixed or predetermined, varying based on the input or other dynamic factors. Examples include open-ended conversation models or generative text models.
    
- **User:** An individual or entity that utilizes the Morpheus network to submit AI inference requests or engage with smart agents.
