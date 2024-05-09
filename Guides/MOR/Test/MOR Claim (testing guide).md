# MOR Claim Testing Guide

>[!NOTE]
> - The purpose of the testing is to familiarize users with the MOR claim process with direct interaction with smart contracts.
> - This testing is conducted on the Ethreum and Arbitrum mainnet (!). Completing all the steps may require $15-25 (at 10-15 gwei gas price) in ETH for fees, depending on network condition.
> - Please note that this testing is not incentivized, and participants will not receive any rewards.
> - Test tokens have no value and intended fot test purpose only.

---

## Introduction
This guide will walk you through the testing MOR rewards claim process starting from providing capital on Ethereum mainnet to obtaining MOR tokens on Arbitrum chain.   
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same. 

There are following steps:
1) [Mint Mock stETH](#mint-test-tokens)
2) [Deposit stETH into the contract](#how-to-deposit-steth-into-the-contract)
3) [Get information about deposit](#how-can-i-get-information-about-how-much-i-deposited)
4) [Get information about MOR rewards](#what-is-the-amount-of-mor-rewards-earned)
5) [Claim MOR rewards](#how-to-claim-rewards)
6) [Get Mock MOR on Arbitrum chain](#how-to-verify-that-i-received-tokens)

---

## Smart Contracts Addresses
**Ethereum:**  
Mock stETH: [0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79](https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79)    
Distribution: [0x2e1fF173085A5ef12046c27E442f12f79A0092b7](https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7) 

**Arbitrum:**  
Mock MOR: [0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E](https://arbiscan.io/address/0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E)

---

## Mint test tokens
> [!IMPORTANT]  
> Test tokens have no value and intended for test purpose only.  
> You need some ETH in your wallet to pay transaction fees which are subject to change according to Ethereum gas price.

Switch your wallet to Ethereum mainnet first. To mint test tokens you need to go to [Mock stETH](https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79#writeContract), open the **"Contract"** tab, then the **"Write Contract"** tab and connect your wallet by clicking **"Connect to Web3"** button.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mint%20mock%20steth.png" width=55% height=55%>

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:  
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH.  
You can use this unit converter calculator https://eth-converter.com to help you.  
On the screenshot, 10 stETH (or 10000000000000000000 in WEI) is going to be minted.

Click **"Write"** and confirm transaction in your wallet. 

---

## Add tokens to Metamask (optional)
In case you want to see Mock stETH tokens in your Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add smart Mock stETH contract address: `0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79`   

---

## How to deposit stETH into the contract?
We need to go to the [Mock stETH](https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79#writeContract) contract, open the **"Contract"** tab, then the **"Write Contract"** tab.  
Don't forget to connect your wallet, which should have enough ETH token to pay for gas.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/approve.png" width=55% height=55%>

Before contributing, we need to give the distribution contract an "approval" to transfer our Mock stETH tokens.  
It is necessary to select the `1. approve()` function that will add allowance for Distribution contract.  
As parameters:
- `spender`: **Distribution contract** address - `0x2e1fF173085A5ef12046c27E442f12f79A0092b7`
- `amount`: amount of tokens in WEI. Should be more or equal to the amount you want to deposit.   
You can use this unit converter calculator https://eth-converter.com to help you.

Click **"Write"** and confirm a transaction.

Next, we need to go to the [Distribution](https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7#writeProxyContract) contract, open the **"Contract"** tab, then the **"Write as Proxy"** tab.  
Don't forget to connect your wallet, which should have enough ETH token to pay for gas.`

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/stake.png" width=55% height=55%>

It is necessary to select the `stake()` function that will deposit stETH tokens to the smart contract.  
As parameters:  
- `poolId_`: pool identifier, allowed only existed and public pools; for testing purpose enter “0”;
- `amount_`: amount of tokens in WEI. (2,5 Mock stETH in the example).

Click **"Write"** and confirm a transaction.

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
> It may take a few minutes for your rewards to appear in your wallet on the Arbitrum chain.

---

## How to verify that I received tokens?
Switch your wallet to Arbitrum mainnet and go to [Mock MOR](https://arbiscan.io/address/0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E) token contract. Open the **"Contract**" tab, then the **"Read Contract"** tab. 

It is necessary to call the function `6. balanceOf()` and specify in the `account (address)` field your address. As a result, you will find out how many tokens are on the wallet reflected in WEI.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Claim%20Test%20Guide/mor%20balance.png" width=55% height=55%>

Another way of checking is to add Mock MOR token in your Metamask token list. To do this, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and fill Mock MOR token contract address `0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E`

---

> [!NOTE]  
> In case you faced with difficulties, find something unclear or have questions, you can get assistance in [Morpheus Discord server](https://discord.com/channels/1151741790408429580/1183666837460897832).


