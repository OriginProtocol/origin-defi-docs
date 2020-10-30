# Fiyat Oracle'ları

OUSD, 1 USD'de sabit kalacak ve temelindeki stabilcoinlerle 1: 1 desteklenecek şekilde tasarlanmıştır. Bu, göründüğünden daha zor çünkü bu temel sabit paralar, sürekli olarak kendi istenen 1 USD sabitlerinden sapıyor. Günlük dalgalanmaların çoğu küçük olsa da, geçmişte meydana gelen ve gelecekte tekrar ortaya çıkması muhtemel olan büyük fiyat dalgalanmaları olmuştur.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Coin</th>
      <th style="text-align:left"><b>Düşük</b>
      </th>
      <th style="text-align:left"><b>Yüksek</b>
      </th>
      <th style="text-align:left"><b>Delta</b>
      </th>
      <th style="text-align:left"><b>Kaynak</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">USDC</td>
      <td style="text-align:left">
        <p>$0,929222 </p>
        <p>13 Mart 2020</p>
      </td>
      <td style="text-align:left">
        <p>$1.11
</p>
        <p>15 Ekim 2018</p>
      </td>
      <td style="text-align:left">$0.180778
</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/usd-coin/">CoinMarketCap
</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDC</td>
      <td style="text-align:left">
        <p>$0.924188</p>
        <p>02 Ağu 2020</p>
      </td>
      <td style="text-align:left">
        <p>$1.17
</p>
        <p>08 Mayıs 2019</p>
      </td>
      <td style="text-align:left">$0.245812
</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/usd-coin">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DAI</td>
      <td style="text-align:left">
        <p>$0.945505
</p>
        <p>10 Mayıs 2020</p>
      </td>
      <td style="text-align:left">
        <p>$1.11
</p>
        <p>13 Mart 2020</p>
      </td>
      <td style="text-align:left">$0.164495
</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/multi-collateral-dai/">CoinMarketCap
</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DAI</td>
      <td style="text-align:left">
        <p> $0.903243
</p>
        <p>Kasım 25, 2019</p>
      </td>
      <td style="text-align:left">
        <p>$1.22</p>
        <p>13 Mart 2020</p>
      </td>
      <td style="text-align:left">$0.316757</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/dai">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDT</td>
      <td style="text-align:left">
        <p>$0.849809</p>
        <p>02 Şubat 2017</p>
      </td>
      <td style="text-align:left">
        <p>$1.21</p>
        <p>27 Mayıs 2017</p>
      </td>
      <td style="text-align:left">$0.360191</td>
      <td style="text-align:left"><a href="https://www.coingecko.com/en/coins/tether">CoinGecko</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">USDT</td>
      <td style="text-align:left">
        <p>$0.572521</p>
        <p>02 Mart 2015</p>
      </td>
      <td style="text-align:left">
        <p>$1.32</p>
        <p>24 Temmuz 2018</p>
      </td>
      <td style="text-align:left">$0.747479</td>
      <td style="text-align:left"><a href="https://coinmarketcap.com/currencies/tether/">CoinMarketCap
</a>
      </td>
    </tr>
  </tbody>
</table>

The rebasing function treats 1 stablecoin as 1 OUSD for simplicity and to protect OUSD balances from being affected by the daily fluctuations in the price of the underlying stablecoins. Since the rebase function only counts coins, OUSD balances should only increase.

In order to mint and redeem the appropriate number of OUSD on entry and exit, the smart contracts need to accurately price the USDT, USDC, and DAI that is entering and exiting the system. As a decentralized protocol, OUSD must rely on non-centralized sources for these prices.

{% hint style="info" %}
OUSD fetches the price from multiple on-chain oracles and uses the exchange rate that is most advantageous for the pool when minting or redeeming.
{% endhint %}

In order to prevent malicious attacks and to encourage long-term investors over short-term speculators, the OUSD contract compares price feeds from multiple sources and will use whichever exchange rate benefits the entire pool over the individual. This mechanism protects the pool's funds from arbitrageurs and prevents any individual from being able to take advantage of any temporary inefficiencies caused by mispriced oracles to deplete the shared pool of assets.

This protects the funds in the pool while rewarding long-term holders. Since the safest price depends on the direction of the trade, the Origin oracle exposes both a `priceUSDMint()` and a `priceUSDRedeem()`.

Here is the initial set of oracles that are being used by OUSD:

{% embed url="https://compound.finance/docs/prices" caption="" %}

{% embed url="https://feeds.chain.link/eth-usd" caption="" %}

The following oracles have been implemented, but are not currently being used due to gas costs:

{% embed url="https://uniswap.org/docs/v2/core-concepts/oracles/" caption="" %}

{% tabs %}
{% tab title="DAI/USD" %}
The following oracles are used to fetch or compute a price for **DAI/USD:**

| Oracle          | Pair      | Contract                                     |
|:--------------- |:--------- |:-------------------------------------------- |
| Open Price Feed | DAI/USD   | 0x922018674c12a7f0d394ebeef9b58f186cde13c1   |
| Chainlink       | DAI/USD   | 0xa7D38FBD325a6467894A13EeFD977aFE558bC1f0   |
| Chainlink       | DAI/ETH   | 0x037E8F2125bF532F3e228991e051c8A7253B642c   |
| _Uniswap v2_    | _DAI/ETH_ | _0xA478c2975Ab1Ea89e8196811F51A7B7Ade33eB11_ |
{% endtab %}

{% tab title="USDT/USD" %}
The following oracles are used to fetch or compute a price for **USDT/USD:**

| O**racle**      | Pair       | Contract                                     |
|:--------------- |:---------- |:-------------------------------------------- |
| Chainlink       | USDT/ETH   | 0xa874fe207DF445ff19E7482C746C4D3fD0CB9AcE   |
| Open Price Feed | USDC/USD   | 0x922018674c12a7f0d394ebeef9b58f186cde13c1   |
| _Uniswap v2_    | _USDT/ETH_ | _0x0d4a11d5eeaac28ec3f61d100daf4d40471f1852_ |
{% endtab %}

{% tab title="USDC/USD" %}
The following oracles are used to fetch or compute a price for **USDC/USD:**

| O**racle**      | Pair       | Contract                                     |
|:--------------- |:---------- |:-------------------------------------------- |
| Chainlink       | USDC/ETH   | 0xdE54467873c3BCAA76421061036053e371721708   |
| Open Price Feed | USDC/USD   | 0x922018674c12a7f0d394ebeef9b58f186cde13c1   |
| _Uniswap v2_    | _USDC/ETH_ | _0xb4e16d0168e52d35cacd2c6185b44281ec28c9dc_ |
{% endtab %}

{% tab title="ETH/USD" %}
Since not all oracles have direct USD pairs, the protocol also fetches the prices for **ETH/USD** in order to calculate USD prices using ETH. Again, to be safe, the protocol chooses the most advantageous for the fund instead of the individual.

| Oracle          | Pair    | Contract                                   |
|:--------------- |:------- |:------------------------------------------ |
| Open Price Feed | ETH/USD | 0x922018674c12a7f0d394ebeef9b58f186cde13c1 |
| Chainlink       | ETH/USD | 0xF79D6aFBb6dA890132F9D7c355e3015f15F3406F |
{% endtab %}
{% endtabs %}

It is possible that additional oracles will be added to the protocol over time. Support may also be removed if any of these oracles become unreliable.

