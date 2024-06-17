# MOR OFT Bridge Guide

## Introduction
Morpheus is chain agnostic, which means that developers can deploy their DAPPs on any blockchain that suits them. To achieve this goal, the MOR token has been integrated with the Wormhole and LayerZero OFT standards. This guide will walk you through the process of bridging the MOR token using LayerZero technology between Arbitrum, Ethereum, and Base chains using smart contracts.




## MOR Token Smart Contract Addresses and LayerZero Codes:
**Ethereum** 
- Smart Contract address: [**0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0**](https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) 
- LayerZero Code: **30101**

**Arbitrum** 
- Smart Contract address: [**0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86**](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)
- LayerZero Code: **30110**

**Base** 
- Smart Contract address: [**0x7431ada8a591c955a994a21710752ef9b882b8e3**](https://basescan.org/address/0x7431ada8a591c955a994a21710752ef9b882b8e3)
- LayerZero Code: **30184**

> [!WARNING]
> **The MOR token is launched only on Arbitrum, Ethereum and Base chains, and only the tokens with the addresses listed above are genuine. All other tokens on any chain are most likely scams.**
>
> **You can verify the addresses with the official twitter/x https://x.com/MorpheusAIs/status/1798115050294816903**




## How to bridge?
There is a two-steps smart contract interaction process to bridge MOR between chains: 

1. Getting fee you have to pay for bridge in native tokens.

2. Executing bridge with `send` function.

Below the list of all possible routes, click on the one you are interested in to jump directly to the instructions:

1. [**Arbitrum to Base**](#arbitrum-to-base-mor-token-bridge)
2. [**Arbitrum to Ethereum**](#arbitrum-to-ethereum-mor-token-bridge)
3. [**Base to Arbitrum**](#base-to-arbitrum-mor-token-bridge)
4. [**Base to Ethereum**](#base-to-ethereum-mor-token-bridge)
5. [**Ethereum to Arbitrum**](#ethereum-to-arbitrum-mor-token-bridge)
6. [**Ethereum to Base**](#ethereum-to-base-mor-token-bridge)



---
## Arbitrum to Base MOR Token Bridge
### Getting Layer Zero Fee For Arbitrum => Base Bridge
Switch your wallet to the Arbitrum chain, go to [Arbitrum MOR contract](https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#readContract) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30184,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30184,"0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed  
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/arb-base-fee.png" width=100% height=100%>


### Executing Arbitrum => Base MOR Bridge Transaction
[![Bridge MOR from Arbitrum to Base](https://img.youtube.com/vi/s6442XvK-m8/0.jpg)](https://www.youtube.com/watch?v=s6442XvK-m8)

Switch your wallet to the Arbitrum chain, go to [Arbitrum MOR contract](https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#writeContract ) **"Write contract"** tab and connect your wallet by clicking on the **"Connect to Web3"** button. 

Find function `11.send (0xc7c7f5b3)` and enter as parameters:
- `send`: but converted to ETH units with https://eth-converter.com;
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value in WEI units obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `send`: 0.000041794856053863
- `_sendParam`: [30184,"0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [41794856053863,0]
- `_refundAddress`: 0xf3ef00168DD40Eae68A7E670d56C7b8724E0c183

Double-check all fields, click **"Write"** and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Base (0x7431ada8a591c955a994a21710752ef9b882b8e3) to your web3 wallet to be able to see the balance.**

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/arb-base-send.png" width=100% height=100%>





---
## Arbitrum to Ethereum MOR Token Bridge
### Getting Layer Zero Fee For Arbitrum => Ethereum Bridge
Switch your wallet to the Arbitrum chain, go to [Arbitrum MOR contract](https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#readContract) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30101,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed;
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/arb-eth-fee.png" width=100% height=100%>


### Executing Arbitrum => Ethereum MOR Bridge Transaction
Switch your wallet to the Arbitrum chain, go to [Arbitrum MOR contract](https://arbiscan.io/token/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86#writeContract ) **"Write contract"** tab and connect your wallet by clicking on the **"Connect to Web3"** button. 

Find function `11.send (0xc7c7f5b3)` and enter as parameters:
- `send`: but converted to ETH units with https://eth-converter.com;
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value in WEI units obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `send`: 0.10325699491872306
- `_sendParam`: [30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [10325699491872306,0]
- `_refundAddress`: 0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E

Double-check all fields, click **"Write"** and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Ethereum (0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) to your web3 wallet to be able to see the balance.**

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/arb-eth-send.png" width=100% height=100%>






---
## Base to Arbitrum MOR Token Bridge
[![Bridge MOR from Base to Arbitrum](https://img.youtube.com/vi/K2n0tWzP_Mw/0.jpg)](https://www.youtube.com/watch?v=K2n0tWzP_Mw)
### Getting Layer Zero Fee For Base => Arbitrum Bridge
Switch your wallet to Base chain, go to [Base MOR contract](https://basescan.org/token/0x7431ada8a591c955a994a21710752ef9b882b8e3#readContract) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30110,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30110,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed;
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/arb-eth-fee.png" width=100% height=100%>


### Executing Base => Arbitrum MOR Bridge Transaction
To execute `call` function we will use REMIX Ethereum Integrated Development Environment.

Switch your wallet to Base chain and visit **https://remix.ethereum.org/**.  
Open **"WORKSPACES"** drop-down menu and select **"Clone"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-clone.png" width=100% height=100%>

Paste Morpheus Smart Contracts repository address https://github.com/MorpheusAIs/SmartContracts and click **"OK"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-link.png" width=100% height=100%>

Wait when the repository is cloned, open **"contracts"** folder and click on **"MOROFT.sol"** contract.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-moroft.png" width=100% height=100%>

Compile the contract after code is opened.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-compile.png" width=100% height=100%>

Wait until compilation is over and connect your web3 wallet, that has to be switched to Base chain.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-connect.png" width=100% height=100%>

Paste the address of the MOR smart contract on Base (0x7431ada8a591c955a994a21710752ef9b882b8e3) chain in **"At Address"** field and click the **"At Address"** blue button.  
If done right, smart contract should appear under the **"Deployed/Unpinned Contracts"** section. 

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-base-ataddress.png" width=100% height=100%>

Paste the fee you got at the previous step (only first number without zero) in the **"VALUE"** field.  
For example, if you got `1032569491872306,0` - you need to paste only `1032569491872306`

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/mor-value.png" width=100% height=100%>

Open the smart contract section, find red **"send"** function and enter as parameters:
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value (with 0) obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `_sendParam`: [30110,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [1032569491872306,0]
- `_refundAddress`: 0x151c2b49CdEC10B150B2763dF3d1C00D70C90956

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-base-arb-transact.png" width=100% height=100%>

Double-check all fields, click **"transact"** red button and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Arbitrum (0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86) to your web3 wallet to be able to see the balance.**





---
## Base to Ethereum MOR Token Bridge
### Getting Layer Zero Fee For Base => Ethereum Bridge
Switch your wallet to Base chain, go to [Base MOR contract](https://basescan.org/token/0x7431ada8a591c955a994a21710752ef9b882b8e3#readContract) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30110,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30101,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed;
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge, reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/base-eth-fee.png" width=100% height=100%>


### Executing Base => Ethereum MOR Bridge Transaction
To execute `call` function we will use REMIX Ethereum Integrated Development Environment.

Switch your wallet to Base chain and visit **https://remix.ethereum.org/**.  
Open **"WORKSPACES"** drop-down menu and select **"Clone"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-clone.png" width=100% height=100%>

Paste Morpheus Smart Contracts repository address https://github.com/MorpheusAIs/SmartContracts and click **"OK"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-link.png" width=100% height=100%>

Wait when the repository is cloned, open **"contracts"** folder and click on **"MOROFT.sol"** contract.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-moroft.png" width=100% height=100%>

Compile the contract after code is opened.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-compile.png" width=100% height=100%>

Wait until compilation is over and connect your web3 wallet, that has to be switched to Base chain.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-connect.png" width=100% height=100%>

Paste the address of the MOR smart contract on Base (0x7431ada8a591c955a994a21710752ef9b882b8e3) chain in **"At Address"** field and click the **"At Address"** blue button.  
If done right, smart contract should appear under the **"Deployed/Unpinned Contracts"** section. 

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-base-ataddress.png" width=100% height=100%>

Paste the fee you got at the previous step (only first number without zero) in the **"VALUE"** field.  
For example, if you got `3206207769497182,0` - you need to paste only `3206207769497182`

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/mor-value.png" width=100% height=100%>

Open the smart contract section, find red **"send"** function and enter as parameters:
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value (with 0) obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `_sendParam`: [30101,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [3206207769497182,0]
- `_refundAddress`: 0x151c2b49CdEC10B150B2763dF3d1C00D70C90956

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-base-eth-transact.png" width=100% height=100%>

Double-check all fields, click **"transact"** red button and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Ethereum (0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) to your web3 wallet to be able to see the balance.**




---
## Ethereum to Arbitrum MOR Token Bridge
### Getting Layer Zero Fee For Ethereum => Arbitrum Bridge
Switch your wallet to Ethereum chain, go to [Ethereum MOR contract](https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0#readContractt) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30110,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30110,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed;
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/eth-arb-fee.png" width=100% height=100%>


### Executing Ethereum => Arbitrum MOR Bridge Transaction
To execute `call` function we will use REMIX Ethereum Integrated Development Environment.

Switch your wallet to Ethereum chain and visit **https://remix.ethereum.org/**.  
Open **"WORKSPACES"** drop-down menu and select **"Clone"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-clone.png" width=100% height=100%>

Paste Morpheus Smart Contracts repository address https://github.com/MorpheusAIs/SmartContracts and click **"OK"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-link.png" width=100% height=100%>

Wait when the repository is cloned, open **"contracts"** folder and click on **"MOROFT.sol"** contract.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-moroft.png" width=100% height=100%>

Compile the contract after code is opened.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-compile.png" width=100% height=100%>

Wait until compilation is over and connect your web3 wallet, that has to be switched to Ethereum chain.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-connect.png" width=100% height=100%>

Paste the address of the MOR smart contract on Ethereum (0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) chain in **"At Address"** field and click the **"At Address"** blue button.  
If done right, smart contract should appear under the **"Deployed/Unpinned Contracts"** section. 

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-ethereum-ataddress.png" width=100% height=100%>

Paste the fee you got at the previous step (only first number without zero) in the **"VALUE"** field.  
For example, if you got `24305570035113,0` - you need to paste only `24305570035113`

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/mor-value.png" width=100% height=100%>

Open the smart contract section, find red **"send"** function and enter as parameters:
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value (with 0) obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `_sendParam`: [30110,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [24305570035113,0]
- `_refundAddress`: 0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/eth-arb-transact.png" width=100% height=100%>

Double-check all fields, click **"transact"** red button and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Arbitrum (0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86) to your web3 wallet to be able to see the balance.**





---
## Ethereum to Base MOR Token Bridge
### Getting Layer Zero Fee For Ethereum => Base Bridge
Switch your wallet to Ethereum chain, go to [Ethereum MOR contract](https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0#readContractt) **"Read contract"** tab, find function `25.quoteSend` and enter as parameters:
- `_sendParam (tuple)`: [30184,"**0x**000000000000000000000000**RECEIVER-ADDRESS**", "**MOR AMOUNT IN WEI**", "**MOR AMOUNT IN WEI**", "0x", "0x", "0x"]
- `_payInLzToken (bool)`: false

For example:  
`[30184,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]`, where you need to input:
- `0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E` - 0x_24zeros_the rest of the receiver address after 0x, no spaces needed;
- `"1000000000000000000", "1000000000000000000"` - two identical amounts of MOR you want to bridge reflected in WEI units (the smallest denomination of ETH).

To convert WEI to ETH units you can use this tool => **https://eth-converter.com**, as examples:
- 1000000000000000000 = 1 MOR  
- 1500000000000000000 = 1,5 MOR  
- 18000000000000000000 = 18 MOR  

When done, click "**Query**.

As a result, you will find out the fee you need to pay in ETH for bridge reflected in WEI.  

Save the resulting value as you will need it for the next step.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/eth-base-fee.png" width=100% height=100%>


### Executing Ethereum => Base MOR Bridge Transaction
To execute `call` function we will use REMIX Ethereum Integrated Development Environment.

Switch your wallet to Ethereum chain and visit **https://remix.ethereum.org/**.  
Open **"WORKSPACES"** drop-down menu and select **"Clone"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-clone.png" width=100% height=100%>

Paste Morpheus Smart Contracts repository address https://github.com/MorpheusAIs/SmartContracts and click **"OK"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-link.png" width=100% height=100%>

Wait when the repository is cloned, open **"contracts"** folder and click on **"MOROFT.sol"** contract.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-moroft.png" width=100% height=100%>

Compile the contract after code is opened.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-compile.png" width=100% height=100%>

Wait until compilation is over and connect your web3 wallet, that has to be switched to Ethereum chain.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-connect.png" width=100% height=100%>

Paste the address of the MOR smart contract on Ethereum (0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0) chain in **"At Address"** field and click the **"At Address"** blue button.  
If done right, smart contract should appear under the **"Deployed/Unpinned Contracts"** section. 

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/remix-ethereum-ataddress.png" width=100% height=100%>

Paste the fee you got at the previous step (only first number without zero) in the **"VALUE"** field.  
For example, if you got `425037811814030,0` - you need to paste only `425037811814030`

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/mor-value.png" width=100% height=100%>

Open the smart contract section, find red **"send"** function and enter as parameters:
- `_sendParam`: copy the input array from the previous step;
- `_fee`: input the fee value (with 0) obtained from the previous step in square brackets `[]`;
- `_refundAddress`: address you want to receive fee refund if actual fee is less than sent, usually the same address from which the transaction was sent.

For example:  
- `_sendParam`: [30184,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]
- `_fee`: [425037811814030,0]
- `_refundAddress`: 0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E

<img src="/Graphics/Docs%20Graphics/English/MOR%20Bridge%20Guide/eth-base-transact.png" width=100% height=100%>

Double-check all fields, click **"transact"** red button and confirm the transaction.  

>[!NOTE]
> **After the transaction is confirmed, it may take up to 10 minutes for MOR to appear in your wallet on the destination chain.**
>
> **You will need to add MOR token on Base (0x7431ada8a591c955a994a21710752ef9b882b8e3) to your web3 wallet to be able to see the balance.**




---
> [!TIP]  
> **In case you face difficulties, find something unclear, or have questions, you can get assistance in the** [**Morpheus Discord server**](https://discord.com/channels/1151741790408429580/1183666837460897832).


# Beware of scams, Morpheus has no tech support team, no support tickets and will not commence any airdrops. Anyone who message you with proposal to help is likely a scammer.


