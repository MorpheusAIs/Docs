# Application Builders Contract Testnet Guide

## Introduction
This guide will walk you through the main functions of the Morpheus Application Builders Smart Contract on Arbitrum Sepolia from both, Builder and End User sides.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

---

## Table of Contents
1) [**Smart Contracts Addresses**](#smart-contracts-addresses)
### For Builders
2) [**Builder Pool Creation**](#builder-pool-creation)
3) [**Edit Builder Pool Before it Goes Live**](#edit-builder-pool-before-it-goes-live)
4) [**Get Pool Id**](#get-pool-id)
5) [**Get Information about Pool Rewards**](#get-information-pool-rewards)
6) [**Claim MOR rewards**](#claim-mor-rewards)
### For End Users
5) [**Get test MOR**](#get-test-mor)
6) [**Get Information about Builder pool**](#get-information-about-builder-pool)
7) [**Deposit test MOR to Builder pool**](#deposit-test-mor-to-builder-pool)
8) [**Get Information about Deposited MOR**](#get-information-about-deposited-mor)
9) [**Withdraw test MOR from Builder pool**](#withdraw-test-mor-from-builder-pool)
10) [**How to use Timestamp and Date converter**](#how-to-use-timestamp-and-date-converter)
11) [**How to use Unit Converter**](#how-to-use-unit-converter)

---

## Smart Contracts Addresses 
**Arbitrum Sepolia Testnet:**

- **Test MOR Contract:** [0x34a285A1B1C166420Df5b6630132542923B5b27E](https://sepolia.arbiscan.io/token/0x34a285A1B1C166420Df5b6630132542923B5b27E)
- **Builders Contract:** [0x649B24D0b6F5A4c3852fD4C0dD91308902E5fe8a](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a)

  
- **Builders Treasury Contract:** [0x1C4b1025bf5b13e6CeD0dcf53f82ed01B5c27fB6](https://sepolia.arbiscan.io/address/0x1C4b1025bf5b13e6CeD0dcf53f82ed01B5c27fB6)
- **FeeConfig Contract:** [0x6F9ea6F9B81feEe17604F7878f1Db22134a3E56A](https://sepolia.arbiscan.io/address/0x6F9ea6F9B81feEe17604F7878f1Db22134a3E56A)

---

## Builder Pool Creation
Users can deposit MOR into Builder pools, which need to be registered first.  
To create a Builder pool, please follow these steps:

- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) page;
- open the **"Contract"** tab, then select the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.
- - find and select the `2.createBuilderPool()` function, then input the following parameters:
  - `name`: choose a unique name for your pool;
  - `admin`: enter the wallet address for rewards and pool management;
  - `poolStart`: input the timestamp in the future for the pool launch;
  - `withdrawLockPeriodAfterDeposit`: enter the duration in seconds if you want to lock users' MOR after deposit;
  - `claimLockEnd`: input the timestamp for the builder reward unlock time, i.e., when you will be able to claim the pool's MOR rewards. If you don't want to stake MOR rewards, enter `0`;
  - `minimalDeposit`: set the minimum amount of MOR required to join your pool in WEI. 1 MOR = 1000000000000000000 WEI;
- click **"Write"** and confirm the transaction in your wallet.

> [!TIP]  
> **Click [here](#how-to-use-unit-converter) to learn how to use WEI Unit Converter**
> 
> **Click [here](#how-to-use-timestamp-and-date-converter) to learn how to use Timestamp and Date Converter**

<img src="https://github.com/user-attachments/assets/bf02fdba-914c-4404-bb60-7c78f5f5897a" width=80% height=80%> 

> [!IMPORTANT]  
> **You won’t be able to create a pool if the pool name has already been registered**
>
> **Once a user reaches the minimum deposit, they can continue to deposit any amount**
>
> **Lock period triggers with every deposit**

---

## Edit Builder Pool Before it Goes Live
Pool admins can edit pool parameters (except name and admin address of the pool) before it is started.  
Follow these steps:  

- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) page;
- open the **"Contract"** tab, then select the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `5.editBuilderPool()` function, then input the following parameters:
  - adjusted parameters similar to the [Builder Pool Creation](#builder-pool-creation);
- click **"Write"** and confirm the transaction in your wallet.

> [!IMPORTANT]  
> **Parameters of a pool that has already started CAN NOT be changed**
>
> **`poolStart`can not be decreased**

---

## Get Pool Id
After the pool is deployed, you will need to obtain the pool ID to allow users to deposit MOR. 
Follow these steps:  
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract ) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `11.getPoolId` function, then input the following parameters:
  - `builderPoolName_ (string)`: name of the pool;
- click **"Query"**.

> [!IMPORTANT]  
> **The pool name MUST be exactly the same you entered in the previous step**

You will find the pool Id next to `bytes32:`

<img src="https://github.com/user-attachments/assets/b3a34b65-97d6-421a-9760-77134922ef98" width=60% height=60%> 

> [!TIP]  
> **To check your pool parameters, you can use `1. builderPools` [here](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) and click "query"**

---

## Get Information about Pool Rewards
Builders can get information about accrued by their pools MOR rewards with these steps:  
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `7.getCurrentBuilderReward` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`: pool id;
- click **"Query"**.

You will find the pool Id next to `uint256:`

> [!TIP]  
> **To convert value, click on it and find `ETH (1)` field in the opened window**

<img src="https://github.com/user-attachments/assets/911cec9b-7088-41d9-9b7e-ba909ca34bb8" width=60% height=60%> 

---

## Claim MOR Rewards
If rewards were not staked with the `claimLockEnd` function when the pool was created, Builders can claim MOR rewards by following these steps:
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) page;
- open the **"Contract"** tab, then select the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `2.claim()` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`: pool id;
  - `receiver_ (address)`: address on the Arbitrum Sepolia chain where you want to receive the rewards;
- click **"Write"** and confirm the transaction in your wallet.

<img src="https://github.com/user-attachments/assets/f39b0ccd-d880-4da9-ad9e-1a7e7dc02053" width=60% height=60%> 

> [!IMPORTANT]
> **A 2% fee will be charged on the claim amount as payment to the Morpheus Protocol-Owned Liquidity.**

---

## Get Test MOR


---

## Get Information about Builder Pool

---

## Deposit Test MOR to Builder Pool

---

## Get Information about Deposited MOR

---

## Withdraw test MOR from Builder Pool
+ fees

---

## How to use Timestamp and Date Converter
### To convert Data & Time to Timestamp: 
- visit **https://etherscan.io/blockdateconverter**;
- select Timestamp & Date;
- select Date & Time to Timestamp;
- set the Date & Time you want to convert and click **"Convert"**.

On the picture Date **Jul-22-2025 12:00:59 PM UTC** is converted to the Timestamp **1753185659**.  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/date%20to%20timestamp.png" width=70% height=70%>

### To convert Timestamp to Data & Time:
- visit **https://etherscan.io/blockdateconverter**;
- select Timestamp & Date;
- select Timestamp to Data & Time;
- paste the Timestamp you want to convert and click **"Convert"**.

On the picture the Timestamp **1753185659** is converted to the Date & Time **Jul-22-2025 12:00:59 PM UTC**  .  

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/timestamp%20to%20date(new).png" width=70% height=70%>

---

## How to use Unit Converter
To convert values to WEI and vice versa you can use **https://etherscan.io/unitconverter**.  

Enter desirable amount in the `Ether` field and copy value from the `Wei` field or enter amount in the `Wei` field and copy value from the `Ether` field.

For example, on the screenshot, 10 ETH represented as 10000000000000000000 Wei.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/wei%20convert.png" width=70% height=70%>
