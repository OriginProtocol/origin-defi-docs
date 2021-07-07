# Гибкое предложение

**Гибкое предложение. Стабильная цена.**

OUSD работает не так, как большинство токенов. Вместо увеличения цены по мере увеличения стоимости активов под управлением (как в случае с Compound cTokens или Yearn yTokens), стоимость одного OUSD остается постоянной и составляет примерно 1 доллар США. Вместо этого контракты постоянно корректируют денежную массу и автоматически обновляют баланс в кошельке каждого держателя токенов, чтобы отразить доход, полученный протоколом.

{% hint style="info" %}
Думайте об этом как о процентах, начисляемых на ваш банковский счет. Расчетная единица и стоимость доллара США не меняются. Вы просто получаете больше долларов США со временем, зарабатывая проценты.
{% endhint %}

![](../../.gitbook/assets/ousd_docs_graphics_4.png)

Этот механизм был вдохновлен новым подходом, принятым [Ampleforth](https://www.ampleforth.org/), но есть некоторые ключевые отличия, которые стоит выделить:

1. OUSD на 100% обеспечен другими стейблкоинами и не имеет такой же проблемы с поддержанием привязки к доллару. Учитывая простоту создания и выкупа OUSD, мы можем рассчитывать на арбитражеров, которые обеспечат поддержание привязки.
2. Перераспределение OUSD будет только увеличивать предложение, поскольку количество вновь созданных OUSD привязано к реализованной прибыли, полученной с помощью лежащих в основе стратегий. Ваш основной капитал защищен до тех пор, пока все в порядке с основными протоколами кредитования/AMM и протоколами стейблкоинов. Ваш баланс OUSD никогда не уменьшится, но его стоимость может упасть, если произойдет сбой в основных системах.
3. В отличие от Ampleforth, который производит перераспределение раз в день, денежная масса OUSD постоянно обновляется в режиме реального времени по мере генерирования доходности. Перераспределение запускается регулярно, когда пользователи взаимодействуют с контрактами OUSD.

**Запуск перераспределения вручную**

Кто угодно в любой момент может запустить перераспределние, [вызвав функцию перераспределения в хранилище](https://etherscan.io/address/originvault.eth#writeProxyContract). Вы можете сделать это в Etherscan, подключив кошелек web3.
