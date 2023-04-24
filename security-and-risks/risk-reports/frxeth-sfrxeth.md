# frxETH/sfrxETH

Frax entered the liquid-staked derivatives market in late 2022 with the launch of frxETH and sfrxETH. frxETH is an ETH-pegged stablecoin that can be used across DeFi whereas sfrxETH is an interest-bearing token that increases in value over time due to the ETH reward it accumulates. \


**TL;DR:**

* The smart contracts follow industry standards and aren’t upgradable. They don’t use any proxies but the multi-sig is controlled by ⅗ keys and the wallet in control has no timelock.&#x20;
* A few concerns that have been rectified were highlighted in the latest audit such as flawed accounting logic and the perceived risk of frontrunning.&#x20;
* frxETH is relatively new to the market and has remained very stable except for the instability that took place as it was newly deployed to the market. It’s still very popular despite this.&#x20;
* frxETH has extremely deep liquidity and fits within our threshold of a $100M secondary market liquidity in case a rebalancing of the LSD basket needs to take place.&#x20;
* The protocol has a strong and public team that represents the product very well.
* Frax’s documentation is clear and professional and directly leads you to find the necessary information you need to find, especially concerning contracts.
* Room for improvement regarding multi-sig key controllers in the documentation. However, very easy to find in smart contracts.&#x20;



## Smart Contracts

Understanding smart contracts was the first step in evaluating frxETH and sfrxETH. It is important to highlight that this solely covers the frxETH and sfrxETH contracts and not the other ones concerning the Frax ecosystem. The smart contracts were easy to find and were generally good although there were a few concerns to mention based on our judgment. The positive was that they are open source and verified on Etherscan and uses a standard token implementation.&#x20;

The contracts are also not upgradeable which means that they cannot deploy additional malicious code in order to steal the funds in the treasury. However, this also comes with a caveat as some vulnerabilities might not be able to be fixed due to the non-upgradeable nature of the contracts. The smart contracts of both frxETH and sfrxETH do not use any proxies either. The multi-sig wallet is controlled by ⅗ keys. However, the wallet is in control of frxETH and has no timelock, and can whitelist any address to mint tokens.&#x20;

### Contracts and other addresses:

\


