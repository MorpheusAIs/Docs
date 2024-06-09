![Image1forYellowstone](https://github.com/MorpheusAIs/Morpheus/assets/1563345/80a6c1cf-fe52-42ba-bfd4-91d9faf67f07)

# Morpheus “Yellowstone” Compute Model
### Erik Voorhees
### January 3rd 2024

> [!Note]
> The content presented in this document were supplemented and expanded in the [Lake Travis Decentralized AI Inference System](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Lake%20Travis%20Decentralized%20AI%20Inference%20System.md) document.

## Summary
In the Yellowstone Compute Model, the Morpheus network pays Providers only for Compute actually provided through a competitive bid process, and allocates the scarce production of IPS (inferences/seconds) pro rata to MOR token holders based on balance, rather than on payment. This drastically improves UX while minimizing Sybil vulnerability. Yellowstone also imbues the important metrics of time and a Pass/Fail test to ensure Providers are adequately prompt and accurate. Yellowstone preserves privacy by never sending prompts or results through the Router, and minimizes blockchain transactions to permit a large scale of operation. Through this model, MOR achieves fundamental value as it enables perpetual (though not unlimited) access to permissionless compute, without requiring transactions per inference. 

This model replaced original version of the “Compute Proof, Registration & Reward” section of the [Morpheus whitepaper](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md)

## Background
Morpheus uses tokenomics to incentivize sufficient and scalable compute as a resource for the purpose of decentralized and permissionless generative AI. In its original conception, Morpheus issued 24% of MOR emissions to Compute Providers directly, pro rata depending on the inference requests received, and it prioritized inference requests to those providers based on how much MOR they held. 

### From the original white paper:
`“The pro-rata MOR transaction fees burned by each Compute Provider serves as proof of the Compute Providers status and earns a proportion of the MOR tokens each day.`
 
`For example, if there are 100 Compute Providers on day 1 when the network launches, then each one gets a pro-rata reward based on the amount of MOR they have burned via fees. In this case, presuming each of the 100 compute providers burned 100 MOR, then 1% of the 3,456 MOR tokens each day = 34.56 MOR.”`

### There are three major issues with this approach:
1) It requires users to pay per-inference transaction fees. Even if low, this is substantial friction and will cause poor UX and an ever-present inferiority to OpenAI’s UX. It also requires at least one blockchain transaction per inference, which is probably not scalable even on L2s. Each inference event is extremely low cost, and if a blockchain transaction was required, the economics would be infeasible. 
2) This model is substantially exploitable because expected revenue for compute providers is far higher than actual compute costs. An adversary could thus flood spam inference requests to his own Compute Provider node, and earn a relatively large portion of MOR tokens each day, even though no economic value was provided to anyone. Likely, it would lead to large amounts of early (unused) compute, which disappears once the huge revenue opportunity dissipates, and the MOR spent on that early subsidy would be wasted/lost.  
3) If inference requests are prioritized based on the MOR amount held by Providers, then the performance of those providers (response time) and the cost of their inference processing are ignored by the network, and it is precisely these two factors which the network should attempt to optimize (response time and compute cost should be ideally driven as low as possible). If the top MOR-holding provider was running a $200 GPU from his college days, inference performance for many users would be extremely poor. Priority should be based on bid price and performance, not MOR holding.

Below is proposed the "Yellowstone Model" which modifies the Morpheus tokenomics for compute provision to address the above issues. This model works regardless of what portion of emissions are allocated to compute, and we’ll assume the status quo of 24% of total emissions. 

### The goals are:
1) Enable users to not pay per inference (ideally, to not pay at all).
2) Achieve efficient, scalable, and sustainable provision of permissionless compute resource without overpaying for it.
3) Incentivize low response time and cost competition among compute Providers.
4) Minimize number of blockchain transactions (whether L2 or otherwise).
5) Demonstrate an economically sound fundamental demand for MOR. 

## Yellowstone Model
Four Components Involved:

