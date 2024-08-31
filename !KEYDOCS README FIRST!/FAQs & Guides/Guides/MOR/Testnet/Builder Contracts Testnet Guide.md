# Builders Contract Testnet Guide

## Introduction
This guide will walk you through the process of direct interaction with the Morpheus Builder Smart Contracts on Arbitrum Sepolia for staking and claiming rewards.  
Metamask wallet is used in this guide, but for other Web3 wallets logic remains the same.

## Table of contents
1) [**Smart Contracts addresses.**](#smart-contracts-addresses)
2) [**Mint mock stETH.**](#mint-mock-steth)
3) [**Add mock stETH to Metamask.**](#add-mock-steth-to-metamask-optional)
4) [**Stake rewards for new Capital Deposit.**](#stake-rewards-for-new-capital-deposit)
5) [**Stake rewards for existing Capital Deposit.**](#stake-rewards-for-existing-capital-deposit)
6) [**Check Power Factor Multiplier.**](#check-power-factor-multiplier)
7) [**Check MOR rewards stake time.**](#check-mor-rewards-stake-time)
8) [**Additional Guide links.**](#additional-guide-links)

---

## Smart Contracts Addresses 
**Arbitrum Sepolia Testnet:**
- **MOR Contract:** [0x34a285A1B1C166420Df5b6630132542923B5b27E](https://sepolia.arbiscan.io/token/0x34a285A1B1C166420Df5b6630132542923B5b27E)
- **Builders Contract:** [0x649B24D0b6F5A4c3852fD4C0dD91308902E5fe8a](https://sepolia.arbiscan.io/address/0x649b24d0b6f5a4c3852fd4c0dd91308902e5fe8a)
- **Builders Treasury Contract:** [0x1C4b1025bf5b13e6CeD0dcf53f82ed01B5c27fB6](https://sepolia.arbiscan.io/address/0x1C4b1025bf5b13e6CeD0dcf53f82ed01B5c27fB6)
- **FeeConfig Contract:** [0x6F9ea6F9B81feEe17604F7878f1Db22134a3E56A](https://sepolia.arbiscan.io/address/0x6F9ea6F9B81feEe17604F7878f1Db22134a3E56A)
- **FeeTreasury Contract:** [0x901F2d23823730fb7F2356920e0E273EFdCdFe17](https://sepolia.arbiscan.io/address/0x901F2d23823730fb7F2356920e0E273EFdCdFe17)

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
Scroll down, find Sepolia and click **"Add to Metamask"**.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/add%20sepolia.png" width=50% height=50%>

To mint test tokens you need to:

- go to [Mock stETH Contract](https://sepolia.etherscan.io/address/0xa878Ad6FF38d6fAE81FBb048384cE91979d448DA#writeContract); 
- open the **"Contract"** tab, then the **"Write Contract"** tab;
- connect your wallet by clicking **"Connect to Web3"** button.

It is necessary to select the `4. mint ()` function that will issue tokens to your address.  
As parameters:  
- `_account (address)`: your wallet address;
- `_amount (uint256)`: amount of tokens in Wei, instead of ETH.  

> [!NOTE]
> Wei is the smallest unit of ETH.  
> One Ether = 1,000,000,000,000,000,000 Wei

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/mint%20mock%20steth.png" width=70% height=70%>

You can use https://etherscan.io/unitconverter for calculations. Enter desirable amount in the `Ether` field and copy value from the `Wei` field.   
On the screenshot, 10 stETH (or 10000000000000000000 Wei) is going to be minted.

<img src="/Graphics/Docs%20Graphics/English/MOR%20Rewards%20Staking%20Guides/Testnet/wei%20convert.png" width=70% height=70%>

Click **"Write"** and confirm the transaction in your wallet. 
