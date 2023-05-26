# Fund Management

The OUSD smart contract aggregates all users' stablecoin deposits into a single pool of assets that are then deployed into earning strategies based on preset allocations. In contrast to Yearn Vaults, TokenSets, or Zapper opportunities, users do not select individual strategies. All deposited stablecoins and consequently all OUSD tokens are fungible. The same goes for all LSTs that are deposited into OETH.

The weighting of how assets are distributed between the supported strategies is decided by veOGV holders using weekly snapshot voting. These votes happen off-chain and do not cost any gas. The results of the weekly poll will then be executed on-chain by members of the [Strategist multi-sig](https://etherscan.io/address/0xF14BBdf064E3F67f51cd9BD646aE3716aD938FDC) (known as "Strategists") subject to their review and discretion.

Ultimately, we believe it should be up to the community to decide what the right balance of risk/reward is appropriate for OUSD. We encourage the community to favor high-yield strategies while still maintaining diversification across multiple strategies to remove single points of failure and minimize risk.

**How strategy allocation voting works:**

* New snapshot proposals will open for voting on [the OUSD governance portal](https://vote.ousd.com) every Monday at 20:00 UTC. The poll will be open for 48 hours, ending on Wednesday at 20:00 UTC.
* During this time, those interested can discuss allocation changes in a thread in the #governance channel on [Origin's Discord](https://www.originprotocol.com/discord).
* Each proposal will use "weighted voting", with options for each coin/strategy combination and an option to keep the existing allocation unchanged. veOGV holders can spread their votes among different listed strategies or the existing allocation.
* After the voting time has ended, Strategists will submit, verify, and execute transactions to change OUSD to the determined allocation percentages for the week. If more than 50% of the weighted votes are cast for the existing allocation, Strategists may choose to take no action.
* Allocations will be executed for strategies that use all stablecoins first (like Convex), then each stablecoin will be allocated to the remaining strategies according to the ratio of votes for that stablecoin / strategy combination.
* If the Strategists deem any of the allocations unsafe, they may choose to not execute those. In addition, Strategists may decline to execute minor adjustments where the gas costs would be greater than the expected benefits.
* Like all governance proposals, Strategist allocations must meet the minimum quorum requirements (currently 10M OGV) to be considered valid.
* From a security standpoint, it is important to know that while Strategists have the ability to move funds between approved strategies or instantly pause rebasing in the case of an emergency, Strategists do not have the power to add new strategies or withdraw funds from the protocol. Community members can use the Strategy Validator tools to more easily [create](https://analytics.ousd.com/strategist/creator) and [decode](https://analytics.ousd.com/strategist) which actions are being performed by the Strategists.
* When voting, please remember it is inefficient to move in and out of the Convex strategy frequently and some funds need to always remain outside of Convex in order to accommodate withdrawals.

***
