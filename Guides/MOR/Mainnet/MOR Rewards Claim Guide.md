# MOR Rewards Claim Guide

## Table of contents
1) [**Smart Contract Addresse**s](#)
2) [**Get information about MOR rewards**](#what-is-the-amount-of-mor-rewards-earned)
3) [**Claim MOR rewards**](#how-to-claim-rewards)
4) [**Get Mock MOR on Arbitrum chain**](#how-to-verify-that-i-received-tokens)
5) [**Add to metamask**]

---

## Introduction
This guide will walk you through the testing MOR rewards claim process starting from providing capital on Ethereum mainnet to obtaining MOR tokens on Arbitrum chain.   
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same. 

Этот гайд описывает процесс прямого взаимодействия с контрактами Морфеус при помощи кошелька Метамаск

---

## Smart Contract Addresses
**Ethereum:**
Distribution: [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)

**Arbitrum:**
MOR Token: [0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)

---

## How can I get information about how much I deposited? 
You need to go to the [Distribution](https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7#readProxyContract) contract, open the **"Contract"** tab, then the **"Read as Proxy"** tab. Don't forget to connect your wallet.

You need to call `12. usersData()` function that will show how many tokens have been deposited by users' address (or the address of the user you want to know about). Enter pool number (`0`) in `<input> (uint256)` field and your address in `<input> (address)`.  
Click "**Query**".  
Your deposited amount will be indicated in WEI next to `deposited` line.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/deposited.png" width=55% height=55%>

---

## What is the amount of MOR rewards earned? 
You need to go to the [Distribution](https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7#readProxyContract) contract, open the **"Contract"** tab, then the **"Read as Proxy"** tab. Don't forget to connect your wallet.

The rewards are earned every block and to check the amount, you need to call the `2. getCurrentUserReward` function, where you need to enter pool number (`0`) in `poolId_ (uint256)` and your address in `user_ (address)`.  
Click "**Query**".  
As a result, you will find out how many rewards there are at the moment. Amount is in WEI and you can use this unit converter calculator https://eth-converter.com to help you.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/rewards.png" width=55% height=55%>

>[!NOTE]
> The speed of awarding awards has been artificially increased many times for testing purposes.

---

## How to claim rewards?
We need to go to the [Distribution](https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7#writeProxyContract) contract, open the **"Contract"** tab, then the **"Write as Proxy"** tab.  
Don't forget to connect your wallet, which should have enough native token to pay for gas.

Call the `claim()` function and put as parameters:
- `claim`: here you need to specify the amount of native token in ETH that you will send with the transaction and that will be used as payment for the gas for a mint on the destination network. You can specify more, the remainder will be returned to the sender;
- `poolId_`: pool identifier; enter "0" for test purpose;
- `receiver_(address)`: the address of the user for whom the tokens will be minted.
  
Click **"Write"** and confirm a transaction.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/claim.png" width=55% height=55%>

>[!NOTE]
> After your Ethereum transaction is confirmed, it may take up to 15 minutes for MOR to appear in your wallet on the Arbitrum chain.

---

## How to verify that I received tokens?
Switch your wallet to Arbitrum mainnet and go to [Mock MOR](https://arbiscan.io/address/0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E) token contract. Open the **"Contract**" tab, then the **"Read Contract"** tab. 

It is necessary to call the function `6. balanceOf()` and specify in the `account (address)` field your address. As a result, you will find out how many tokens are on the wallet reflected in WEI.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mor%20balance.png" width=55% height=55%>

Another way of checking is to add MOR token in your Metamask token list. To do this, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and fill Mock MOR token contract address `0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E`

---

## Add tokens to Metamask (optional)
In case you want to see Mock stETH tokens in your Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add smart Mock stETH contract address: `0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79`   


> [!NOTE]  
> In case you faced with difficulties, find something unclear or have questions, you can get assistance in [Morpheus Discord server](https://discord.com/channels/1151741790408429580/1183666837460897832).

---


Capital guide link + contents

1) Smart Contracts addresses.
2) How to get stETH?
3) How to deposit stETH into the contract? 
4) What is the amount of MOR rewards earned? 
5) How can I get information about how much I have deposited?
6) How to withdraw stETH from the contract?

https://github.com/MorpheusAIs/Docs/edit/main/Guides/MOR/Mainnet/Morpheus%20Capital%20Providers%20Contract%20Guide.md
