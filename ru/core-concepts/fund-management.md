# Управление средствами

The OUSD smart contract aggregates all users' stablecoin deposits into a single pool of deployable assets. Затем средства распределяются по одной или нескольким стратегиям получения прибыли**** в любой момент времени. Vault отдает предпочтение высокодоходным стратегиям, но также стремится поддерживать диверсификацию по нескольким стратегиям. Диверсификация устраняет единые точки сбоя и снижает риски.

В отличие от Yearn Vaults, TokenSets или Zapper, пользователи не выбирают индивидуальные стратегии. Все депонированные стейблкоины и, следовательно, все токены OUSD являются взаимно конвертируемыми. Once our full governance structure is implemented, these decisions will be made with input from OUSD governance token holders. OGN holders are encouraged to participate in creating and voting on proposals that impact the protocol in the [OGN governance portal](https://vote.originprotocol.com).

**Стратегии заработка**

Стратегии заработка позволяют задействовать вложенный капитал на различных платформах DeFi. Vault будет определять, какие стратегии активны и какой процент от задействованного капитала они получат. Эти стратегии будут улучшаться и заменяться со временем.

**Стратегия**

Первоначальная версия смарт-контракта OUSD Vault (Хранилища OUSD) дает каждой действующей стратегии некоторый вес, колеблющийся от 0% до 100% для выполнения простого распределения активов. Эти веса стратегий будут часто смещаться посредством обновлений Origin в краткосрочной перспективе и децентрализованного управления в долгосрочной перспективе.

**Диверсификация**

Диверсификация между несколькими базовыми [платформами](supported-strategies/) DeFi снизит риски смарт-контрактов и других системных рисков. Смарт-контракт будет рассчитывать текущие и ожидаемые APY, чтобы обеспечить конкурентоспособную прибыль держателям OUSD. Со временем контракт Vault (Хранилища) будет обновлен для интеллектуального и автономного переключения между стратегиями без ручного вмешательства. Например, Vault будет автоматически перемещать капитал между различными стратегиями кредитования для оптимизации доходности.

Тем не менее, все еще ожидается, что определенные параметры риска или решения о том, будут ли определенные стратегии включены в автоматизированный механизм принятия решений, будут приниматься посредством голосования руководства. 
