# Маркет-мейкинг

**Владейте долей на децентрализованных биржах**

Автоматизированные маркет-мейкеры \(AMM\) быстро стали предпочтительной формой децентрализованного бирж в сети Ethereum. Частично это связано со сложностью поддержки стакана заявок в DEXах на Ethereum 1.0, который может конкурировать с быстрой работой и низким проскальзыванием на централизованных биржах. Кроме того, такие AMM, как Uniswap, относительно понятны в использовании и экономят больше газа.

AMM могут открывать новые рынки только тогда, когда поставщики ликвидности предоставляют ликвидность (например, несколько токенов для данных торговых пар или пулов). В обмен на предоставление ликвидности, поставщики ликвидности вознаграждаются торговыми комиссиями, когда другие пользователи обменивают токены. For example, when traders swap two tokens on Uniswap v3, they are currently charged anywhere between 0.05% and 1% on top of the gas fees. These fees are distributed pro-rata to liquidity providers of the pair based on the percentage of total liquidity that they have provided.

{% hint style="info" %}
[Непостоянная потеря](https://medium.com/@pintail/uniswap-a-good-deal-for-liquidity-providers-104c0b6816f2) - важный фактор риска, который необходимо осознать, но эта проблема в значительной степени смягчается за счет того, что OUSD предоставляет ликвидность только для стейблкоинов примерно равной стоимости.
{% endhint %}

The OUSD protocol routes USDT, USDC, and DAI to highly-performing liquidity pools as determined by trading volume and rewards tokens \(e.g. Curve rewards CRV tokens to liquidity providers\). Затем доходность передается держателям OUSD.

В настоящее время мы интегрируем следующий автоматизированный маркет-мейкер:

{% page-ref page="../supported-strategies/curve.md" %}




