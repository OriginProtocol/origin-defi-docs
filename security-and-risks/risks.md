# Risks

{% hint style="danger" %}
Use at your own risk. Do not deploy more capital than you are willing to lose.
{% endhint %}

As with any yield-generating DeFi product, there are associated risks with holding OUSD or OETH that are important to understand. These risks can be broadly classified into 4 categories:

* OUSD smart contract risk
* Underlying third-party platform risk
* Underlying collateral risk
* Regulatory risk

**Smart contract risk**

Our smart contracts have been [audited](audits.md) by multiple, well-respected security firms. However, it is important to note that even with formal audits, it is still possible for there to be logic errors that could lead to the loss of funds. The contracts involve complex math and logic. While we have taken every precaution to ensure the safety and security of our smart contracts, users are reminded to use at their own risk. Origin Protocol will not be held responsible for any loss of funds, regardless of who is at fault.

**Third-party platform risk**

Both OUSD and OETH are built on top of other DeFi platforms like Aave, Compound, and Curve that add significant smart contract risk. We are choosing to work with platforms that have literally billions of dollars of assets under management and have made reasonable efforts to ensure the security of their protocols. However, there are no guarantees that the underlying third-party platforms will continue to work as intended, and any failure in an underlying strategy would potentially lead to a loss of funds for OUSD or OETH holders.

**Collateral risks**

It is important to understand that OUSD and OETH are only as strong as the backing collateral. Any loss of value to underlying stablecoin assets or LSTs will cause a similar loss to the value of OUSD or OETH. While OUSD is designed to maintain a 1:1 relationship between supply and number of backing stablecoins, it does not guarantee which stablecoins will make up that backing nor the value of those coins. The same goes for OETH.

It is important to note that each of the supported stablecoins introduces non-trivial counter-party risk. Tether, in particular, has had well-documented banking troubles and regulatory challenges. In addition, both USDT and USDC have backdoors that grant their issuers the power to freeze money in their holder's wallets. While DAI does not have any direct backdoors, its assets can also be negatively impacted since USDC and USDT are accepted as collateral for minting DAI.

There is also significant centralization and slashing risk associated with the various LSTs that act as collateral for OETH. If any of the node operators that are backing the LSTs that are backing OETH are slashed, you can expect that OETH holders will similarly lose money. In the case of a minor slashing like we've seen to date, the result will be that OETH holders will earn slightly less yield. In the event of a major slashing, you can expect that OETH will drop in value proportional to the percentage of the backing LST that was impacted.&#x20;

**Regulatory risk**

On Feb. 21, 2023, a judge in the High Court of England and Wales ordered Oasis, a gateway for the DeFi lender MakerDAO, to "take all necessary steps" to retrieve assets that were stolen as part of a $320M heist last year. Unfortunately as a result, no risk assessment would be complete without mentioning the risk of antagonistic regulators trying to meddle in the affairs of the protocol.

There are **no back doors** into OUSD or OETH. There is no function the Origin devs can call to freeze or steal your money. The protocol is fully decentralized and the contracts can not be upgraded without the coordination and permission of thousands of OGV stakers around the world.&#x20;

In the extreme case where core devs are compelled to submit or vote for proposals to upgrade the contracts against their wishes, the timelock acts as the final line of defense, giving those who are paying attention time to withdraw their money before the upgrades can go into effect.&#x20;

The #defi-bot in Origin's Discord publicly announces every proposal that is submitted to governance or is queued in the timelock. We encourage other community members to set up their own monitoring as well.

**Risk mitigation**

While it's impossible to guarantee our contracts are 100% safe, we have taken every step possible to mitigate the chance of losing funds:

We regularly have our work [audited ](audits.md)by the top auditors in the industry.

In situations where collateral falls below the peg, [OIP-4 disables minting](https://github.com/OriginProtocol/origin-dollar/issues/1000) of additional OUSD/OETH tokens using the de-pegged asset.

[DeFi insurance](insurance.md) is available to offer smart contract coverage as an optional add-on service for OUSD holders.

We have retained [Certora](https://www.certora.com/) to formally verify the various security properties of our contracts. They helped us establish automated verifications that will run anytime we update our contract code. We have automated checking for common errors with [Slither](https://github.com/crytic/slither) and [Echidna](https://github.com/crytic/echidna) tests. Together, these alert our team to common security issues in addition to our own test suite.

Code reviews involving our smart contracts are incredibly rigorous. We require at least two engineers to review each change with a detailed checklist and we prioritize security reviews over new feature development.

Finally, we have formalized an engineering [rotation](https://github.com/OriginProtocol/security/blob/master/incidents/ROTATION.md) for reviewing [attacks on other projects](https://github.com/OriginProtocol/security/tree/master/incidents) as well as ensuring we deep dive into each of these reviews, including reviewing the affected contracts' source code ourselves. We've observed that attackers often exploit the same fundamental vulnerability on multiple different projects. By reviewing other project's vulnerabilities, we force ourselves to stay up to date on the latest security threats in our industry and are constantly learning from their mistakes.

**Actions speak louder than words**

You should also know that many members of the Origin team, including both founders, are holding a significant portion of their personal wealth in OUSD (and soon, OETH!). Origin Protocol's corporate treasury is also holding millions of dollars in OUSD. We have skin in the game and are willing to put our own money at risk with the code we have written.
