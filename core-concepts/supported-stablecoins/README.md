# Supported Stablecoins

**Supported Stablecoins**

It is important to understand that OUSD is only as strong as the stablecoins that are backing it. Any loss to the underlying assets will cause a similar loss to the value of OUSD. Because of this, the protocol goes to great lengths to evaluate each stablecoin before adding as a backing asset, including running each through an in-depth [Stablecoin Evaluation Framework](stablecoin-evaluation-framework.md).

Currently, OUSD supports the following stablecoins:

{% content-ref url="usdt.md" %}
[usdt.md](usdt.md)
{% endcontent-ref %}

{% content-ref url="usdc.md" %}
[usdc.md](usdc.md)
{% endcontent-ref %}

{% content-ref url="dai.md" %}
[dai.md](dai.md)
{% endcontent-ref %}

None of these stablecoins are perfect, but we selected them because of their widespread usage. While these stablecoins have lost their USD peg on multiple occasions, they have demonstrated resiliency in eventually getting back to their 1 USD targets.

It is important to note that all these stablecoins introduce non-trivial counter-party risk. Tether, in particular, has had well-documented banking troubles and regulatory challenges. In addition, both USDT and USDC have backdoors that grant their issuers the power to freeze money in their holder's wallets. While DAI does not have any direct backdoors, its assets can also be negatively impacted since USDC and USDT are accepted as collateral for minting DAI.

Despite these concerns, there are already billions of dollars betting on the security of these stablecoins. It is possible that additional stablecoins will be added to the protocol over time. Support may also be removed if any of these stablecoins prove to be too unreliable or put OUSD holders' funds in jeopardy.

**Turning FUD into Profit**

March 2023 was the first time we saw a major depegging since the launch of OUSD. After the collapse of Silicon Valley Bank, both USDC and DAI (which is largely backed by USDC) dropped to $0.96. Thankfully, OUSD was designed with the assumption that the backing collateral could drop in value at any time. OUSD has multiple protections in place to protect the protocol in case of a depegging. We were proud to see that these protections protected the vault, maintained a superior peg than either USDC or DAI, and generated record-breaking profits for the protocol during this stressful event.

{% embed url="https://twitter.com/joshfraser/status/1634654570298130432?s=20" %}

