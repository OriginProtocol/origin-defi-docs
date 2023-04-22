# Governance

{% hint style="warning" %}
OETH will be initially governed by a 5 of 8 multisig upon launch. After launch, the timelock will be gradually increased from 0 to 48 hours, before ownership is fully transferred over to OGV stakers. This is in case any major issues are discovered.
{% endhint %}

### Fully decentralized governance

The OUSD smart contracts are governed entirely by [OGV stakers](ogv-staking.md). Proposals can be submitted by anyone with 10,000,000 or more veOGV. A minimum of 20% of the veOGV supply is required to reach quorum. There is no minimum to vote on existing proposals. All passing proposals are subject to the [48 hour timelock](../smart-contracts/api/timelock.md) before being executed.

{% hint style="info" %}
Time-delayed admin actions give users a chance to exit OUSD if any malicious proposals are passed or the protocol is changing in a way that users do not like.
{% endhint %}

### Strategists

Some functionality, such as rebalancing funds between strategies or pausing deposits, can be triggered without the timelock and with far fewer signers. This allows the Origin team to react more quickly to market conditions or security threats. These signers, known as Strategists, have the ability to execute a limited number of functions \_\_ with only 2 of 9 signers.

The strategist multisig can do the following actions on the vault:

* reallocate - move funds between strategies
* setVaultBuffer - adjust the amount of funds held outside strategies for cheaper redeems.
* setAssetDefaultStrategy - which strategy mints and redeems pull from for a particular strategy
* withdrawAllFromStrategy - remove funds from a single strategy and send them to the vault
* withdrawAllFromStrategies - remove funds from all active strategies and send them to the vault
* pauseRebase - pause all rebases
* pauseCapital - pause all mints and redeems
* unpauseCapital - allow all mints and redeems
