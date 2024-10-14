# Application Builders Contract Testnet Guide

## Introduction
This guide will walk you through the main functions of the Morpheus Application Builders Smart Contract on Arbitrum Sepolia from both, Builder and End User sides.

---

## Table of Contents
1) [**Smart Contracts Addresses**](#smart-contracts-addresses)
2) [**Mint mock stETH**](#mint-mock-steth)
3) [**Deposit stETH with Referral Address**](#deposit-steth-with-referral-address)
4) [**Check Referral Bonus**](#check-referral-bonus)
5) [**Check Referral Rewards**](#check-referral-rewards)
6) [**Claim Referral Rewards**](#claim-referral-rewards)
7) [**How to Use Unit Converter**](#how-to-use-unit-converter)
8) [**How to use Timestamp and Date converter**](#how-to-use-timestamp-and-date-converter)

---

## Smart Contracts Addresses 
**Arbitrum Sepolia Testnet:**

- **Test MOR Contract:** [0x34a285A1B1C166420Df5b6630132542923B5b27E](https://sepolia.arbiscan.io/token/0x34a285A1B1C166420Df5b6630132542923B5b27E)
  
**Ethereum Sepolia Testnet:**

- **Distribution Contract:** [0x7c46d6bebf3dcd902eb431054e59908a02aba524](https://sepolia.etherscan.io/address/0x7c46d6bebf3dcd902eb431054e59908a02aba524)

- **Mock stETH Contract:** [0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA)

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
If you don't have it added to your wallet, you can use this [link](https://chainlist.org/?testnets=true&search=Sepolia).  
Scroll down, find Sepolia and click **Add to Metamask**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/add%20sepolia.png" width=50% height=50%>

To mint mock stETH, please follow these steps:
- go to the [Mock stETH Contract](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract); 
- open the **Contract** tab, then the **Write Contract** tab;
- connect your wallet by clicking the **Connect to Web3** button;
- find and select the `4. mint ()` function, then input the following parameters:
  - `_account (address)`: your wallet address;
  - `_amount (uint256)`: amount of tokens in Wei, instead of ETH. 
- click **Write** and confirm the transaction in your wallet.

> [!TIP]  
> **Click [here](#how-to-use-unit-converter) to learn how to use WEI Unit Converter**

<img src="https://github.com/user-attachments/assets/f2636955-5498-41f6-ad83-9d30d1256f19" width=60% height=60%> 

---
## Deposit stETH with Referral Address
The process is quite similar to normal stETH deposit.  
Before depositing stETH, you need to give the Morpheus Distribution contract an **Approval**, for this you need to follow these steps:
- go to the [mock stETH](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract) contract;
- open the **Contract** tab, then the **Write Contract** tab;
- connect your wallet by clicking the **Connect to Web3** button;
- find and select the `3.approve()` function and input the following parameters:
  - `_spender (address)`: **Distribution contract** address: `0x7c46d6bebf3dcd902eb431054e59908a02aba524`;
  - `_amount (uint256)`: amount of tokens in Wei. Should be more or equal to the amount of stETH you want to deposit;
- click **Write** and confirm the transaction.
  
> [!TIP]  
> **Click [here](#how-to-use-unit-converter) to learn how to use WEI Unit Converter**

<img src="https://github.com/user-attachments/assets/b5c2983f-fc4b-4032-83ee-4b3844bf4a0d" width=60% height=60%> 

After confirmation, you need to:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7c46d6bebf3dcd902eb431054e59908a02aba524#writeProxyContract) contract;
- open the **Contract** tab, then the **Write as Proxy** tab;
- connect your wallet by clicking the **Connect to Web3** button;  
- Find and select the `13.stake()` function that will deposit stETH tokens into the smart contract and input the following parameters:   
  - `poolId_ (uint 256)`: enter `0` for capital providers pool;
  - `amount_ (uint 256)`: amount of tokens in Wei. (the same or less than amount you approved);
  - `claimLockEnd_ (uint 128)`: timestamp of the reward unlock time, i.e. when you will be able to claim your MOR reward. If you don't want to stake MOR rewards, type `0` in the field;
  - `referrer_` (address): the address of the user you want to assign as referer or enter `0` if there is no referrer;
- click **Write** and confirm the transaction.

> [!TIP]  
> **Click [here](#how-to-use-timestamp-and-date-converter) to learn how to use Timestamp and Date Converter**

<img src="https://github.com/user-attachments/assets/f72b33b3-b07e-4543-b387-5c80034befcb" width=75% height=75%> 

---

## Check Referral Bonus
You can check the referral bonus for and address by following these steps:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7c46d6bebf3dcd902eb431054e59908a02aba524#readProxyContract) contract;
- open the **Contract** tab, then select the **Read as Proxy** tab;
- find and select the `7. getReferrerMultiplier` function, then input the following parameters:
  - `poolId_ (uint256)`: enter `0` for capital providers pool;
  - `referrer_ (address)`: the address you want to know referral bonus for;
- click **Query**.

> [!TIP]  
> **To convert value, click on it, find `MEther` and multiply it by ten**

<img src="https://github.com/user-attachments/assets/559cbd4f-1116-4b5e-98ce-5af9d42cac4c" width=60% height=60%> 

---

## Check Referral Rewards

You can check the referral bonus for and address by following these steps:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7c46d6bebf3dcd902eb431054e59908a02aba524#readProxyContract) contract;
- open the **Contract** tab, then select the **Read as Proxy** tab;
- find and select the `3. getCurrentReferrerReward` function, then input the following parameters:
  - `poolId_ (uint256)`: enter `0` for capital providers pool;
  - `referrer_ (address)`: the address you want to know referral reward for;
- click **Query**.

> [!TIP]  
> **To convert value, click on it and find `ETH (1)` field in the opened window**

<img src="https://github.com/user-attachments/assets/11bcd917-6569-4fb4-89d1-21ed57195865" width=75% height=75%> 

---

## Claim Referral Rewards
Referral rewards are separated from other bucket rewards and unlocked.  
To claim them, please follow these steps:
- go to the [Distribution](https://sepolia.etherscan.io/address/0x7c46d6bebf3dcd902eb431054e59908a02aba524#writeProxyContract) contract;
- open the **Contract** tab, then the **Write as Proxy** tab;
- connect your wallet by clicking the **Connect to Web3** button;  
- Find and select the `4.claimReferrerTier()` and input the following parameters:   
  - `claimReferrerTier`: specify the amount of native token in ETH that you will send with the transaction and that will be used as payment for the gas for a mint on the destination network, 0.01 should be enough in majority of cases;
  - `poolId_(uint256)`: enter `0` for capital providers pool;
  - `receiver_(address)`: the address that will get MOR rewards on Arbitrum Sepolia chain;
- click **Write** and confirm the transaction.

>[!NOTE]
> It may take a few minutes for your rewards to appear in your wallet on the Arbitrum Sepolia chain.|

<img src="https://github.com/user-attachments/assets/102ffabd-373a-49d1-8a74-027beb6f481c" width=85% height=85%>

---

## How to use Unit Converter
To convert values to WEI and vice versa you can use **https://etherscan.io/unitconverter**.  

Enter desirable amount in the `Ether` field and copy value from the `Wei` field or enter amount in the `Wei` field and copy value from the `Ether` field.

For example, on the screenshot, 10 ETH represented as 10000000000000000000 Wei.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/wei%20convert.png" width=70% height=70%>

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
