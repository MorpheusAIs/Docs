# MOR Token Uniswap Testing Guide

>[!NOTE]
> - The purpose of the testing is to familiarize users with the swapping process and liquidity operations of the Uniswap decentralized exchange, as well as to identify any issues that users may encounter.  
> - This testing is conducted on the Arbitrum mainnet. Completing all the steps may require $1-3 in ETH for fees.  
> - Please note that this testing is not incentivized, and participants will not receive any rewards.
> - Test tokens have no value and intended fot test purpose only.



## Introduction
This guide will walk you through the testing main Uniswap functions as swap tokens, add, remove, increase and decrease liquidity with Metamask wallet.

There are following steps:
1) Obtaining test tokens
2) Adding tokens to Metamask
3) Connecting to Uniswap
4) Swapping tokens
5) Adding and removing liquidity
6) Increasing and decresing added liquidity



## Smart Contracts Addresses
Arbitrum mainnet:  
**MOR_Test_1 (MT1):** [0x84efb4db4265966742fa3671aa841a8f21dd2d4f](https://arbiscan.io/token/0x84efb4db4265966742fa3671aa841a8f21dd2d4f)  

**WETH_Test_1 (WT1):** [0x3b0a436dc056fd17901922147dc1d2f557b81edd](https://arbiscan.io/token/0x3b0a436dc056fd17901922147dc1d2f557b81edd)  

**USDT_Test_1 (UT1):** [0x3d83ba928974e07f35a246d50eae0ae269baef16](https://arbiscan.io/token/0x3d83ba928974e07f35a246d50eae0ae269baef16)  

**ARB_Test_1 (AT1):** [0xd1e404c02f73c2c9cbadaf400028690f466fe206](https://arbiscan.io/token/0xd1e404c02f73c2c9cbadaf400028690f466fe206)  

## Switch Metamask to Arbitrum chain
You should choose Arbitrum chain in the chain list or add it using [Chainlist](https://chainlist.org/chain/42161) service and clicking **“Add to Metamask”**.  

You need to have $1-3 in ETH for fees. You can bridge ETH from other chain or buy it on CEX. 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/change%20chain.png" width=50% height=50%>



## Mint Test tokens
Test tokens have no value and intended for test purpose only.  

> [!IMPORTANT]  
> You can get tokens by asking in [Discord](https://discord.com/channels/1151741790408429580/1183666837460897832) or mint them yourself.  

To mint test tokens you need to go to the [MOR_Test_1 (MT1) token contract](https://arbiscan.io/token/0x84efb4db4265966742fa3671aa841a8f21dd2d4f), open the **“Contract”** tab, then the **“Write Contract”** tab and connect your wallet by clicking **"Connect to Web3**" button.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/mint.png" width=75% height=75%>

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH.  
You can use this unit converter calculator https://eth-converter.com to help you.

Click **"Write"** and confirm a transaction. 

Perform the same actions with:
- **WETH_Test_1 (WT1) Contract** [0x3b0a436dc056fd17901922147dc1d2f557b81edd](https://arbiscan.io/token/0x3b0a436dc056fd17901922147dc1d2f557b81edd)
  
- **USDT_Test_1 (UT1) Contract** [0x3d83ba928974e07f35a246d50eae0ae269baef16](https://arbiscan.io/token/0x3d83ba928974e07f35a246d50eae0ae269baef16)
  
- **ARB_Test_1 (AT1) Contract** [0xd1e404c02f73c2c9cbadaf400028690f466fe206](https://arbiscan.io/token/0xd1e404c02f73c2c9cbadaf400028690f466fe206)  



## Add tokens to Metamask 
To add tokens to Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add smart contracts addresses:    

**MOR_Test_1 (MT1):** `0x84efb4db4265966742fa3671aa841a8f21dd2d4f`  

**WETH_Test_1 (WT1):** `0x3b0a436dc056fd17901922147dc1d2f557b81edd`  

**USDT_Test_1 (UT1):** `0x3d83ba928974e07f35a246d50eae0ae269baef16`  

**ARB_Test_1 (AT1):** `0xd1e404c02f73c2c9cbadaf400028690f466fe206`

After these steps you will be able to see the tokens and their amount in your Metamask wallet.



## Connect wallet to Uniswap
Go to the Uniswap web app https://app.uniswap.org and choose Arbitrum chain in the top right corner of the screen.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/arb.png" width=100% height=100%>

Click **"Connect"** button 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/connect1.png" width=100% height=100%>

Select the wallet you would like to connect and approve the connection.  
Once approved your wallet will be connected!

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/connect2.png" width=100% height=100%>



## How to swap tokens on Uniswap?
Go to the Uniswap web app https://app.uniswap.org/swap and search for and select the token you wish to swap.

`0x84efb4db4265966742fa3671aa841a8f21dd2d4f` for **MOR_Test_1 (MT1)** 

`0x3b0a436dc056fd17901922147dc1d2f557b81edd` for **WETH_Test_1 (WT1):** 

`0x3d83ba928974e07f35a246d50eae0ae269baef16` for **USDT_Test_1 (UT1):** 

`0xd1e404c02f73c2c9cbadaf400028690f466fe206` for **ARB_Test_1 (AT1):** 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/chose%20token.png" width=60% height=60%>

Click on **"You pay"** (token you want to sell) field drop-down menu and enter contract address.  
On picture, there is MOR_Test_1 (MT1) `0x84efb4db4265966742fa3671aa841a8f21dd2d4f` address.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/add%20token.png" width=60% height=60%>

Click on the token to add it. If warning message appears, click `I understand`.

Perform the same actions with **"You receive"** (token you want to buy) field.  

Enter the amount of tokens you want to sell in **"You pay"** field, the amount of tokens you receive will calculate automatically accordingly to current price.  
Check conditions and click `Swap` 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/swap.png" width=60% height=60%>

In your wallet, approve spending for the token you are swapping, sign message and confirm swap.  
For more information on token approvals see this [article](https://support.uniswap.org/hc/en-us/articles/8120520483085-What-is-an-approval-transaction).

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/approve.png" width=75% height=75%>

After swap transaction is confirmed, you will see updated balances.  

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/swap%20success.png" width=60% height=60%>

> [!TIP]
> Make multiple swaps with different combinations of tokens and amounts.



## How to add liquidity to Uniswap?
Go to https://app.uniswap.org/pool 

Click `+New position`

Add MOR Mock and wETH Mock tokens by entering their smart conctract addresses



## How to increase or decrease liquidity on Uniswap?


## How to remove liquidity from Uniswap?




**Additional info**
- what are dexs
- https://academy.binance.com/en/articles/impermanent-loss-explained 
https://support.uniswap.org/hc/en-us/articles/8370549680909-How-to-swap-tokens-with-the-Uniswap-Web-app 
