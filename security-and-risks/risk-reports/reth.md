# rETH

Rocketpool was launched with the aim of decentralizing Ethereum staking to ensure it was not solely controlled by one party. By lowering the barriers to entry for ETH staking from 32 ETH to 16 ETH as well as facilitating the process by not requiring the average user to run a node. It has allowed anyone to stake ETH in a trustless manner while still maintaining autonomy of the underlying staked collateral through their liquid staked derivative rETH (Rocketpool ETH).\


**TL;DR:**&#x20;

* Smart contracts are well designed and there is no one that can mint rETH without supplying backing collateral of underlying ETH
* Concerns regarding reentrancy risk and rollback between new and old code that could sandwich transactions were caught and rectified in the latest audit report.&#x20;
* rETH doesn’t work like the other LSDs and represents the underlying farmed rewards, which means that it trades at a premium to ETH. It has managed to do that except during the early stages of its launch.&#x20;
* rETH has extremely deep liquidity and fits within our threshold of a $100M secondary market liquidity in case a rebalancing of the LSD basket needs to take place.&#x20;
* The protocol has a strong team that represents the product well although the majority of them are not public.&#x20;
* RocketPool's documentation is clear and professional and directly leads you to find the necessary information you need to find, especially concerning contracts and the thought process behind them.
* .The contracts follow industry standard by having no clear owner of the contracts that can take over or destroy the contracts. \


Rocketpool launched their liquid-staked derivative of Ethereum in November 2021 as they aspired to diversify the risk of Ethereum to protect it from being staked by one entity. Their liquid-staked derivative is called rETH and is a token that goes up in value based on the underlying staking rewards that the token is accruing. Thus, it works differently from the other solutions that always aim to maintain a peg with ETH.

## Smart Contracts

Understanding the smart contracts was the first step in evaluating frxETH and sfrxETH. The assessment of the contracts only covers the rETH contracts and not other contracts regarding Rocketpool. There is no method that allows anyone to mint rETH without supplying any ETH backing which is very positive. The contracts don’t use any proxies and aren’t upgradeable within the same address. However, fixes can still be deployed through the RocketStorage contract and the ecosystem is reliant on this contract. Multiple contracts have write access to it which is where the potential danger lies in case one of them would become compromised. Also, still unclear whether there is a timelock for a change of guardian that is bound to be explored further. Otherwise, they are following good practice as the contracts are open-source and verified on Etherscan while they have undergone multiple audits from reputable firms.&#x20;

\


