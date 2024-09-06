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
5) [**Get Information about Pool Rewards**](#get-information-about-pool-rewards)
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
  - `claimLockEnd`: input the timestamp for the builder reward unlock time, i.e., when you will be able to claim the pool's MOR rewards. If you don't want to stake MOR rewards and get power factor, enter `0`;
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
After the pool is deployed, you will need to obtain the Pool ID to allow users to deposit MOR. 
Follow these steps:  
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract ) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `11.getPoolId` function, then input the following parameters:
  - `builderPoolName_ (string)`: name of the pool;
- click **"Query"**.

> [!IMPORTANT]  
> **The pool name MUST be exactly the same you entered in the previous step**

You will find the Pool ID next to `bytes32:`

<img src="https://github.com/user-attachments/assets/b3a34b65-97d6-421a-9760-77134922ef98" width=60% height=60%> 

> [!TIP]  
> **To check your pool parameters, you can use `1. builderPools` [here](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) and click "query"**

---

## Get Information about Pool Rewards
Builders can get information about accrued by their pools MOR rewards with these steps:  
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `7.getCurrentBuilderReward` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`: Builder Pool ID you want to get information about;
- click **"Query"**.

You will find the Pool ID next to `uint256:`

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
  - `builderPoolId_ (bytes32)`: Pool ID you want to claim MOR rewards from;
  - `receiver_ (address)`: address on the Arbitrum Sepolia chain where you want to receive the rewards;
- click **"Write"** and confirm the transaction in your wallet.

<img src="https://github.com/user-attachments/assets/f39b0ccd-d880-4da9-ad9e-1a7e7dc02053" width=60% height=60%> 

> [!IMPORTANT]
> **A 2% fee will be charged on the claim amount as payment to the Morpheus Protocol-Owned Liquidity**

---

## Get Test MOR
To test the Contract as the End User, you will need test MOR.  

There are two ways to obtain it:
- claim it as a reward if you participated in [code](https://github.com/antonbosss/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Testnet/Code%20Rewards%20Staking%20Testnet%20Guide.md) or [capital](https://github.com/antonbosss/Docs/blob/main/!KEYDOCS%20README%20FIRST!/FAQs%20%26%20Guides/Guides/MOR/Testnet/Capital%20Rewards%20Staking%20Testnet%20Guide.md) rewards staking and have it unlocked;
- ask @antonb to send you some. 

---

## Get Information about Builder Pool
To stake MOR towards a Builder Pool, you must know the Pool ID.  
If you want to check the pool conditions such as the admin address, start time, MOR deposit lock status, whether the Builder’s MOR rewards are staked, and the minimum deposit, please follow these steps:
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `1. builderPools` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`: Pool ID you want to get information about;
- click **"Query"**.

You will find the relevant pool details under the `[ builderPools(bytes32) method Response ]` line.

> [!TIP]  
> **To understand what each parameter means head to the [**Builder Pool Creation**](#builder-pool-creation) section**

<img src="https://github.com/user-attachments/assets/0d327cc8-4997-44bb-98b6-1529b16d5164" width=60% height=60%> 

---

## Deposit Test MOR to Builder Pool
The process consists of two steps.  
### Step 1. Approve the Builder Contract to Use Your Test MOR Tokens.
Before depositing, you need to give the Builder contract approval to use your test MOR tokens.  
Follow these steps:
- go to the Arbitrum Sepolia [test MOR Contract](https://sepolia.arbiscan.io/token/0x34a285A1B1C166420Df5b6630132542923B5b27E) page;
- open the **"Contract"** tab, then select the **"Write Contract"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `1.approve()` function, then input the following parameters:
  - `spender (address)`: **Builders Contract** address `0x649B24D0b6F5A4c3852fD4C0dD91308902E5fe8a`;
  - `amount (uint256)`: amount of tokens in WEI. 1 MOR = 1000000000000000000 WEI. Should be more or equal to the amount you want to deposit. 
- click **"Write"** and confirm the transaction in your wallet.

> [!TIP]  
> **Click [here](#how-to-use-unit-converter) to use WEI Unit Converter**

<img src="https://github.com/user-attachments/assets/6ad245c2-b46e-49d8-af05-514455376187" width=60% height=60%> 

### Step 2. Deposit MOR to a Builder Pool.
The next step is MOR deposit into a Builder pool:
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) page;
- open the **"Contract"** tab, then select the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `4.deposit()` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`:  Pool ID where you want to deposit MOR;
  - `amount (uint256)`: amount of tokens in WEI. 1 MOR = 1000000000000000000 WEI. Should be less or equal to the amount you approved at previous step. 
- click **"Write"** and confirm the transaction in your wallet.

<img src="https://github.com/user-attachments/assets/e98aed41-fc95-4c92-af5f-aa8a5f70c7cf" width=60% height=60%> 

> [!IMPORTANT]
> **You can not deposit amount less than minimum set by the Pool owner**
> **Builders have the discretion to decide how to incentivize their users to stake MOR and determine what benefits to provide**

---

## Get Information about Deposited MOR
If you want to know amount of MOR deposited in a Builders pool, follow these steps: 
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#readProxyContract) page;
- open the **"Contract"** tab, then select the **"Read as Proxy"** tab;
- find and select the `17.usersData` function, then input the following parameters:
  - `user (address)`: address you want to get information about ;
  - `builderPoolId (bytes32)`: Builder Pool ID where MOR is deposited;
- click **"Query"**.

You will find deposited amount next to `**deposited** uint256:`

> [!TIP]  
> **To convert value, click on it and find `ETH (1)` field in the opened window**

<img src="https://github.com/user-attachments/assets/0b77a1a6-df77-4e81-ad3a-4d5132125a3e" width=60% height=60%>

---

## Withdraw test MOR from Builder Pool
If your MOR deposit is not locked according to the Builder Pool settings, you can withdraw it by following these steps:
- go to the Arbitrum Sepolia [Builders Contract](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a#writeProxyContract) page;
- open the **"Contract"** tab, then select the **"Write as Proxy"** tab;
- connect your wallet by clicking the **"Connect to Web3"** button;
- find and select the `14.withdraw()` function, then input the following parameters:
  - `builderPoolId_ (bytes32)`: Pool ID you want to withdraw MOR from;
  - `amount_ (uint256)`: amount of tokens in WEI. (1 MOR = 1000000000000000000 WEI);
- click **"Write"** and confirm the transaction in your wallet.

> [!TIP]  
> **Click [here](#how-to-use-unit-converter) to use WEI Unit Converter**

<img src="https://github.com/user-attachments/assets/ce526392-ad3f-4fd9-8923-d9b6428d09cf" width=60% height=60%> 

> [!IMPORTANT]
> **A 1% fee will be charged on the claim amount as payment to the Morpheus Protocol-Owned Liquidity**
> **If you do a partial withdrawal, the remaining balance must be greater than the minimum pool deposit**

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
