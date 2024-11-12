# Compute Guide for Beginners

## Table of Contents
1. [**Summary**](#summary)
2. [**Use Cases**](#use-cases)
3. [**What is a subnet?**](#what-is-a-subnet)
4. [**How does it work?**](#how-does-it-work)
5. [**What are the incentives?**](#what-are-the-incentives)
6. [**Consumer Setup**](#consumer-setup)
7. [**Provider Setup**](#provider-setup)

## Summary

As a key part of the Morpheus Ecosystem, the compute node has been launched, providing a marketplace to facilitate transactions between consumers (i.e. people who a way to execute LLM prompts) and provider subnets (i.e. people who have compute resources to execute LLM prompts. The compute node has previously been in testnet, and launched to mainnet on 11/18/24. Compute emissions will begin accruing for providers hosting a subnet as per the Yellowstone compute Model. 

![Screenshot 2024-11-11 at 10 49 55 PM](https://github.com/user-attachments/assets/2080c13e-5b63-4577-a630-d191a07f6882)


Important Links:

Lake Travis Decentralized AI Inference System Proposal: MRC25 - https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Lake%20Travis%20Decentralized%20AI%20Inference%20System.md

Morpheus Lumerin Model - https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Morpheus%20Lumerin%20Model.md

Morpheus "Yellowstone" Compute Model - https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers/Yellowstone%20Compute%20Model.md

## Use Cases

Throughout this document we will consider use cases, and actions required by consumers and providers separately. 

Consumers: A consumer within the Morpheus ecosystem can be one of 3 categories: 
* (1) Individual users interested in engaging with an Open-source AI model hosted within the ecosystem. These users have preference for privacy and do not want their data being used for training purposes. 
* (2) AI Platforms (b2b) who need compute resources to deliver LLM prompts for their users (i.e. Venice AI)
* (3) Smart Agents that require compute resources in order to conduct their designed function

Providers: Providers within the Morpheus ecosystem can be one of 3 categories:

* (1) People/businesses with compute resources they are looking to monetize through hosting a subnet
* (2) People/businesses renting compute to host a subnet
* (3) People/businesses hosting models without a subnet (or for local compute)


## What is a subnet?

A Morpheus Compute Subnet is a specific Compute Provider who is offering "Inference" (LLM & Diffusion Models) to users of Morpheus, utilizing the Morpheus / Lumerin router. To create a subnet, providers must stake MOR within the proxy router, and host a proxy-router and LLM to accept inference. Subnets will be eligible to receive a portion of the daily compute emissions defined in the Yellowstone model. 

More information on subnets is available here: 

https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Subnets.md

## How does it work?

At the simplest level, the compute node employs a “proxy router” that functions as an information transfer mechanism and a marketplace for consumer/provider subnet transaction. Both parties host this “proxy router”, which is used to create “sessions” or engagements to send and receive prompts.

From the consumer side, they can access the marketplace via the proxy router in 3 ways:
*	(1) Download and run the Desktop UI as the simplest means of interacting with the compute node  https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/04-consumer-setup.md
*	(2) Install the proxy router from the Morpheus github repo, and interact via the web based “Swagger UI” https://github.com/MorpheusAIs/Morpheus-Lumerin-Node
*	(3) Install the proxy router from the Morpheus github repo, and instact via CLI (https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/proxy-router-api-direct.md

As a provider, you can access the proxy router via option (2) or (3) above. Additionally, providers will be hosting their LLM, where the prompts from the proxy router are directed. The proxy router can call the LLM via a host:port in OpenAI format, which is configured within .env and model-config.json files within the router setup. 

When setup properly, this is the basic flow diagram for consumers and providers:

![Screenshot 2024-11-10 at 11 38 45 PM](https://github.com/user-attachments/assets/1b9587a7-91c4-47fb-b696-b32f3106a78e)
![Screenshot 2024-11-11 at 12 19 12 AM](https://github.com/user-attachments/assets/04f32c39-eddd-4bec-af74-205f9d808bf9)

The more detailed diagram is below:
![overview](https://github.com/user-attachments/assets/57c69044-8ccb-4461-8c64-e79c131ca362)

It is important to note that not all providers are the same. Providers choose what they will charge for access to their compute, and they will be selected for session initiation based on a ranking algorithm that includes:
* Staked amount
* Total session duration
* Success rate
* Average TPS
* Average TTFT
* Bid Fee
* and other on-chain metrics denoted in the link below

https://docs.google.com/document/d/1jQPcGcjpO-vu9PTiMKyEqXOwRyuE_gzmQq56irXd3Zc/edit?tab=t.0#heading=h.m15gchuzoli8

## What are the incentives?

As a consumer, you can gain access to compute in 2 ways:
* By “staking” MOR token, you accrue a daily amount of Morpheus compute based on the amount staked compared to the total MOR supply. These compute credits can be used towards creating sessions with provider subnets
* There are many cases where the daily amount of Morpheus compute from “staking” is not sufficient to handle all the user’s prompts (ie load spike for consumer). This can be mitigated by purchase compute directly within the marketplace. This will achieve a 1:1 rate of compute budget to MOR

As a provider of a subnet, you will be both “staking” MOR and accruing MOR tokens:
*	Staking MOR: There is a minimum MOR to be staked in order to create a subnet, which at current time is 10,000 MOR. This mechanism was built to ensure that users will be initiating sessions with providers who have made a significant commitment from both a hardware and MOR staking perspective, preventing bad actors from attempting to enter the marketplace. 
*	Accruing MOR: As a subnet provider, you will be entitled to daily emissions from the Morpheus Compute “bucket”. The emissions will be based on your total “revenue” (i.e. Bid Price * Total Session Length), which is explained further through the Yellowstone model

## Consumer Setup

Detailed consumer setup instructions exist here (https://github.com/MorpheusAIs/Morpheus-Lumerin-Node/blob/main/docs/04-consumer-setup.md)

On a basic level, you can:
* Download the Desktop-UI from the github folder 
(https://github.com/MorpheusAIs/Morpheus-Lumerin-Node)
* Run a launch command via CLI to start the program. (mor-launch.exe for windows, ./mor-launch for linux and macOS).
* Following this setup, you will need to connect your existing wallet or create a new wallet in the UI. 

For more advanced users, you can download and host the proxy router via CLI. Here are basic instructions:

* Install and configure OS-specific dependencies: git, go, node, make, yarn
* Clone the Morpheus Node Github
```
git clone https://github.com/MorpheusAIs/Morpheus-Lumerin-Node.git
```

* Navigate to the proxy-router directory
```
cd <your_path>/Morpheus-Lumerin-Node/proxy-router
```
* Copy and edit the /.env file with your: Private key, WSS Node, and the Listening & Hosting Ports
```
cp .env.example .env
vi .env 
```

* Build and run the proxy-router
```
./build.sh 
make run
```
* Utilize the CLI or the swagger-UI to interact with the proxy-router. The swagger UI is available at the hosting IP:PORT selected, like this http://localhost:8082/swagger/index.html

Consumers will typically use the following functions within the proxy router:
* Approve MOR
  
  ![Screenshot 2024-11-11 at 10 52 37 PM](https://github.com/user-attachments/assets/a4407129-5629-45e4-abb0-65bde4f058c3)
* Initiate Session (by Model)
  
 ![Screenshot 2024-11-11 at 10 53 35 PM](https://github.com/user-attachments/assets/d0bd1080-8a64-41c8-8e97-c2d5bd2e4d34)
* Chat / Prompt LLM
  
![Screenshot 2024-11-11 at 10 54 22 PM](https://github.com/user-attachments/assets/33ab6bf0-2491-4a44-814d-0a23a61be224)

## Provider Setup

Setting up a subnet is complex, and required advanced users with advanced compute hardware. Provider subnets technically only require a proxy-router and an ip:port where open-ai format prompts will be delivered, executed and returned. The provider will typically be hosting the LLM as well for that port and can use any hosting methodology they choose. 

For these instructions, we will consider a local proxy-router build, and local LLM build using llama.cpp as the host. In many cases, a provider may choose another service to host the proxy-router (i.e. AWS) or a load balancer to provide deeper security for their system. 

Detailed instructions on how to setup a provider are here: https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/blob/9f356385eae0afea4aaf7b4a44bcd4973685598c/docs/02-provider-setup.md

Basic instructions are below

* Download and configure the proxy router files using the same steps 1-4 from the last section, then:
* Ensure the .env file that was created contains the proper OPENAI_BASE_URL that points to your LLM. If you are using AWS or another host for your proxy-router, you may also need to include your path to the models config file that you are about to create MODELS_CONFIG_PATH=<path_to_proxy-router>/models-config.json
* Within the proxy-router directory, copy and edit the models-config.json file
```
cp models-config.json.example models-config.json
vi models-config.json
```
* Edit this file and be sure to include the MODEL_ID, which you can find on the top of this document for commonly hosted models, or your own MODEL_ID if you are hosting a new model. Include the modelName, apiType (typically openai), and the apiUrl (where you are hosting the LLM)
* Build and run the proxy-router
```
./build.sh 
make run
```
* Utilize the CLI or the swagger-UI to interact with the proxy-router. The swagger UI is available at the hosting IP:PORT selected
```
http://localhost:8082/swagger/index.html
```

Hosting an LLM is complex and requires optimizations to best fit your compute hardware. There are some detailed instructions here, xxxx, but they are not comprehensive. Here are some basic instructions:

* Install all dependencies for llama.cpp, which can be found in their readme file. Install GPU dependencies, including CUDA for NVIDIA GPUs (this can be burdensome if this has not been done before). 

* Install llama.cpp

```
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
make -j 8 LLAMA_CUDA=1
```

* Download Model, either through Huggingface directly and placing in the "models" folder of llama.cpp directory, or downloading via CLI

```
model_url=https://huggingface.co/NousResearch
model_collection=Hermes-2-Theta-Llama-3-8B-GGUF
model_file_name=Hermes-2-Pro-Llama-3-Instruct-Merged-DPO-Q8_0.gguf
wget -O models/${model_file_name} ${model_url}/${model_collection}/resolve/main/${model_file_name}
```

* Host Model

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

* Interact with Model via the UI
```
http://<model_host>:<model_port>
```

Upon completion of setup of the LLM, you will need to conduct the following transactions within the proxy-router

* Create Provider
  
  ![Screenshot 2024-11-11 at 10 55 48 PM](https://github.com/user-attachments/assets/45fc8d82-f39f-4244-ae04-ab7ba5d6ed55)

* Create Model (if it does not exist)
  
  ![Screenshot 2024-11-11 at 10 55 59 PM](https://github.com/user-attachments/assets/3c95721b-4e33-45c9-a503-f5326b863cb0)

* Create Bid (what cost are you willing to accept for offering your compute)
  
  ![Screenshot 2024-11-11 at 10 56 12 PM](https://github.com/user-attachments/assets/654e77aa-281a-4e04-aa27-5c7afa71e7f2)


  When complete, your subnet will be ready for consumers to create sessions and interact with your model!
