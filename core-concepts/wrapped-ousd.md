# Wrapping

Wrapped versions of OUSD and OETH are available as non-rebasing alternatives that still earn yield. This may make it easier to use these coins as building blocks in other contracts. The wrapped versions may also provide tax benefits in some jurisdictions.

![Two flavors, up only](https://cdn-images-1.medium.com/max/1600/1\*cqRG-8-64XYx9QChoMxk3g.png)

### How wrapped tokens work

When you wrap OUSD, you get back a fixed number of wOUSD tokens. This number will not go up - you will have the same number of wOUSD tokens tomorrow as you have today. However, the number of OUSD tokens that you can unwrap will go up over time.

For example, if you wrap 10,000 OUSD, you might receive 9,423 wOUSD. If you hold for a while, you will still have 9,423 wOUSD, but when you unwrap the wOUSD, you receive 11,500 OUSD.

Both OUSD and wOUSD earn at the same rate and can be transferred just like any other ERC-20 token. wOUSD is one of the first implementations of [ERC-4626](https://eips.ethereum.org/EIPS/eip-4626), which is an extension on ERC-20 that provides basic functionality for depositing and withdrawing tokens and reading balances on a tokenized vault. wOUSD was independently [audited by Solidified](https://github.com/OriginProtocol/security/blob/3dc8c1dec2f6fbf4f7d0bdf92408f79262624647/audits/Solidified%20-%20OGV,%20wOUSD,%20and%20ERC721a%20-%20May%202022.pdf) in May 2022 and is ready for production use.

wOETH works exactly the same as wOUSD.

### Wrapping

If you don’t already have OUSD, you can buy it from Gate.io, KuCoin, Curve, Uniswap, or [get it directly from the OUSD DApp](https://www.youtube.com/watch?v=UabjvL-7iu4).

Once you have OUSD in your wallet, visit [ousd.com/wrap](https://ousd.com/wrap) and follow these steps:

1. Connect your wallet
2. Enter the amount of OUSD that you want to wrap
3. Submit the allowance for the wOUSD contract to use your OUSD
4. Submit the transaction to wrap your OUSD

OETH can similarly be wrapped by visiting [oeth.com/wrap](https://www.oeth.com/wrap).



![ousd.com/wrap](https://cdn-images-1.medium.com/max/1600/1\*57fSZSSlzebhpIl8R4UqUQ.png)

### Unwrapping

Unwrapping your OUSD or OETH does not require any approvals since you already hold the wrapped version in your wallet. There's also no minimum term or lock-up period. You can use the same form shown above and just click the arrow to flip it to unwrap mode. This form calls the `redeem` function to unwrap a specific amount of wrapped tokens. You can also [use Etherscan](https://etherscan.io/address/0xd2af830e8cbdfed6cc11bab697bb25496ed6fa62#writeProxyContract) to call the `withdraw` function if you prefer to specify the amount of OUSD or OETH that you want to be taken out.
