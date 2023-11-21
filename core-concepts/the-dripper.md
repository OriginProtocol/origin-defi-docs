# The Dripper

When reward tokens are harvested, the resulting yield is received by the Dripper contract and slowly distributed to OToken holders. This smooths out the otherwise choppy yield and prevents attackers from being able to front-run large liquidity events for the protocol. Other yield sources, such as lending interest and redemption fees, do not go through the Dripper.

Below you can see how daily APYs changed after the Dripper was implemented:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

|      | Dripper configuration |
| ---- | --------------------- |
| OUSD | 604800 (7 days)       |
| OETH | 259200 (3 days)       |
