# Application Builders Contract Testnet Guide

## Introduction
This guide will walk you through the main functions of the Morpheus Application Builders Smart Contract on Arbitrum Sepolia from both, Builder and End User sides.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

---

## Table of Contents
1) [**Smart Contracts Addresses**](#smart-contracts-addresses)
## For Builders
2) [**Builder Pool Creation**](#builder-pool-creation)
3) [**Get Pool Id**](#get-pool-id)
4) [**Edit builder pool before it goes live**](#edit-builder-pool-before-it-goes-live)
5) [**Get MOR rewards**](#get-mor-rewards)
## For End Users
6) [**Get test MOR**](#check-power-factor-multiplier)
7) [**Get information about Builder pool**](#get-information-about-builder-pool)
8) [**Deposit test MOR to Builder pool**](#deposit-test-mor-to-builder-pool)
9) [**Withdraw test MOR from Builder pool**](#withdraw-test-mor-from-builder-pool)
10) [**How to use Timestamp and Date converter**](#how-to-use-timestamp-and-date-converter)

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

- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) contract;
- open the **"Contract"** tab, then the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button.

Find and select the `2.createBuilderPool()` function and input the following parameters under `builderPool_(tuple)`:
- `name`: choose a unique name for your pool;
- `admin`: enter the wallet address for rewards and pool management;
- `poolStart`: input the timestamp in the future for the pool launch; 
- `withdrawLockPeriodAfterDeposit`: enter the duration in seconds if you want to lock users' MOR after deposit;
- `claimLockEnd`: input the timestamp for the builder reward unlock time, i.e., when you will be able to claim the pool's MOR rewards. If you don't want to stake MOR rewards, enter `0`;
- `minimalDeposit`: set the minimum amount of MOR required to join your pool.

> [!NOTE]  
> **Click [here](#how-to-use-timestamp-and-date-converter) to learn how to use Timestamp and Date Converter**

<img src="https://github.com/user-attachments/assets/bf02fdba-914c-4404-bb60-7c78f5f5897a" width=80% height=80%> 

Click **"Write"** and confirm the transaction in your wallet.

---

## Get Pool Id
After the pool is deployed, you will need to obtain the pool ID to allow users to deposit MOR. 
Follow these steps:  
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract ) contract;
- open the **"Contract"** tab, then the **"Read as Proxy"** tab;
- find and select the `11.getPoolId` function;
- input the name of your pool under `builderPoolName_ (string)` field;
- click **"Query"**.

You will find the pool Id next to `bytes32:`

<img src="https://github.com/user-attachments/assets/b3a34b65-97d6-421a-9760-77134922ef98" width=60% height=60%> 

> [!IMPORTANT]  
> **The pool name MUST be exactly the same you entered in the previous step**

---

## Edit Builder Pool Before it Goes Live
Pool admins can edit pool parameters (except name of the pool) before it is started.  
Follow these steps:  

- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) contract;
- open the **"Contract"** tab, then the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `5.editBuilderPool()` function;
- fill in new parameters similar to [Builder Pool Creation](#builder-pool-creation)

> [!IMPORTANT]  
> **Parameters of a pool that has already started CAN NOT be changed**

---

## Get MOR rewards

+ fees

---

## Get test MOR

---

## Get information about Builder pool

---

## Deposit test MOR to Builder pool

---

## Withdraw test MOR from Builder pool
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
