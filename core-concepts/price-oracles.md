---
description: OUSD uses Chainlink to secure the protocol from pricing attacks
---

# Price Oracles

OUSD is designed to stay pegged at 1 USD and be 1:1 backed with its underlying stablecoins. This is trickier than it sounds because these underlying stablecoins are constantly deviating from their own desired 1 USD pegs. While the majority of daily fluctuations are minor, there have been major swings in price that have occurred in the past and are likely to occur again in the future.

| Coin | **Low**                             | **High**                        | **Delta** | **Source**                                                                  |
| ---- | ----------------------------------- | ------------------------------- | --------- | --------------------------------------------------------------------------- |
| USDC | <p>$0.929222</p><p>Mar 13, 2020</p> | <p>$1.11</p><p>Oct 15, 2018</p> | $0.180778 | [CoinMarketCap](https://coinmarketcap.com/currencies/usd-coin/)             |
| USDC | <p>$0.924188</p><p>Aug 02, 2020</p> | <p>$1.17</p><p>May 08, 2019</p> | $0.245812 | [CoinGecko](https://www.coingecko.com/en/coins/usd-coin)                    |
| DAI  | <p>$0.945505</p><p>May 10, 2020</p> | <p>$1.11</p><p>Mar 13, 2020</p> | $0.164495 | [CoinMarketCap](https://coinmarketcap.com/currencies/multi-collateral-dai/) |
| DAI  | <p>$0.903243</p><p>Nov 25, 2019</p> | <p>$1.22</p><p>Mar 13, 2020</p> | $0.316757 | [CoinGecko](https://www.coingecko.com/en/coins/dai)                         |
| USDT | <p>$0.849809</p><p>Feb 02, 2017</p> | <p>$1.21</p><p>May 27, 2017</p> | $0.360191 | [CoinGecko](https://www.coingecko.com/en/coins/tether)                      |
| USDT | <p>$0.572521</p><p>Mar 02, 2015</p> | <p>$1.32</p><p>Jul 24, 2018</p> | $0.747479 | [CoinMarketCap](https://coinmarketcap.com/currencies/tether/)               |

The rebasing function treats 1 stablecoin as 1 OUSD for simplicity and to protect OUSD balances from being affected by the daily fluctuations in the price of the underlying stablecoins. Since the rebase function only counts coins, OUSD balances should only increase. 

In order to mint and redeem the appropriate number of OUSD on entry and exit, the smart contracts need to accurately price the USDT, USDC, and DAI that is entering and exiting the system. 

As an added precaution, OUSD never pays more than a dollar for a stablecoin. This prevents the protocol from being attacked via mispriced oracles. Any additional gains that are collected as a result of stablecoins slipping from their peg are redistributed to the remaining holders of OUSD in the form of additional yield.

As a decentralized protocol, OUSD must rely on non-centralized sources for these prices. OUSD uses Chainlink oracles for pricing data for DAI, USDC and USDT. You can read more about [our decision to work with Chainlink](https://blog.originprotocol.com/how-origin-uses-chainlink-oracles-to-secure-ousd-bff5601e840e) on our blog. Here are the Chainlink oracles we are currently using:

{% embed url="https://data.chain.link/usdt-usd" %}

{% embed url="https://data.chain.link/usdc-usd" %}

{% embed url="https://data.chain.link/dai-usd" %}

The specific smart contract address for each oracle being used are listed on our [registry](../smart-contracts/registry.md) page. It is possible that additional oracles will be added to the protocol over time. Support may also be removed if any of these oracles become unreliable.