### Users
* Have Queries
* Want fast/accurate inference for free and without censorship/surveillance

### Providers
* Have compute
* Want money (MOR)

### Router 
* High throughput processing engine
* Decentralized

### Compute Contract
* Permissionless smart contract which receives emissions of MOR, tracks credits and debits to Providers, and pays Providers when called.

## Standard Weights and Measures

There is an atomic unit of inferences in AI, measured in inferences per second (IPS). This can be conceptually compared to wei on the blockchain. Inferences are used to define rates in the Yellowstone router. The weight of a single Morpheus AI unit is therefore an inference. Depending on the type of request, this can be applied to any compute task.  

As AI and blockchain merge commonalities, Morpheus looks to provide an open-source standard of measurements in order to clarify terminology used by both AI and Blockchain. 


There are two types of prompts, defined by the size of response returned by a model:  

**Determined Length Prompts**, where the response considers the length of the response to return. Examples of this are:
- Chat/Image creation
- Disease diagnosis
- Object recognition
- Fraud detection


**Undetermined Length Prompts** require resources to respond that are only knowable after the response is created. Example prompts of non deterministic responses are:
- Sing a sonata about spaghetti.
- Generate a Happy Birthday video
- Combine model X with model Y
- Slice a 3D model into an .stl file

Yellowstone focuses on Determined Length Prompts.  The router described will be constructed in a fashion to handle undetermined prompts in the future, but not to service them today. To accomplish this we use a standardized measurement of Decentralized AI.

## DeAI Rates

### Expressions of inference/second:

| Type | Response | Rate |
|------|----------|------|
| Determined | Language | Inferred Tokens per second (TPS)|
| Undetermined - media | Audio | Inferred Samples per second (ISPS) |
| Undetermined - media | Video | Inferred Frames per second (IFPS) |
| Undetermined - future tech | Unknown Future Format | NA |

The first measure of inference for the Yellowstone router will be TPS. Other inference formats to follow.

### Time

The block time for inference is 12 seconds, meaning a block of inference transactions is published and accounted for 5 times per minute.  

## Definitions

**“Users”**: defined as any entity that has a MOR address and sends Requests to the Router, using the compute. This can be a specific individual person sending Requests from a Morpheus desktop node, or it could be a bot, or it could be a company or 3rd party website which interacts with the Morpheus network on behalf of its end-users (such 3rd-party “end-users” in this case are meaningless to the Morpheus network and should not be confused with Users as defined above). 

**“Providers”**: defined as any entity, running a node that provides compute resources, has a MOR address and offers IPS bids through the Router. When a Provider wins the bid from the Router, Provider provides the compute resource (GPUs, etc.) for the User's requested AI model to the User. 

**“Router”**:  defined as a software application that has a MOR address and negotiates the 2-sided market between Users and Providers. The Router registers and tracks Provider addresses and bids, processes Requests from Users, records [milliseconds] and Pass/Fail tests of processed Requests, and instructs the Compute Contract to credit eligible Providers for payment in MOR. The Router never sends or receives MOR transactions (nor transactions on any blockchain). The Router never sees the content of a Request, nor the response. 

**“Compute Contract”**: defined as a smart contract that has a MOR address, receives all emitted MOR allocated to the Compute bucket, tracks amounts owed to eligible Providers, and pays MOR to eligible Providers when Providers request payment.

**"Inferences per second" (IPS)**: is an atomic unit of inferences in AI. Inferences are used to define rates in the Yellowstone router. The weight of a single Morpheus AI unit is therefore an inference.

**“IPSMax”**: refers to a maximum number of IPS accepted for payment by the Router. 

**“RFC”**: stands for “Request for Compute.” A user sends an RFC to the Router, and specifies the [LLM] User desires access to as well as the [IPSMax], which is a cap on the acceptable IPS in response. User will want to cap this because higher numbers = longer wait times for answers, and count more toward [UserMax], which is limited each day. 

### Compute Bootstrapping Incentive

