# Analytics Dashboard

{% hint style="info" %}
Visit [analytics.ousd.com](https://analytics.ousd.com) to see how funds are allocated, view historical performance data, and track your personal gains.
{% endhint %}

The [APY dashboard](https://analytics.ousd.com/apy) is primarily intended for consumption by our engineering team, but we went ahead and deployed it since our ethos is "public by default" and everything that we do is [open-source](http://github.com/OriginProtocol). Unfortunately, that often means erring on the side of transparency and not necessarily the side of taking the time to explain things clearly.

Before diving into the yield calculation, it's important to understand how OUSD works both in terms of [yield generation](https://docs.ousd.com/core-concepts/yield-generation) and [rebasing](https://docs.ousd.com/core-concepts/elastic-supply). You can read all about that in these [docs](https://docs.ousd.com/), including [the part about smart contracts being excluded from yield](https://docs.ousd.com/core-concepts/elastic-supply/rebasing-and-smart-contracts).

To summarize how APY is calculated, it's the annualized rate of change in OUSD's internal accounting of users' balances between two points in time. To understand that, let's break down the columns in the historical APY table (in reverse order).

**Ratio**

There are two types of OUSD balances: rebasing (most accounts) and non-rebasing (smart contracts that have not opted in). The OUSD token contract maintains a separate internal accounting for each type of balance using what it calls "credits". The ratio shown here is the rebasing supply of OUSD divided by the rebasing credits, which gives us the exchange rate between the two.

**Credits**

Some smart contracts holding OUSD have unique credit balances because their rebasing status has changed at some point in the past (by opting in or out). Here we show the sum of all rebasing credits and non-rebasing credits. When multiplied by the ratio, it gives the difference between backing supply and non-rebasing supply.

**Non-rebasing**

This is the portion of supply held in other smart contracts that have not opted in to rebasing. When added to (credits \* ratio), this equals backing supply. Note also that the **%** column shows the percentage of OUSD that is non-rebasing.

**Boost**

The APY is effectively "boosted" for rebasing accounts thanks to the fact that some OUSD is non-rebasing. Think about all of the stablecoins that were used as collateral to mint the non-rebasing OUSD. Those stablecoins are still earning through our yield farming strategies, but the gains are accruing only to the rebasing accounts. The result is that the effective APY is higher than it would be without this mechanism. The boost is the measure of this difference. If boost is 100%, then regular OUSD holders are enjoying double the APY that they otherwise would.

**APR/APY calculation**

Bringing this full circle, we currently measure yield by measuring the change in the [rebasing credits per token](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/token/OUSD.sol#L45) between two points in time. But there are a few other considerations to note. First, we have to make an assumption about how many Ethereum blocks are mined on an average day. We use a [fixed 6,500](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L43), but the actual number of blocks per day is variable. Second, we need a reasonable time horizon to measure. We focus on 30 days, which has proven to be a relatively consistent window of time during which a complete sample of yield-generating activities has occurred. Third, we convert APR into APY by assuming [constant daily compounding](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L449-L451). In other words, yield is constantly being reinvested into the same strategies. Finally, there is one notable drawback to using the rebase ratio to measure yield. Since rebase events currently occur sporadically (and not very frequently in a world of high gas prices), the APY won't reflect earnings that have not yet been translated to account balances. For example, there could be an interest rate spike in Compound or a volume spike in the Curve 3pool strategy, which would cause OUSD to earn more than it does on an average day. Until [the rebase method](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/vault/VaultCore.sol#L365-L370) gets called, the APY will underreport these earnings. In fact, anyone who sells OUSD during that time would be missing out on the "[next rebase](https://analytics.ousd.com/)". The good news is that you should be able to observe the change in your balance over one week and it (annualized) should approximately equal our advertised APY.
