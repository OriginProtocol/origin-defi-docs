---
description: Chainlink secures the protocol from pricing attacks
---

# Price Oracles

### Stablecoin Pricing

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

As an added precaution, OUSD never pays more than a dollar for a stablecoin, nor sells a stablecoin for less than a dollar. In situations where DAI, USDC or USDT fall below the $1 peg, [OIP-4 disables minting](https://github.com/OriginProtocol/origin-dollar/issues/1000) of additional OUSD tokens using the de-pegged asset. Oracles giving wrong prices will not result in a reduction of the number of stablecoins held. Gains that are collected as a result of stablecoins slipping from their peg are redistributed to the remaining holders of OUSD in the form of additional yield.

As a decentralized protocol, OUSD must rely on non-centralized sources for these prices. OUSD uses Chainlink oracles for pricing data for DAI, USDC, and USDT. You can read more about [our decision to work with Chainlink](https://blog.originprotocol.com/how-origin-uses-chainlink-oracles-to-secure-ousd-bff5601e840e) on our blog. The specific Chainlink oracles being utilized are listed in the [Registry](../smart-contracts/registry.md).

### Liquid Staking Token Pricing

Similar to the rebasing function in OUSD that treats 1 stablecoin as 1 OUSD for clarity, OETH employs the accessible Chainlink oracles to ensure that the protocol doesn’t overcompensate for LSTs which might be traded at a diminished rate. In order to accurately price stETH and rETH as they interface with the system, Chainlink's pricing oracles come into play. For the specifics of frxETH, OETH leans on the [Frax Oracle](https://docs.frax.finance/frax-oracle/frax-oracle-overview). This oracle integrates data from dual on-chain sources: the EMA oracle stemming from the frxETH/ETH liquidity pool on Curve and the TWAP oracle from the Uniswap frxETH/FRAX pool.

The oracles are just one of multiple security features protecting the vault. You are, however, relying on the Strategists multisig to manually pause deposits in the case of a major depegging of the underlying assets.



| Coin   | Low                                | High                             | Delta       | Source                                                                         |
| ------ | ---------------------------------- | -------------------------------- | ----------- | ------------------------------------------------------------------------------ |
| stETH  | <p>Ξ0.3356<br>Dec 24, 2020</p>     | <p>Ξ3.0304<br>Nov 16, 2021</p>   | Ξ2.6948     | [Coinmarketcap](https://coinmarketcap.com/currencies/steth/)                   |
| stETH  | <p>Ξ0.72793330<br>Dec 22, 2020</p> | <p>Ξ1.272594<br>Nov 10, 2021</p> | Ξ0.5446496  | [Coingecko](https://www.coingecko.com/en/coins/lido-staked-ether)              |
| rETH   | <p>Ξ0.5411<br>Jun 18, 2022</p>     | <p>Ξ2.9001<br>Dec 1, 2021</p>    | Ξ2.359      | [Coinmarketcap](https://coinmarketcap.com/currencies/rocket-pool-eth/)         |
| rETH   | <p>Ξ0.69870372<br>Jun 18, 2022</p> | <p>Ξ3.002089<br>Dec 01, 2021</p> | Ξ2.30338528 | [Coingecko](https://www.coingecko.com/en/coins/rocket-pool-eth)                |
| frxETH | <p>Ξ0.8363<br>Mar 10, 2023</p>     | <p>Ξ1.3420<br>Apr 17, 2023</p>   | Ξ0.5057     | [Coinmarketcap](https://coinmarketcap.com/currencies/frax-finance-frax-ether/) |
| frxETH | <p>Ξ0.98370559<br>Nov 23, 2022</p> | <p>Ξ1.015148<br>Apr 16, 2023</p> | Ξ0.03144241 | [Coingecko](https://www.coingecko.com/en/coins/frax-ether)                     |

Oracles that produce inaccurate valuations will not necessarily lead to a diminished number of tokens preserved. Surpluses obtained as a consequence of tokens deviating from their peg are reallocated to the ongoing holders of OETH in the form of supplementary yield.

### Reward Token Oracles & Front Running Protection

When reward tokens from the various strategies are sold for additional yield, Chainlink oracles are used to ensure that the sale price slippage has not exceeded normal bounds. The same is also true for OGV buybacks that are executed using a portion of the yield that is generated by the protocol.\
\
When minting and redeeming, a minimum required amount can be passed into the contract call to ensure that the entire transaction fails if not enough OUSD/OETH or stablecoins/LSTs would be returned to the user due to changing prices.
