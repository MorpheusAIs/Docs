# Capital Providers Reference

---

## Overview & Eligibility
Capital providers supply stETH to the Morpheus protocol, enabling the creation of protocol-owned liquidity and earning MOR rewards. Anyone with stETH can participate by depositing into the Morpheus contract on Ethereum mainnet.

---

## Supported Chains & Contracts
- **Deposit Chain:** Ethereum mainnet
- **Deposit Contract Address:** [See #verified-links in Morpheus Discord](https://discord.com/channels/1151741790408429580/1183934719155515463)
- **Multisig Management:** 4 of 7 multisig by trusted open source contributors ([MOR.ETH](https://etherscan.io/address/0x1FE04BC15Cf2c5A2d41a0b3a96725596676eBa1E))
- **Audit Reports:** [Security Audit Reports on GitHub](https://github.com/MorpheusAIs/Docs/tree/main/Security%20Audit%20Reports)

---

## Deposit & Withdrawal Mechanics
| Parameter                | Value/Description                |
|--------------------------|----------------------------------|
| Asset                    | stETH (Lido staked ETH)          |
| Minimum Deposit          | 0.01 stETH                       |
| Maximum Deposit          | No maximum                       |
| Initial Lockup           | 7 days                           |
| Withdrawal               | Allowed any time after lockup     |
| Conversion               | stETH is not converted to MOR; only yield is used |
| Impermanent Loss         | None                              |

- stETH can be minted via Lido or purchased on exchanges.
- Withdrawals return the full stETH amount after the 7-day lockup.

---

## Rewards & Emissions
- **MOR Emissions:** 24% of daily MOR emissions are allocated to capital providers.
- **Distribution:** Proportional to user's share of the total stETH pool.
- **Emission Schedule:** See [Tokenomics Reference](./MOR%20Token%20and%20Liquidity%20FAQ.md)
- **No vesting or lock on MOR rewards.**
- **No cut-off date:** Emissions continue for at least 16 years (Epoch 1).

---

## Claiming Process
1. Visit [dashboard.mor.org](https://dashboard.mor.org) and switch to Ethereum mainnet.
2. Connect the wallet used for stETH deposit.
3. View claimable MOR amount and click **"Claim MOR"**.
4. Input the address to receive MOR on Arbitrum.
5. Sign the transaction.

- Claims can be made as frequently as desired (every Ethereum block), but each claim incurs a transaction fee.
- No minimum or maximum claim amount.

---

## Security & Audits
- Contracts have undergone community and professional audits, plus a public bug bounty.
- Security reports are available on [GitHub](https://github.com/MorpheusAIs/Docs/tree/main/Security%20Audit%20Reports).
- Protection Fund (4% of emissions) exists to mitigate risk.

---

## Risks & Protection
- **Smart Contract Risk:** As with all DeFi, there is risk of bugs or vulnerabilities.
- **Protection:** Multiple audits and a dedicated Protection Fund.
- **No impermanent loss:** Withdrawals always return the deposited stETH amount.

---

## Support & Resources
- [Morpheus Discord Support Channel](https://discord.com/channels/1151741790408429580/1183666837460897832)
- [Dashboard](https://dashboard.mor.org)
- [Community Analytics: morlord.com](https://morlord.com/), [morstats.info](https://morstats.info/), [morcheck.xyz](https://morcheck.xyz/)
- [Multisignature Account Details](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Morpheus%20Multisignature%20Account.md)
- [Add a question](https://forms.gle/6yt5ps3kAfUfkF4N8)

---

## Warnings
> **Beware of scams:** Only trust information and links from official Morpheus channels. Anyone messaging you with unsolicited offers of help is likely a scammer.

---

## [Placeholder: Add contract addresses and additional technical details as available]
