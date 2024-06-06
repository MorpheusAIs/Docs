# MOR OFT Bridge Guide.md

## Introduction
Morpheus is chain agnostic, which means that developers can deploy their DAPPs on any blockchain that suits them. To achieve this goal, the MOR token has been integrated with the Wormhole and LayerZero OFT standards. This guide will walk you through the process of bridging the MOR token using LayerZero technology between Arbitrum, Ethereum, and Base chains using smart contracts.

## MOR Token Smart Contract Addresses
**Ethereum:** [**0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0**](https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) 

**Arbitrum:** [**0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86**](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)

**Base:** [**0x7431ada8a591c955a994a21710752ef9b882b8e3**](https://basescan.org/address/0x7431ada8a591c955a994a21710752ef9b882b8e3)

> [!WARNING]
> **The MOR token is launched only on Arbitrum, Ethereum and Base chains, and only the tokens with the addresses listed above are genuine. All other tokens on any chain are most likely scams.**
>
> **You can verify the addresses with the official twitter/x https://x.com/MorpheusAIs/status/1798115050294816903**

## How to bridge?
There are two-steps process to bridge MOR between chains: 

1. Get fee you have to pay for bridge in native tokens

2. Execute bridge with `send` function.

## Getting LayerZero bridge for:

### - Bridging to Base
You can bridge MOR token to Base from Arbitrum or Ethereum.  
If you are on Arbitrum, switch your wallet to the Arbitrum chain, go to [Arbitrum MOR contract](https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#readContract) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:

- `_sendParam (tuple)`: [30184,"**0x**000000000000000000000000**YOUR-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:
[30184,"0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"], where you need to replace:

- `0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183` - 0x_24zeros_the rest of your address after 0x, no spaces needed
- `"1000000000000000000", "1000000000000000000"` - two identical amount of MOR you want to bridge reflected in WEI, the smallest denomination of ETH.


Click "**Query**"

As a result, you will find out how many MOR tokens are in the wallet, reflected in WEI.  
To convert WEI you can use this tool https://eth-converter.com.




### - Bridging to Ethereum

[30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.003060201202870756
[3060201202870756,0]

### - Bridging to Arbitrum

[30110,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.000022422266371209
[22422266371209,0]





https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#readContract 
https://basescan.org/token/0x7431ada8a591c955a994a21710752ef9b882b8e3#readContract
https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0#readContract


https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#writeContract 


https://basescan.org/token/0x7431ada8a591c955a994a21710752ef9b882b8e3#writeContract 


https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0#writeContract


## Send tokens

Call send function: 
payableAmount / value: you have to convert a fee from Wei to Ether and pass the value here. 
_sendParam: copy the input array from the previous step. 
_fee: pass a “fee” value obtained from the previous step.
_refundAddress: usually the same address from which the transaction was sent.

### SEND TO ETHEREUM

[30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.003060201202870756
[3060201202870756,0]


### SEND TO BASE

[30184,"0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.000039804175519067
[39804175519067,0]

### SEND TO ARBITRUM

[30110,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.000022422266371209
[22422266371209,0]

Links to other guides
https://eth-converter.com/

Можно ли клеймить награды на эти сети 
ликвидность
