# OUSD Registry

Most of Origin's contracts are upgradable via a well-known proxy wrapper and an implementation contract. The Vault is split into VaultAdmin and VaultCore to work around the maximum contract size limit on Ethereum

**OUSD Core**

<table><thead><tr><th width="190">Contract</th><th width="633">Address</th></tr></thead><tbody><tr><td>OUSD Implementation</td><td><a href="https://etherscan.io/address/0x33db8d52d65F75E4cdDA1b02463760c9561A2aa1"><img src="../../.gitbook/assets/image (26).png" alt="" data-size="line"></a> 0x33db8d52d65F75E4cdDA1b02463760c9561A2aa1</td></tr><tr><td>wOUSD Implementation</td><td><a href="https://etherscan.io/address/0xbf3b9b141cb3629f5bb8f721cba9265c92494539"><img src="../../.gitbook/assets/image (7).png" alt="" data-size="line"></a> 0xbf3b9b141cb3629f5bb8f721cba9265c92494539</td></tr><tr><td>OUSD Vault</td><td><a href="https://etherscan.io/address/0xe75d77b1865ae93c7eaa3040b038d7aa7bc02f70"><img src="../../.gitbook/assets/image (23).png" alt="" data-size="line"></a> 0xE75D77B1865Ae93c7eaa3040B038D7aA7BC02F70</td></tr><tr><td>OUSD VaultAdmin</td><td><a href="https://etherscan.io/address/0x6a16335a203d4151892ca1260cca9d500fe82298#code"><img src="../../.gitbook/assets/image (19) (1).png" alt="" data-size="line"></a> 0x6a16335a203d4151892ca1260cca9d500fe82298</td></tr><tr><td>OUSD VaultCore</td><td><a href="https://etherscan.io/address/0x48cf14dea2f5dd31c57218877195913412d3278a"><img src="../../.gitbook/assets/image (21).png" alt="" data-size="line"></a> 0x48cf14dea2f5dd31c57218877195913412d3278a</td></tr></tbody></table>

**OUSD Strategies**

<table><thead><tr><th width="276">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OUSD Aave</td><td>0x5e3646A1Db86993f73E6b74A57D8640B69F7e259</td></tr><tr><td>OUSD Compound</td><td>0x9c459eeb3FA179a40329b81C1635525e9A0Ef094</td></tr><tr><td>OUSD Convex DAI+USDC+USDT</td><td>0xEA2Ef2e2E5A749D4A66b41Db9aD85a38Aa264cb3</td></tr><tr><td>OUSD Convex LUSD+3Crv</td><td>0x7A192DD9Cc4Ea9bdEdeC9992df74F1DA55e60a19</td></tr><tr><td>OUSD Convex OUSD+3Crv (AMO)</td><td>0x89eb88fedc50fc77ae8a18aad1ca0ac27f777a90</td></tr><tr><td>OUSD Morpho Compound</td><td>0x5A4eEe58744D1430876d5cA93cAB5CcB763C037D</td></tr><tr><td>OUSD Morpho Aave</td><td>0x79F2188EF9350A1dC11A062cca0abE90684b0197</td></tr></tbody></table>

**OUSD Yield Harvesting, Rewards Distribution & Swapping**

Flipper is a gas-optimized way for users to swap in and out of OUSD at a fixed 1:1 rate with other stablecoins. This contract may become empty on one side (e.g., contain 0 OUSD balance), and thus sometimes provides limited swap routes. Flipper is currently only available for OUSD.

<table><thead><tr><th width="194">Contract</th><th>Address</th></tr></thead><tbody><tr><td>OUSD Harvester</td><td>0x21fb5812d70b3396880d30e90d9e5c1202266c89</td></tr><tr><td>OUSD Dripper</td><td>0x80c898ae5e56f888365e235ceb8cea3eb726cb58</td></tr><tr><td>OUSD Buyback</td><td>0xD7B28d06365b85933c64E11e639EA0d3bC0e3BaB</td></tr><tr><td>OUSD Flipper</td><td>0xcecaD69d7D4Ed6D52eFcFA028aF8732F27e08F70</td></tr></tbody></table>

**OUSD Assets**

OUSD is backed by the following stablecoins:

<table data-header-hidden><thead><tr><th width="136"></th><th></th></tr></thead><tbody><tr><td><a href="https://etherscan.io/address/0xdac17f958d2ee523a2206206994597c13d831ec7">USDT</a></td><td>0xdac17f958d2ee523a2206206994597c13d831ec7</td></tr><tr><td><a href="https://etherscan.io/address/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48">USDC</a></td><td>0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48</td></tr><tr><td><a href="https://etherscan.io/address/0x6b175474e89094c44da98b954eedeac495271d0f">DAI</a></td><td>0x6b175474e89094c44da98b954eedeac495271d0f</td></tr></tbody></table>

**Oracles**

The following Chainlink oracles are used to protect the vault in case a backing asset loses value. They also offer slippage protection when harvesting rewards tokens.

<table><thead><tr><th width="181">Pair</th><th>Contract</th></tr></thead><tbody><tr><td><a href="https://data.chain.link/ethereum/mainnet/stablecoins/usdt-usd">USDT/USD</a></td><td>0x3E7d1eAB13ad0104d2750B8863b489D65364e32D</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/stablecoins/usdc-usd">USDC/USD</a></td><td>0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/stablecoins/dai-usd">DAI/USD</a></td><td>0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-usd/comp-usd">COMP/USD</a></td><td>0xdbd020caef83efd542f4de03e3cf0c28a4428bd5</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-usd/aave-usd">AAVE/USD</a></td><td>0x547a514d5e3769680Ce22B2361c10Ea13619e8a9</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-usd/crv-usd">CRV/USD</a></td><td>0xcd627aa160a6fa45eb793d19ef54f5062f20f33f</td></tr><tr><td><a href="https://data.chain.link/ethereum/mainnet/crypto-usd/cvx-usd">CVX/USD</a></td><td>0xd962fC30A72A84cE50161031391756Bf2876Af5D</td></tr></tbody></table>

**Deprecated**

These contacts are no longer actively used but are included here for historical purposes.

<table><thead><tr><th width="224">Contract</th><th>Address</th></tr></thead><tbody><tr><td>Original OGN Staking</td><td>0x501804B374EF06fa9C427476147ac09F1551B9A0</td></tr><tr><td>Original OGN Staking Implementation</td><td>0x8cd68a1e0b79150455c5498882d5d5d3df2dde08</td></tr><tr><td>OUSD Compensation</td><td>0x9C94df9d594BA1eb94430C006c269C314B1A8281</td></tr><tr><td>Old OUSD Vault</td><td>0x277e80f3E14E7fB3fc40A9d6184088e0241034bD</td></tr><tr><td>Old Buyback (1 of 2)</td><td>0x77314EB392b2be47C014cde0706908b3307Ad6a9</td></tr><tr><td>Old Buyback (2 of 2)</td><td>0x6C5cdfB47150EFc52072cB93Eea1e0F123529748</td></tr></tbody></table>
