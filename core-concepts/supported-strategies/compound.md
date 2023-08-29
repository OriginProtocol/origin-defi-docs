# Compound

Compound is a lending protocol and platform built on Ethereum and launched in September 2018. Users can earn compounding interest on or borrow assets against collateral. Each supported asset is aggregated in its own liquidity pool and interest rates are adjusted automatically based on supply and demand.

Collateral balances are represented by ERC-20 cTokens, which automatically accrue interest and increase in value over time relative to the underlying asset they represent. Users can borrow assets against the value of their cTokens. cTokens are freely transferable and can be used on many other DeFi protocols. cTokens can be redeemed for their underlying collateral at any time.

Compound is governed by COMP, an ERC-20 governance token. COMP holders can propose and vote on protocol changes or delegate their votes to someone else. COMP tokens are awarded pro-rata to users of the protocol daily, split equally between borrowers and lenders. A large portion of the COMP token supply was retained by the Compound team, investors, and advisors.

Compound has undergone multiple security audits by OpenZeppelin and Trail of Bits. The Compound protocol was formally verified by CertiK and has undergone economic stress testing by Gauntlet. Compound maintains a bug bounty program.

OUSD's Compound strategy collects and sells COMP tokens. The resulting stablecoins are added to the OUSD vault and distributed as yield.



| Resources      |                                                                                                                |
| -------------- | -------------------------------------------------------------------------------------------------------------- |
| Official site  | [https://compound.finance/](https://compound.finance/)                                                         |
| Developer docs | [https://compound.finance/docs](https://compound.finance/docs)                                                 |
| GitHub         | [https://github.com/compound-finance/compound-protocol](https://github.com/compound-finance/compound-protocol) |

{% hint style="info" %}
The Compound strategy is currently inactive due to [governance consensus](https://governance.ousd.com/proposals/30894412376194853647122581916496530536830189795097427662392821757029264128284). However, any veOGV holder can propose its activation anytime.
{% endhint %}
