# Overview

At genesis, the Morpheus network utilizes six smart contracts. This includes the MOR token itself, used to incentivize key contributors to the network, as well as contracts enabling the [Techno Capital Machine](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/TechnoCapitalMachineTCM.md) bootstrapping mechanism.

Morpheus smart contracts are deployed across Ethereum and Arbitrum. This hybrid model allows the Techno Capital Machine to tap into deep stETH (Lido Staked Ethereum) liquidity on Ethereum while maintaining low transaction costs for the MOR token on Arbitrum.

**Morpheus Smart Contracts:**
* [`MOROFT`](MOROFT.md) – the Morpheus token, a [LayerZero Omnichain Fungible Token](https://docs.layerzero.network/v2/developers/evm/oft/quickstart) (OFT)
* [`Distribution`](Distribution.md) – used to lock capital for the Techno Capital Machine and claim rewards
* [`LinearDistributionIntervalDecrease`](LinearDistributionIntervalDecrease.md) – a library for calculating rewards
* [`L1Sender`](L1Sender.md) – sends MOR minting requests; wraps and transfers stETH to Arbitrum
* [`L2MessageReceiver`](L2MessageReceiver.md) – receives and processes MOR minting requests on Arbitrum
* [`L2TokenReceiverV2`](L2TokenReceiverV2.md) – receives wstETH and manages Protocol-Owned Liquidity on Arbitrum

With the exception of the MOR token and LinearDistributionIntervalDecrease library, all contracts utilize the UUPS proxy pattern to enable upgradeability. For more information on this, see the [OpenZeppelin `UUPSUpgradeable` documentation](https://docs.openzeppelin.com/contracts/5.x/api/proxy#UUPSUpgradeable).

[**Source Code Repository**](https://github.com/MorpheusAIs/SmartContracts)

## Deployments

### Arbitrum Contracts

|                     | Proxy                                                                                                                | Implementation                                                                                                       |
|---------------------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `MOROFT`            | -                                                                                                                    | TBD                                                                                                                  |
| `L2MessageReceiver` | [0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427](https://arbiscan.io/address/0xd4a8ECcBe696295e68572A98b1aA70Aa9277d427) | [0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://arbiscan.io/address/0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84) |
| `L2TokenReceiverV2` | TBD                                                                                                                  | TBD                                                                                                                  |

## Ethereum Contracts

|                                      | Proxy                                                                                                                 | Implementation                                                                                                        |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| `Distribution`                       | [0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790](https://etherscan.io/address/0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790) | [0x24C09A0C047e8A439f26682Ea51c7157b3cCc20b](https://etherscan.io/address/0x24C09A0C047e8A439f26682Ea51c7157b3cCc20b) |
| `L1Sender`                           | [0x2Efd4430489e1a05A89c2f51811aC661B7E5FF84](https://etherscan.io/address/0x2efd4430489e1a05a89c2f51811ac661b7e5ff84) | [0x6b1A3D8F84094667e38247D6FcA6F814e11aE9fE](https://etherscan.io/address/0x6b1A3D8F84094667e38247D6FcA6F814e11aE9fE) |
| `LinearDistributionIntervalDecrease` | -                                                                                                                     | [0x7431aDa8a591C955a994a21710752EF9b882b8e3](https://etherscan.io/address/0x7431aDa8a591C955a994a21710752EF9b882b8e3) |

## Nomenclature

Within the contracts, **deposit token** is used to refer to the token deposited by Capital Providers (stETH) or its wrapped counterpart, while **reward token** refers to the MOR token.

## Ownership

With the exception of the `LinearDistributionIntervalDecrease` library which is not ownable, all contracts are owned by the Morpheus multisigs on their respective chains:
- `L2MessageReceiver` and `L2TokenReceiver` are owned by the Arbitrum multisig [0x151c2b49CdEC10B150B2763dF3d1C00D70C90956](https://arbiscan.io/address/0x151c2b49CdEC10B150B2763dF3d1C00D70C90956)
- `Distribution` and `L1Sender` are owned by the Ethereum multisig [0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E](https://etherscan.io/address/0x1fe04bc15cf2c5a2d41a0b3a96725596676eba1e)

For ownability, these smart contracts inherit `OwnableUpgradeable`. For more information on this, see the [OpenZeppelin Access Control Documentation](https://docs.openzeppelin.com/contracts/5.x/api/access).

## Audits

The Morpheus smart contracts were audited privately [by Renasence](https://github.com/MorpheusAIs/Docs/blob/main/Testing%20Reports/report-v2%20of%20Morpheus%20Audit.pdf) and later subject to a public [CodeHawks audit](https://www.codehawks.com/contests/clrzgrole0007xtsq0gfdw8if).