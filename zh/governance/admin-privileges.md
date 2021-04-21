# 管理员权限

The OUSD smart contracts are designed to be owner upgradable. The Origin team uses two different Gnosis multisig wallet contracts in order to make changes to the protocol. These multisig wallets have been [audited by OpenZeppelin](https://blog.openzeppelin.com/gnosis-multisig-wallet-audit-d702ff0e2b1e/), [ConsenSys Dilligence](https://blog.gnosis.pm/the-gnosis-multisig-wallet-and-our-commitment-to-security-ce9aca0d17f6), Origin’s team, and others.

{% hint style="info" %}
Time-delayed admin actions gives users a chance to exit OUSD if its admins become malicious, are compromised, or make a change that the users do not like.
{% endhint %}

The primary admin is a 5 of 8 multisig contract which is required to make any code changes to the protocol. OUSD can only be upgraded from this 5 of 8 multi-sig wallet. The keys to this multi-sig are held by individuals with close ties to the company, and not even the Origin founders acting together have enough control to execute owner functions on their own. In addition, the OUSD contracts are owned by the [timelock](../smart-contracts/api/timelock.md) which allows the Origin team to continue making changes to the protocol, but only after a time delay.

Some functionality, such as rebalancing funds between strategies or pausing deposits, can be triggered without the timelock and with far less signers. This allows the Origin team to react more quickly to market conditions or security threats. These signers, known as Strategists,  have the ability to execute a limited number of functions __with only 2 of 9 signers.

Having these admin privileges is necessary in the early days to ensure that the protocol is secure and optimized for earning yields while minimizing risks. We expect to release multiple iterations of our smart contracts in the first several months of the protocol's existence.

Once several upgrade cycles have been completed, we intend to transfer ownership from our company control to a decentralized governance contract, thereby allowing the community to vote and participate in future protocol updates.

