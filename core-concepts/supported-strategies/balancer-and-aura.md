# Balancer & Aura

Balancer is a decentralized AMM (automated market maker) that launched in March 2020. It is a protocol built on Ethereum and represents a flexible building block for programmable liquidity. Aura is a protocol that boosts rewards from liquidity mining on Balancer. These two protocols have a similar relationship to that of Curve and Convex.&#x20;

Aura is a fork of Convex and has a very similar architecture. Balancer, on the other hand, offers comparable functionality to Curve but has a significantly different architecture. By separating the AMM curve logic and math from the core swapping functionality, Balancer becomes an extensible AMM that can incorporate any number of swap curves and pool types. This includes:&#x20;

* Traditional 50/50  _x \* y = k_ weighted pools
* Custom weights like 80/20 for controlled exposure
* Stable swap curves
* Nested pools
* Pools with changing weights&#x20;
* Concentrated liquidity pools
* Managed pools that allow customizable parameters
* Entire protocols to be built on top (e.g. Gyroscope)

All of the aggregated liquidity on Balancer is then easily accessible for swappers, aggregators, and arbitrageurs. The Balancer [Vault](https://docs.balancer.fi/concepts/vault) optimizes batching and path logic so that gas costs and capital requirements remain extremely low. Each individual pool and project built on top benefits from the global liquidity within Balancer, which brings deep liquidity for base assets and opens up swap paths.

The Balancer/Aura strategies utilize the Aura protocol to earn boosted BAL and AURA token rewards.&#x20;



| Resources               |                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Balancer Official site  | [https://balancer.fi/](https://balancer.fi/)                                                                     |
| Balancer Developer Docs | [https://docs.balancer.fi/concepts/overview/basics.html](https://docs.balancer.fi/concepts/overview/basics.html) |
| Balancer Github         | [https://github.com/balancer](https://github.com/balancer)                                                       |
| Aura Official site      | [https://aura.finance/](https://aura.finance/)                                                                   |
| Aura Developer Docs     | [https://docs.aura.finance/](https://docs.aura.finance/)                                                         |
| Aura Github             | [https://github.com/aurafinance](https://github.com/aurafinance)                                                 |