For the first year following the Capital Contract's bootstrapping period, the top 100 Compute providers may be entitled to a pro rata amount of 2.4% of MOR emissions.  This is calculated by the routers and accounted for in the compute contract.

## Workflow
1) Users, Providers, and Router all create MOR pub keys (this is their identity, all messages signed as such). 
2) If User hodls any balance of MOR, User may submit a signed Request for Compute “RFC” message to the Router. User specifies [LLM] and [IPSMax].
3) Router prioritizes RFCs based on User’s MOR balance (solves sybil issue)
4) Router selects Provider that supports the [LLM], prioritized based on lowest Bid per IPS in MOR. 
5) Router sends liveness check to Provider. If Pass, then
6) Router connects User to the Provider over TCP/IP
7) User sends Query ([LLM],[prompt]) to Provider 
8) Provider computes Query, sends Result to User
9) User reports success metrics to Router (such as IPSs received or time taken, or pass/fail vote)
10) Router instructs Compute Contract to credit Provider with MOR if job was completed satisfactorily.
11) (Some time later) Provider requests payment of MOR from Compute Contract and Compute Contract sends MOR payment if valid (first blockchain TX so far, can be batched).

![ComputeContractImage2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/e66ea20c-9851-4f9e-9caa-66c6d798c462)

## Outcome
* User received fast Result for her Query, and paid nothing (this will lead to amazing UX and thus adoption). **Solves Goal 1.**
* Compute Contract paid for Compute through a competitive bidding process, and a check for quality/satisfaction from the User who ordered it. **Solves Goal 2.**
* Provider received money (MOR) from Compute Contract so long as response was fast enough. Provider received exactly what he asked for to provide the compute. If his ask is too high, others will bid lower, thus the system is efficient and will drive down Provider prices toward the cost of base electricity.  **Solves Goal 3**
* Number of on-chain transactions was minimized (many Queries can flow with few on-chain TXs). **Solves Goal 4**
* The ability to get fast, free compute drives the demand for MOR tokens to be held by Users. **Solves Goal 5**
* Steps 6 & 7 provide reasonable privacy (Query never touches the Router, nor does Result). Providers are selected somewhat randomly, and never know identity of User other than IP address. Better privacy can be later achieved with TOR and/or FHE
* MOR balance was reduced from Compute Contract. Contract will be solvent so long as MOR paid < MOR earned per period from emissions.
* If User sends an RFC which exceeds User’s UserMax, the Router will reject the request.

—-------------

## Compute Budget
The Morpheus network needs to determine how much MOR it is willing to spend on compute in a given period (such as each day), this is referred to as the Compute Budget. Each period, up to this amount of MOR may be spent by the Compute Contract. This number multiplied by the MOR price gives us a dollar budget for acquisition of Compute each day. 

Compute Budget = 1% of Compute Contract MOR balance at end of the prior day.

* Because the budget is a fixed percent of the pool, it can never run out (it can only decay asymptotically).
* Further, because under no realistic circumstances would every single MOR utilize its max capacity each day, this means in reality the budget will never hit its limit of 1% of the prior day’s Compute Contract balance. This holds true so long as even a single MOR sits idly in a wallet or exchange.

## AccessRate
The Morpheus network allocates the scarce resource of IPS production through the concept of the “AccessRate”. The AccessRate determines how many IPS each MOR token can access per day. Unused access does not accrue. AccessRate is always displayed as a quantity of IPS per 1 MOR token (such as 1 MOR = 15,000 IPS). AccessRate is determined in part by MaxIPS, which quantifies the maximum number of IPS the network can purchase per day.

**MaxIPS** = ((MOR Compute Budget * MOR Price) / IPS Price) * 1000  
**AccessRate** = (1/MOR Supply) * MaxIPS   
**UserMax** = AccessRate * User MOR balance

