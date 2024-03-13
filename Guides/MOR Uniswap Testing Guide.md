# MOR Uniswap Testing Guide

## Introduction
This guide will walk you through the testing main Uniswap functions for Mock MOR and Mock wETH tokens on the Ethereum Sepolia testnet. There are following steps:
1) Obtaining SepoliaETH
2) Obtaining Mock MOR and wETH tokens
3) Swapping tokens on Uniswap
4) Adding and removing liquidity

## Smart Contracts Addresses
Ethereum Sepolia 
- MOR Mock: [0x781e74ab59498c9b710e1f00512a3d0a747e7fa0](https://sepolia.etherscan.io/address/0x781e74ab59498c9b710e1f00512a3d0a747e7fa0#code) 
- wETH Mock: [0x1f233de18d7bfc28dffe05574627606d2a938a43](https://sepolia.etherscan.io/address/0x1f233de18d7bfc28dffe05574627606d2a938a43#code)
  
## How to get Sepolia ETH?
- To start you should have installed Metamask or another web3 wallet. You need to go to network settings which by default are usually set to Ethereum, then choose the Sepolia testnet as the network.
- The next step is to fund your address with SepoliaETH. You may use a website like https://sepolia-faucet.pk910.de/# or https://sepoliafaucet.com/ to earn SepoliaETH if you are using a fresh address.

## How to mint Mock tokens?
Please note that testing is carried out on the Sepolia testnet, but the mainnet token will be launched on the Arbitrum chain.  
When you got some SepoliaETH to pay network fees, you need to go to the [MOR Mock](https://sepolia.etherscan.io/address/0x781e74ab59498c9b710e1f00512a3d0a747e7fa0#writeContract) contract, open the “Contract” tab, then the “Write Contract” tab. Don't forget to connect your wallet.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stake.png)

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH. You can use this unit converter calculator https://eth-converter.com to help you.

Click `Write` and confirm a transaction. 

Perform the same actions with [MOR wETH](https://sepolia.etherscan.io/address/0x1f233de18d7bfc28dffe05574627606d2a938a43#readContract) contract.

## How can I see tokens in my wallet?
For Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and fill  
MOR Mock `0x781e74ab59498c9b710e1f00512a3d0a747e7fa0` and  
wETH Mock `0x1f233de18d7bfc28dffe05574627606d2a938a43` contract addresses

## How to connect to Uniswap on Sepolia testnet?
Go to the https://app.uniswap.org/pool 

Connect your wallet (Up right corner)

Click to your address (The same position)

Click to the settings button (Up right corner)

Turn on “Show testnets”

Change the network to “Sepolia” (the 3rd in the list)

## How to swap tokens on Uniswap?
Go to the https://app.uniswap.org/swap and add tokens you want to swap.

Click on "You pay" token 

Enter wETH Mock contract address `0x1f233de18d7bfc28dffe05574627606d2a938a43` 

Click on the token to add it

Perform the same actions with "You receive field", but add MOR Mock token address `0x781e74ab59498c9b710e1f00512a3d0a747e7fa0`

Enter the amount you want to swap and click `Swap`

Approve the amount you want to spend, sign message and confirm swap.

After swap transaction is confirmed, you will see updated balances.  
Make multiple swaps with different combinations of tokens and amounts.


## How to add liquidity tokens to Uniswap?


## How to remove liquidity from Uniswap?

