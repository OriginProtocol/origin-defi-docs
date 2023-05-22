# Timelock

Both OUSD and OETH are protected by timelock contracts, which prevent changes from taking effect without advance notice. Because OUSD's governance is fully decentralized and OETH has not yet made this transition, there are separate timelock implementations for each.

#### Origin DeFi governance

Both OUSD and OGV are subject to a 48-hour timelock contract based on [OpenZeppelin's Governor](https://docs.openzeppelin.com/contracts/api/governance). This prevents any on-chain upgrades from taking effect without Origin's community having advance notice of the impending change.

#### Origin Ether governance

Although OETH mostly consists of battle-tested code from OUSD and every new addition is extensively audited, it's important for the Admin (5 of 8) to be able to make swift upgrades in the unlikely event that a vulnerability is discovered. For this reason, the OETH timelock is initially configured with a minimum delay of 60 seconds. Over time, this will be extended before ownership is fully transferred over to OGV stakers.

| Time period                 | Minimum delay |
| --------------------------- | ------------- |
| Current                     | 60 seconds    |
| After one week              | 24 hours      |
| After one month             | 48 hours      |
| After full decentralization | 48 hours      |
