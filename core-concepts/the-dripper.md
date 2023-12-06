# The Dripper

When reward tokens are harvested, the resulting yield is received by the Dripper contract and slowly distributed to OToken holders. This smooths out the otherwise choppy yield and prevents attackers from being able to front-run large liquidity events for the protocol. Other yield sources, such as lending interest and redemption fees, do not go through the Dripper.

Below you can see how daily APYs changed after the Dripper was implemented:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

| Token | Dripper configuration |
| ----- | --------------------- |
| OUSD  | 604800 (7 days)       |
| OETH  | 1209600 (14 days)     |

### How it works

Here's a demonstration of the flow of funds for OETH:

* Reward tokens (e.g. CRV) are earned by a strategy
* [Someone calls the harvest function](https://docs.oeth.com/guides/incentivized-harvesting-guide) to swap reward tokens for ETH
* ETH proceeds from the harvest are added to the Dripper's balance
* The Dripper gradually allows ETH to be available for distribution to the Vault
* The Vault collects available ETH from the Dripper once per day via Chainlink automation
* The drip rate is updated each time funds are _collected_ (not when they are harvested/added)
* OETH wallets grow due to the increase in the Vault's ETH balance
