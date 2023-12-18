# Funds Management

***

The OUSD and OETH smart contracts each aggregate users' deposits into pools of assets that are then deployed into earning strategies based on preset allocations.

## OUSD Funds Allocation

veOGV holders decide how OUSD assets are distributed between the supported strategies using Snapshot voting. These votes happen off-chain and do not cost any gas. The results of any successful reallocation proposals are executed on-chain by members of the [Strategist multi-sig](https://etherscan.io/address/0xF14BBdf064E3F67f51cd9BD646aE3716aD938FDC) (known as "Strategists") subject to their review and discretion.

We encourage the community to favor high-yield strategies to ensure OUSD provides the highest risk-adjusted stablecoin yield in DeFi.&#x20;

## **OETH Funds Allocation**

OETH funds are managed according to parameters developed and agreed upon by the Origin DeFi DAO. These parameters establish a framework for maximizing OETH’s risk-adjusted yield while ensuring transparency in the allocation of funds.

* Allocate a minimum of 5% of OETH collateral and no more than 66% to any individual LST (stETH, rETH, frxETH) in order to diversify funds while safeguarding against major losses from slashing or de-peg events. (Note: In extraordinary circumstances, strategists may convert all LSTs into WETH.)
* Maintain a minimum allocation of 15% to WETH or ETH (combined) across vault and all strategies.
* Holding of LSTs stETH and rETH should stay below 50% of their individual supply-side exit liquidity to ensure easy exits of LST collateral. If this 50% threshold is exceeded by 500bps the strategists will take action to exit a portion of the position.
* Prior to this framework being proposed, frxETH was already above the on-chain liquidity threshold. As we already have been given indications that direct withdrawals will be available soon, we should aim to avoid selling below the peg at a loss. Thus, an exception of 60% exit liquidity cap is placed on frxETH.
* Maintain our share of our Convex AMO pool between 80-90%. Make adjustments if our share falls to 75% or exceeds 95%.
* Any individual non-AMO strategy should not exceed 50% of total OETH funds in order to prevent over-reliance on one strategy and manage risk. If a pool goes 100 bps over this cap, start de-risking.
* For non-AMO strategies, OETH funds should account for no more than 50% of a pool's total TVL. This helps avoid major slippage and liquidity issues when exiting.
* Ensure that a sufficient portion of each collateral type is held either in default strategies or directly in the vault, guaranteeing that 1% of OETH circulating supply can be redeemed at any time without requiring Strategist intervention.
* For new strategies, start with a test allocation of no more than 50 ETH.
* If the initial test allocation proves successful, ramp up allocation in a geometric sequence over a two-week period at the discretion of the Strategists.
* Minimize costly reallocations by limiting them to a maximum of twice per week.
* Only reallocate when doing so will boost OETH yield by at least 5 bps.
* Consider the breakeven point for any reallocation, aiming for a threshold of 7 days.

| Parameter                                                               | Value     | Intervention Threshold |
| ----------------------------------------------------------------------- | --------- | ---------------------- |
| Allocation to stETH                                                     | 5% - 66%  | - -                    |
| Allocation to rETH                                                      | 5% - 66%  | - -                    |
| Allocation to frxETH                                                    | 5% - 66%  | --                     |
| Minimum allocation to WETH & ETH (combined)                             | 15%       | - -                    |
| Maximum share of stETH supply-side exit liquidity                       | 50%       | 500 bps                |
| Maximum share of rETH supply-side exit liquidity                        | 50%       | 500 bps                |
| Maximum share of frxETH supply-side exit liquidity                      | 60%       | 500 bps                |
| OETH share of Convex AMO                                                | 80% - 90% | 500 bps                |
| Maximum share of OETH funds allocated to any non-AMO strategy           | 50%       | 100 bps                |
| OETH maximum share of any non-AMO strategy                              | 50%       | 100 bps                |
| Minimum OETH circulating supply held in default strategies or the vault | 1%        | - -                    |
| Maximum test allocation for net-new strategies                          | 50 ETH    | N/A                    |
| Funding ramp-up period for net-new strategies                           | 2 weeks   | N/A                    |
| Maximum reallocations per week                                          | 2         | N/A                    |
| Minimum OETH yield boost for reallocation                               | ≥ 5 bps   | N/A                    |
| Minimum breakeven threshold for reallocation                            | 7 days    | N/A                    |

**Strategist Role and Discretion:**

Strategists are tasked with implementing these rules, monitoring market conditions, and making informed decisions to reallocate funds within the set guidelines.

Reallocation suggestions are permissionless and can be posted in the **Strategy allocations** topic on the **#defi-governance-forum** in [Origin's Discord](https://discord.com/channels/404673842007506945/1080502855720513557) provided they meet the established criteria and are subject to review by Strategists. Use the [OETH Math](https://docs.google.com/spreadsheets/d/1SwV9FagWOCw1hkv5l6Uqf6iWOn51-SONWcw2ODqBxfo/edit#gid=1917942072) sheet for reference.

Any amendments to these rules require approval through a governance vote conducted in the [Origin DeFi Snapshot Space](https://vote.ousd.com/).

{% hint style="info" %}
From a security standpoint, it is important to know that while Strategists have the ability to move funds between approved strategies or instantly pause rebasing in the case of an emergency, Strategists do not have the power to add new strategies or withdraw funds from the protocol.
{% endhint %}

***

***
