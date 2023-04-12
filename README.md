---
description: The easiest way to stack ETH or USD
---

# Introduction

{% hint style="warning" %}
These docs are very much a work in progress. We're working on updating them in time for the launch of OETH in May 2023. For the most part, OETH works almost exactly like OUSD. If you understand OUSD, you already understand how OETH works too.
{% endhint %}

This documentation explains the technical design of both **Origin Dollar (OUSD)** and **Origin Ether (OETH)**. Both products are designed to deliver superior DeFi yields directly to your Ethereum wallet. Access the best yields available on ETH or USD with none of the hassles typically associated with yield-farming. No staking. No lockups. Constant compounding.

OUSD and OETH use the same codebase but accept different collateral and utilize different combinations of strategies depending on the opportunities in the market. OUSD is designed to help you accumulate more dollars, whereas OETH helps you accumulate more ETH. OUSD is a stablecoin that tracks the price of USD. OETH works in the same way but tracks the price of ETH instead of US dollars. Both assets are 100% permissionless and always redeemable for their backing collateral.

OUSD was originally launched in September 2020 and has been battle-tested over time with hundreds of millions of dollars in circulating supply. The smart contracts have also been thoroughly audited by some of the top firms in the space including Trail of Bits and Open Zeppelin. OETH is scheduled to launch in May 2023 using the same core contracts as OUSD. The main difference is that OETH uses ETH and liquid staking derivates (LSDs) as the backing collateral instead of dollar-backed stablecoins. OETH also normalizes the accounting across the various supported LSDs so you don't need to do any math to figure out the amount of underlying ETH. 1 OETH = 1 ETH worth of value.

Both tokens are governed by OGV stakers who earn a portion of the fees that are generated.

|                          |                              Origin Dollar (OUSD)                              |                        Origin Ether (OETH)                        |
| ------------------------ | :----------------------------------------------------------------------------: | :---------------------------------------------------------------: |
| 100% redeemable for      |       <img src=".gitbook/assets/image (19).png" alt="" data-size="line">       | <img src=".gitbook/assets/image (1).png" alt="" data-size="line"> |
| Strategies               |        <img src=".gitbook/assets/image (2).png" alt="" data-size="line">       |   <img src=".gitbook/assets/image.png" alt="" data-size="line">   |
| Network                  |                                    Ethereum                                    |                              Ethereum                             |
| Address                  |       [origindollar.eth](https://etherscan.com/address/origindollar.eth)       |    [origineth.eth](https://etherscan.io/address/origineth.eth)    |
| DApp URL                 |                        [ousd.com](https://www.ousd.com)                        |                  [oeth.com](https://www.oeth.com)                 |
| Conversion rate          |                                 1 OUSD = 1 USD                                 |                           1 OETH = 1 ETH                          |
| Backing Assets           |                                 USDT, USDC, DAI                                |                      ETH, stETH, rETH, frxETH                     |
| Strategies               |        Compound, Aave, Curve, Convex, Curve AMO, Morpho, Uniswap (soon)        |                      Curve, Convex, Curve AMO                     |
| Auto-compounding         |                                     Daily+                                     |                               Daily+                              |
| Collateralization        |                                      100%                                      |                                100%                               |
| Oracles                  |                                    Chainlink                                   |                 Chainlink + Curve TWAP for frxETH                 |
| Timelock                 |                                    48 hours                                    |                        0 -> 48 hours (soon)                       |
| Governance               |                                   OGV stakers                                  |               5 of 8 multisig -> OGV stakers (soon)               |
| Audits                   |                Trail of Bits, Solidified, Certora, OpenZeppelin                |          Trail of Bits, Solidified, Certora, OpenZeppelin         |
| Bug bounty               |                                    $250,000                                    |                              $250,000                             |
| Insurace Security Rating |                                       AAA                                      |                                N/A                                |
| Launched                 |                                 September 2020                                 |                              May 2023                             |
| Performance fee          | <p>10% for veOGV holders -> <br> +10% for buying protocol owned CVX (soon)</p> |                 20% for buying protocol owned CVX                 |
| Redemption fee           |                                      0.25%                                     |                               0.25%                               |

While the code powering OUSD and OETH is the same, there are a number of configuration differences between the two products. We are also planning on deploying the latest smart contracts for OETH and then back-porting those improvements to OUSD.  We will do our best to keep these docs updated but consider the smart contracts as the authoritative source of truth on these.

|                       | Origin Dollar (OUSD) | Origin Ether (OETH) |
| --------------------- | -------------------- | ------------------- |
| AutoAllocateThreshold | 25,000 USD           | 10 ETH              |
| VaultBuffer           | 0                    | 0                   |
| RebaseThreshold       | 1,000 USD            | 1 ETH               |
| MaxSupplyDiff         | 5%                   | 3%                  |
| TrusteeAddress        | Strategist multisig  | Strategist multisig |
| TrusteeFee            | 10% -> 20% soon      | 20%                 |

