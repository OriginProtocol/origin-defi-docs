# OETH Registry

Most of Origin's contracts are upgradable via a well-known proxy wrapper and an implementation contract. The Vault is split into VaultAdmin and VaultCore to work around the maximum contract size limit on Ethereum

**OETH Core**

| Contract    | Address                                     |
| ----------- | ------------------------------------------- |
| OETH Token  | 0x856c4Efb76C1D1AE02e20CEB03A2A6a08b0b8dC3  |
| wOETH Token | 0xDcEe70654261AF21C44c093C300eD3Bb97b78192  |
| OETH Vault  |  0x39254033945AA2E4809Cc2977E7087BEE48bd7Ab |
| OETH Zapper | 0x9858e47BCbBe6fBAC040519B02d7cd4B2C470C66  |

**OETH Strategies**

| Contract                    | Address                                    |
| --------------------------- | ------------------------------------------ |
| OETH Convex ETH +OETH (AMO) | Not yet live                               |
| OETH Frax Staking           | 0x3fF8654D633D4Ea0faE24c52Aec73B4A20D0d0e5 |

**OUSD Yield Harvesting & Rewards Distribution**

| Contract       | Address                                    |
| -------------- | ------------------------------------------ |
| OETH Harvester | Not yet live                               |
| OETH Dripper   | 0xc0F42F73b8f01849a2DD99753524d4ba14317EB3 |
| OETH Buyback   | Not yet live                               |

**Chainlink Keepers**

Chainlink Keepers are an automated and decentralized way for OETH to perform regularly scheduled tasks.

| Keeper        | Address                                    | Purpose                  |
| ------------- | ------------------------------------------ | ------------------------ |
| OUSD Keeper 4 | 0xAAdf7D0f2E217168ACC90e5d39A42a24857620d5 | Executing a daily rebase |

**OETH Assets**

OETH is backed by WETH and the following liquid staking derivates:

| WETH                      | 0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2 |
| ------------------------- | ------------------------------------------ |
| Lido stETH                | 0xae7ab96520de3a18e5e111b5eaab095312d7fe84 |
| Rocketpool rETH           | 0xae78736cd615f374d3085123a210448e74fc6393 |
| Frax frxETH               | 0x5e8422345238f34275888049021821e8e08caa1f |
| Coinbase cbETH (inactive) | 0xBe9895146f7AF43049ca1c1AE358B0541Ea49704 |

**Oracles**

The following Chainlink oracles are used to protect the vault in case a backing asset loses value. They also offer slippage protection when harvesting rewards tokens.

| Pair                                                                                  | Contract                                   |
| ------------------------------------------------------------------------------------- | ------------------------------------------ |
| [stETH/ETH](https://data.chain.link/ethereum/mainnet/crypto-eth/steth-eth)            | 0x86392dc19c0b719886221c78ab11eb8cf5c52812 |
| [rETH/ETH](https://data.chain.link/ethereum/mainnet/crypto-eth/reth-eth)              | 0x536218f9e9eb48863970252233c8f271f554c2d0 |
| [cbETH/ETH](https://data.chain.link/ethereum/mainnet/crypto-eth/cbeth-eth) (inactive) | 0xf017fcb346a1885194689ba23eff2fe6fa5c483b |
| [CRV/USD](https://data.chain.link/ethereum/mainnet/crypto-usd/crv-usd)                | 0xcd627aa160a6fa45eb793d19ef54f5062f20f33f |
| [CVX/USD](https://data.chain.link/ethereum/mainnet/crypto-usd/cvx-usd)                | 0xd962fC30A72A84cE50161031391756Bf2876Af5D |
