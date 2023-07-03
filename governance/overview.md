# Overview

**Principles**

Origin Dollar and Origin Ether are decentralized protocols governed by multiple stakeholders around the world. Everything from yield generation to fee collection and distribution is managed by a set of smart contracts on the Ethereum blockchain. These contracts are upgradeable with a timelock and controlled by hundreds of governance token holders. While the initial contracts and yield-earning strategies were developed by the Origin team, anyone can shape the future of the protocol by creating or voting on proposals, submitting new strategies, or contributing code improvements. We intend for all important decisions to be made through community governance and for limited powers to be delegated to trusted contributors who are more actively involved in the day-to-day management of the protocol.

**Proposal lifecycle**

Changes to the Origin Dollar and Origin Ether contracts and the movement of funds require on-chain proposals to be created, approved, and executed by governance token holders. All pending and historical on-chain proposals are visible on the [Origin DeFi Governance DApp](https://governance.ousd.com).

Initiating this type of formal, binding proposal requires technical skills and knowledge of the protocol’s code. On-chain proposals also involve transaction costs (Ethereum gas) necessary to update the state of the blockchain. As a result, most proposals go through an informal, off-chain process occurring on the [Origin DeFi Governance Snapshot Space](https://vote.ousd.com). Snapshot enables any eligible governance token holder to create a proposal or vote at no cost. This also reduces the complexity and expense required to make a proposal and allows for the community to signal its approval or opposition to a given change. We encourage everyone to propose improvements at any time.

It’s natural for proposals to be accompanied by healthy debate or discussion regarding implementation, reasoning, methodology, etc. Rather than host these discussions on a separate forum, they currently live in the [Origin Protocol Discord server](https://originprotocol.com/discord) under the defi-governance-forum channel.

**Participating**

Two high-level criteria are required to vote and make proposals:

1. Hold sufficient veOGV tokens (Vote-Escrowed Origin DeFi Governance)
   * No minimum to vote on existing proposals
   * 10,000 veOGV to create a Snapshot proposal
   * 10,000,000 veOGV to create an on-chain proposal
2. If you staked OGV prior to March 2023, you will need to [self-delegate](https://governance.ousd.com/register-vote) as a separate transaction. All new first-time stakers will have their voting power self-delegated going forward.
   * Can also be delegated to another Ethereum account
   * Partial delegation is not supported

Here are the step-by-step instructions to vote and create a proposal:

1. Buy OGV from [Curve](https://curve.fi/#/ethereum/pools/factory-crypto-205/swap), [Uniswap](https://app.uniswap.org/#/swap?outputCurrency=0x9c354503C38481a7A7a51629142963F98eCC12D0\&chain=mainnet) or an exchange such as [Huobi](https://www.huobi.com/en-in/exchange/ogv\_usdt), [KuCoin](https://www.kucoin.com/trade/OGV-USDT), [Gate](https://gate.io/trade/OGV\_USDT), [Bitget](https://www.bitget.com/en/spot/OGVUSDT\_SPBL), or [MEXC Global](https://www.mexc.com/exchange/OGV\_USDT?inviteCode=1498J)
2. Stake OGV at [governance.ousd.com/stake](https://governance.ousd.com/stake)
3. Discuss the proposal in the [Origin Protocol Discord server](https://originprotocol.com/discord)
4. Submit the proposal to [vote.ousd.com](https://vote.ousd.com) for a signaling vote
5. Vote for the implementation to be executed at [governance.ousd.com/proposals](http://governance.ousd.com/proposals)

Feel free to use one of the [templates](../guides/governance-templates/) as a guide for writing governance proposals

Routine funds management and precautionary actions are handled by multi-sig signers known as the [Strategists](https://docs.ousd.com/governance/admin-privileges#strategist). These users have been delegated authority to implement reallocations across OUSD’s and OETH's yield-generating strategies in addition to being granted other limited emergency powers. Strategist actions do not require an on-chain vote involving veOGV holders since they are executed from a 2 of 9 multi-sig account. However, they are usually accompanied by an off-chain Snapshot proposal except in rare cases when the Strategists proactively respond to market conditions (e.g. de-risking from a given strategy or collateral type).
