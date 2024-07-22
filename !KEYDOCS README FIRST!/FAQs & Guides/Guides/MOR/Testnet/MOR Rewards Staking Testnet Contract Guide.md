![image](https://github.com/user-attachments/assets/1f4ba052-5a19-40e8-8c00-c98324b7e3cf)# MOR Rewards Staking Testnet Contract Guide

## Introduction
This guide will walk you through the process of direct interaction with the Morpheus Distribution Smart Contract on Sepolia Ethereum testnet for reward staking purpose.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

## Table of contents
1) [**Smart Contracts addresses**](#smart-contracts-addresses)
2) [**Mint mock stETH?**](#mint-mock-steth)
3) Add mock stETH to Metamask
4) [**Stake with new Capital Deposit**](#how-to-deposit-steth-into-the-contract)
5) [**What is the amount of MOR rewards earned?**](#what-is-the-amount-of-mor-rewards-earned)
6) [**How can I get information about how much I have deposited?**](#how-can-i-get-information-about-how-much-i-have-deposited)
7) [**How to withdraw stETH from the contract?**](#how-to-withdraw-steth-from-the-contract)

APproval
Deposit capital and lock (new deposit)

Existed deposit

Withdraw
Claim rewards
How to check multiplier
How to check claimLock time

How to check balance (link)
How to withdraw capital 
How to check rewards (link)

https://etherscan.io/blockdateconverter
https://etherscan.io/unitconverter 

---

## Smart Contracts Addresses 
**Ethereum Sepolia Testnet:**

- Morpheus Distribution Sepolia Testnet Contract: [0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524](https://sepolia.etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524)
   
- stETHMock Contract: [0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA)

---

## Mint mock stETH
> [!IMPORTANT]  
> Test tokens have no value and intended for test purpose only.  
> You need some ETH Sepolia in your wallet to pay transaction fees. It is easy obtainable with faucets like:
> - https://faucet.quicknode.com/ethereum/sepolia  
> - https://faucets.chain.link/sepolia  
> - https://www.alchemy.com/faucets/ethereum-sepolia  
> - https://sepolia-faucet.pk910.de/  

Switch your wallet to Ethereum Sepolia testnet first.  

If you don't have it added to your wallet, you can use this [link](https://chainlist.org/?testnets=true&search=Sepolia), scroll down, find Sepolia and click **"Add to Metamask"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mint%20mock%20steth.png" width=80% height=80%>

To mint test tokens you need to:

- go to [Mock stETH Contract](https://etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract); 
- open the **"Contract"** tab, then the **"Write Contract"** tab;
- connect your wallet by clicking **"Connect to Web3"** button.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mint%20mock%20steth.png" width=55% height=55%>

It is necessary to select the `4. mint ()` function that will issue tokens to your address.  
As parameters:  
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in Wei, instead of ETH.  

> [!NOTE]
> Wei is the smallest unit of ETH. One ether = 1,000,000,000,000,000,000 Wei

You can use https://etherscan.io/unitconverter for calculations. Enter desirable amount in the `Ether` field and copy value from the `Wei` field.   
On the screenshot, 10 stETH (or 10000000000000000000 in WEI) is going to be minted.

Click **"Write"** and confirm the transaction in your wallet. 

---

## Add mock stETH to Metamask (optional)
In case you want to see mock stETH token in your Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add mock stETH smart contract address: `0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA`   

--- 

## Stake with new Capital Deposit

Before contributing mock stETH, you need to give the Distribution contract an **approval**, for this you need to:
- go to the [mock stETH Contract](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/approval.png" width=70% height=70%>

Select the `1.approve()` function that will add allowance for the Distribution contract to spend users' mock stETH.  
Input as parameters:
- `spender`: **Distribution contract** address: `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790`;
- `amount`: amount of tokens in Wei. Should be more or equal to the amount of mock stETH you want to deposit.
- 
> [!NOTE]
> Wei is the smallest unit of ETH. One ether = 1,000,000,000,000,000,000 Wei

You can use **https://etherscan.io/unitconverter** for calculations. Enter desirable amount in the `Ether` field and copy value from the `Wei` field.   
On the screenshot, 10 stETH (or 10000000000000000000 in WEI) is going to be minted.

Click “**Write**” and confirm the transaction.

After confirmation, you need to:
- go to the [Distribution](https://etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#writeProxyContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Find and select the `10.stake()` function that will deposit stETH tokens into the smart contract.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital providers pool;
- `amount_ (uint 256)`: amount of tokens in Wei. (the same or less than amount you approved).
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock period, i.e. when you will be able to claim your MOR reward. If you don't want to stake MOR rewards, type `0` in the field.

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.
- 
On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**. That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Click “**Write**” and confirm the transaction.

> [!IMPORTANT]
> **Double check the correctness of the date to timestamp convertion as the operation is irreversible**
> 

> 
> **You will not be able to withdraw MOR rewards until the end of the staking period.**
>
**The transaction will ONLY stake your future rewards. Nothing changes the ability to withdraw capital contribution (beyond the normal 7 days delay). However, when you withdraw stETH, you will no longer get rewards.**
> **If you deposit additional stETH, the 7-days lock-up is restarted for all your deposited stETH from that address.**
> 
> **MOR Rewards Staking period cannot be decreased, but can be increased.**
>
> **If you don't want to stake MOR rewards, just type `0` in the field `claimLockEnd_ (uint 128)`.**

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
