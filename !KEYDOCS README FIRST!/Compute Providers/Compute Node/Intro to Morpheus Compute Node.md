# Intro to Morpheus Compute Node

## Table of Contents
1. [**Summary**](#summary)
2. [**General Structure**](#general-structure)
3. [**How does the Node Work?**](#how-does-the-node-work)
4. [**What is a subnet?**](#what-is-a-subnet)
5. [**Roles**](#roles)
6. [**What are incentives?**](#what-are-incentives)
7. [**Consumer Setup**](#consumer-setup)
8. [**Provider Setup**](#provider-setup)
9. [**Important Links**](#important-links)

---

## Summary
The Morpheus Compute Node is a vital component of the Morpheus Ecosystem. It leverages the Lumerin protocol routing pattern to establish a peer-to-peer, decentralized, and anonymous network that connects AI users with providers of AI models and agents. Specifically, it facilitates transactions between consumers (users seeking to execute LLM prompts) and compute providers (those offering the computational resources needed to process these prompts).

After a successful testnet phase, the Compute Node is set to officially launch on mainnet on November 17th 2024, marking a significant milestone for the ecosystem.

![Screenshot 2024-11-11 at 10 49 55 PM](https://github.com/user-attachments/assets/2080c13e-5b63-4577-a630-d191a07f6882)

---

## General Structure
The **Morpheus Compute Node** is designed to enable seamless interaction with distributed, decentralized LLMs on the Morpheus network through a desktop chat interface. Let's take a look at main elements of the system:

<img src="https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/blob/dev/docs/images/simple.png" width=90% height=90%>

1. **AI Models Available for Inference:**  
   Existing hosted AI models are made available for inference via the Morpheus network.
   
2. **Proxy-Router Functionality:**  
   The proxy-router communicates with the blockchain, routing prompts and inferences between providers’ models and the consumers who purchase and use these models.
   
3. **Provider Model Registration:**  
   Providers register their models by submitting bids on the blockchain, making them available for consumer use.
   
4. **Consumer Node (Client):**  
   The consumer node acts as the “client,” purchasing bids from the blockchain, sending prompts via the proxy-router, and receiving inferences back from providers' models.
    
5. **Session Setup with MOR Staking:**  
   Consumers purchase bids and stake MOR tokens to secure their session time.
   
6. **Chat Interaction Begins:**  
   Once the bid is purchased, the interaction (e.g., ChatGPT-like prompt and inference exchange) can begin, enabling a smooth user experience.  

This structure provides a robust framework for connecting AI consumers and providers within a decentralized ecosystem.

> [!NOTE]  
> - Compute contract deployed on Arbitrum blockchain.    
> - MOR and ETH on Arbitrum chains is used for staking and bidding. 

---

## How Does the Node Work?
At the simplest level, the compute node employs a **“proxy router”** that functions as an information transfer mechanism and helps create a marketplace for consumer/provider transactions. Both parties host this “proxy router”, which is used to create “sessions” or engagements to send and receive prompts.

From the **consumer side**, they can access the marketplace via the proxy router in 3 ways:
1. Download and run the [pre-packaged Desktop UI](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/04-consumer-setup.md) as the simplest means of interacting with the compute node.  A user simply needs to have MOR and Arbitrum ETH in their wallet to run inference on available models.
 
2. Install the proxy router from the [Morpheus-Lumerin Node github repo](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node), and interact via the web based **“Swagger UI”**. Users can use the web-based API to interact with the blockchain to configure their subset settings, initiate sessions, chat and manage their account.

3. Install the proxy router from the [Morpheus github repo](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/proxy-router-api-direct.md), and install via CLI. Users can conduct the same transactions as `2` via CLI.

As a **provider**, you can access the proxy router via option `2` or `3` above.  

Additionally, providers host their LLM, where the prompts from the proxy router are directed. The proxy router can call the LLM via a `host:port` in OpenAI format, which is configured within `.env` and `model-config.json` files within the router setup. 

When setup properly, this is the basic flow diagram for consumers and providers:

<img src="https://github.com/user-attachments/assets/1b9587a7-91c4-47fb-b696-b32f3106a78e" width=75% height=75%>
<img src="https://github.com/user-attachments/assets/04f32c39-eddd-4bec-af74-205f9d808bf9" width=80% height=80%>


The more detailed diagram is below:
![overview](https://github.com/user-attachments/assets/57c69044-8ccb-4461-8c64-e79c131ca362)

> [!IMPORTANT]
> Not all providers are the same. Providers choose what they will charge for access to their compute, and they will be selected for session initiation based on a [**ranking algorithm**](https://docs.google.com/document/d/1jQPcGcjpO-vu9PTiMKyEqXOwRyuE_gzmQq56irXd3Zc/edit?tab=t.0#heading=h.m15gchuzoli8) that includes:
> * Staked amount
> * Total session duration
> * Success rate
> * Average TPS (Tokens per Second)
> * Average TTFT (Time to First Token)
> * Bid Fee
> * and other on-chain metrics denoted in the link below

When the providers have completed the registration of their subnets, and hosted their models, they begin entering **"bid"**, or offers to run inference on their models at a given price. Consumers have the option of opening **"sessions"** to send prompts based on a Model ID, which selects a provider based on the ranking denoted above, by a **BID ID**, which is a single provider & model paid, or by provider (which is not preferrable if they have multiple models hosted). 

![Screenshot 2024-11-14 at 10 39 46 PM](https://github.com/user-attachments/assets/049d74ea-ddad-4b3d-ae29-f66d00d99f60)

---

## What is a Subnet?
A Morpheus Compute Subnet is a specific Compute Provider who is offering "Inference" (LLM & Diffusion Models) to users of Morpheus, utilizing the Morpheus / Lumerin router. To create a subnet, providers must stake MOR within the proxy router, and host a proxy-router and LLM to accept inference. 

Subnets will be eligible to receive a portion of the daily compute emissions defined in the Yellowstone model. Staked MOR will be locked within the proxy router contracts for 1 year. 

More information on subnets is available [here](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Subnets.md)

---

## Roles
Here, we take a closer look at the role types within the compute system.  

### **Consumers**  
A consumer in the Morpheus ecosystem can fall into one of three categories:  

1. **Individual Users**  
   - Individuals interested in interacting with open-source AI models hosted within the ecosystem. These users value privacy and prefer that their data not be used for training purposes.  

2. **AI Platforms (B2B)**  
   - Businesses or platforms (e.g., Venice AI) that require compute resources to deliver LLM prompts to their end-users.  

3. **Smart and AI Agents**  
   - Autonomous agents that need compute resources to perform their designated functions effectively.
     
### **Providers**  
Providers in the Morpheus ecosystem also fall into three categories:  

1. **Compute Resource Owners**  
   - Individuals or businesses with compute resources, seeking to monetize by hosting a subnet.  

2. **Compute Renters**  
   - Individuals or businesses renting compute resources to host a subnet.  

3. **Model Hosts Without Subnets**  
   - Individuals or businesses hosting AI models without leveraging a subnet, either as compute providers or for local compute purposes.  

---

## What are Incentives?
### **For Consumers**  
Consumers can access compute in two ways:  

1. **Staking MOR Tokens:**  
   - By staking MOR tokens, they accrue a daily amount of Morpheus compute resources. The amount is proportional to the MOR they have staked compared to the total MOR supply. These compute credits can be used to create sessions with provider subnets.  

2. **Purchasing Compute Directly:**  
   - In cases where the daily compute quota from staking are insufficient to handle all user's prompts (e.g., during a load spike), it is possible to purchase compute directly from the marketplace. This operates at a **1:1 rate of compute budget to MOR**, ensuring flexibility to meet increased demand.  

### **For Subnet Providers**  
Subnet providers benefit from both staking MOR tokens and earning MOR tokens:  

1. **Staking MOR:**  
   - To create a subnet, providers must stake a minimum of 10,000 MOR (subject to change).  
   - This staking requirement ensures that only committed providers, with significant investments in both hardware and MOR tokens, can participate, reducing the risk of bad actors entering the marketplace.  

2. **Accruing MOR:**  
   - As a subnet providers, users are eligible to receive daily emissions from the Morpheus Compute "bucket".  
   - These emissions are based on users` **total revenue**, calculated as:   
     `Bid Price × Total Session Length` 
   - This mechanism is further detailed in the Yellowstone model.  

---

## Consumer Setup

Detailed consumer setup instructions located [here](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/04-consumer-setup.md).

**Basic level:**  
1) Download the Desktop-UI from the [github folder.](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)
2) Run a launch command via CLI to start the program:
  - `mor-launch.exe` for windows;
  - `./mor-launch` for linux and macOS.
4) Following this setup, you will need to connect your existing wallet or create a new wallet in the UI. 

**Advanced approach:**  

You need to download and host the proxy router via CLI following the instructions:

*  1) Install and configure OS-specific dependencies: git, go, node, make, yarn
*  2) Clone the Morpheus Node Github
```
git clone https://github.com/MorpheusAIs/Morpheus-Lumerin-Node.git
```

*  3) Navigate to the proxy-router directory
```
cd <your_path>/Morpheus-Lumerin-Node/proxy-router
```
*  4) Copy and edit the /.env file with your: Private key, WSS Node, and the Listening & Hosting Ports
```
cp .env.example .env
vi .env 
```

*  5) Build and run the proxy-router
```
./build.sh 
make run
```
*  6) Utilize the CLI or the swagger-UI to interact with the proxy-router. The swagger UI is available at the hosting IP:PORT selected, like this http://localhost:8082/swagger/index.html

**Consumer functions within the proxy router:**
* `Approve MOR`
  
  ![Screenshot 2024-11-11 at 10 52 37 PM](https://github.com/user-attachments/assets/a4407129-5629-45e4-abb0-65bde4f058c3)
* `Initiate Session` (by Model)
  
 ![Screenshot 2024-11-11 at 10 53 35 PM](https://github.com/user-attachments/assets/d0bd1080-8a64-41c8-8e97-c2d5bd2e4d34)
* `Chat / Prompt LLM`
  
![Screenshot 2024-11-11 at 10 54 22 PM](https://github.com/user-attachments/assets/33ab6bf0-2491-4a44-814d-0a23a61be224)

---

## Provider Setup

Setting up a subnet is complex, and required advanced technical skills with advanced compute hardware. Provider subnets technically only require a proxy-router and an ip:port where open-ai format prompts will be delivered, executed and returned. The provider will typically be hosting the LLM as well for that port and can use any hosting methodology they choose. This includes hosting from a local machine, from a server farm, or from rented compute on a service like Akash.

For these instructions, we will consider a local proxy-router build, and local LLM build using `llama.cpp` as the host. In many cases, a provider may choose another service to host the proxy-router (i.e. AWS) or a load balancer to provide deeper security for their system. Connections to external compute systems can be achieved by providing the proper host:port within your models-config file explained below. 

Detailed instructions on how to setup a provider are [here.](https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/blob/9f356385eae0afea4aaf7b4a44bcd4973685598c/docs/02-provider-setup.md) 

**Basic instructions:**

*  1) Download and configure the proxy router files using the same steps 1-4 from the last section, then:
*  2) Ensure the `.env` file that was created contains the proper **OPENAI_BASE_URL1** that points to your LLM. If you are using AWS or another host for your proxy-router, you may also need to include your path to the models config file that you are about to create `MODELS_CONFIG_PATH=<path_to_proxy-router>/models-config.json`
*  3) Within the proxy-router directory, copy and edit the `models-config.json` file
```
cp models-config.json.example models-config.json
vi models-config.json
```
*  4) Edit this file and be sure to include the **MODEL_ID**, which you can find on the top of this document for commonly hosted models, or your own MODEL_ID if you are hosting a new model. Include the modelName, apiType (typically openai), and the apiUrl (where you are hosting the LLM)
*  5) Build and run the proxy-router
```
./build.sh 
make run
```
*  6) Utilize the CLI or the swagger-UI to interact with the proxy-router. The swagger UI is available at the hosting IP:PORT selected
```
http://localhost:8082/swagger/index.html
```

Hosting an LLM is complex and requires optimizations to best fit your compute hardware.  
There are some detailed instructions [here](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Sample%20Basic%20Compute%20Provider%20Build.md), but they are not comprehensive. Here are some basic instructions:

*  1) Install all dependencies for llama.cpp, which can be found in their readme file. Install GPU dependencies, including CUDA for NVIDIA GPUs (this can be burdensome if this has not been done before). 

*  2) Install llama.cpp

```
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
make -j 8 LLAMA_CUDA=1
```

*  3) Download Model, either through Huggingface directly and placing in the "models" folder of llama.cpp directory, or downloading via CLI

```
model_url=https://huggingface.co/NousResearch
model_collection=Hermes-2-Theta-Llama-3-8B-GGUF
model_file_name=Hermes-2-Pro-Llama-3-Instruct-Merged-DPO-Q8_0.gguf
wget -O models/${model_file_name} ${model_url}/${model_collection}/resolve/main/${model_file_name}
```

*  4) Host Model

```
model_host=localhost
model_port=8080
model_file_name=Hermes-2-Pro-Llama-3-Instruct-Merged-DPO-Q8_0.gguf
ctx_size=8192
threads=8
parallel=16
./llama-server -m models/${model_file_name} --host ${model_host} --port ${model_port} --n-gpu-layers 99 --ctx-size ${ctx_size} --threads ${threads} --parallel ${parallel} --flash-attn
```
> [!Note]
> ctx-size, n-gpu-layers, and parallel are dependent on your GPU selection. Threads are based on your CPU selection. 

*  5) Interact with Model via the UI
```
http://<model_host>:<model_port>
```

Upon completion of setup of the LLM, you will need to conduct the following transactions within the proxy-router:

*  6) `Create Provider`
  
  ![Screenshot 2024-11-11 at 10 55 48 PM](https://github.com/user-attachments/assets/45fc8d82-f39f-4244-ae04-ab7ba5d6ed55)

*  7) `Create Model` (if it does not exist)
  
  ![Screenshot 2024-11-11 at 10 55 59 PM](https://github.com/user-attachments/assets/3c95721b-4e33-45c9-a503-f5326b863cb0)

*  8) `Create Bid` (what cost are you willing to accept for offering your compute)
  
  ![Screenshot 2024-11-11 at 10 56 12 PM](https://github.com/user-attachments/assets/654e77aa-281a-4e04-aa27-5c7afa71e7f2)


  When complete, your subnet will be ready for consumers to create sessions and interact with your model!

---

## Important Links

1. [Lake Travis Decentralized AI Inference System.](/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Lake%20Travis%20Decentralized%20AI%20Inference%20System.md)

2. [Morpheus Lumerin Model.](/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Morpheus%20Lumerin%20Model.md)
   
3. [Morpheus "Yellowstone" Compute Model.](/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Yellowstone%20Compute%20Model.md) 

4. [Morpheus Lumerin Node Github.](https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)

5. [Sample Compute Provider Build.](/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Compute%20Node/Sample%20Basic%20Compute%20Provider%20Build.md)

6. [Model ID Register](/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Model_ID%20Register.md)
 
7. [Compute Providers Ranking](https://docs.google.com/document/d/1jQPcGcjpO-vu9PTiMKyEqXOwRyuE_gzmQq56irXd3Zc/edit?tab=t.0#heading=h.m15gchuzoli8)


> [!TIP]
> ### If you encounter any difficulties or have any questions, you can get support in [#compute-providers Discord chat.](https://discord.com/channels/1151741790408429580/1167520834139738289)


