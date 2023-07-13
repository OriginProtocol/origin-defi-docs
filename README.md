---
description: The easiest way to stack ETH and USD
---

# Introduction

This documentation explains the technical design of Origin DeFi's OTokens: **Origin Dollar (OUSD)** and **Origin Ether (OETH)**. OTokens are designed to deliver superior DeFi yields directly to your Ethereum wallet. Access the best yields available on ETH or USD with none of the hassles typically associated with yield-farming. No staking. No lockups. Constant compounding.

Origin DeFi's OTokens use the same codebase but accept different collateral and utilize different combinations of strategies depending on the opportunities in the market. OUSD is designed to help you accumulate more dollars, whereas OETH helps you accumulate more ETH. OUSD is a stablecoin that tracks the price of USD. OETH works in the same way but tracks the price of ETH instead of US dollars. Both assets are 100% permissionless and always redeemable for their backing collateral.

OUSD was originally launched in September 2020 and has been battle-tested over time with hundreds of millions of dollars in circulating supply. The smart contracts have also been thoroughly audited by some of the top firms in the space including Trail of Bits and OpenZeppelin. OETH launched in May 2023 using the same core contracts as OUSD. The main difference is that OETH uses ETH and liquid staking tokens (LSTs) as the backing collateral instead of dollar-backed stablecoins. OETH also normalizes the accounting across the various supported LSTs so you don't need to do any math to figure out the amount of underlying ETH. 1 OETH is always worth 1 ETH.

Both tokens are governed by **Origin DeFi Governance (OGV)** stakers who earn a portion of the fees generated and a share of protocol-owned value.

<table><thead><tr><th></th><th width="235.33333333333331" align="center">Origin Dollar (OUSD)</th><th align="center">Origin Ether (OETH)</th></tr></thead><tbody><tr><td>100% redeemable for</td><td align="center"> <img src=".gitbook/assets/image (19).png" alt="" data-size="line"> </td><td align="center"><img src=".gitbook/assets/image (1) (1) (3).png" alt="" data-size="line"></td></tr><tr><td>Strategies</td><td align="center"><img src=".gitbook/assets/image (2) (2).png" alt="" data-size="line"></td><td align="center"><img src=".gitbook/assets/image.png" alt="" data-size="line"></td></tr><tr><td>Network</td><td align="center">Ethereum</td><td align="center">Ethereum</td></tr><tr><td>Address</td><td align="center"><a href="https://etherscan.com/address/origindollar.eth">origindollar.eth</a></td><td align="center"><a href="https://etherscan.io/address/origineth.eth">origineth.eth</a></td></tr><tr><td>DApp URL</td><td align="center"><a href="https://www.ousd.com">ousd.com</a></td><td align="center"><a href="https://www.oeth.com">oeth.com</a></td></tr><tr><td>Conversion rate</td><td align="center">1 OUSD = 1 USD</td><td align="center">1 OETH = 1 ETH</td></tr><tr><td>Backing Assets</td><td align="center">USDT, USDC, DAI</td><td align="center">ETH, stETH, rETH, frxETH</td></tr><tr><td>Strategies</td><td align="center">Compound, Aave, Curve, Convex, Curve AMO, Morpho, Uniswap (soon)</td><td align="center">Curve, Convex, Curve AMO</td></tr><tr><td>Auto-compounding</td><td align="center">Daily+</td><td align="center">Daily+</td></tr><tr><td>Collateralization</td><td align="center">100%</td><td align="center">100%</td></tr><tr><td>Oracles</td><td align="center">Chainlink</td><td align="center">Chainlink + Curve TWAP for frxETH</td></tr><tr><td>Timelock</td><td align="center">48 hours</td><td align="center">48 hours</td></tr><tr><td>Governance</td><td align="center"> OGV stakers</td><td align="center">OGV stakers</td></tr><tr><td>Audits</td><td align="center">Trail of Bits, Solidified, Certora, OpenZeppelin</td><td align="center">Trail of Bits, Solidified, Certora, OpenZeppelin</td></tr><tr><td>Bug bounty</td><td align="center">$1,000,000</td><td align="center">$1,000,000</td></tr><tr><td>Insurace Security Rating</td><td align="center">AAA</td><td align="center">N/A</td></tr><tr><td>Launched</td><td align="center">September 2020</td><td align="center">May 2023</td></tr><tr><td>Performance fee</td><td align="center">10% for veOGV holders<br> 10% for buying protocol-owned flywheel tokens</td><td align="center">20% for buying protocol-owned flywheel tokens</td></tr><tr><td>Redemption fee</td><td align="center">0.25%</td><td align="center">0.50%</td></tr></tbody></table>

While the code powering OUSD and OETH is similar, there are a number of configuration differences between the two products. We are also planning on deploying the latest smart contracts for OETH and then back-porting those improvements to OUSD.  We will do our best to keep these docs updated but consider the smart contracts as the authoritative source of truth on these.

|                       | Origin Dollar (OUSD) | Origin Ether (OETH) |
| --------------------- | -------------------- | ------------------- |
| AutoAllocateThreshold | 25,000 USD           | 10 ETH              |
| VaultBuffer           | 0                    | 0                   |
| RebaseThreshold       | 1,000 USD            | 1 ETH               |
| MaxSupplyDiff         | 5%                   | 3%                  |
| TrusteeAddress        | Strategist multisig  | Strategist multisig |
| TrusteeFee            | 20%                  | 20%                 |

