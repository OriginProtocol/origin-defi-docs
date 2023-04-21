---
description: >-
  Henlo fren, so you’ve lost two Toyota Corollas on UST’s pyramid scheme, and
  now you’d like to determine if a stablecoin is safu before throwing in your
  paycheck? Well, you’ve come to the right place.
---

# Stablecoin Scorecard

The Stablecoin Scorecard is a quantitative framework for evaluating risk, but is certainly not exhaustive nor prescriptive. Risk cannot be removed completely from any system, but it can be managed.

When it comes to stablecoins, the best place to start is understanding the assets or collateral that help support its purported value, and then diving into the people and processes that support it. Risk is broken down into 4 separate scores with weighting that reflects their aggregate level of importance across each of these key areas.

Scores are calculated based on the guidelines below and templates have been provided for both [centralized](https://docs.google.com/spreadsheets/d/1eX85MBj1l9NLGWZwwlXtFg6fSz0PnRhdohVseblQ8RE/edit#gid=1053910649) and [decentralized](https://docs.google.com/spreadsheets/d/1YEyNqE7P2iGDm3zXcsdIXXVgllLKrlR74EivT2a74pc/edit#gid=1418231256) stablecoins.

{% embed url="https://docs.google.com/spreadsheets/d/1eX85MBj1l9NLGWZwwlXtFg6fSz0PnRhdohVseblQ8RE/edit?usp=sharing" %}
Scorecard Template for Centralized Stablecoin - Tether as an example
{% endembed %}

{% embed url="https://docs.google.com/spreadsheets/d/1YEyNqE7P2iGDm3zXcsdIXXVgllLKrlR74EivT2a74pc/edit?usp=sharing" %}
Scorecard Template for Decentralized Stablecoin - UST as an example
{% endembed %}

{% tabs %}
{% tab title="Financial Score (80%)" %}
Liabilities: The first thing you need to determine is just how much of a stablecoin exists - these are considered liabilities, so long as they are outside of the smart contracts controlled directly by the protocol (more on that later). To find this information, first check on the protocol’s own website (first-party) since their data should be more reliable. Look for analytics pages or a dune dashboard, but if you can’t find it, I also tend to check across two different sources, such as coingecko, messari, and coinmarketcap. As a last resort, I will join their discord or Telegram and ask one of their admins/core members. Another place to check is Etherscan’s token tracker, and then look at where they are held. This can help you identify if any of the liabilities are actually not true liabilities since they are held by the protocol’s own smart contracts (eg. alUSD or FRAX). The ones held by the protocol can be burned and therefore are not actual liabilities.

Collateral: Once you’ve determined the amount of liabilities, the next step is to find out how much collateral is backing them. This data should be readily available on the protocol’s website, typically under the analytics tab or in a Dune dashboard.

Net Liquidation Value: Once you have each of the collateral assets, they shouldn’t necessarily be taken at the current face value. The recovery value (aka liquidation value) depends on the ability to readily convert those somewhat more volatile assets back into less volatile assets, and can vary based on several factors, including the liquidity of the asset (how much is available to be exchanged) relative to the amount. To help with this process, I’ve provided some guidelines for common reserve assets (both real world and digital)

<figure><img src="../../.gitbook/assets/Screen Shot 2022-10-16 at 8.47.03 PM.png" alt=""><figcaption><p>Net liquidation values across different asset types</p></figcaption></figure>

As a rule of thumb, try to be conservative by selecting the lowest net liquidation value and see where you net out. This can give you an idea of how well collateralized it is and the likelihood of a death spiral. For an algo stable (yikes!) I try to estimate the ability for the current market demand to support a forced liquidation of the stablecoin. In simple terms, I calculate how many multiples of the average daily volume it would take to sell the reserve and the higher the multiple the riskier it becomes. If there is $200M in the reserve and the average daily trading volume is $100M, then it would equal two days. A more rigorous way to analyze this would be to look at the actual order book depth on exchanges and estimate price slippage, which is something done by companies such as Gauntlet.

Collateral Ratio: Once you’ve calculated the NLV, you can determine whether the stablecoin’s balance sheet is sufficient to meet its outstanding liabilities. Ideally, the collateral ratio will be greater than or equal to 100%. If it is below 85%, we assume it is not worth exploring further.

| Collateral Ratio |              |
| ---------------- | ------------ |
| 100+             | Excellent    |
| 90-100           | Good         |
| 85-90            | Ok           |
| 0-85             | Insufficient |

Days Live: Finding out how long the protocol has been in existence is not always straightforward. This can sometimes be found by going into their gitbook documents, but often I have to rely on Twitter posts and medium blog posts announcing their launch. Other sources include coingecko, messari, and coinmarketcap, but sometimes those aren’t indicative of the “public” launch date which can be either before (if they didn’t start tracking it right away) or after (if there was a beta or closed launch period) the start of the chart. Note also if there have been any major updates, since these would restart the timer for the Lindy Effect. This score increases by a squared factor of (\[# of days]/10)^2, up until 100 at 100 days. Ex. 50 days would be equal to 25, 90 days would be equal to 81.

Volatility: Volatility is somewhat unreliable at times since often they do not show the real volatility on Curve markets. I will check Messari as a starting point and cross reference on Coinmarketcap and Coingecko. In general, we care less about volatility so long as the asset has sound fundamentals and will return to peg long term. We apply a function where any volatility beyond 0.05 decreases the score by a squared factor of 100-100\*(\[volatility]-0.05)^2.

Redemption Mechanism: These should be explicitly spelled out in the documentation, if it isn’t, run. Check for where the redemption occurs, what fees are involved, and whether it is permissioned or not. Permissioned could be either KYC or only borrowers (to unlock collateral). In the latter case, this can make it difficult to estimate the price floor as borrowers are incentivized to allow the peg break down. A PSM or AMO can help alleviate this, as well as some other mechanisms such as forced repayment (eg. LUSD). This also provides a price floor and should be taken into consideration when entering a new position for "worst case" recovery value.

Liquidity & Balance: Liquidity should be easily identified by looking at Curve, which is the de-facto on-chain liquidity source for stablecoins. It is located on the pool’s individual page. Rule of Thumb: must be 10X the amount invested in the strategy to avoid high slippage on exit.

<figure><img src="../../.gitbook/assets/Screen Shot 2022-10-16 at 8.57.54 PM.png" alt=""><figcaption><p>Liquidity Depth and Balance for OUSD-3Crv Pool</p></figcaption></figure>

Liquidity Sustainability: This can sometimes be difficult to ascertain - one of the first places to check is [https://daocvx.com/leaderboard/](https://daocvx.com/leaderboard/) If you don't see CVX holdings there, but they still have a good gauge on Curve, check bribing history on Llama Airforce [https://llama.airforce/#/bribes/rounds/votium/cvx-crv/](https://llama.airforce/#/bribes/rounds/votium/cvx-crv/). If you don't see any bribes still, there's a good chance that they control that much CVX but it isn't tracked. This isn’t necessarily a deal breaker, but worth keeping track of since unsustainable liquidity can lead to a de-pegging event (of course there should be a natural floor as highlighted in redemption mechanism).
{% endtab %}

{% tab title="Governance Score (5%)" %}
Ownership: If they have a native token, typically it is a DAO. Otherwise, you can search for more information - and sometimes they might list their company name and location on their website - otherwise a Google search is pretty much the best option. I will cross reference multiple sources including Crunchbase, LinkedIn, and CBInsights, and often finding the founders on LinkedIn gives you an idea of where they actually operate and the name of the entities.

Investors: These are usually either in a fundraising announcement or listed directly on the website. Some of them may have raised through public sales (eg. JPEG’d), CoinList, or through other private placements. I always check their investor’s website to see if they actually invested in them (there have been scams claiming to have big name backers).

Identities: Most have a “Team” page of some kind, but if they are a full DAO, then I first look at who is posting their updates on Medium and join their Discord server (if one exists). If they have a forum or snapshot, see if they have any profiles there, and in Discord, look for the level of activity of key members or moderators. Github is another great place to check for the people actively contributing to the project. If they are too difficult to find and link to a real world identity, then I assume they are anon vs going full ZachXBT on them. If they have VC or other institutional backers, they are likely not completely anon since most VCs will not invest in a fully anon-team due the need to abide by KYC requirements and international sanctions.

Accounting Firm: This usually only applies to centralized stablecoins or protocols with centralization of some kind (eg. Goldfinch). The name and more importantly the location of the Audit firm matters. I also Google the firm to see that it exists and that its office isn’t an elementary school parking lot (as was the case with Luckin Coffee). If there are any names listed on the audit reports, I also look them up on LinkedIn to make sure they are real (or at least put in the effort to create a fake identity).
{% endtab %}

{% tab title="Security Score (10%)" %}
**Code Quality & Github Activity: Well documented, organized, concise code is a strong indicator of the strength of the team writing it and the overall quality. It is highly recommended to poke around in their Github repository and see if things pass the smell test. This is something that should be covered during the audit phase of the project, but you would be surprised to find out what actually gets shipped is not always identical. It is also a good sign if the project is still active and has contributions occurring regularly, but this factor is not completely necessary if the code is more or less immutable (eg., LUSD).**

Audits & Bug Bounties: This should be listed somewhere in the docs, if not, they likely do not have one because this is a good marketing tool.

Access Controls & Upgradeability: These should also be clearly spelled out in the documentation, but in practice I’ve had trouble finding this information and sometimes have to go into the Discord to ask. If they don’t have things clearly documented, this is a big red flag. In the case of BEAN stalk, they had an important piece that went overlooked about supermajority emergency powers which lead to a massive governance attack. So beware and bring in https://twitter.com/danielvf when in doubt. The best practices for security are things like multi-day timelock delays for any changes on chain, clearly delineated multi-sigs with >5 signers. The last thing you want is for critical components such as minting to be controlled by just 2 signers and the ability to act with impunity. Even if you trust the team holding the keys, key security is a real concern so the more layers the better.

Security Incidents: To find out I typically check the name of the protocol along with “hack,” “rekt,” or “exploit.” When a project gets hacked or exploited, it can be a sign of poor security controls and engineering processes, but not always. Sometimes things just go wrong - there is often no way to know with 100% certainty whether a set of contracts are safe and unable to be exploited. But how a project responds to a security incident matters more than whether or not one has occured. The speed with which the team communicates and the actions they take to remediate the incident can tell you a lot about the future likelihood of a hack occuring. While many people will write off a project following an incident, sometimes a hack can be a good thing, but it really comes down to what is learned and done to prevent it going forward. Read their post-mortem, look at how they communicated during the incident, and find out who lost money and what was done to help them.
{% endtab %}

{% tab title="Legal Score (5%)" %}
Regulatory Risk: This can be somewhat subjective, but I start with looking at how much of their backing relies on regulation-susceptible assets such as USDT and USDC. Beyond that, search the name of the stablecoin along with “fines” or “licenses” - a few of them that are more regulatory forward will have it listed on their website or in the docs as well. This is not exhaustive, but more to give an idea of how likely something is to be shut down and regulated out of existence. For a fully decentralized stablecoin, the more permissionless and autonomous the DAO and/or the code itself, the better.
{% endtab %}
{% endtabs %}

### Summary

While this level of research and detail can help with identifying the risks of a given stablecoin or strategy, it is the ultimate responsibility of the OGV holder community to determine the right risk level for OUSD. The best way to manage risk is to move slowly and abide by the old adage “don’t put all of your eggs in one basket.” With the help of all of you, we can stay vigilant, constantly reviewing projects and new exploits to avoid getting rekt.
