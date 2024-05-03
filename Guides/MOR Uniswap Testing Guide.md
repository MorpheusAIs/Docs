# MOR Token Uniswap Testing Guide

>[!NOTE]
> - The purpose of the testing is to familiarize users with the swapping process and liquidity operations of the Uniswap decentralized exchange, as well as to identify any issues that users may encounter.  
> - This testing is conducted on the Arbitrum mainnet. Completing all the steps may require $1-3 in ETH for fees, depending on network condition.
> - Please note that this testing is not incentivized, and participants will not receive any rewards.
> - Test tokens have no value and intended fot test purpose only.

---

## Introduction
This guide will walk you through the testing main Uniswap functions as swap tokens, add, remove, increase and decrease liquidity with Metamask wallet, but for other Web3 wallets logic remains the same.

There are following steps:
1) [Obtaining test tokens](#mint-test-tokens)
2) [Adding tokens to Metamask](#add-tokens-to-metamask) 
3) [Connecting to Uniswap](#connect-wallet-to-uniswap)
4) [Swapping tokens](#how-to-swap-tokens-on-uniswap)
5) [Adding liquidity](#how-to-add-liquidity-to-uniswap)
6) [Removing or decreasing liquidity](#how-to-remove-or-decrease-liquidity-from-uniswap)
7) [Increasing and decresing added liquidity](#how-to-increase-liquidity-on-uniswap)

---

## Smart Contracts Addresses
Arbitrum mainnet:  

**MOR_Test_1 (MT1):** [0x84efb4db4265966742fa3671aa841a8f21dd2d4f](https://arbiscan.io/token/0x84efb4db4265966742fa3671aa841a8f21dd2d4f)  

**WETH_Test_1 (WT1):** [0x3b0a436dc056fd17901922147dc1d2f557b81edd](https://arbiscan.io/token/0x3b0a436dc056fd17901922147dc1d2f557b81edd)  

**USDT_Test_1 (UT1):** [0x3d83ba928974e07f35a246d50eae0ae269baef16](https://arbiscan.io/token/0x3d83ba928974e07f35a246d50eae0ae269baef16)  

**ARB_Test_1 (AT1):** [0xd1e404c02f73c2c9cbadaf400028690f466fe206](https://arbiscan.io/token/0xd1e404c02f73c2c9cbadaf400028690f466fe206)  

---

## Switch Metamask to Arbitrum chain
You should choose Arbitrum chain in the chain list or add it using [Chainlist](https://chainlist.org/chain/42161) service and clicking **“Add to Metamask”**.  

You need to have $1-3 in ETH for fees. You can bridge ETH from other chain or buy it on CEX. 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/change%20chain.png" width=40% height=40%>

---

## Mint test tokens
Test tokens have no value and intended for test purpose only.  

> [!IMPORTANT]  
> You can get tokens by asking in [Discord](https://discord.com/channels/1151741790408429580/1183666837460897832) or mint them yourself.  

To mint test tokens you need to go to [MOR_Test_1 (MT1) token contract](https://arbiscan.io/token/0x84efb4db4265966742fa3671aa841a8f21dd2d4f#writeContract), open the **“Contract”** tab, then the **“Write Contract”** tab and connect your wallet by clicking **"Connect to Web3**" button.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/mint.png" width=75% height=75%>

It is necessary to select the `4. mint (0x40c10f19)` function that will issue tokens to your address.  
As parameters:
- `to_ (address)`: your wallet adress;
- `amount_ (uint256)`: amount of tokens in WEI, instead of ETH.  
You can use this unit converter calculator https://eth-converter.com to help you.

Click **"Write"** and confirm a transaction in your wallet. 

Perform the same actions with:

- **WETH_Test_1 (WT1) Contract** [0x3b0a436dc056fd17901922147dc1d2f557b81edd](https://arbiscan.io/token/0x3b0a436dc056fd17901922147dc1d2f557b81edd#writeContract)
  
- **USDT_Test_1 (UT1) Contract** [0x3d83ba928974e07f35a246d50eae0ae269baef16](https://arbiscan.io/token/0x3d83ba928974e07f35a246d50eae0ae269baef16#writeContract)
  
- **ARB_Test_1 (AT1) Contract** [0xd1e404c02f73c2c9cbadaf400028690f466fe206](https://arbiscan.io/token/0xd1e404c02f73c2c9cbadaf400028690f466fe206#writeContract)  

---

## Add tokens to Metamask 
To add tokens to Metamask wallet, please follow steps from this [guide](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) and add smart contracts addresses:    

**MOR_Test_1 (MT1):** `0x84efb4db4265966742fa3671aa841a8f21dd2d4f`  

**WETH_Test_1 (WT1):** `0x3b0a436dc056fd17901922147dc1d2f557b81edd`  

**USDT_Test_1 (UT1):** `0x3d83ba928974e07f35a246d50eae0ae269baef16`  

**ARB_Test_1 (AT1):** `0xd1e404c02f73c2c9cbadaf400028690f466fe206`

After these steps you will be able to see the tokens and their amount in your Metamask wallet.

---

## Connect wallet to Uniswap
Go to the Uniswap web app https://app.uniswap.org and choose Arbitrum chain in the top right corner of the screen.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/arb.png" width=100% height=100%>

Click **"Connect"** button 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/connect1.png" width=100% height=100%>

Select the wallet you would like to connect and approve the connection.  
Once approved your wallet will be connected!

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/connect2.png" width=100% height=100%>

---

## How to swap tokens on Uniswap?
Go to the Uniswap web app swap page https://app.uniswap.org/swap and search for and select the token you wish to swap.

`0x84efb4db4265966742fa3671aa841a8f21dd2d4f` for **MOR_Test_1 (MT1)** 

`0x3b0a436dc056fd17901922147dc1d2f557b81edd` for **WETH_Test_1 (WT1):** 

`0x3d83ba928974e07f35a246d50eae0ae269baef16` for **USDT_Test_1 (UT1):** 

`0xd1e404c02f73c2c9cbadaf400028690f466fe206` for **ARB_Test_1 (AT1):** 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/chose%20token.png" width=60% height=60%>

Click on **"You pay"** (token you want to sell) field drop-down menu and enter contract address.  
On picture, there is MOR_Test_1 (MT1) `0x84efb4db4265966742fa3671aa841a8f21dd2d4f` address.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/add%20token.png" width=60% height=60%>

Click on the token to add it. If warning message appears, click **I understand**.

Perform the same actions with **"You receive"** (token you want to buy) field.  

Enter the amount of tokens you want to sell in **"You pay"** field, the amount of tokens you receive will calculate automatically accordingly to current price.  
Check conditions and click **Swap.** 

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/swap.png" width=60% height=60%>

In your wallet, approve spending for the token you are swapping, sign message and confirm swap.  
For more information on token approvals see this [article](https://support.uniswap.org/hc/en-us/articles/8120520483085-What-is-an-approval-transaction).

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/approve1.png" width=75% height=75%>

After swap transaction is confirmed, you will see updated balances.  

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/swap%20success.png" width=50% height=50%>

> [!TIP]
> Make multiple swaps with different combinations of tokens and amounts.

---

## How to add liquidity to Uniswap?
Go to the Uniswap web app pool page https://app.uniswap.org/pool and click **+ New position**

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/new%20position.png" width=80% height=80%>

Add two test tokens you want to add liquidity with. You can find them with name or with smart contract address.   
`MOR_Test_1 (MT1)` selected in screenshot below.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/add%20token.png" width=60% height=60%>

Click **"Edit"** and set [fee tier](https://docs.uniswap.org/concepts/protocol/fees) for your liquidity position.  
A liquidity pool may or may not exist at the fee tier selected. If the pool already exists, then your liquidity position will be added to the pool.  
If the pool does not exist, your liquidity position will create a new pool at the fee tier selected.  

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/select%20tokens.png" width=60% height=60%>
<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/fee%20tier.png" width=60% height=60%>

Set the Price Range in which to provide liquidity.  
You can enter a specific range, or provide liquidity for the full price range.  
If the price moves out of your set range, then your liquidity position will be concentrated into one of the two assets and not earn fees.  
Learn more about concentrated liquidity [here](https://docs.uniswap.org/concepts/protocol/concentrated-liquidity).

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/price%20range.png" width=60% height=60%>

Enter the amount of tokens you want to deposit into the liquidity pool, or select **“Max”** for the maximum amount of tokens.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/deposit%20amounts.png" width=60% height=60%>

Next you need to click **"Approve"** and confirm transaction in your wallet to allow your tokens to be used for providing liquidity.  
After approval transaction is confirmed, click **"Preview"**.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/approve2.png" width=60% height=60%>

> [!TIP]
> The best cybersecurity practice is to approve only amount you want to spend.

Review the liquidity position details, click **“Add”** and confirm the transaction in your wallet.  
A confirmation notification will appear once the transaction is complete.  

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/swap%20success.png" width=50% height=50%>

Once completed, you can view and manage your liquidity position from the [Pool page](https://app.uniswap.org/pool).

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/positions.png" width=80% height=80%>

When a liquidity position is created, it is represented by an NFT. The wallet address that owns the NFT is the owner of the liquidity position.  
Read more about LP NFTs [here.](https://support.uniswap.org/hc/en-us/articles/20980786685069-Why-is-liquidity-position-ownership-represented-by-tokens-or-NFTs)

> [!TIP]
> Try to add liquidity positions with different assets, fee tiers and token amounts.

> [!WARNING]  
> Providing liquidity on Uniswap with tokens that have value (not testing) involves certain risks that all participants should be aware of before making any decisions. These risks include, but are not limited to: impermanent loss, smart contract risks and market volatility.  
Before providing liquidity on Uniswap or engaging in any DeFi activities, it is crucial to thoroughly understand these risks and conduct proper research to make informed decisions based on your risk tolerance and financial goals.  
Read more about liquidity providing risks [here.](https://medium.com/@pintail/uniswap-a-good-deal-for-liquidity-providers-104c0b6816f2)

---

## How to remove or decrease liquidity from Uniswap?
Go to the Uniswap web app [pool page](https://app.uniswap.org/pool), where you will see liquidity positions you have.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/positions.png" width=80% height=80%>

Select the position you want to remove or decrease liquidity from and click **"Remove liquidity"** button.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/remove%20liquidity.png" width=80% height=80%>

Review the details of your liquidity position. Then enter the percentage amount you would like to decrease your position or select **"Max"** if you want to remove liquidity.  
Finally click **"Remove"** two times to confirm liquidity withdrawal.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/percentage.png" width=50% height=50%>

Confirm the transaction in the wallet to finalize remove or decrease of liquidity.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/approve3.png" width=80% height=80%>

> [!TIP]
> Try several scenarious with different pairs and  percentages.

---

## How to increase liquidity on Uniswap?
Go to the Uniswap web app [pool page](https://app.uniswap.org/pool), select the position you want to increase liquidity and click **"Increase liquidity"** button.

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/increase%20liquidity.png" width=80% height=80%>

Enter amount of tokens you want to increase your position with and click **"Approve"** to allow tokens to be used for increasing liquidity.  
After approval transaction is confirmed, click **"Preview"**

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/approve%20increase.png" width=60% height=60%>

> [!TIP]
> The best cybersecurity practice is to approve only amount you want to spend.

Review the liquidity position details, click **“Add”** and confirm the transaction in your wallet.  

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/add%20increase.png" width=45% height=45%>

A confirmation notification will appear once the transaction is complete and you can view your increased liquidity position size at the [pool page](https://app.uniswap.org/pool).

<img src="/Graphics/Docs%20Graphics/English/Uniswap%20Guide/success%20increase.png" width=45% height=45%>

---

## Additional information
If you need more information about Uniswap exchange functions, please refer to this page: https://support.uniswap.org/hc/en-us  

If you identify any issues while testing or need support, please ask in Morpheus' [Discord](https://discord.com/channels/1151741790408429580/1183666837460897832).
