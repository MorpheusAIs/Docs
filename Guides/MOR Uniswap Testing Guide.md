# MOR Token Uniswap Testing Guide

>[!NOTE]
> - The purpose of the testing is to familiarize users with the swapping process and liquidity operations of the Uniswap decentralized exchange, as well as to identify any issues that users may encounter.  
> - This testing is conducted on the Arbitrum mainnet. Completing all the steps may require $1-3 in ETH for fees.  
> - Please note that this testing is not incentivized, and participants will not receive any rewards.  

## Introduction
This guide will walk you through the testing main Uniswap functions as swap tokens, add, remove, increase and decrease liquidity with Metamask wallet.

There are following steps:
1) Obtaining test tokens
2) Adding tokens to Metamask and connecting to Uniswap
3) Swapping tokens
3) Adding and removing liquidity
5) Increasing and decresing added liquidity

## Smart Contracts Addresses
Arbitrum mainnet chain: 
MOR_Test_1 (MT1): [0x84efb4db4265966742fa3671aa841a8f21dd2d4f](https://arbiscan.io/token/0x84efb4db4265966742fa3671aa841a8f21dd2d4f)
WETH_Test_1 (WT1): [0x3b0a436dc056fd17901922147dc1d2f557b81edd](https://arbiscan.io/token/0x3b0a436dc056fd17901922147dc1d2f557b81edd)
USDT_Test_1 (UT1): https://arbiscan.io/token/0x3d83ba928974e07f35a246d50eae0ae269baef16
ARB_Test_1 (AT1): https://arbiscan.io/token/0xd1e404c02f73c2c9cbadaf400028690f466fe206

  
## Get Sepolia ETH
- To start you should have installed Metamask or another web3 wallet. You need to go to network settings which by default are usually set to Ethereum, then choose the Sepolia testnet as the network.
- The next step is to fund your address with SepoliaETH. You may use a website like https://sepolia-faucet.pk910.de/# or https://sepoliafaucet.com/ to earn SepoliaETH if you are using a fresh address.

## Mint Mock tokens
Please note that testing is carried out on the Sepolia testnet, but the mainnet token will be launched on the Arbitrum chain.  
When you got some SepoliaETH to pay network fees, you need to go to the [MOR] contract, open the “Contract” tab, then the “Write Contract” tab and connect your wallet.

[PICTURE]

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH. You can use this unit converter calculator https://eth-converter.com to help you.

Click `Write` and confirm a transaction. 

Perform the same actions with [MOR wETH](https://sepolia.etherscan.io/address/0x1f233de18d7bfc28dffe05574627606d2a938a43#writeContract) contract.

## Add tokens and send tokens from the wallet
For Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and fill  
MOR Mock `0x781e74ab59498c9b710e1f00512a3d0a747e7fa0` and  
wETH Mock `0x1f233de18d7bfc28dffe05574627606d2a938a43` contract addresses

## How to connect to Uniswap on Sepolia testnet?
Go to the https://app.uniswap.org and connect your wallet

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Uniswap connect wallet.png" width=100% height=100%>

Click to your address and then settings button

<<img src="/Graphics/Docs Graphics/English/Uniswap guide/Settings button.png" width=100% height=100%>

Turn on “Show testnets”

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Show testnets.png" width=100% height=100%>

Change the network to “Sepolia” (the 3rd in the list)

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Choose Sepolia.png" width=100% height=100%>

## How to swap tokens on Uniswap?
Go to the https://app.uniswap.org/swap and add tokens you want to swap.

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Add Mock tokens.png" width=60% height=60%>

Click on **"You pay"** token and enter wETH Mock contract address `0x1f233de18d7bfc28dffe05574627606d2a938a43`.  
Click on the token to add it. If warning message appears, click `I understand`. 

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Add Mock wETH.png" width=60% height=60%>

Perform the same actions with **"You receive"** field, and add MOR Mock token address `0x781e74ab59498c9b710e1f00512a3d0a747e7fa0`

<img src="/Graphics/Docs Graphics/English/Uniswap guide/Add Mock MOR.png" width=60% height=60%>

Enter the amount you want to swap and click `Swap`



Approve the amount you want to spend, sign message and confirm swap.



After swap transaction is confirmed, you will see updated balances.  
Make multiple swaps with different combinations of tokens and amounts.


## How to add liquidity to Uniswap?
Go to https://app.uniswap.org/pool 

Click `+New position`

Add MOR Mock and wETH Mock tokens by entering their smart conctract addresses



## How to increase or decrease liquidity on Uniswap?


## How to remove liquidity from Uniswap?




Additional info
- what are dexs
- https://academy.binance.com/en/articles/impermanent-loss-explained 
https://support.uniswap.org/hc/en-us/articles/8370549680909-How-to-swap-tokens-with-the-Uniswap-Web-app 
