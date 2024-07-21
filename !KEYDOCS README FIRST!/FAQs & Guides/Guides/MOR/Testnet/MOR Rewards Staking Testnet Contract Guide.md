# MOR Rewards Staking Testnet Contract Guide

Convertation
Mint
APproval
Deposit capital and lock (new deposit)
Existed deposit
Withdraw
Claim rewards
How to check multiplier
How to check claimLock time

How to check balance (link)
How to check rewards (link)

## Introduction
This guide will walk you through the process of direct interaction with the Morpheus Distribution Smart Contract on Sepolia Ethereum testnet for reward staking purpose.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

## Table of contents
1) [**Smart Contracts addresses**](#smart-contracts-addresses)
2) [**How to get mock stETH?**](#how-to-get-mock-steth)
3) [**How to deposit stETH into the contract?**](#how-to-deposit-steth-into-the-contract)
4) [**What is the amount of MOR rewards earned?**](#what-is-the-amount-of-mor-rewards-earned)
5) [**How can I get information about how much I have deposited?**](#how-can-i-get-information-about-how-much-i-have-deposited)
6) [**How to withdraw stETH from the contract?**](#how-to-withdraw-steth-from-the-contract)

---

## Smart Contracts Addresses 
**Ethereum Sepolia Testnet:**
- Morpheus Distribution Sepolia Testnet Contract: [0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524](https://sepolia.etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524) 
- stETHMock Contract: [0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA)

---

## How to get stETH?
The shortest way is to stake ETH with [Lido](https://lido.fi/) following the website instructions.

Alternatively, a user can swap stETH on Ethereum DEXes or buy stETH on centralized exchanges that support it.  

---

## How to deposit stETH into the contract?
You need to go to the [stETH](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.   

Don't forget to connect your wallet by clicking on the **"Connect to Web3"** button.  
Make sure your wallet has enough ETH to cover gas fees.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/approval.png" width=70% height=70%>

Before contributing, you need to give the Distribution contract an **approval**.

It is necessary to select the `3.approve()` function that will add allowance for the Distribution contract to spend users' stETH.  
Input parameters:
- `spender`: **Distribution contract** address: `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790`;
- `amount`: amount of tokens in WEI. Should be more or equal to the deposited amount.
  
You can use this unit converter calculator https://eth-converter.com to help you. In the example on the image, it is 1 ETH in WEI.

Click “**Write**” and confirm the transaction.

After confirmation, you need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.   

Don't forget to connect your wallet by clicking on the **"Connect to Web3"** button.  
Make sure your wallet has enough ETH to cover gas fees.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Find and select the `9.stake()` function that will deposit stETH tokens into the smart contract.   
Input parameters:
- `poolId_`: pool identifier, enter `0` for capital providers pool;
- `amount_`: amount of tokens in WEI. (the same or less than amount you approved).

Click “**Write**” and confirm the transaction.

> [!IMPORTANT]
> **DO NOT SEND stETH DIRECTLY TO THE CONTRACT ADDRESS AS IT WILL BE LOST**
>  
> **If you deposit additional stETH, the 7-days lock-up is restarted for all your deposited stETH from that address.**

---

## What is the amount of MOR rewards earned? 

You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **“Contract”** tab, then the **“Read as Proxy”** tab. 

Don't forget to connect your wallet by clicking on the **"Connect to Web3"** button.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/rewards.png" width=70% height=70%>

The rewards are earned every block and to check the amount, you need to call the `2.getCurrentUserReward` function, where you need to enter pool number `0` and your address (or the address of the user you want to know about). 

Click "**Query**".  

As a result, you will find out how many rewards there are at the moment.  
Amount is in WEI and you can use this unit converter calculator https://eth-converter.com. 

---

## How can I get information about how much I have deposited? 

You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **“Contract”** tab, then the **“Read as Proxy”** tab. 

Don't forget to connect your wallet by clicking on the **"Connect to Web3"** button.

Select the `12.usersData()` function that will show how many tokens have been invested by the user, enter your wallet address and `0` as the pool identifier. 

Click "**Query**". 

Your deposited amount will be indicated in WEI next to `deposited` line.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposited.png" width=60% height=60%>

---

## How to withdraw stETH from the contract?

> [!Note] 
> **You can withdraw funds no earlier than 7 days after the deposit.**

Go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.  

Don't forget to connect your wallet by clicking on the **"Connect to Web3"** button.  
Make sure your wallet has enough ETH to cover gas fees.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/withdraw.png" width=70% height=70%>

It is necessary to select the `13.withdraw()` function that will withdraw the required number of stETH.  
Input parameters:
- `poolId_`: pool identifier; enter `0` for capital providers pool;
- `amount_`: amount of tokens in WEI. You can use this unit converter calculator https://eth-converter.com.  
 
In the example on the picture, 0.1 stETH indicated in WEI.

Click “**Write**” and confirm the transaction.

---

> [!TIP]  
> **In case you face with difficulties, find something unclear or have questions, you can get assistance in** [**Morpheus Discord server**](https://discord.com/channels/1151741790408429580/1183666837460897832).

## Beware of scams, Morpheus has no tech support team, no support tickets and will not commence any airdrops. Anyone who message you with proposal to help is likely a scammer.
