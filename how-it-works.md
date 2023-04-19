# How It Works

**100% Backed and Stable**

Origin Dollar (OUSD) and Origin Ether (OETH) are ERC-20 tokens for the Ethereum network.

**OUSD** is a stable currency that is backed 1:1 by USDT, USDC and DAI. As a result, 1 OUSD should always be very close to 1 USD in value.&#x20;

**OETH** is a stable currency that is backed 1:1 by Ether and liquid staking derivatives like stETH, rETH, and sfrxETH. As a result, 1 OETH should always be very close to 1 ETH in value.

{% hint style="success" %}
1 OUSD = 1 USD

1 OETH = 1 ETH
{% endhint %}

**Buying OUSD or OETH**

Users can upgrade their existing stablecoins to OUSD using [app.ousd.com](https://app.ousd.com) or convert their ETH or supported LSDs to OETH using [app.oeth.com](https://app.oeth.com). Once upgraded, your OUSD or OETH will immediately begin accruing yield that compounds automatically.

The Origin dapps will intelligently route users' transactions to give them the best available price while taking slippage and gas costs into consideration. This means that the dapps will sometimes encourage users to buy OUSD or OETH that is already in circulation versus minting new coins from the vault. The dapps will choose from multiple sources of liquidity and will suggest the option that gives the user the best possible rate.

**Selling OUSD or OETH**

Users can redeem their OUSD or OETH for the underlying collateral at any time. Just as with buying, the Origin dapp will intelligently route users' transactions to give them the best available price while taking slippage, gas costs, and the vault's exit fee into consideration. This means that the dapps will often help users sell their OUSD or OETH on AMMs instead of redeeming with the vault and incurring the protocol's exit fee.

A 0.25% exit fee is charged upon redemption of OUSD via the vault. The exit fee for OETH has initially been set to 0 but will be updated prior to the public launch. This fee is distributed as additional yield to the remaining participants in the vault (ie. other OUSD or OETH holders). The fee serves as a security feature to make it difficult for attackers to take advantage of lagging oracles, preventing them from siphoning stablecoins from the vault in the event of mispriced underlying assets. The fee exists to incentivize long-term holders over short-term speculators.

Upon redemption, the vault will determine which coins to return to the user. The vault will return coins in the same ratio as the current holdings. This lack of user optionality protects the vault in the event that any of the supported stablecoins loses their peg.

{% hint style="warning" %}
Redemptions incur an **exit fee** and the user doesn't get to pick which coins they receive. Users can often avoid this fee by swapping on an exchange instead.
{% endhint %}

#### A**utomated Yield Farming**

The smart contracts generate yield by deploying the deposited collateral into trusted DeFi protocols such as Compound, Aave, Curve, Convex and Morpho. There may be new diversified strategies added to the vault in the future as approved by governance. Earned interest, trading fees, and rewards tokens are swapped and reinvested to produce OUSD or OETH-denominated yields. Over time, the protocol will rebalance assets between different earning strategies in order to maximize yields. Users are able to benefit from faster compounding and rebalancing of assets as the farming costs are shared across the entire pool.

#### **Elastic Supply**

The generated returns are passed on to the holders of OUSD and OETH via constant rebasing of the money supply (up only). Both coins constantly increase their money supply in response to the yield the protocol has generated. This allows the price of OUSD to stay pegged at 1 USD and OETH to stay pegged at 1 ETH while the balances in token holders' wallets adjust in real-time to reflect yields that have been earned by the protocol.

The end result is two tokens that are easy to spend, earn outsized risk-adjusted yields automatically, and are more desirable to hold than ether, stablecoins, or liquid staking derivatives.
