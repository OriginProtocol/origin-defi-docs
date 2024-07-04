# OETH Registry

Most of Origin's contracts are upgradable via a well-known proxy wrapper and an implementation contract. The Vault is split into VaultAdmin and VaultCore to work around the maximum contract size limit on Ethereum.

<figure><img src="../../.gitbook/assets/oethContracts (5).png" alt=""><figcaption><p>OETH Contract Dependencies</p></figcaption></figure>

### **Core (Mainnet)**

<table><thead><tr><th width="305">Contract</th><th width="633">Address</th></tr></thead><tbody><tr><td>OETH Token</td><td>0x856c4Efb76C1D1AE02e20CEB03A2A6a08b0b8dC3</td></tr><tr><td>OETH Implementation</td><td>0x7c1F8b1824f2758060CfC9Dd964C590710367A1E</td></tr><tr><td>wOETH Token</td><td>0xDcEe70654261AF21C44c093C300eD3Bb97b78192</td></tr><tr><td>wOETH Implementation</td><td>0x9C5a92AaA2A4373D6bd20F7b45cdEb7A13f9AA79</td></tr><tr><td>OETH Vault</td><td> 0x39254033945AA2E4809Cc2977E7087BEE48bd7Ab</td></tr><tr><td>OETH VaultAdmin Implementation</td><td>0x0Bb9C9496e2294A89efF3c8A25ba9730BdED4B8C</td></tr><tr><td>OETH VaultCore Implementation</td><td>0x8f371d8e65F35914CDb8Dd58B997411871dABb37</td></tr><tr><td>OETH Zapper</td><td>0x9858e47BCbBe6fBAC040519B02d7cd4B2C470C66</td></tr></tbody></table>

### Bridged (Arbitrum)

<table><thead><tr><th width="307">Contract</th><th>Address</th></tr></thead><tbody><tr><td>wOETH Token</td><td>0xd8724322f44e5c58d7a815f542036fb17dbbf839</td></tr><tr><td>wOETH / OETH Exchange Rate</td><td>0x03a1f4b19aaeA6e68f0f104dc4346dA3E942cC45</td></tr></tbody></table>

### **Strategies**

<table><thead><tr><th width="305">Contract</th><th>Address</th></tr></thead><tbody><tr><td>Native Staking SSV Strategy</td><td>0x34edb2ee25751ee67f68a45813b22811687c0238</td></tr><tr><td>OETH Convex ETH+OETH (AMO)</td><td>0x1827F9eA98E0bf96550b2FC20F7233277FcD7E63</td></tr><tr><td>OETH Morpho Aave V2</td><td>0xc1fc9E5eC3058921eA5025D703CBE31764756319</td></tr><tr><td>Lido Withdrawal Strategy</td><td>0xD9B488280d723338Dd32d56b3900f379Eb7A7aF1</td></tr></tbody></table>

### **Yield Harvesting & Rewards Distribution**

<table><thead><tr><th width="204">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OETH Harvester</td><td>0x0D017aFA83EAce9F10A8EC5B6E13941664A6785C</td></tr><tr><td>OETH Dripper</td><td>0xc0F42F73b8f01849a2DD99753524d4ba14317EB3</td></tr><tr><td>OETH Buyback</td><td>0xfd6c58850cacf9ccf6e8aee479bfb4df14a362d2</td></tr><tr><td>Native Staking Fee Accumulator</td><td>0x7eD4ccb74A1eE903Af5fBd9be00CA8616F23D627</td></tr></tbody></table>

### **Assets**

<table><thead><tr><th width="205">Token</th><th>Address</th></tr></thead><tbody><tr><td>WETH</td><td>0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2</td></tr><tr><td>Lido stETH</td><td>0xae7ab96520de3a18e5e111b5eaab095312d7fe84</td></tr><tr><td>Rocketpool rETH</td><td>0xae78736cd615f374d3085123a210448e74fc6393</td></tr></tbody></table>

### **Oracles**

<figure><img src="../../.gitbook/assets/oethOracles (2).png" alt=""><figcaption><p>OETH Oracle contracts</p></figcaption></figure>

<table><thead><tr><th width="204">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OETH Oracle Router</td><td>0x468a68da3cefcdd644ce0ea9b9564b246218aeec</td></tr></tbody></table>

The following Chainlink oracles are used to protect the vault in case a backing asset loses value. They also offer slippage protection when harvesting rewards tokens.

<table><thead><tr><th width="204">Pair</th><th>Contract</th></tr></thead><tbody><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-eth/steth-eth">stETH/ETH</a></td><td>0x86392dc19c0b719886221c78ab11eb8cf5c52812</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-eth/reth-eth">rETH/ETH</a></td><td>0x536218f9e9eb48863970252233c8f271f554c2d0</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-eth/crv-eth">CRV/ETH</a></td><td>0x8a12be339b0cd1829b91adc01977caa5e9ac121e</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-eth/cvx-eth">CVX/ETH</a></td><td>0xC9CbF687f43176B302F03f5e58470b77D07c61c6</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-eth/bal-eth">BAL/ETH</a></td><td>0xC1438AA3823A6Ba0C159CfA8D98dF5A994bA120b</td></tr></tbody></table>

The AURA/ETH price comes from Origin's `AuraWETHPriceFeed` contract that uses the Balancer 80 AURA, 20 WETH pool to get a time weighted average price (TWAP). The TWAP used is the latest AURA/WETH price with a five minute interval. This is cross checked with the one hour interval price from five minutes ago. If the two TWAPs are more than 2% out the price is rejected.

<table><thead><tr><th width="220">Contract</th><th>Address</th></tr></thead><tbody><tr><td>AuraWETHPriceFeed</td><td>0x94e16bC08d7CCd7f2999Eb5eA3f35DD1EDCBd15B</td></tr><tr><td><p>Balancer</p><p>80 Aura 20 WETH Pool</p></td><td>0xc29562b045D80fD77c69Bec09541F5c16fe20d9d</td></tr></tbody></table>



### Automated Redemption Manager (ARM)

Read the latest ARM announcement [here](https://www.originprotocol.com/arm-announcement).

<table><thead><tr><th width="220">Contract</th><th>Address</th></tr></thead><tbody><tr><td><a href="https://app.1inch.io/#/1/advanced/swap/stETH/ETH">stETH/ETH</a></td><td>0x85B78AcA6Deae198fBF201c82DAF6Ca21942acc6</td></tr></tbody></table>



### **Deprecated**

<table><thead><tr><th width="305">Contract</th><th>Address</th></tr></thead><tbody><tr><td>Original governor / timelock</td><td>0x72426BA137DEC62657306b12B1E869d43FeC6eC7</td></tr><tr><td>OETH Frax Staking Strategy</td><td>0x3fF8654D633D4Ea0faE24c52Aec73B4A20D0d0e5</td></tr><tr><td>OETH Frax Redemption Strategy</td><td>0x95A8e45afCfBfEDd4A1d41836ED1897f3Ef40A9e</td></tr><tr><td>OETH Aura rETH/WETH Strategy</td><td>0x49109629aC1deB03F2e9b2fe2aC4a623E0e7dfDC</td></tr></tbody></table>
