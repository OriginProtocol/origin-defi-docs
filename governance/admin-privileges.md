# Governance

### Fully decentralized governance

The OUSD and OETH smart contracts are governed entirely by [OGV stakers](ogv-staking.md). Proposals can be submitted by anyone with 10,000,000 or more veOGV. A minimum of 20% of the veOGV supply is required to reach quorum. There is no minimum to vote on existing proposals. All passing proposals are subject to the [48-hour timelock](../smart-contracts/api/timelock.md) before being executed.

{% hint style="info" %}
Time-delayed admin actions give users a chance to exit OUSD or OETH if any malicious proposals are passed or the protocol is changing in a way that users do not like.
{% endhint %}

Here are the parameters currently\* configured on the Origin DeFi governance contract:

| Name                  | Value                      | Description                                                                                                                                                                              |
| --------------------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Voting delay          | 1 block                    | How soon the voting period begins following the submission of a proposal - can be used to enforce a delay after a proposal is published for users to buy tokens, or delegate their votes |
| Voting period         | 17,280 blocks (\~2.4 days) | The window of time for votes to be cast following the end of the voting delay                                                                                                            |
| Proposal threshold    | 10,000,000 veOGV           | The minimum number of tokens required for an account to be eligible to submit a proposal                                                                                                 |
| Quorum                | 20% of veOGV supply        | The minimum number of votes needed for a proposal to succeed (assuming a majority of them are in support of the proposal)                                                                |
| Late quorum extension | 11,520 blocks (\~1.6 days) | The amount of time required to pass from when a proposal reaches quorum until its voting period ends                                                                                     |
| Timelock delay        | 172,800 seconds (2 days)   | The minimum amount of time required after the end of the voting period before a proposal can be executed and take effect                                                                 |

> [\*as of 2023-08-09](#user-content-fn-1)[^1]

### Strategists

Some functionality, such as rebalancing funds between strategies or pausing deposits, can be triggered without the timelock and with far fewer signers. This allows the Origin team to react more quickly to market conditions or security threats. These signers, known as Strategists, have the ability to execute a limited number of functions with only 2 of 9 signers.

The strategist multi-sig can do the following actions on the vault:

* depositToStrategy - deposit multiple assets from the vault into the strategy.
* withdrawFromStrategy - withdraw multiple assets from the strategy to the vault.
* setVaultBuffer - adjust the amount of funds held outside strategies for cheaper redeems.
* setAssetDefaultStrategy - which strategy mints and redeems pull from for a particular strategy
* withdrawAllFromStrategy - remove funds from a single strategy and send them to the vault
* withdrawAllFromStrategies - remove funds from all active strategies and send them to the vault
* pauseRebase - pause all rebases
* pauseCapital - pause all mints and redeems
* unpauseCapital - allow all mints and redeems
* swapCollateral - swaps collateral assets sitting in the vault

[^1]: 
