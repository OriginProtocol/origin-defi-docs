# Incentivized Harvesting Guide

The OUSD Harvester contract collects reward tokens earned by the OUSD strategies, sells them, and sends them on to increase protocol yield. **Anyone can call the harvest and earn 1% of the resulting USDT** for doing so. This creates a self-incentivizing system that operates at a known cost to the protocol.

### When to call

You'll want to call this contract when it is profitable to do so. You gain the 1% harvest USDT given by the contract, and spend the gas cost to send the transaction.

The simplest way to calculate both of these is to simulate the transaction. You can then look at the resulting transfers to know the income received, and you can look at the gas amount used, the current gas prices, and the current cost of ETH, to find out the cost.

Alternatively you can precompute the gas used for a given strategy's harvest, look up the pending reward tokens using various online services, then do your calculations without using the blockchain.

The amount of rewards increases at a fairly steady, predictable rate. The primary variation is in gas prices, which will make a much bigger minute to minute difference on when you should call this.

When calculating profitability, remember to account for the cost to swap back to ETH from USDT.

### How to call

When you call the harvest, **you will want to use some form of MEV protection** such as [Flashbots](https://docs.flashbots.net/flashbots-protect/rpc/quick-start/). Otherwise bots will see that your transaction is profitable, and execute it ahead of you, leaving you no gain and only gas fees.

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