| Contract Name     | Address                                                                                                               | Comments    |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- | ----------- |
| rETH              | [0xae78736Cd615f374D3085123A210448E74Fc6393](https://etherscan.io/token/0xae78736cd615f374d3085123a210448e74fc6393)   | <p><br></p> |
| RocketStorage     | [0x1d8f8f00cfa6758d7be78336684788fb0ee0fa46](https://etherscan.io/address/0x1d8f8f00cfa6758d7be78336684788fb0ee0fa46) | <p><br></p> |
| Guardian          | ??                                                                                                                    | <p><br></p> |
| RocketVault       | [0x3bdc69c4e5e13e52a65f5583c23efb9636b469d6](https://etherscan.io/address/0x3bdc69c4e5e13e52a65f5583c23efb9636b469d6) | <p><br></p> |
| RocketDepositPool | [0x4d05e3d48a938db4b7a9a59a802d5b45011bde58](https://etherscan.io/address/0x4d05e3d48a938db4b7a9a59a802d5b45011bde58) | <p><br></p> |

\
Audit findings
--------------

In our assessment of rETH being included in the underlying basket of OETH, we have factored in if the protocol has undergone an audit and if it was performed by a reputable firm. The protocol has undergone multiple audits with reputable audit firms and the latest Rocketpool audit was performed by Consensys in February 2023 which is a tier-A audit firm. In the findings, there was 1 critical issue identified, 4 major issues identified, 7 medium issues identified, and 7 minor issues identified.\


One of the critical issues identified was concerning the RocketNodeDistributorDelegate function that was subject to reentrancy which left the risk of a node draining the wallet that interacts with it. To mitigate this t was suggested that the team adds a reentrancy guard in cases where functions interact with an untrusted contract. This was the largest security threat and has been acknowledged and fixed by the team. \


Still, there were some other concerns to factor in such as in RocketMinipoolDelegateOld where the finalise() function was at risk. This was because a node operator could call finalise() to finalize a minipool, meanwhile, as this process goes on they could also call the \_refund() function if there is a node refund balance available to be transferred. When funds get distributed from nodeRefundBalance to nodeWithdrawalAddress the withdrawal address receives control of the flow and can call back into finalise() which leaves it open for reentrancy. The state finalised = true, was only set at the end of the function, making multiple system settings vulnerable to manipulation. This had also been mentioned in a prior audit during the Immunify bug bounty and has been sorted out. \


Also, there was a risk of rollback between prior versions and new upgrades through RocketMinipoolDelegate as it exposed delegateUpgrade and delegateRollBack functions which allow the minipool owner to switch between delegate implementations. The minipool owner can then rollback malfunctioning upgrades. Although it is more troublesome that the owner could alternate between executing old code and new code. This leaves room for sandwiching user calls to the minipool → any user can call RocketMinipoolDelegate.slash which slashes the delegator node if a slashing has been recorded on their validator. The minipool owner can avoid this flag from being set on a validator by sandwiching user calls. This was partially fixed by the team but could not be fully changed as it has been deployed in a non-upgradeable way to over 12,000 contracts. The team doesn’t view it as a security issue or a function that can cause any threat but more as a guide to follow.\


Apart from that the remaining part of the highlighted threats have been acknowledged although the majority of them don’t pose any direct threat to rETH. Some of these include access to ETH during the challenge process concerning slashing if you’re not a DAO member and checks violations concerning upgraded contract states after an external call.&#x20;

## Price Stability

rETH does not function in the same manner as the other liquid-staked derivatives as it is a claim in the ETH principal and all the accrued staking rewards over time. This means that it naturally will increase in price over time as rewards accrue. While the others aim to have as close to a 1:1 price with ETH at all times. When rETH launched, it was trading at a discount due to the uncertainty regarding the functionality of withdrawals at the time. However, as time passed and the underlying ETH has accrued rewards, rETH has been trading at a premium. Based on the underlying ETH that represents 1 rETH, arbitragers can take advantage of market inefficiencies when it either trades at a wide premium or discounts to rebalance the price. The line chart below displays the change in rETH price over time and factors in fair value vs market price:&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2023-04-25 at 14.52.56.png" alt=""><figcaption></figcaption></figure>

Despite some large discrepancies in fair value vs market value at times, over time it is natural for rETH to trend towards its fair value as arbitrageurs stake their ETH and receive rETH in return to then sell it to the market for a premium.&#x20;

## Liquidity & Composability

Factoring in liquidity in our assessment is paramount as there is a necessity for users to be able to exit without any complications. We need to be aware if we would be able to exit our position with sufficient liquidity in the market and rebalance the underlying LSDs without any issues. Therefore we believe that there should be at least $100M liquidity available for it to be considered an option. Considering exits are made possible after Shanghai and rETH are backed 1:1 with the underlying deposited ETH along with accrued rewards, there is more than sufficient liquidity to cover every person’s deposits in case of emergency. $988M worth of Ethereum has been deposited into Rocketpool and there are further ≈$500M distributed across liquidity pools in DeFi allowing rETH holders to swap out of their position to ETH and other tokens.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-04-25 at 14.57.34.png" alt=""><figcaption></figcaption></figure>

The liquidity has continued to get deeper over time and has seen a stark increase since the Shanghai upgrade which is a positive sign of rETH gaining strength in the market. rETH is very composable and can be deployed across over 50 pools across the DeFi ecosystem depending on preference. This includes highly liquid pools in reputable platforms such as Curve, Balancer, Aura, Convex, and Yearn to name a few.&#x20;

## Team

Having a public team builds trust and accountability for the people involved. We have factored in things here as everybody working on the project necessarily doesn’t have to be public.

* At least two people can be seen publicly working on the project.&#x20;
* The figureheads of the protocol are active.
* There is no history of nefarious activities

In all cases, Rocketpool fits the bill as both their co-founders are public figures and represent the organization well. It is also easy to find which people are on the team and there have been no incidents of nefarious behavior since the inception of the protocol.&#x20;

## Documentation

The documentation of the protocol is important to build confidence for outsiders that want to get an understanding of how the protocol works and assess it correctly. Rocketpool has very thorough documentation that clearly outlines how to become a node or contribute to the network.&#x20;

There is also clear documentation regarding the smart contracts that have been deployed and the idea behind them which makes it easy for developers to follow the thought process behind every smart contract. It also links every contract that has been deployed to their corresponding page on Etherscan along with the external integrations of other protocols as well. Making it very easy to find the contract address of external rETH pools within DeFi as well. However, what the documentation is lacking is the contract address to the multi-sigs that are being used by the protocol.

## Admin Controls

Finding information about the admin controls of the protocol isn’t a straightforward process for the average user as there is no information about it in the documentation. However, most contract does not have an owner that can take over control or destroy the contracts which is a positive indication of how decentralized the protocol aspires to be.&#x20;

\
\
