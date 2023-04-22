# Curve AMO

Both OUSD and OETH utilize Automated Market Operations (AMO). Origin uses the same battle-tested AMO design that was first pioneered by Frax. The AMO helps to maintain the peg, increases capital efficiency, and maximizes yields for OUSD and OETH holders. The AMO is allowed to enact arbitrary monetary policy so long as it does not negatively impact the peg. It is important to know that the protocol remains 100% collateralized at all times even as the money supply programmatically expands and contracts in response to market conditions.

{% hint style="info" %}
The AMO helps to maintain the peg, increase capital efficiency, and maximize yields for OUSD and OETH holders.&#x20;
{% endhint %}

MetaPools are Curve pools that allow for one token to trade with another underlying base pool. 3Pool is the most common base pool and it is the only one currently supported by our strategy codebase. For example, a TUSD MetaPool using 3Pool as its base pool enables users to seamlessly trade between TUSD and 3Pool (DAI/USDC/USDT).

Having 3Pool as a base pool is helpful in multiple ways:

* Prevents diluting existing pools
* Allows Curve to list less liquid assets
* More volume and more trading fees for the DAO

MetaPool liquidity providers can then deposit the LP tokens to Convex gauge to earn boosted CRV and CVX rewards.

### Understanding Curve's MetaPool

From Curve's point of view, the OUSD and OETH MetaPools are no different from any other MetaPool running on Curve's contracts. The difference with the AMO is the way the protocol deploys and withdraws funds to the pool.

In order to maintain the peg, both sides of a Curve pool must remain balanced. When the protocol deposits funds into the MetaPool, it deploys liquidity to both sides of the pool -- 3CRV (USDT/DAI/USDC) on one side and OUSD or OETH on the other. This ensures that after deploying liquidity, the balance of the pool doesn't change - since we deploy equal amounts to both sides of the pool. When the MetaPool is more heavily balanced towards 3CRV tokens, we deploy extra OUSD or OETH to preserve the pool balance, but never more than a 1:2 ratio.

This approach of providing (in most cases) double the liquidity to the OUSD MetaPool allows the protocol to earn up to twice as many rewards using the same amount of capital.&#x20;

The AMO strategy collects and sells CRV and CVX tokens and the resulting collateral (stables for OUSD, LSDs for OETH) are added to the vault and show up in the form of extra units of OUSD or OETH in your wallet.

#### Protocol Owned Liquidity

It is important to note that the OUSD and OETH deployed into the AMO is not minted by the Vault in a classic manner using backing collateral. Instead, the OUSD/OETH that is minted by the AMO is backed by itself. When the strategy removes liquidity from the AMO alongside 3Pool tokens, the OUSD/OETH is also removed and burned.

Remaining 100% collateralized is an important bedrock component of the protocol. The protocol owned OUSD/OETH held in the MetaPool is controlled by the protocol and it never enters circulation without generating profit for the protocol. When traders add or remove OUSD/OETH from the MetaPool, it has an effect similar to redeeming or minting since our strategy is capable of burning or creating new supply to maintain the pool's balance. Ultimately, OUSD/OETH can still be redeemed at any time for the underlying collateral on a 1:1 basis.

It's a bit counterintuitive that the protocol can remain fully collateralized even while deploying unbacked collateral into the pool. Let's look at an example to understand how this is possible. Let's say 1000 OETH/ETH has been deployed into the Curve pool by the AMO. This means the protocol owns 500 ETH and 500 unbacked OETH. A user comes along and swaps 100 ETH for 99.8 OETH. They receive slightly fewer units of because of the trading fees and slippage. At the end of this transaction, the user is holding 99.8 OETH and the protocol is holding 600.2 ETH and 400 unbacked OETH. Since the user must transfer their ETH to Curve in order to withdraw OETH, the previously unbacked OETH immediately becomes backed as part of the transaction. The extra .2 ETH is owned by the liquidity provider (aka the protocol) and is distributed to holders as extra profit.&#x20;

Not only has this model been extensively tested and proven by the Frax team, but we have also completed extensive testing in forked Mainnet node environment simulating how flash loans could mint large amounts, deploy liquidity and then redeem it, manipulating the MetaPool at various stages of that procedure. No vulnerabilities have been found. For safety, funds are never directly deployed or withdrawn from the AMO as a result of a mint or redeem. Like the rest of the code, the AMO has been thoroughly audited by OpenZeppelin.
