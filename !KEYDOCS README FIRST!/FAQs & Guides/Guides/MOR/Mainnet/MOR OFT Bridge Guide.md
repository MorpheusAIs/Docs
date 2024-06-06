Deploying MOR OFT to multiple chains

Validated Address for Ethereum
https://etherscan.io/address/0xcBB8f1BDA10b9696c57E13BC128Fe674769DCEc0 Multisig: https://etherscan.io/address/0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E
Validated Address for Base
https://basescan.org/address/0x7431ada8a591c955a994a21710752ef9b882b8e3 Multisig: https://basescan.org/address/0xf3ef00168dd40eae68a7e670d56c7b8724e0c183
Validated Address for Arbitrum
https://arbiscan.io/address/0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86 
Multisig: https://arbiscan.io/address/0x151c2b49CdEC10B150B2763dF3d1C00D70C90956


To transfer tokens from Arbitrum to Ethereum (30101) you can call the next functions: 

Note, that it’s a view function, so you don’t need to send any transaction now:

Make sure the last 12 digits of amountLD are 0. 
Then amountLD and minAmountLD are the same.

Call quoteSend function:
_sendParam: 
[
	dstEid: 30101,
	to: receiver on Ethereum in bytes32
   	amountLD: amount in wei
    	minAmountLD: amount in wei
    	extraOptions: “0x”
composeMsg: “0x”,
    	oftCmd: “0x”
]
_payInLzToken: false


[30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]


You will get 2 integers. Let's call this value a “fee” (in native tokens). Note: the second (in LZ tokens) is always 0 in our case.




Call send function: 
payableAmount / value: you have to convert a fee from Wei to Ether and pass the value here. 
_sendParam: copy the input array from the previous step. 
_fee: pass a “fee” value obtained from the previous step.
_refundAddress: usually the same address from which the transaction was sent.





SEND TO ETHEREUM

[30101,"0x0000000000000000000000001FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.003060201202870756
[3060201202870756,0]


SEND TO BASE

[30184,"0x000000000000000000000000f3ef00168DD40Eae68A7E670d56C7b8724E0c183", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.000039804175519067
[39804175519067,0]

SEND TO ARBITRUM

[30110,"0x000000000000000000000000151c2b49CdEC10B150B2763dF3d1C00D70C90956", "1000000000000000000", "1000000000000000000", "0x", "0x", "0x"]

0.000022422266371209
[22422266371209,0]


