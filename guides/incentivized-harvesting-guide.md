# Incentivized Harvesting Guide

The OToken Harvester contracts collect reward tokens earned by the strategies, sells them, and sends them on to increase protocol yield. **Anyone can call the harvest and earn 1-2% of the resulting USDT or WETH** for doing so. This creates a self-incentivizing system that operates at a known cost to the protocol.

### When to call

You'll want to call this contract when the reward returned is greater than the cost of gas to execute the function. The Harvester smart contract pays a 2% reward when harvesting CRV and 1% for everything else. The reward is paid in USDT for OUSD and WETH for OETH.

The simplest way to calculate both of these is to simulate the transaction. You can then look at the resulting transfers to know the income received, and you can look at the gas amount used, the current gas prices, and the current cost of ETH, to find out the cost.

Alternatively, you can precompute the gas used for a given strategy's harvest, look up the pending reward tokens using various online services, then do your calculations without using the blockchain.

The amount of rewards increases at a fairly steady, predictable rate. The primary variation is in gas prices, which will make a much bigger minute-to-minute difference on when you should call this.

When calculating profitability, you may also want to account for the cost to swap back to ETH from USDT or from WETH to ETH.

### How to call

When you call the harvest, **you will want to use some form of MEV protection** such as [Flashbots](https://docs.flashbots.net/flashbots-protect/rpc/quick-start/). Otherwise, bots will see that your transaction is profitable, and execute it ahead of you, leaving you no gain and only gas fees.

To harvest, you call `harvester.harvestAndSwap(strategyAddress, rewardTo)`.

The harvester address and strategyAddresses can be found in the [contract registry](../smart-contracts/registry.md). The `rewardTo` address is the account that will receive the USDT funds as a reward for calling the function - use your own address for it.

Below is the harvestAndSwap ABI:

```
[{
  "inputs": [
    {
      "internalType": "address",
      "name": "_strategyAddr",
      "type": "address"
    },
    {
      "internalType": "address",
      "name": "_rewardTo",
      "type": "address"
    }
  ],
  "name": "harvestAndSwap",
  "outputs": [],
  "stateMutability": "nonpayable",
  "type": "function"
}]
```

### **Harvesting from Curve/Convex**

When harvesting rewards from Convex, you may want to first claim the rewards from Curve on behalf of Convex. Convex offers a similar incentive to whoever covers the gas costs to perform this work. Whoever calls the function first will receive 1% of the CRV that is claimed.  Additional token incentives that are offered on some pools are not included in the calculation for your caller reward, just the CRV.

You can see how many rewards have been earned but not yet claimed by Convex by [filtering for Convex's address on Curve](https://classic.curve.fi/pools?see=0x989AEb4d175e16225E39E87d0D97A3360524AD80). Search for "ousd" or "oeth" to see how many CRV are available to be claimed.&#x20;

To claim these pending rewards from[^1] Curve, you'll want to call the `earmarkRewards()` function on [Convex's Booster contract](https://etherscan.io/address/0xf403c135812408bfbe8713b5a23a04b3d48aae31). You'll need to pass the `_pid` for the specific pool you wish to call. You can find these pool IDs by clicking the info tab next to each pool on [Convex staking](https://www.convexfinance.com/stake). The Convex pool (\_pid) is 56 for OUSD and 174 for OETH. Once earmarked, these rewards will be slowly distributed over a week to prevent them from being stolen with opportunistic flash loans.&#x20;

Happy harvesting!



[^1]: 
