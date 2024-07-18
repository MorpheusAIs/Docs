# MOR20 Launch Guides

These guide has been developed to help MOR20 developers with deploying their MOR20 contracts via the Morpheus Ecosystem Dashboard (https://morpheus-dev.206.189.243.3.nip.io/#/mor20-ecosystem?network=testnet)

## Link for PDF of Testnet Launch Guide:
https://drive.google.com/file/d/1-XUOaKwwgogP-4JHyPx8kGJbU-gM0i2z/view?usp=drive_link

## Launch Guide for MOR20 Testnet Deployment

### Intro
This guide has been developed to assist MOR20 developers with their deployment using the Morpheus MOR20 ecosystem. MOR20 allows users to replicate the Morpehus tokenomics ecosystem for their project. This guide does not provide any recommendations, only information about the deployment steps and settings that were utilized for the MOR token. 

To successfully deploy a MOR20 token, you will provide the form with token information to launch the token on the Arbitrum network. You will also provide information to automatically generate the associated smart contracts that power the tokenomics, including the pools with staking functionality and varying token emissions as well as the automated swaps via uniswap. These deployments will require transactions on both the Ethereum and Arbitrum networks.

This version of the guide is for deployment on the Ethereum and Arbitrum Sepolia testnets. You will need sepolia eth on both networks for testing. 

### Getting Started

1) Go to https://morpheus-dev.206.189.243.3.nip.io/#/mor20-ecosystem?network=testnet
2) Click ”Ethereum Sepolia” for testnet deployment
3) Click "Create Contract"
   ![image](https://github.com/user-attachments/assets/5e9438b6-fa31-4abd-8479-fdcb64f13db1)

### General Config

1) Name your project
2) Click "Next"
   ![image](https://github.com/user-attachments/assets/7cb4e6cc-09e7-4039-b854-ad6b6a421586)

### Arbitrum Config

1) Choose the name of your token, this is what will show on the blockchain
2) Choose your token symbol, this is traditionally 3 or 4 letters (i.e. "MOR")
3) Choose if the contact will be upgradeable. This is an important decision that cannot be undone if you do not allow upgradeability.
4) Enter the Arbitrum wallet address or safe address that will be used as the administrator for the token and smart contracts
   ![image](https://github.com/user-attachments/assets/0502b4f7-dbc4-4f46-a629-3d398d3d9361)

### Uniswap Settings

The MOR20 ecosystem works where users will “stake” a yield generating asset (i.e. stETH for MOR) into the MOR20 contract. The yield will then be “claimed” by the MOR20 project and bridged to Arbitrum. The MOR20 project will then swap some of that asset to the token used as a trading pair for the project.

1) Enter the address of the yield token on the arbitrum sepolia network (i.e. wstETH for MOR)
2) Enter the address of the token used as a trading pair on the arbitrum sepolia network (i.e. wETH for MOR)
3) Choose the fee for the swap of the 2 tokens above
4) Choose the fee for the swap in the MOR20 pool

