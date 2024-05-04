# MOR Rewards Claim Guide

## Table of contents
1) [**Smart Contract Addresses**](#)
2) [**Get information about MOR rewards**](#what-is-the-amount-of-mor-rewards-earned)
3) [**Claim MOR rewards**](#how-to-claim-rewards)
4) [**Get Mock MOR on Arbitrum chain**](#how-to-verify-that-i-received-tokens)
5) [**Add to metamask**](#)

---

## Introduction
This guide will walk you through the process of testing the MOR rewards claim, starting from providing capital on the Ethereum mainnet to obtaining MOR token rewards on the Arbitrum mainnet chain. The Metamask wallet is used as a reference in this guide, but the logic remains the same for other Web3 wallets.

---

## Smart Contract Addresses
**Ethereum:**
Distribution contract: [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)

**Arbitrum:**
MOR Token: [0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)

---

## How can I get information about how much I deposited? 
You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **"Contract"** tab, then the **"Read as Proxy"** tab.  
Don't forget to connect your wallet by clicking on **"Connect to Web3"** button.

You need to call `12. usersData()` function that will show how many tokens have been deposited by your address (or the address of the user you want to know about) and put as parameters:
- `<input> (uint256)`: pool identifier; enter (`0`) for capital providers pool;
- `<input> (uint256)`: user wallet address.
  
Click "**Query**".  

Your deposited amount will be indicated in WEI next to `deposited` line. To convert WEI amount you can use this tool https://eth-converter.com.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/deposited.png" width=55% height=55%>

---

## How much MOR have I earned as rewards?
You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the **"Contract"** tab, then the **"Read as Proxy"** tab.  
Don't forget to connect your wallet by clicking on **"Connect to Web3"** button.

The rewards are earned every block and to check the amount, you need to call the `2.getCurrentUserReward` function and put as parameters:
- `poolId_ (uint256)`: pool identifier; enter (`0`) for capital providers pool;
- `user_ (address)`: user wallet address.
  
Click "**Query**".  

As a result, you will find out how many rewards there are at the moment. Amount is in WEI and you can use this unit converter calculator https://eth-converter.com..

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/rewards.png" width=55% height=55%>

---

## How to claim rewards?
Yoy need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the **"Contract"** tab, then the **"Write as Proxy"** tab.  
Don't forget to connect your wallet by clicking on **"Connect to Web3"** button, which should have enough native token to pay for gas.

Call the `claim()` function and put as parameters:
- `claim`: here you need to specify the amount of native token in ETH that you will send with the transaction and that will be used as payment for the gas for a mint on the destination network. You can specify more, the remainder will be returned to the sender;
- `poolId_`: pool identifier; enter (`0`) for capital providers pool;
- `receiver_(address)`: the address of the user for whom the tokens will be minted. **Double check the address as transaction is irreversible.**

Click **"Write"** and confirm the transaction.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/claim.png" width=55% height=55%>

>[!NOTE]
> After your Ethereum transaction is confirmed, it may take up to 15 minutes for MOR to appear in your wallet on the Arbitrum chain.

---

## How to verify that I received tokens?
Switch your wallet to Arbitrum chain, 

Go to [MOR](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86) token contract. Open the **"Contract**" tab, then the **"Read Contract"** tab. 

It is necessary to call the function `6. balanceOf()` and specify in the `account (address)` field your address. 

Click "**Query**".  

As a result, you will find out how many tokens are on the wallet reflected in WEI. To convert WEI amount you can use this tool https://eth-converter.com.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mor%20balance.png" width=55% height=55%>

---

## Add tokens to Metamask
In case you want to see MOR tokens in your Metamask wallet, you need to follow steps from the [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add MOR smart contract address: `0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86`   


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
