# MOR Claim Testing Guide

>[!NOTE]
> - The purpose of the testing is to familiarize users with the MOR claim process with direct interaction with smart contracts.
> - This testing is conducted on the Ethreum and Arbitrum mainnet (!). Completing all the steps may require $5-15 in ETH for fees, depending on network condition.
> - Please note that this testing is not incentivized, and participants will not receive any rewards.
> - Test tokens have no value and intended fot test purpose only.

---

## Introduction
This guide will walk you through the testing MOR rewards claim process starting from providing capital on Ethereum mainnet to obtaining MOR tokens on Arbitrum chain. Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same. 

There are following steps:
1) [Mint Mock stETH](#connect-wallet-to-uniswap)
2) [Deposit stETH into the contract](#connect-wallet-to-uniswap)
3) [Get information about deposit](#how-to-swap-tokens-on-uniswap)
4) [Get information about MOR rewards](#how-to-add-liquidity-to-uniswap)
5) [Claim MOR rewards](#how-to-remove-or-decrease-liquidity-from-uniswap)
6) [Get Mock MOR on Arbitrum chain](#how-to-increase-liquidity-on-uniswap)

---

## Smart Contracts Addresses
**Ethereum:**  
Mock stETH: https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79 
Distribution: https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7 

**Arbitrum:**  
Mock MOR: https://arbiscan.io/address/0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E 

---

## Mint test tokens
> [!IMPORTANT]  
> Test tokens have no value and intended for test purpose only.
> You need some ETH in your wallet to pay transaction fees which are subject to change according based on Ethereum gas price.

Switch your wallet to Ethereum mainnet first. To mint test tokens you need to go to [Mock stETH](https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79#writeContract), open the **“Contract”** tab, then the **“Write Contract”** tab and connect your wallet by clicking **"Connect to Web3**" button.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/mint.png" width=75% height=75%>

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH.  
You can use this unit converter calculator https://eth-converter.com to help you.  
On the screenshot, 100 stETH (or 100000000000000000000 in WEI) is going to be minted.

Click **"Write"** and confirm transaction in your wallet. 

---

## Add tokens to Metamask (optional)
In case you want to see Mock stETH tokens in your Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add smart Mock stETH contract address: `0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79`   

---

## How to deposit stETH into the contract?
We need to go to the [stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#writeContract) contract, open the “Contract” tab, then the “Write Contract” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stethapproval.png)

Before contributing, we need to give the distribution contract an "approval" to transfer our stETH tokens. It is necessary to select the `approve()` function that will add allowance for Distribution contract. As parameters:
- `spender`: Distribution contract address - `0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b`
- `amount`: amount of tokens in WEI. Should be more or equal to the deposited amount. You can use this unit converter calculator https://eth-converter.com to help you.

Click “Write” and confirm a transaction.

Then, we need to go to the [Distribution](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract) contract, open the “Contract” tab, then the “Write as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stake.png)

It is necessary to select the `stake()` function that will deposit stETH tokens to the smart contract. 
As parameters:
- `poolId_`: pool identifier, allowed only existed and public pools; for testing purpose enter “0”;
- `amount_`: amount of tokens in WEI. (10 stETH in this example).

Click “Write” and confirm a transaction.


## How can I get information about how much I have deposited? What is the amount of rewards earned?
We need to go to the [Distribution](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#readProxyContract) contract, open the “Contract” tab, then the “Read as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

For this purpose we have two functions, the first shows how many rewards have already been earned, the rewards are earned every second.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/rewards.png)

To check the amount of rewards, you need to call the `getCurrentUserReward` function, where you need to pass the group number and your address (or the address of the user you want to know about). As a result, we will find out how many rewards there are at the moment. Amount is in WEI and you can use this unit converter calculator https://eth-converter.com to help you.

The second function will show how many tokens have been invested by the user, the parameters are similar to the first function call. The name of the function is `usersData()`.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stakedamount.png)


## How to withdraw stETH from the contract?
We need to go to the [Distribution](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract) contract, open the “Contract” tab, then the “Write as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/withdraw.png)

