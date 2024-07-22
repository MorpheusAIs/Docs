# MOR Rewards Staking Mainnet Contract Guide

## Introduction
This guide will walk you through the process of direct interaction with the Morpheus Distribution Smart Contract on Sepolia Ethereum testnet for reward staking purpose.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

## Table of contents
1) [**Smart Contracts addresses.**](#smart-contracts-addresses)
2) [**Stake rewards for new Capital Deposit.**](#stake-rewards-for-new-capital-deposit)
3) [**Stake rewards for existing Capital Deposit.**](#stake-rewards-for-existing-capital-deposit)
4) [**Stake rewards for existing Code Weights.**](#stake-rewards-for-existing-code-weights)
5) [**Check Power Factor Multiplier.**](#check-power-factor-multiplier)
6) [**Check MOR rewards stake time.**](#check-mor-rewards-stake-time)
7) [**Additional Guide links.**](#additional-guide-links)

---

## Smart Contracts Addresses 

**Ethereum Mainnet:**

- Morpheus Distribution Contract: [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790)

- stETH Contract:  

---

## Stake rewards for new Capital Deposit

Before contributing mock stETH, you need to give the Distribution contract an **approval**, for this you need to:
- go to the [mock stETH Contract](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

Select the `1.approve()` function that will add allowance for the Distribution contract to spend users' mock stETH.  
Input as parameters:
- `spender`: **Distribution contract** address: `0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790`;
- `amount`: amount of tokens in Wei. Should be more or equal to the amount of mock stETH you want to deposit.
  
> [!NOTE]
> Wei is the smallest unit of ETH. One ether = 1,000,000,000,000,000,000 Wei

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/approve.png" width=70% height=70%>

You can use **https://etherscan.io/unitconverter** for calculations. Enter desirable amount in the `Ether` field and copy value from the `Wei` field.   
On the screenshot, 10 stETH (or 10000000000000000000 in WEI) is going to be minted.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/wei%20convert.png" width=70% height=70%>

Click “**Write**” and confirm the transaction.

After confirmation, you need to:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7C46d6BEBF3DCd902Eb431054E59908a02Aba524#writeProxyContract) contract;
- open the **“Contract”** tab, then the **“Write as Proxy”** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.  

Find and select the `10.stake()` function that will deposit stETH tokens into the smart contract.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital providers pool;
- `amount_ (uint 256)`: amount of tokens in Wei. (the same or less than amount you approved).
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward. If you don't want to stake MOR rewards, type `0` in the field.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/stake.png" width=70% height=70%>

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**.  
That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/date%20to%20timestamp.png" width=70% height=70%>

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

Find and select the `6.lockClaim()` function that will stake rewards for your existing deposit.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital providers pool;
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/capital%20lockclaim.png" width=70% height=70%>

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**.  
That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/date%20to%20timestamp.png" width=70% height=70%>

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

Find and select the `6.lockClaim()` function that will stake rewards for your existing deposit.   
Input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `1` for code contributors pool;
- `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/weights%20lockclaim.png" width=70% height=70%>

To convert Data to Timestamp and vice versa you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** converted to the Timestamp **1753185659**.  
That effectively means that the user stake their MOR rewards until Jul-22-2025 12:00:59 PM UTC.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/date%20to%20timestamp.png" width=70% height=70%>

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

Find and select the `3. getCurrentUserMultiplier` function and input as parameters:
- `poolId_ (uint 256)`: pool identifier, enter `0` for capital contributors pool or `1` for code contributors pool;
- `user_ (address)`: paste wallet address you want to know Power Factor for.

Click “**Query**” and wait until value calculated.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/user%20multiplier.png" width=70% height=70%>

On the picture you can see value `uint256 :  51255802852192050990000000`  
To convert it to more human friendly value click on it to open converter and divide MEther value by ten.  
`51.3 / 10 = 5,13` Power Factor multiplier for the given address in the capital providers pool.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/convert%20multiplier.png" width=60% height=60%>

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

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/claimlockend.png" width=60% height=60%>

On the picture you can see value `claimLockEnd   uint128 :  1799928036`  
To convert the Timestamp to the Date and Time you can use **https://etherscan.io/blockdateconverter**:
- select Timestamp & Date;
- select Timestamp to Date & Time;
- paste value you got to the Timestamp field;
- click **"Convert"**.

On the picture the Timestamp **1799928036** converted to Date and Time **Jan-14-2027 12:00:36 PM**.  
Put it simply, the user staked their MOR rewards until Jan-14-2027 12:00:36 PM

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/timestamp%20to%20date.png" width=60% height=60%>

---

## Additional Guide links

Here are links to the smart contract operations you might be interested in:
1. [How to claim MOR rewards.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20Rewards%20Claim%20Guide.md#how-to-claim-rewards)

2. [How to check earned MOR rewards.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/MOR%20Rewards%20Claim%20Guide.md#how-much-mor-have-i-earned-as-rewards)
     
3. [How to check deposited stETH amount.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/Morpheus%20Capital%20Providers%20Contract%20Guide.md#how-can-i-get-information-about-how-much-i-have-deposited)

4. [How to withdraw stETH.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Mainnet/Morpheus%20Capital%20Providers%20Contract%20Guide.md#how-to-withdraw-steth-from-the-contract)

---

> [!TIP]  
> **In case you face with difficulties, find something unclear or have questions, you can get assistance in** [**Morpheus Discord server**](https://discord.com/channels/1151741790408429580/1183666837460897832).

## Beware of scams, Morpheus has no tech support team, no support tickets and will not commence any airdrops.  
## Anyone who message you with proposal to help is likely a scammer.
