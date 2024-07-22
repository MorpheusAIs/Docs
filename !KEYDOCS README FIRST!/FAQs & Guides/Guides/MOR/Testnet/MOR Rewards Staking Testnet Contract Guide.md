![image](https://github.com/user-attachments/assets/6f0df0cc-2715-4b05-95ec-c569b519dd83)# MOR Rewards Staking Testnet Contract Guide

## Introduction
This guide will walk you through the process of direct interaction with the Morpheus Distribution Smart Contract on Sepolia Ethereum testnet for reward staking purpose.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

## Table of contents
1) [**Smart Contracts addresses.**](#smart-contracts-addresses)
2) [**Mint mock stETH?**](#mint-mock-steth)
3) [**Add mock stETH to Metamask.**](#add-mock-steth-to-metamask-(optional))
4) [**Stake rewards for new Capital Deposit.**]()
5) [**Stake rewards for existing Capital Deposit.**]()
6) [**Stake rewards for existing Code Weights.**]()
7) [**Check Power Factor Multiplier.**]()
8) [**Check MOR rewards stake time.**]()
9) [**Additional Guide links.**]()

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

## Stake rewards for new Capital Deposit

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
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward. If you don't want to stake MOR rewards, type `0` in the field.

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**. That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Click “**Write**” and confirm the transaction.

> [!IMPORTANT]
> **Double check the correctness of the Date to the Timestamp convertion as the operation is irreversible.**
> 
> **You will not be able to withdraw MOR rewards until the end of the staking period.**
>
> **MOR Rewards Staking period cannot be decreased, but can be increased.**
>
> **If you don't want to stake MOR rewards, just type `0` in the field `claimLockEnd_ (uint 128)`.**
>
> **Any new transaction with the Distribution contract (withdraw capital, add capital, prolong stalking) will trigger Power Factor multiplier recalculation based on conditions and stake time on the transaction execution moment.**
>
> **The transaction will ONLY stake your future rewards. Nothing changes the ability to withdraw capital contribution (beyond the normal 7 days delay). However, when you withdraw stETH, you will no longer get rewards.**
>
> **If you deposit additional stETH, the 7-days lock-up is restarted for all your deposited stETH from that address and Power multiplier is recalculated.**

---

## Stake rewards for existing Capital Deposit

If you are already a Capital Provider, i.e have stETH deposited before reward staking went live and want to stake your future rewards to gain Power Factor multiplier, please follow these steps:
- go to the [Distribution](https://etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#writeProxyContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Find and select the `6.lockClaim()` function that will stake rewards for your existing deposit.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital providers pool;
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward.

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**. That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Click “**Write**” and confirm the transaction.

> [!IMPORTANT]
> **Double check the correctness of the Date to the Timestamp convertion as the operation is irreversible.**
> 
> **You will not be able to withdraw MOR rewards until the end of the staking period.**
>
> **MOR Rewards Staking period cannot be decreased, but can be increased.**
>
> **Any new transaction with the Distribution contract (withdraw capital, add capital, prolong stalking) will trigger Power Factor multiplier recalculation based on conditions and stake time on the transaction execution moment.**
>
> **The transaction will ONLY stake your future rewards. Nothing changes the ability to withdraw capital contribution (beyond the normal 7 days delay). However, when you withdraw stETH, you will no longer get rewards.**
>
> **If you deposit additional stETH, the 7-days lock-up is restarted for all your deposited stETH from that address and Power multiplier is recalculated.**

---

## Stake rewards for existing Code Weights

If you are a Code provider and have weights assigned before reward staking went live and want to stake your future rewards to gain Power Factor multiplier, please follow these steps:
- go to the [Distribution](https://etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#writeProxyContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Find and select the `6.lockClaim()` function that will stake rewards for your existing deposit.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `1` for code contributors pool;
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward.

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**. That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Click “**Write**” and confirm the transaction.

> [!IMPORTANT]
> **Double check the correctness of the Date to the Timestamp convertion as the operation is irreversible.**
> 
> **You will not be able to withdraw MOR rewards until the end of the staking period.**
>
> **MOR Rewards Staking period cannot be decreased, but can be increased.**
>
> **Any new transaction with the Distribution contract (add weights for new contribution or decrease weights due to Weight Time expiration) will trigger Power Factor multiplier recalculation based on conditions and stake time on the transaction execution moment.**

---

## Check Power Factor Multiplier

In order to check your Power Factor multiplier directly with smart contract please follow these steps:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#readProxyContract) contract;
- open the **“Contract”** tab, then the **“Read as Proxy”** tab.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

Find and select the `3. getCurrentUserMultiplier` function and input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital contributors pool or `1` for code contributors pool;
- `user_ (address)`: paste wallet address you want to know Power Factor for.

Click “**Query**” and wait until value calculated.

On the picture you can see value `uint256 :  51255802852192050990000000`  
To convert it to more human friendly value click on it to open converter and divide MEther value by ten.  
51.3 / 10 = 5,13 Power Factor multiplier for the given address in the capital providers pool.

---

## Check MOR rewards stake time

In you want to know for how long MOR rewards are staked (if staked) for a certain address you need to:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#readProxyContract) contract;
- open the **“Contract”** tab, then the **“Read as Proxy”** tab.

Find and select the `14. usersData` function and input as parameters:
- `<input> (address)`: paste wallet address you want to know MOR rewards stake time for.
- `<input> (uint 256)`: pool identifier, enter `0` for capital contributors pool or `1` for code contributors pool;

Click “**Query**” and wait until value calculated.
The end time for staking will be indicated in the `claimLockEnd uint128` line.

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

On the picture you can see value `claimLockEnd   uint128 :  1799928036`  
To convert the Timestamp to the Date and Time you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Timestamp to Date & Time;
- paste value you got to the Timestamp field;
- click **"Convert"**.

On the picture the Timestamp **1799928036** converted to Date and Time **Jan-14-2027 12:00:36 PM**.  
Put it simply, the user staked their MOR rewards until Jan-14-2027 12:00:36 PM

<img src="/Graphics/Docs%20Graphics/English/Morpheus%20Capital%20Providers%20Contract%20Guide/deposit.png" width=70% height=70%>

---

## Additional Guide links

Here are links to the smart contract operations you might be interested in:
1. [How to claim MOR rewards.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20Rewards%20Claim%20Guide.md#how-to-claim-rewards)

2. [How to check earned MOR rewards.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20Rewards%20Claim%20Guide.md#how-much-mor-have-i-earned-as-rewards)
     
3. [How to check deposited stETH amount.]((https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/Morpheus%20Capital%20Providers%20Contract%20Guide.md#how-can-i-get-information-about-how-much-i-have-deposited)

4. [How to withdraw stETH.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/Morpheus%20Capital%20Providers%20Contract%20Guide.md#how-to-withdraw-steth-from-the-contract)

---

> [!TIP]  
> **In case you face with difficulties, find something unclear or have questions, you can get assistance in** [**Morpheus Discord server**](https://discord.com/channels/1151741790408429580/1183666837460897832).

## Beware of scams, Morpheus has no tech support team, no support tickets and will not commence any airdrops.  
## Anyone who message you with proposal to help is likely a scammer.
