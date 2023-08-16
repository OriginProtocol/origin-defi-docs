# Yield Generation

**Automated Yield Farming**

While the Cambrian explosion of new lending and automated market maker pools has fueled total value locked (TVL), it has also made it increasingly challenging for yield farmers to manually allocate capital in efficient and optimal ways.

[Yearn](https://yearn.finance/) has demonstrated that smart contracts can automate the rebalancing of funds across various strategies to optimally earn lending interest, market-making fees, and rewards tokens. Over time, new strategies will be deployed that maximize returns while minimizing risk and dependencies.

![Automated yield farming on the OUSD protocol](../../.gitbook/assets/ousd\_earnings\_graphic.png)

OUSD uses the following high-level strategies for generating yield:

{% content-ref url="lending.md" %}
[lending.md](lending.md)
{% endcontent-ref %}

{% content-ref url="market-making.md" %}
[market-making.md](market-making.md)
{% endcontent-ref %}

{% content-ref url="rewards.md" %}
[rewards.md](rewards.md)
{% endcontent-ref %}

The protocol is able to generate higher yields than competing protocols due to a combination of important design decisions that amplify the rewards that are returned to OToken holders:

* Exit fees are returned to the pool, rewarding long-term holders.
* Price oracles favor the collective over the individual, again rewarding long-term holders.
* Smart contracts must manually opt-in to earn yield. This allows the protocol to put more capital to work than would be otherwise possible. For example, the OUSD that is being held on Uniswap does not rebase, but the backing stablecoins are still deployed and earning yield on behalf of OUSD holders.
* Yields tend to get compressed as more funds are deployed into a given strategy. By spreading capital across multiple strategies at once, OUSD is able to able to deploy more capital with less yield compression.
* The gas costs of harvesting yield are amortized across the entire pool. This makes it economical to harvest more frequently, leading to faster compounding. The more frequent the compounding periods, the faster your money grows.
* The [AMO](../supported-strategies/curve-metapools.md) allows the protocol to earn up to 2x the rewards using the same amount of capital.
* The protocol invests in ensuring future rewards by using a portion of the performance fee to buy flywheel tokens such as CVX. The purchased CVX tokens are vote-locked and used to vote for the AMO pools which drive additional CRV incentives to the pools, creating a sustainable source of yield for OTokens.

The net effect of these benefits is that **OTokens are able to consistently return higher yields** than you would get deploying directly into any of the underlying strategies on their own.