Note: Uniswap pools have inherent fees set by liquidity providers, these vary by liquidity pool and are generally lower in larger pools. The above uses test tokens for testing purposes only. DO NOT use these for your actual MOR20 launch. 
Gotcha: Ensure the addresses above are on the arbitrum sepolia network, or else the transaction will fail
![image](https://github.com/user-attachments/assets/bd3e2c1c-d128-4e61-b396-fc2cbbc1a078)

### Arbitrum Deployment

1) When uniswap settings are verified, click "deploy" to initiate the first transaction
2) Verify the wallet is set to the arbitrum sepolia network (reminder: this is for test purposes only)
3) Verify gas fees and any other TX details and click "confirm"
4) You will receive confirmation of the TX submittal and a link to the TX
5) You will reveive confirmation of successful transaction and a link to the smart contract
   ![image](https://github.com/user-attachments/assets/561a2504-14b1-4442-8f75-29361c6305d0)

### Ethereum Config

1) Similar to the earlier step on Arbitrum, Enter the Ethereum wallet address or safe address that will be used as the administrator for the test token and smart contracts
2) Choose if you would like the contract to be upgradeable, similar to the decision on the arbitrum configuration
   ![image](https://github.com/user-attachments/assets/6cace97d-b8f7-4c63-87cf-4afd5ad9142e)

### Pool Creation
This is where the "pools" will be created. These pools determine how token emissions are generated, thus the total supply of the token, and the emissions curve. For MOR, there are 5 pools (Capital, Code, Compute, Community and Protection) with varying settings.

1) Select/deselect "Is Public": Selection for users to be able to "stake" assets into pool
2) Payout start: "Launch" date when rewards start accruing
3) Decrease interval: Rate in which rewards decrease occurs (i.e. for MOR this is daily)
4) Withdraw lock period: "Waiting" period until a user can claim rewards after stake
5) Claim lock period: Bootstrapping period length (i.e. for MOR this was 90 days)
6) Withdraw lock period after stake: "Waiting" period until a user can unstake assets
7) Initial reward: Starting emission amount (i.e. for MOR this was 3456 for the 4 pools and 576 for the protection fund)
8) Reward decrease: Daily token emission decrease (i.e. emission curve, for MOR this is 0.59255872724 for the 4 pools and 0.09875978804 for the protection fund
9) Minimal stake: Minimum that a user can stake in the contract
10) Click save to move to the next pool
    
 Note: Initial reward & rewards decrease across all pools determine total token supply
![image](https://github.com/user-attachments/assets/6a782051-feca-4d98-b3fb-cd553d06a44a)

11) Upon creating your first pool, it will show on the righthand side of the screen. As you add additional pools, they will populate within the list. When all pools have been verified, click "Deploy"
12) Your wallet will likely ask to switch to the Ethereum Netowrk (Sepolia shown for test purposes). Click "Switch Network"
13) Verify all gas and contract information and click "Confirm" to submit TX. When submitted successfully, you will be prompted with a link to the TX
![image](https://github.com/user-attachments/assets/0254efc3-a998-4cc7-8519-e75e37a95b0c)

14) When the transaction completed successfully, you will receive a success message, and a popup box with links to all of the smart contracts that have been deployed. 

Congratulations on deploying your MOR20 smart contracts
![image](https://github.com/user-attachments/assets/b6f2de33-82e6-49a8-98db-d9605c8ee4b8)

### Testing
If you would like to manually test staking within the contract and review token emissions, you can continue with this guide. For any testing, you will need to use stETHmock, a test token created to simulate stETH on Sepolia. 

1) In your distribution contract on sepolia etherscan, the address of the token is available under "Read As Proxy" and 1. deposittoken
2) Once on the page for stETHmock, go to "Write Contract" within the contracts tab, then click "Connect to web3"
3) Choose your wallet type and connect wallet
4) Click "Mint", and enter your wallet address. Choose the number of tokens to mint by entering the amount and then 18 zeroes following. Write and Sign the tx
5) Click "Approve" adn enter the address of the distribution contract. Choose the number of tokens that you will be staking by entering the amount and then 18 zeroes following. Write and Sign the tx.
![image](https://github.com/user-attachments/assets/262c2394-4bc7-450c-9fc7-99c2d073477d)

6) To start generating token emissions, stake the stETHmock into the distribution contact. Go to the distribution contract and connect to web3 as you had previously. Click "write to proxy" and go to 8. stake
7) Enter the poolid setup for the staking during the MOR20 deployment. For Morpheus, this value is "0".
8) Enter the amount to stake. Enter the token amount, followed by 18 zeroes. This amount must be equal or less than what was approved in the earlier step.
9) You will start earning emissions as per the "payout start" date and can withdraw them based on the associated lock periods. You can check emissions in 3. "getCurrentUserReward"
10) Enter the poolid for the staking pool. Enter the wallet address you woudl like to verify. Click query and the output will be your emissions, in wei
![image](https://github.com/user-attachments/assets/03aac56f-1a58-4df8-89ea-c61271c8e9ac)



## Launch Guide for MOR20 Mainnet Deployment

This guide is currently under construction and will be added soon
