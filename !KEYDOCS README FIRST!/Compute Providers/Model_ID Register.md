# Model ID Register

## Introduction
Within the Mopheus Compute Node, users can add new models to the marketplace. For the simplicity of consumers, some model_IDs have been pre-seeded into the marketplace. Consumers have the option of initiating sessions with providers by Bid_ID (meaning a specific provider/model pair), or by Model_ID (all providers hosting a specific model). Ideally, all providers hosting the same model utilize the same model_ID for that model, allowing users to match with the best provider for their session. 

When opening sessions by Model_ID (expected common path), the value of the system increases exponentially when providers use standard Model_IDs 
* Value to users: User matches with best provider, utilizing ranking of a larger subset of providers
* Value to providers: Provider has higher liklihood to match with a consumer, entering a larger pool of demand

NOTE: If you are a provider and using one of the below models, DO NOT create a new model within the proxy router. Use the Model_ID below for your models-config.json file

NOTE: If you are a provider and using a model that is not on the list below, edit this file and submit a pull request to faciliate larger scale use

## Common Models

Meta Llama Models
| Model Name| Filename | URL | Model ID |
| :---------------- | :----------: | :----------: | ----: |
| Llama-3.1-405B | Meta-Llama-3.1-405B-Instruct-Q4_K_M | [https://huggingface.co/ThomasBaruzier/Meta-Llama-3.1-405B-Instruct-GGUF/tree/main/Meta-Llama-3.1-405B-Instruct-Q4_K_M] | 0x01a95edd655e15a0043b2a2329258e165660794f98f63c2b03842c0a98f6d74c |
| Llama-3.1-70B | Meta-Llama-3.1-70B-Instuct.Q5_K_M.gguf | [https://huggingface.co/MaziyarPanahi/Meta-Llama-3.1-70B-Instruct-GGUF/resolve/main/Meta-Llama-3.1-70B-Instruct.Q5_K_M.gguf] | 0xcb6bd9a66175ab6d1a96c6acf33ac70e8666e6dcd71dd7be6903f3c1ab80fd7d |
| Llama-3.1-8B | Meta-Llama-3.1-8B-Instruct-Q8_0.gguf | [https://huggingface.co/bartowski/Meta-Llama-3.1-8B-Instruct-GGUF/resolve/main/Meta-Llama-3.1-8B-Instruct-Q8_0.gguf] | 0x85686c6f53cc5d0b01820bd802832633d89f35cbcee3f8e1b82df2f27d982ef8 |




NousReseach Models
| Model Name| Filename | URL | Model ID |
| :---------------- | :----------: | :----------: | ----: |
| Hermes-3-Llama-3.1-70B | Hermes-3-Llama-3.1-70B.Q5_K_M.gguf | [https://huggingface.co/NousResearch/Hermes-3-Llama-3.1-70B-GGUF/resolve/main/Hermes-3-Llama-3.1-70B.Q5_K_M.gguf] | 0xc823a1b04ea113fffa28b3663f12976fda0285e2a3df90303a3bd7488e7fdeed |
| Hermes-3-Llama-3.1-8B | Hermes-3-Llama-3.1-8B.Q8_0.gguf | Hermes-3-Llama-3.1-8B.Q8_0.gguf | [https://huggingface.co/NousResearch/Hermes-3-Llama-3.1-8B-GGUF/resolve/main/Hermes-3-Llama-3.1-8B.Q8_0.gguf] | 0x790d53e2386b9c6a8a20d133f20e0e9f30c3bbcd58443866adbdde242bdb1b8c |
| Hermes-2-Pro-Llama-3-8B | Hermes-2-Pro-Llama-3-Instruct-Merged-DPO-Q8_0.gguf | [https://huggingface.co/NousResearch/Hermes-2-Theta-Llama-3-8B-GGUF/resolve/main/Hermes-2-Pro-Llama-3-Instruct-Merged-DPO-Q8_0.gguf] | 0xfc91411c689d11319171c2e29f9d8533cd87348b6c5d15016c230df266af3d0a |

Qwen Models
| Model Name| Filename | URL | Model ID |
| :---------------- | :----------: | :----------: | ----: |
| Qwen2.5-Coder-32B | qwen2.5-coder-32b-instruct-q8_0.gguf | [https://huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct-GGUF/resolve/main/qwen2.5-coder-32b-instruct-q8_0.gguf] | 0xb5edae401693f2aaa83908ef9d65d4b89d889eb0bace51a5ee3d1f92bc56408f |
| Qwen2.5-14B-Instruct | qwen2.5-14b-instruct-q8_0 | [https://huggingface.co/Qwen/Qwen2.5-14B-Instruct-GGUF/tree/main] | 0x1a2b8bf57423a72a9aff8fb4adebaf17b8ef2c1370be20e22f82bf24fa8175bb |
| Qwen2.5-72B | qwen2.5-72b-instruct-q8_0 | [https://huggingface.co/Qwen/Qwen2.5-72B-Instruct-GGUF/tree/main] | 0x1a2b8bf57423a72a9aff8fb4adebaf17b8ef2c1370be20e22f82bf24fa8175bb |

CognitiveComputations Models

| Model Name| Filename | URL | Model ID |
| :---------------- | :----------: | :----------: | ----: |
| Dolphin-2.94-Llama3.1-8B | dolphin-2.9.4-llama3.1-8b-Q8_0.gguf | [https://huggingface.co/cognitivecomputations/dolphin-2.9.4-llama3.1-8b-gguf/resolve/main/dolphin-2.9.4-llama3.1-8b-Q8_0.gguf] | 0xdfa6c1a4e4d3c56fb985de46debd9d4b6fb8e624dd770f0fc1e3feb2b7a26d5b |

