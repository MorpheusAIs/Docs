# Sample Compute Provider Build:

## Table of Contents
1. Summary
2. Sample Build
3. Build and Configuration
4. LLM Configuration
5. Proxy Router Configuration

## Summary

The below information describes a sample basic compute build that can be used to provide compute within the Morpheus Compute ecosystem. The Morpheus Compute ecosystem is an open marketplace, where compute providers of all sizes and capabilities can enter “bids” or offers for consumers to execute prompts against the LLM they are hosting. As the ecosystem scales, providers will likely consolidate towards models in the highest demand, and this sample build may or may not be capable of hosting those models effectively. 

For more information on the Morpheus Compute Node, visit the githubs here: https://github.com/MorpheusAIs/Docs/tree/main/!KEYDOCS%20README%20FIRST!/Compute%20Providers, https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/tree/dev/docs


## Sample Build

This computer was developed to optimize for cost, while meeting minimum requirements to effectively host a commonly used LLM (8B parameter, multi GPU for larger model or larger number of parallel prompts). This was designed with consideration for dual GPU capacity, although some further improvements could be made for optimization (noted below). This compute build delivers ~80TPS on the 8B parameter models. 

PCPartPicker Link: https://pcpartpicker.com/list/tDDq6D [note: this link may not persist forever, information also included below. Use you own judgment on sellers via pcpartpicker]. Estimated cost with all new parts $4500. 

Parts:
* CPU: Intel i7-13700K 
* CPU Cooler: Thermalright Aqua Elite V3 Liquid
* Motherboard: ASRock B760 Pro RS ATX LGA1700
* RAM: Silicon Power XPOWER Zenith Gaming 64GB (2 x 32GB) DDR5-6000 CL30
* SSD: Leven JPS600 1TB M.2-2280 PCIe 3.0 X4 NVME
* GPU: MSI GeForce RTX3090 VENTUS 3X 24G OC GeForce RTX 3090
* GPU2: EVGA FTW3 ULTRA HYBRID GAMING GeForce RTX3090 24 GB
* Case: Lian Li O11D EVO RGB ATX
* Power Supply: Apevia Galaxy 1000W 80+ Gold Certified Semi-modular ATX
* Case Fans: UNI Fan 120mm Reverse Case Fan Infinity Mirror Module 5V 120mm ARGB PWM
* Case Fans: UNI Fan 120mm Case Fan Infinity Mirror Module 5V 120mm ARGB PWM

Recommended improvements to above list: Following the addition of the second GPU, I may have made the following decisions differently. First, although the case properly fits all the components, I may have decided on a case with additional top venting. This is currently running with an open case for additional air flow, and it is not clear if any temperature issues exist running with a closed case. The power supply needs to be increased to 1200W-1500W, but is dependent on the testing load. A higher end motherboard could have been selected, but it is unclear if there is any performance impact relating to this. 

Purchase note: RTX3090 GPUs are no longer being sold new (generally), and the RTX4090 is the upgraded model. Since GPU VRAM is our largest bottleneck for large models, finding an RTX3090 is a more economical option (used cards can be found in secondary markets). When the RTX5090 launches, if it contains more than 24GB RAM, it may be a more optimal solution (at an expectedly much higher cost). 

## Build and configuration
_Connect all the parts together_

![signal-2024-10-25-005008_002](https://github.com/user-attachments/assets/afca6e73-a0f4-4ff7-aa45-b7f4e30d0386)


To fit everything in the case and achieve proper air flow, the following key notes are recommended:
* Motherboard in “upper” position
* CPU radiator to back of case
* Case fans on CPU radiator as intake
* Case fans on bottom of case as intake
* GPU radiator to side of case
* Case fans on GPU radiator as exhaust
* GPU with AIO radiator in lower PCIe slot
* GPU with AIO radiator installed before standard GPU
* Makeshift support for GPUs required, as standard support systems will not fit

## Configuration for LLMs 
This system was configured with Ubuntu latest build (https://ubuntu.com/download/desktop). Nvidia toolkit installation is required to support CUDA functionality along with all common dependency packages (i.e. Git, Go, etc.)

Technically any LLM server can be used to provide compute within the Morpheus Compute Node, but we have found success using llama.cpp. The instruction below will leverage llama.cpp and huggingface for model download. 

These instructions generally follow the information from the bootstrapping github doc, which will be updated more frequently than this document. https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/blob/dev/docs/mac-boot-strap.md

To install llama.cpp and host your model locally, follow these instructions:

1) Install llama.cpp

```git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
make -j 8 LLAMA_CUDA=1
```

2) Download Model

```model_url=https://huggingface.co/TheBloke
model_collection=TinyLlama-1.1B-Chat-v1.0-GGUF
model_file_name=tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf
wget -O models/${model_file_name} ${model_url}/${model_collection}/resolve/main/${model_file_name}
```

For this example, this is the direct input: 
```wget -o models/Hermes-3-Llama-3.1-8B.Q8_0.gguf https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF/resolve/main/tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf```

4) Host Model

```model_host=127.0.0.1
model_port=8080
model_file_name=tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf
./llama-server -m models/${model_file_name} --host ${model_host} --port ${model_port} --n-gpu-layers 99 --ctx-size 8192 --threads 8
```

For this example, this is the direct input for a single GPU: ```./llama-server -m models/tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf --host 127.0.0.1 --port 8080 --n-gpu-layers 99 --ctx-size 8192 --threads 8```

For this example, this is the direct input for a dual GPU: ```./llama-server -m models/tinyllama-1.1b-chat-v1.0.Q4_K_M.gguf --host 127.0.0.1 --port 8080 --n-gpu-layers 99 --ctx-size 135168 --threads 8 --parallel 22```

Note: ctx-size, n-gpu-layers, and parallel are dependent on your GPU selection. Threads are based on your CPU selection. 

5) Interact with Model

Go to: ```http://<model_host>:<model_port>```

For this example: ```http://127.0.0.1:8080```

When providing compute to the Morpheus Compute Node, it is recommended to manage your operational security. Many providers will choose to implement network security between their LLM hosting and the Proxy Router (if on a different machine), and within their hosting of the proxy router. A simple execution could be the utilization of a small AWS EC2 instance to host the proxy router, providing a level of separation between external proxy router communication and the provider’s network. This is purely up to the provider, and Morpheus will not provide any official guidance or recommendations for this. 

## Proxy Router
The configuration of the proxy router will not be described in this document. Please review this github, and any accompanying github documents for instructions for this installation. 

https://github.com/Lumerin-protocol/Morpheus-Lumerin-Node/blob/dev/docs/02-provider-setup.md










