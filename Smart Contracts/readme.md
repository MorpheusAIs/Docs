# Overview

At genesis, the Morpheus network utilizes six smart contracts. This includes the MOR token itself, used to incentivize key contributors to the network, as well as contracts enabling the [Techno Capital Machine](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md) bootstrapping mechanism.

Morpheus smart contracts are deployed across Ethereum and Arbitrum. This hybrid model allows the Techno Capital Machine to tap into deep stETH (Lido Staked Ethereum) liquidity on Ethereum while maintaining low transaction costs for the MOR token on Arbitrum.

**Morpheus Smart Contracts:**
* [`MOROFT`](MOROFT.md) – the Morpheus token, a [LayerZero Omnichain Fungible Token](https://docs.layerzero.network/v2/developers/evm/oft/quickstart) (OFT)
* [`DistributionV4`](Distribution.md) – used to lock capital for the Techno Capital Machine and claim rewards
* [`LinearDistributionIntervalDecrease`](LinearDistributionIntervalDecrease.md) – a library for calculating rewards
* [`L1Sender`](L1Sender.md) – sends MOR minting requests; wraps and transfers stETH to Arbitrum
* [`L2MessageReceiver`](L2MessageReceiver.md) – receives and processes MOR minting requests on Arbitrum
* [`L2TokenReceiverV2`](L2TokenReceiverV2.md) – receives wstETH and manages Protocol-Owned Liquidity on Arbitrum

With the exception of the MOR token and LinearDistributionIntervalDecrease library, all contracts utilize the UUPS proxy pattern to enable upgradeability. For more information on this, see the [OpenZeppelin `UUPSUpgradeable` documentation](https://docs.openzeppelin.com/contracts/5.x/api/proxy#UUPSUpgradeable).

[**Source Code Repository**](https://github.com/MorpheusAIs/SmartContracts)

## Deployments

## Arbitrum Contracts

|                     | Proxy                                                                                                                | Implementation                                                                                                       |
|---------------------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `MOROFT`            | -                                                                                                                    | [0x092bAaDB7DEf4C3981454dD9c0A0D7FF07bCFc86](https://arbiscan.io/token/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86)   |
| `L2MessageReceiver` | [0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427](https://arbiscan.io/address/0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427) | [0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://arbiscan.io/address/0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84) |
| `L2TokenReceiverV2` | [0x47176b2af9885dc6c4575d4efd63895f7aaa4790](https://arbiscan.io/address/0x47176b2af9885dc6c4575d4efd63895f7aaa4790) | -                                                                                                                    |
| `ComputeRouter`     | [0xde819aaee474626e3f34ef0263373357e5a6c71b](https://arbiscan.io/address/0xde819aaee474626e3f34ef0263373357e5a6c71b) | [0x8621e6b808a3d925533446b767b7bca6accb62a2](https://arbiscan.io/address/0x8621e6b808a3d925533446b767b7bca6accb62a2) |
| `Builder`           | [0xc0ed68f163d44b6e9985f0041fdf6f67c6bcff3f](https://arbiscan.io/address/0xc0ed68f163d44b6e9985f0041fdf6f67c6bcff3f) | [0x969c0f87623dc33010b4069fea48316ba2e45382](https://arbiscan.io/address/0x969c0f87623dc33010b4069fea48316ba2e45382) |
| `BuilderTreasury`   | [0xCBE3d2c3AdE62cf7aa396e8cA93D2A8bff96E257](https://arbiscan.io/address/0xCBE3d2c3AdE62cf7aa396e8cA93D2A8bff96E257) | [0x232c15275affa0ee944f6894d57e013647416aa1](https://arbiscan.io/address/0x232c15275affa0ee944f6894d57e013647416aa1) |


## Ethereum Contracts

|                                      | Proxy                                                                                                                 | Implementation                                                                                                        |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| `DistributionV4`                     | [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790) | [0x68b9d05add55769b1e4808a74b616fa37f6da294](https://etherscan.io/address/0x68b9d05add55769b1e4808a74b616fa37f6da294) |
| `L1Sender`                           | [0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://etherscan.io/address/0x2efd4430489e1a05a89c2f51811ac661b7e5ff84) | [0x6b1A3D8F84094667e38247D6FcA6F814e11aE9fE](https://etherscan.io/address/0x6b1A3D8F84094667e38247D6FcA6F814e11aE9fE) |
| `LinearDistributionIntervalDecrease` | -                                                                                                                     | [0x7431aDa8a591C955a994a21710752EF9b882b8e3](https://etherscan.io/address/0x7431aDa8a591C955a994a21710752EF9b882b8e3) |


## Base Contracts

|                     | Proxy                                                                                                                 | Implementation                                                                                                        |
|---------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| `Builder`           | [0x42BB446eAE6dca7723a9eBdb81EA88aFe77eF4B9](https://basescan.org/address/0x42BB446eAE6dca7723a9eBdb81EA88aFe77eF4B9) | [0x7ec3dda3e83ddd4b9f2cfcff0a5213bb8cf31b79](https://basescan.org/address/0x7ec3dda3e83ddd4b9f2cfcff0a5213bb8cf31b79) |
| `BuilderTreasury`   | [0x9eba628581896ce086cb8f1A513ea6097A8FC561](https://basescan.org/address/0x9eba628581896ce086cb8f1A513ea6097A8FC561) | [0xe5e06c8a6c9938873b20efc1af3a0254cc57c5ca](https://basescan.org/address/0xe5e06c8a6c9938873b20efc1af3a0254cc57c5ca) |



## Liquidity Pool Contracts

|                     | Contract |                                                                                                        |
|---------------------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `Uniswap V3` | [0xe5cf22ee4988d54141b77050967e1052bd9c7f7a](https://arbiscan.io/address/0xe5cf22ee4988d54141b77050967e1052bd9c7f7a) |
| `Uniswap V3` | [0xb2Eb5849e2606F99Fc492E9aDD0103c667f806d3](https://arbiscan.io/address/0xb2eb5849e2606f99fc492e9add0103c667f806d3#code) |

## Nomenclature

Within the contracts, **deposit token** is used to refer to the token deposited by Capital Providers (stETH) or its wrapped counterpart, while **reward token** refers to the MOR token.

## Ownership

With the exception of the `LinearDistributionIntervalDecrease` library which is not ownable, all contracts are owned by the Morpheus multisigs on their respective chains:
- `L2MessageReceiver` and `L2TokenReceiver` are owned by the Arbitrum multisig [0x151c2b49CdEC10B150B2763dF3d1C00D70C90956](https://arbiscan.io/address/0x151c2b49CdEC10B150B2763dF3d1C00D70C90956)
- `DistributionV4` and `L1Sender` are owned by the Ethereum multisig [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://etherscan.io/address/0x1fe04bc15cf2c5a2d41a0b3a96725596676eba1e)
- `ComputeRouter`, `Builder` and `BuilderTreasury` (on arbitrum) are owned by the Arbitrum multisig [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://arbiscan.io/address/0x1fe04bc15cf2c5a2d41a0b3a96725596676eba1e)
- `Builder` and `BuilderTreasury` (on base) are owned by the Base multisig [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://basescan.org/address/0x1fe04bc15cf2c5a2d41a0b3a96725596676eba1e)

For ownability, these smart contracts inherit `OwnableUpgradeable`. For more information on this, see the [OpenZeppelin Access Control Documentation](https://docs.openzeppelin.com/contracts/5.x/api/access).

## Audits

The Morpheus smart contracts were audited privately [by Renasence](https://github.com/MorpheusAIs/Docs/blob/main/Testing%20Reports/report-v2%20of%20Morpheus%20Audit.pdf) and later subject to a public [CodeHawks audit](https://www.codehawks.com/contests/clrzgrole0007xtsq0gfdw8if).