| Contract Name                        | Address                                                                                                                                 | Comments                                                                     |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| frxETH                               | [0x5e8422345238f34275888049021821e8e08caa1f](https://etherscan.io/address/0x5e8422345238f34275888049021821e8e08caa1f)                   | <p><br></p>                                                                  |
| Staked frxETH                        | [0xac3e018457b222d93114458476f3e3416abbe38f](https://etherscan.io/address/0xac3e018457b222d93114458476f3e3416abbe38f)                   | <p><br></p>                                                                  |
| Multi-sig wallet                     | [0x8306300ffd616049FD7e4b0354a64Da835c1A81C](http://etherscan.io/address/0x8306300ffd616049FD7e4b0354a64Da835c1A81C)                    | <p>3/5 and owns frxETH</p><p><br></p>                                        |
| Timelock                             | [0x8412ebf45bAC1B340BbE8F318b928C466c4E39CA](https://etherscan.io/address/0x8412ebf45bAC1B340BbE8F318b928C466c4E39CA)                   | <p><br></p>                                                                  |
| Comptroller (Also, multi-sig wallet) | [0xB1748C79709f4Ba2Dd82834B8c82D4a505003f27](https://etherscan.io/address/0xB1748C79709f4Ba2Dd82834B8c82D4a505003f27#readProxyContract) | Controls timelock, shares two of the signers with the other multi-sig wallet |

You can find the full smart contract review [here](https://docs.google.com/document/d/1voXJs2PlLiSUGhOB4sF8i62l1d1AvN7gmJ8diQyXZy4/edit?usp=sharing).

## Audit findings

In our assessment of frxETH being included in the underlying basket of OETH, we have factored in if the protocol has undergone an audit and if it was performed by a reputable firm. The audit of frxETH and sfrxETH have been conducted by a tier A audit firm in the form of Trail of Bits and also through multiple white hat hackers in order to get as many eyes as possible on the code.&#x20;

These audits took place in September and November 2022 respectively and there were some key issues that were identified where 2 of them were deemed as critical at the time (in total: 2 high-risk findings, 10 medium-risk findings, and 12 low-risk or non-critical issues).&#x20;



One concern that was identified in the latest audit was that there was that the accounting logic was flawed which meant that the token balance was updated of storedTotalAssets was updated prior to users calling the beforeWithdraw function which causes a discrepancy in the value lastRewardAmount leaves the contract vulnerable for users stealing the rewards of other users. The Frax team acknowledged this and mitigated it by moving the function to a modifier that gets called before the withdrawal takes place.&#x20;



The second one with high severity was that there was a perceived risk of frontrunning by a malicious validator. However, the validator that operates using the underlying staked ETH on Frax is controlled by the protocol and thus not deemed as high risk as suggested. Frontrunning would only take place if the keys were compromised and fell into the hands of a malicious actor.&#x20;



Other issues were of lesser severity including delayed rewards and loss of peg. This has been acknowledged by the team and the issues that could be fixed prior to Shanghai have already been dealt with. However, there will be some new necessary implementations in the contract after ETH withdrawals have been made accessible by Shanghai that most likely will require an additional audit for security reasons.&#x20;

## frxETH Peg Stability

In order for an LSD to be a viable option for usage, there needs to be a clear indication that it has the capability to maintain its peg to ETH (or remain very close to it). An LSD that is too volatile in relation to ETH poses too much of a risk for the LSD aggregator and can severely imbalance the stability of the aggregator. Thus, it is paramount that we take a look into how each LSD has maintained its peg in relation to ETH over time.\


frxETH is the most nascent of the LSDs that we are looking into and Dune only tracks its data from February. Still, attached below is a line chart that demonstrates the peg stability over time.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-04-24 at 20.02.47.png" alt=""><figcaption></figcaption></figure>

Apart from the instability that normally occurs as a new 1:1 derivative is being deployed and available on the market, frxETH has remained relatively stable and provided a sound 1:1 ratio with ETH. This has made it easy for users to take advantage of a reliable peg that has been integrated with numerous DeFi protocols to incentivize users to acquire frxETH to get access to attractive yields.&#x20;

## Liquidity & Composability

In our assessment of the LSDs, it is paramount that we factor in the available liquidity of the tokens and how composable it is across DeFi. Using $100M available liquidity on the market acts as a reasonable benchmark not factoring in the TVL that is locked in the contracts on the platform that mints the LSD. Frax has created deep liquidity for frxETH in order to facilitate the process for users that want to swap between frxETH / ETH without any major issues. There is over ≈ $350M worth of frxETH liquidity available across DeFi to facilitate swaps between frxETH and other tokens in the ecosystem.&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2023-04-24 at 20.06.02.png" alt=""><figcaption></figcaption></figure>

FrxETH is also an LSD that has benefitted strongly from the Shanghai upgrade and their rate of deposits is currently growing faster than other competitors (although you have to factor in that they had a smaller piece of the pie, to begin with, making growth in relation to prior deposits higher). Despite not being as battle tested as other liquid-staked derivatives, frxETH, and sfrxETH can be deployed in pools throughout the DeFi ecosystem and is highly composable. This includes pools in reputable platforms such as Curve, Convex, Aura, and Balancer to name a few.&#x20;

## Team

Having a public team builds trust and accountability for the people involved. We have factored in things here as everybody working on the project necessarily doesn’t have to be public.

* At least two people can be seen publicly working on the project.&#x20;
* The figureheads of the protocol are public.
* No prior history of nefarious activities

In all cases, Frax fits the bill as both their co-founders are public figures and represent the organization well and the team members can be found easily. Also, they have so far proven to be very reliable and have no history of any nefarious behavior.

## Documentation

Documentation plays a significant role in outsiders being able to find clear information about the protocol and being able to judge it from an outside view. In Frax’s case, the documentation is very strong and provides insightful information about the protocol, and directs you seamlessly to additional information whenever that’s needed. The documentation comes across as professional and thoughtful and is helpful for both developers and researchers. The documentation also covers the deployed contracts of the protocol and links you to the respective address that can be found on Etherscan.&#x20;

## Admin Controls

While the protocol is open about the multi-sig control in their smart contracts there is a lack of information about it in the documentation. In the documentation, it is very easy to find the respective multi-sigs of the contracts deployed by the protocol and draw conclusions from investigating these contracts at hand. However, this will not be intuitive for the average user and can be improved upon in the docs by the Frax team.

\
\
\
