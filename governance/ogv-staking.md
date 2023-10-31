# OGV Staking

### Why Staking

{% hint style="info" %}
The goal of OGV Staking is to transfer both economic and governance power to those most committed to the long-term success of the protocol.
{% endhint %}

Origin's products are built for the long term. As such, we need community governance that is similarly focused on the long-term good of the protocol. We incentivize long-term thinking by having users lock Origin DeFi Governance tokens (OGV) for a period of time in exchange for economic and voting power in the form of Vote-Escrowed Origin DeFi Governance tokens (veOGV). The longer users choose to stake, the more power they receive. This ensures that power is held by those who are most committed to the long-term success of the protocol. In return for staking OGV, users not only earn the ability to create proposals and vote on the future of the protocol. They are also rewarded with additional OGV that can be collected at any time.

### Economic & Voting Power Calculation

To receive voting power in the form of veOGV, you stake OGV for a duration of your choice. You cannot withdraw the staked OGV amount until the lock-up period is over, and veOGV cannot be transferred.

The amount of veOGV you receive is based on two factors: the amount of OGV you stake and the end date (expiration) of the lock-up. A multiplier is applied to the OGV amount to calculate the resulting veOGV amount, and this multipler increases according to the length of the lock-up. In other words, the further into the future the end date is, the higher the multiplier. If two users stake the same amount of OGV on different occasions but their lock-up periods end on the same date, they will still receive the same amount of veOGV. The user who stakes earlier will accrue more rewards and be able to exercise her power earlier, but both users will have the same power once they have staked the same amount with the same expiration.

The staking multiplier curve is exponential. The multiplier grows by 1.8x with each additional year forward. As a result, a 4-year stake will be approximately 10.5 times larger than a 30-day stake. (1.8 \* 1.8 \* 1.8 \* 1.8 = 10.5). Similarly, a 1-year stake created 4 years from now will be roughly 10.5 times larger in OGV terms than the same stake created now. Extending stakes works similarly. If you extend your stake by a year, you immediately receive a 1.8x multiplier on your veOGV for that stake since the end date has moved forward by a year.

The maximum staking duration is 4 years. The minimum is 30 days.

Over time, the effective power of old stakes is diluted by newer stakes having larger multipliers. When the lock-up period ends, you keep your economic and voting power until you choose to unstake. The way to maximize your power is to stake for the full 4-year period and regularly extend the lock-up period. You can also compound your power by claiming accrued rewards and staking them to increase your veOGV balance.

#### Comparing veOGV to veCRV

If you're familiar with [Curve Finance](https://curve.fi)'s governance token model, you'll notice that OUSD's is similar in many ways. When designing the veOGV model, we were initially inspired by veCRV and borrowed the general concept of rewarding longer-term stakers with significantly more power. However, we introduced several improvements that drastically reduce the code complexity and gas costs for stakers of OGV. Here are a few differences between the two implementations:

* OGV holders can stake for multiple periods of time from the same Ethereum account.
* OGV stakers can delegate their votes, allowing for users to participate in governance from a hot wallet while holding a large amount of OGV in a cold wallet or with an insured custodian.
* ve**OGV** uses an exponential decay function as opposed to ve**CRV**'s linear equation.
* ve**CRV** holders see their balances go down as time passes, ending at 0 when their lock-up periods expire. ve**OGV** holders see their balances remain the same throughout their lock-up periods. Instead of their balances falling, their share becomes a lower percentage of the overall vote-escrowed token supply.

{% embed url="https://www.youtube.com/watch?v=0ETwQ0La6gc" %}
Origin Founder, Josh Fraser explaining veOGV at ETH Seoul
{% endembed %}

### Staking Rewards

Rewards for staking OGV can be collected at any time. These rewards are generated from OETH and OUSD performance fees, as well as from the front-loaded inflation schedule that is designed to encourage OGV holders to stake OGV and remove it from circulation even as the total supply of the token grows.

| OGV per month inflation | Time range              |
| ----------------------- | ----------------------- |
| 100,000,000             | 1657584000 - 1660176000 |
| 80,000,000              | 1660176000 - 1665360000 |
| 56,000,000              | 1665360000 - 1675728000 |
| 33,600,000              | 1675728000 - 1696464000 |
| 16,800,000              | 1696464000 - 1727568000 |
| 6,720,000               | 1727568000 - 1779408000 |
| 2,016,000               | 1779408000              |

We intend for inflationary staking rewards to be a bootstrapping mechanism that will continually be replaced by more sustainable protocol revenue. As a reminder, 20% of all yield generated by OUSD and OETH is collected as a protocol fee. Half of this fee is used to buy back OGV on the open market to be distributed as additional rewards for stakers. While this protocol revenue will start as a small percentage of the rewards, we anticipate it will become the primary source of rewards as OToken adoption grows.

{% hint style="info" %}
Visit [the Origin DeFi Governance dapp](https://governance.ousd.com/stake) in a Web3-enabled browser to stake your OGV.
{% endhint %}

### Buying OGV

OGV is currently available on [1inch](https://app.1inch.io/#/1/simple/swap/ETH/OGV), [Curve](https://curve.fi/#/ethereum/pools/factory-crypto-205/swap), [Uniswap](https://app.uniswap.org/#/swap?outputCurrency=0x9c354503C38481a7A7a51629142963F98eCC12D0\&chain=mainnet), [Huobi](https://www.huobi.com/exchange/ogv\_usdt/), [KuCoin](https://www.kucoin.com/trade/OGV-USDT), [Gate.io](https://www.gate.io/trade/OGV\_USDT), [MEXC](https://www.mexc.com/exchange/OGV\_USDT), and [Bitget](https://www.bitget.com/spot/OGVUSDT\_SPBL).
