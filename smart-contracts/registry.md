# Registry

Here is the list of OUSD, OETH, and OGV smart contracts that have been deployed to the Ethereum mainnet.&#x20;

**ERC20 Tokens**

<table><thead><tr><th width="180">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OUSD</td><td><a href="https://etherscan.io/address/0x2A8e1E676Ec238d8A992307B495b45B3fEAa5e86"><img src="../.gitbook/assets/image (16).png" alt="" data-size="line"></a> 0x2A8e1E676Ec238d8A992307B495b45B3fEAa5e86<br>origindollar.eth | ousd.eth</td></tr><tr><td>OETH</td><td><a href="https://etherscan.io/address/0x856c4Efb76C1D1AE02e20CEB03A2A6a08b0b8dC3"><img src="../.gitbook/assets/image (2) (1).png" alt="" data-size="line"></a> 0x856c4Efb76C1D1AE02e20CEB03A2A6a08b0b8dC3<br>originether.eth</td></tr><tr><td>wOUSD</td><td><a href="https://etherscan.io/address/0xD2af830E8CBdFed6CC11Bab697bB25496ed6FA62"><img src="../.gitbook/assets/image (24).png" alt="" data-size="line"></a> 0xD2af830E8CBdFed6CC11Bab697bB25496ed6FA62<br>wousd.eth</td></tr><tr><td>wOETH</td><td><a href="https://etherscan.io/address/0xDcEe70654261AF21C44c093C300eD3Bb97b78192"><img src="../.gitbook/assets/image (8).png" alt="" data-size="line"></a> 0xDcEe70654261AF21C44c093C300eD3Bb97b78192<br>woeth.eth</td></tr><tr><td>OGV</td><td><a href="https://etherscan.io/address/0x9c354503C38481a7A7a51629142963F98eCC12D0"><img src="../.gitbook/assets/image (25) (1).png" alt="" data-size="line"></a> 0x9c354503C38481a7A7a51629142963F98eCC12D0<br>ogv.eth</td></tr><tr><td>veOGV</td><td><a href="https://etherscan.io/address/0x0C4576Ca1c365868E162554AF8e385dc3e7C66D9"><img src="../.gitbook/assets/image (10) (2).png" alt="" data-size="line"></a> 0x0C4576Ca1c365868E162554AF8e385dc3e7C66D9<br>veogv.eth</td></tr></tbody></table>

{% content-ref url="registry/ousd-registry.md" %}
[ousd-registry.md](registry/ousd-registry.md)
{% endcontent-ref %}

{% content-ref url="registry/oeth-registry.md" %}
[oeth-registry.md](registry/oeth-registry.md)
{% endcontent-ref %}

**Timelock & Multisigs**

<table><thead><tr><th width="198">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OUSD Timelock</td><td>0x35918cDE7233F2dD33fA41ae3Cb6aE0e42E0e69F</td></tr><tr><td>OETH Governor / Timelock</td><td>0x72426BA137DEC62657306b12B1E869d43FeC6eC7</td></tr><tr><td>Admin (5 of 8)</td><td>0xbe2AB3d3d8F6a32b96414ebbd865dBD276d3d899</td></tr><tr><td>Strategist (2 of 8)</td><td>0xF14BBdf064E3F67f51cd9BD646aE3716aD938FDC</td></tr></tbody></table>

**OGV Rewards**

<table><thead><tr><th width="194">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OGV Rewards Source</td><td>0x7d82e86cf1496f9485a8ea04012afeb3c7489397</td></tr></tbody></table>

**Chainlink Keepers**

Chainlink Keepers are an automated and decentralized way to perform regularly scheduled tasks.

| Keeper                                                                                                                               | Address                                    | Purpose                                         |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ | ----------------------------------------------- |
| [OUSD Keeper 5](https://automation.chain.link/mainnet/80310800131671020338601273445439145162738398695605141883575959303659215247238) | 0x9c979C2687B2E64293c45B2D122d688e2d7fD8ec | Executing a daily rebase for both OUSD and OETH |
