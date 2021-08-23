- - -
description: OUSD uses Chainlink to secure the protocol from pricing attacks
- - -

# Oracle Harga

OUSD is designed to stay pegged at 1 USD and be 1:1 backed with its underlying stablecoins. This is trickier than it sounds because these underlying stablecoins are constantly deviating from their own desired 1 USD pegs. While the majority of daily fluctuations are minor, there have been major swings in price that have occurred in the past and are likely to occur again in the future.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Koin</th>
      <th style="text-align:left"><b>Rendah</b>
      </th>
      <th style="text-align:left"><b>Tinggi</b>
      </th>
      <th style="text-align:left"><b>Delta</b>
      </th>
      <th style="text-align:left"><b>Sumber</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">USDC</td>
      <td style="text-align:left">
        <p>$ 0,929222</p>
        <p>13 Maret 2020</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,11</p>
        <p>15 Oktober 2018</p>
      </td>
      <td style="text-align:left">$ 0,180778</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/usd-coin/">CoinMarketCap</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDC</td>
      <td style="text-align:left">
        <p>$ 0,924188</p>
        <p>02 Agu 2020</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,17</p>
        <p>08 Mei 2019</p>
      </td>
      <td style="text-align:left">$ 0,245812</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/usd-coin">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DAI</td>
      <td style="text-align:left">
        <p>$ 0,945505</p>
        <p>10 Mei 2020</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,11</p>
        <p>13 Maret 2020</p>
      </td>
      <td style="text-align:left">$ 0,164495</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/multi-collateral-dai/">CoinMarketCap</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DAI</td>
      <td style="text-align:left">
        <p>$ 0,903243</p>
        <p>25 November 2019</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,22</p>
        <p>13 Maret 2020</p>
      </td>
      <td style="text-align:left">$ 0,316757</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/dai">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDT</td>
      <td style="text-align:left">
        <p>$ 0,849809</p>
        <p>02 Feb 2017</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,21</p>
        <p>27 Mei 2017</p>
      </td>
      <td style="text-align:left">$ 0,360191</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/tether">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDT</td>
      <td style="text-align:left">
        <p>$ 0,572521</p>
        <p>02 Maret 2015</p>
      </td>
      <td style="text-align:left">
        <p>$ 1,32</p>
        <p>24 Juli 2018</p>
      </td>
      <td style="text-align:left">$ 0,747479</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/tether/">CoinMarketCap</a>
      </td>
    </tr>
  </tbody>
</table>

The rebasing function treats 1 stablecoin as 1 OUSD for simplicity and to protect OUSD balances from being affected by the daily fluctuations in the price of the underlying stablecoins. Since the rebase function only counts coins, OUSD balances should only increase.

In order to mint and redeem the appropriate number of OUSD on entry and exit, the smart contracts need to accurately price the USDT, USDC, and DAI that is entering and exiting the system.

As an added precaution, OUSD never pays more than a dollar for a stablecoin. This prevents the protocol from being attacked via mispriced oracles. Any additional gains that are collected as a result of stablecoins slipping from their peg are redistributed to the remaining holders of OUSD in the form of additional yield.

As a decentralized protocol, OUSD must rely on non-centralized sources for these prices. OUSD uses Chainlink oracles for pricing data for DAI, USDC and USDT. You can read more about [our decision to work with Chainlink](https://blog.originprotocol.com/how-origin-uses-chainlink-oracles-to-secure-ousd-bff5601e840e) on our blog. Here are the Chainlink oracles we are currently using:

{% embed url="https://data.chain.link/usdt-usd" %}

{% embed url="https://data.chain.link/usdc-usd" %}

{% embed url="https://data.chain.link/dai-usd" %}

The specific smart contract address for each oracle being used are listed on our [registry](../smart-contracts/registry.md) page. It is possible that additional oracles will be added to the protocol over time. Support may also be removed if any of these oracles become unreliable.

