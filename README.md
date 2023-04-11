---
description: The easiest way to stack ETH or USD
---

# Introduction

This documentation explains the technical design of both **Origin Dollar (OUSD)** and **Origin Ether (OETH)**. Both OUSD and OETH are designed to deliver superior DeFi yields directly to your Ethereum wallet. Both products use the same codebase but accept different collateral. OUSD is designed to help you accumulate more dollars, whereas OETH helps you accumulate more ETH. Both OUSD and OETH are stablecoins that track the price of their respective currencies.&#x20;

OUSD was originally launched in September 2020 and has been battle-tested over time with hundreds of millions of dollars in circulating supply. OETH is launching in May 2023 using the same core contracts as OUSD. The main difference is that OETH uses ETH and liquid staking derivates (LSDs) as collateral instead of dollar-backed stablecoins.

|                        |                                                                                                     Origin Dollar (OUSD)                                                                                                    |                                                                      Origin Ether (OETH)                                                                     |
| ---------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------: |
| 100% collateralized by |                                                 ![USDT](<.gitbook/assets/image (6).png>)![USDC](<.gitbook/assets/image (17).png>)![DAI](<.gitbook/assets/image (11).png>)                                                   | ![ETH](<.gitbook/assets/image (1).png>)![stETH](<.gitbook/assets/image (7).png>)![rETH](<.gitbook/assets/image (2).png>)![frxETH](.gitbook/assets/image.png) |
| Strategies             | ![](<.gitbook/assets/image (13).png>)![](<.gitbook/assets/image (8).png>)![](<.gitbook/assets/image (4).png>)![](<.gitbook/assets/image (5).png>)![](<.gitbook/assets/image (18).png>)![](<.gitbook/assets/image (15).png>) |                                           ![](<.gitbook/assets/image (4).png>)![](<.gitbook/assets/image (5).png>)                                           |
| Network                |                                                                                                           Ethereum                                                                                                          |                                                                           Ethereum                                                                           |
| Token Address          |                                                                              [origindollar.eth](https://etherscan.com/address/origindollar.eth)                                                                             |                                                  [origineth.eth](https://etherscan.io/address/origineth.eth)                                                 |
| DApp URL               |                                                                                               [ousd.com](https://www.ousd.com)                                                                                              |                                                               [oeth.com](https://www.oeth.com)                                                               |
| Conversion rate        |                                                                                                        1 OUSD = 1 USD                                                                                                       |                                                                        1 OETH = 1 ETH                                                                        |
| Assets                 |                                                                                                       USDT, USDC, DAI                                                                                                       |                                                                   ETH, stETH, rETH, frxETH                                                                   |
| Strategies             |                                                                                       Compound, Aave, Curve, Convex, Curve AMO, Morpho                                                                                      |                                                                   Curve, Convex, Curve AMO                                                                   |
| Auto-compounds         |                                                                                                            Daily+                                                                                                           |                                                                            Daily+                                                                            |
| Collateralization      |                                                                                                             100%                                                                                                            |                                                                             100%                                                                             |
| Oracles                |                                                                                                          Chainlink                                                                                                          |                                                               Chainlink + Curve TWAP for frxETH                                                              |
| Timelock               |                                                                                                           48 hours                                                                                                          |                                                                       0 hours (for now)                                                                      |
| Governance             |                                                                                                        veOGV holders                                                                                                        |                                                                   5 of 8 multisig (for now)                                                                  |
| Audits                 |                                                                                       Trail of Bits, Solidified, Certora, OpenZeppelin                                                                                      |                                                       Trail of Bits, Solidified, Certora, OpenZeppelin                                                       |
| Launched               |                                                                                                        September 2020                                                                                                       |                                                                           May 2023                                                                           |
| Performance fee        |                                                                              <p>10% for veOGV holders<br>10% for buying protocol owned CVX</p>                                                                              |                                                               20% for buying protocol owned CVX                                                              |
| Redemption fee         |                                                                                                            0.25%                                                                                                            |                                                                             0.25%                                                                            |

While the code powering OUSD and OETH is the same, there are a number of configuration differences between the two products. We are also planning on deploying the latest smart contracts for OETH and then back-porting those improvements to OUSD.  We will do our best to keep these docs updated but consider the smart contracts as the authoritative source of truth on these.

|                       | Origin Dollar (OUSD) | Origin Ether (OETH) |
| --------------------- | -------------------- | ------------------- |
| AutoAllocateThreshold | 25,000 USD           | 10 ETH              |
| VaultBuffer           | 0                    | 0                   |
| RebaseThreshold       | 1,000 USD            | 1 ETH               |
| MaxSupplyDiff         | 5%                   | 3%                  |
| TrusteeAddress        | Strategist multisig  | Strategist multisig |
| TrusteeFee            | 10% -> 20% soon      | 20%                 |