### Example Assumptions: 
**MOR Supply** = 10,000,000 MOR tokens  
**Prior Day Compute Contract Balance** = 300,000  
**MOR Compute Budget** = 3,000 MOR tokens per day (1% of above)  
**MOR Price** = $20  
**IPS Price** = $0.002 per 1000 IPS  
**User Balance** = 5 MOR tokens

### Example Result:
**MaxIPS** = 30,000,000,000 IPS (this is the maximum IPS the network can buy/produce each day)  
**AccessRate** = 3,000 (thus each MOR token grants access to 3,000 IPS per day)  
**UserMax** = 15,000 (a User with 5 MOR tokens can access up to 15,000 IPS per day)


* Each period (each day), Morpheus as a network has enough funds to buy X number of IPS from compute Providers. X is a function of the amount of MOR the Compute Contract is willing to spend (the “Compute Budget”) multiplied by the current MOR price divided by the market rate for IPS. 
* If the Compute Budget is 3,000 MOR, and each is worth $20, then the network can buy (produce) up to $60,000 of IPS that day. If the going rate for 1,000 IPS is $0.002, then the network can buy up to 30 billion IPS (30m x 1000 IPS). 
* That potential production of 30 billion IPS is allocated by MOR balance, pro rata. Assume there are 10,000,000 MOR in existence. A user with 500 MOR tokens (0.005% of total) could freely access up to 1.5m IPS that day. 
* So long as Compute Budget is set as a % of the Compute Contract balance, the Compute Contract cannot run out of MOR (it can only asymptotically decay).  
* In reality, most MOR tokens will sit in wallets and exchanges, and only a fraction will be used to demand the IPS production.

## Notes
* Fundamental demand for MOR comes from Users who wish to have access to generative AI and other forms of compute on the Morpheus network “for free” on an on-demand basis. The more MOR they hold, they more AI they can obtain every day. 
 
* Provider’s hardware type is irrelevant to the network, so long as they satisfy the User’s pass/fail test. Any Provider bidding on more Queries than they can efficiently process will be penalized by failing this test (they won't be paid).

* The above model importantly pays Providers ONLY when there is demand for their compute. This prevents the situation where large portions of MOR are emitted prematurely when the network doesn’t need it. 

* Providers should need to prove they have a given LLM, by signing hash of LLM model with their key. This doesn’t prove they used it, but it proves they downloaded and installed it, which represents work, thus preventing some forms of sybil-sensitive fraud. If Providers provide garbage results to User, User can send [Fail] along with [milliseconds] back to Router, and Provider won’t be credited for that compute. Morpheus doesn’t need all answers to be perfect… it only needs enough answers to be good enough, relative to competing alternatives. 

* Sybil attacks of flooding the network with RFCs is prevented by the AccessRate. The “cost” of sending and RFC is the cost of acquiring a MOR token divided by the number of RFCs submitted on its behalf. Cost is thus never zero, and yet a user won’t feel a loss each time an RFC is made. It will feel cheap to all real users, and prohibitively expensive to spammers. In fact, like with Bitcoin mining fees, Morpheus can consider all RFC’s valid and doesn’t care to decipher between spam and “legitimate.” In all cases, a User held a sufficient amount of MOR to make the request in the first place, and thus had the right to do so, regardless of content.  

* Pass/Fail is determined by User, and polices quality to some degree. User conveys Pass/Fail result alongside [milliseconds] back to Router. If Fail, either no reward or penalty point (TBD). There is no incentive to falsely Fail a Provider (no monetary incentive in doing so). This mechanism prevents Providers from sending fast but useless Results.
Consider: perhaps No Reward occurs on Fail only if User MOR > Provider MOR. Otherwise, just a negative point which Router can use in its privatization logic.

* All four parties (User, Provider, Router, and Compute Contract) have unique MOR address as their identity. All messages between the parties require signatures (but most don’t require blockchain txs)

* Providers must have non-zero balance to discourage Sybil attack from Provider side.

* If [milliseconds] criteria is higher, network will be generally faster, but discourages smaller Providers

* There is a disincentive to provide slow Results (no revenue after computation)
