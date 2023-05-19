# Timelock

The timelock contract enforces a 48 hour wait period before any changes to the OUSD or OETH contracts can be executed. The timelock is the owner of our [ERC-20](../architecture.md), [Vault](vault.md), and [Strategies](strategies.md) contracts. Time-delaying admin actions gives users a chance to exit OUSD or OETH if its admins become malicious, are compromised, or make a change that the users do not like.

{% hint style="info" %}
The timelock is a safety measure that gives OUSD/OETH holders 48 hours to withdraw their funds if they have objections to any proposed upgrades to the protocol.
{% endhint %}

Origin Protocol is using a slightly modified version of the [Compound Timelock](https://compound.finance/docs/governance) which has been [audited by OpenZeppelin](https://blog.openzeppelin.com/compound-finance-patch-audit/). The two notable differences are:

1. OUSD/OETH will initially use a shorter wait period (48 hours) than Compound (72 hours) to allow for a faster response if any issues are discovered.
2. Some actions, such as reallocating funds between existing strategies and freezing deposits can be called immediately by a multisig wallet without requiring the 48 waiting period. This is in case a major vulnerability is discovered.
