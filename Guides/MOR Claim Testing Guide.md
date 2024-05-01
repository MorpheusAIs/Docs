We've created a clone of the system. New contract addresses:

Ethereum:
Distribution: https://etherscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7 
L1Sender: https://etherscan.io/address/0x845FBB4B3e2207BF03087b8B94D2430AB11088eE 


Mocks:
StETH: https://etherscan.io/address/0x7EC3dda3e83dDD4b9f2cFCfF0A5213Bb8cf31b79 

WStETH: https://etherscan.io/address/0x42BB446eAE6dca7723a9eBdb81EA88aFe77eF4B9 




Arbitrum:

L2TokenReceiver: https://arbiscan.io/address/0x2e1fF173085A5ef12046c27E442f12f79A0092b7
L2MessageReceiver: https://arbiscan.io/address/0x845FBB4B3e2207BF03087b8B94D2430AB11088eE 
MOR: https://arbiscan.io/address/0x3c3A26c978Bf6AF40D7c1A36e9cBD3C1c055786E 



Mocks:

WStETH: https://arbiscan.io/address/0x4Cf928C827F15CbCC9A8781Eb9b2BC3CA52b2501 

WETH: https://arbiscan.io/address/0x52D00439eADfc53D0005dcaF1914BAf9015f82fe


We created a test pair on Uniswap on Arbitrum WETH <=> WStETH with the same properties as the real pair.

Also checked:
Claim MOR from distribution on Arbitrum.
Bridge Overplus (stETH) from distribution on Arbitrum.
Swap WStEth to WETH on Arbitrum using L2TokenReceiver.