It is necessary to select the `withdraw()` function that will withdraw the required number of stETH. 
As parameters:
- `poolId_`: pool identifier; enter "0" for test purpose;
- `amount_`: amount of tokens in WEI.

Click “Write” and confirm a transaction.


## How to claim rewards?
We need to go to the [Distribution](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract), open the “Contract” tab, then the “Write as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/claim.png)

The mint of the MOR token takes place on the Arbitrum Sepolia network, so we need a Layer Zero bridge to help us do this. 

All the user needs to do is to call the `claim()` function.
As parameters:
- `claim`: here you need to specify the amount of native token in ETH that you will send with the transaction and that will be used as payment for the gas for a mint on the destination network. You can specify more, the remainder will be returned to the sender.
- `poolId_`: pool identifier; enter "0" for test purpose;
- `user_`: the address of the user for whom the tokens will be minted.
  
Click “Write” and confirm a transaction.

Great, our rewards are now in the form of a MOR token on Arbitrum Sepolia, you can import the token address `0xe6d01d086a844a61641c75f1bca572e7aa70e154` to your list in metamask using this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) or check your balance via smart contract as we did with stETH token.


## How to get Arbitrum Sepolia ETH?
To start we should have installed Metamask or another web3 wallet. Then we need to add Arbitrum Sepolia manually or using [Chainlist](https://chainlist.org/?testnets=true&search=arbitrum+sepolia) and clicking “Add to Metamask”

The next step is to fund your address with Arbitrum Sepolia ETH. You may use faucets like https://faucet.quicknode.com/arbitrum/sepolia or https://faucet.triangleplatform.com/arbitrum/sepolia to get some for paying fees.

**In case you are interested in more in depth testnet guidance, please follow the [link](https://docs.google.com/document/d/1DbNx-CBpHjFUvIhbKHJSOshCKNTWlng7SeLzzn95AKY/edit)** 


## How to deposit stETH into the contract?
You need to go to the [stETH](https://etherscan.io/address/0xae7ab96520de3a18e5e111b5eaab095312d7fe84#writeProxyContract) contract, open the “Contract” tab, then the “Write as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/main/MorpheusGuide/approval.png)

Before contributing, you need to give the distribution contract an "approval" to transfer your stETH tokens. It is necessary to select the `approve()` function that will add allowance for Distribution contract.  
As parameters:
- `spender`: **Distribution contract** address - `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790`
- `amount`: amount of tokens in WEI. Should be more or equal to the deposited amount. You can use this unit converter calculator https://eth-converter.com to help you. In the example on picture, it's 1ETH in WEI.

Click “**Write**” and confirm a transaction.

Then, you need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#writeProxyContract) contract, open the “Contract” tab, then the “Write as Proxy” tab.   
Don't forget to connect your wallet, which should have enough native token to pay for gas.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/main/MorpheusGuide/deposit.png)

It is necessary to select the `stake()` function that will deposit stETH tokens to the smart contract.   
As parameters:
- `poolId_`: pool identifier, allowed only existed and public pools; enter `“0”`;
- `amount_`: amount of tokens in WEI. (the same or less than amount you approved)

Click “**Write**” and confirm a transaction.


## What is the amount of MOR rewards earned? 
You need to go to the [Distribution](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790#readProxyContract) contract, open the “Contract” tab, then the “Read as Proxy” tab. Don't forget to connect your wallet, which should have enough native token to pay for gas.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/main/MorpheusGuide/rewards.png)

The rewards are earned every block and to check the amount, you need to call the `getCurrentUserReward` function, where you need to enter pool number (`0`) and your address (or the address of the user you want to know about). Click "**Query**". As a result, you will find out how many rewards there are at the moment. Amount is in WEI and you can use this unit converter calculator https://eth-converter.com to help you. 


## How can I get information about how much I have deposited? 
The second function will show how many tokens have been invested by the user, the parameters are similar to the previous function call. The name of the function is `usersData()`. Click "**Query**". Your deposited amount is indicated in WEI next to `deposited` line.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/main/MorpheusGuide/deposited.png)
