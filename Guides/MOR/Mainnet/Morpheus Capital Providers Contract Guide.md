# Morpheus Capital Providers Contract Guide

## Introduction
The purpose of the guide is to pass you through the process of direct interaction with the Morpheus Capital Providers Distribution Contract.

## Table of contents
1) [Smart Contracts addresses](#smart-contracts-addresses)
2) [How to get stETH?](#how-to-get-steth)
3) [How to deposit stETH into the contract?](#how-to-deposit-steth-into-the-contract)
4) [What is the amount of MOR rewards earned?](#what-is-the-amount-of-mor-rewards-earned)
5) [How can I get information about how much I have deposited?](#how-can-i-get-information-about-how-much-i-have-deposited)
6) [How to withdraw stETH from the contract?](#how-to-withdraw-steth-from-the-contract)

---

## Smart Contracts Addresses 
**Ethereum:**
- Morpheus Distribution Contract: [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790) 
- stETH Contract: [0xae7ab96520de3a18e5e111b5eaab095312d7fe84](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84)

---

## How to get stETH?
First, a user must get stETH (staked ETH) from [Lido](https://lido.fi/).  

You can get this by swapping ETH for stETH on the Ethereum mainnet by following instructions at their website or buy stETH on different exchanges that support it.  

---

## How to deposit stETH into the contract?
You need to go to the [stETH](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.   
Don't forget to connect your wallet by clicking **"Connect to Web3"** button, which should have enough native token to pay for gas.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/approval.png" width=70% height=70%>

Before contributing, you need to give the distribution contract an **"approval"** to transfer your stETH tokens.   
It is necessary to select the `3.approve()` function that will add allowance for Distribution contract.  
As parameters:
- `spender`: **Distribution contract** address: `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790`
- `amount`: amount of tokens in WEI. Should be more or equal to the deposited amount.
  
You can use this unit converter calculator https://eth-converter.com to help you. In the example on picture, it's 1 ETH in WEI.

Click “**Write**” and confirm a transaction.

Then, you need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.   
Don't forget to connect your wallet, which should have enough native token to pay for gas.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

It is necessary to select the `9.stake()` function that will deposit stETH tokens to the smart contract.   
As parameters:
- `poolId_`: pool identifier, enter `0`for capital providers pool.
- `amount_`: amount of tokens in WEI. (the same or less than amount you approved)

Click “**Write**” and confirm a transaction.

> [!IMPORTANT]
> **DO NOT SEND stETH DIRECTLY TO THE CONTRACT ADDRESS**  
> If you deposit additional stETH the 7-days lock-up is restarted for all your deposited stETH from that address.

---

## What is the amount of MOR rewards earned? 

You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **“Contract”** tab, then the **“Read as Proxy”** tab. Don't forget to connect your wallet by clicking **"Connect to Web3"** button.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/rewards.png" width=70% height=70%>

The rewards are earned every block and to check the amount, you need to call the `2.getCurrentUserReward` function, where you need to enter pool number `0` and your address (or the address of the user you want to know about). 

Click "**Query**".  
As a result, you will find out how many rewards there are at the moment. Amount is in WEI and you can use this unit converter calculator https://eth-converter.com. 

---

## How can I get information about how much I have deposited? 

You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **“Contract”** tab, then the **“Read as Proxy”** tab. Don't forget to connect your wallet by clicking **"Connect to Web3"** button.

Select the `12.usersData()` function that will show how many tokens have been invested by the user, enter your wallet address and `0` number of pool. 

Click "**Query**". Your deposited amount will be indicated in WEI next to `deposited` line.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposited.png" width=60% height=60%>

---

## How to withdraw stETH from the contract?

> [!Note] 
> You can withdraw funds no earlier than 7 days after the deposit.

You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the **“Contract”** tab, then the **“Write as Proxy”** tab.  
Don't forget to connect your wallet, which should have enough native token to pay for gas.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/withdraw.png" width=70% height=70%>

It is necessary to select the `13.withdraw()` function that will withdraw the required number of stETH.  
As parameters:
- `poolId_`: pool identifier; enter `0` for capital providers pool;
- `amount_`: amount of tokens in WEI. You can use this unit converter calculator https://eth-converter.com.   
In the example on the picture, 0.1 stETH indicated in WEI.

Click “**Write**” and confirm a transaction.

---

> [!TIP]  
> **In case you faced with difficulties, find something unclear or have questions, you can get assistance in** [**Morpheus Discord server**](https://discord.com/channels/1151741790408429580/1183666837460897832).
