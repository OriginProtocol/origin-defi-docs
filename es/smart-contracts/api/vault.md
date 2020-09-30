---
description: >-
  La bóveda es el contrato principal del protocolo. La bóveda es responsable de acuñar/canjear tokens OUSD, reequilibrar fondos entre las diversas estrategias compatibles y liquidar tokens de recompensa.
---

# Bóveda

## Métodos

### mint\(\) <a id="mint"></a>

**`función mint (dirección _asset, uint256 _amount)`**

Acuñar OUSD a cambio de un depósito de un determinado `_amount` de moneda estable especificado por el `_asset` parámetro. The caller receives a certain amount of OUSD depending on the **exchange rate**.

| Nombre del parámetro | Tipo      | Descripción                                                                                                                                        |
|:-------------------- |:--------- |:-------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset            | dirección | Address of the [supported](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) stablecoin |
| \_amount           | uint256   | monto depositado, expresado en unidades decimales                                                                                                  |

### mintMultiple\(\) <a id="mintmultiple"></a>

**`function mintMultiple(address[] _assets, uint256[] _amounts)`**‌

Mints OUSD in exchange for a deposit of multiple stablecoins in a single call. Stablecoins are specified by the `_assets` array parameter and the amounts by the `_amounts` array parameter. The caller receives a certain amount of OUSD depending on the **exchange rate**.

| Parameter Name | Type          | Description                                                                                                                                           |
|:-------------- |:------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_assets     | address\[\] | Addresses of the [supported](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) stablecoins |
| \_amounts    | uint256\[\] | amounts deposited, expressed in decimal units                                                                                                         |

{% hint style="warning" %}
On redemptions, it is the protocol and not the user that decides which stablecoin\(s\) are returned to the user. This decision of which coin\(s\) to return is based on the internal ratios of the assets that are being held in the vault.‌
{% endhint %}

### redeem\(\) <a id="redeem"></a>

**`function redeem(uint256 _amount)`**‌

OUSD specified by the `_amount` parameter is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

| Parameter Name | Type    | Description                               |
|:-------------- |:------- |:----------------------------------------- |
| \_amount     | uint256 | amount of OUSD expressed in decimal units |

### redeemAll\(\)‌ <a id="redeemall"></a>

**`function redeemAll()`**‌

All OUSD in user's possession is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

### rebase\(\) <a id="rebase"></a>

**`function rebase()`**‌

Updates the balances for all users based on the value of the assets currently stored in the vault. Returns total value of the underlying assets and strategies represented by `uint256` type.‌

### allocate\(\) <a id="allocate"></a>

**`function allocate()`**‌

Moves the assets under management into their prescribed [Stategies](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/architecture/strategies) to maximize yield and diversify risk.‌

### totalValue\(\) <a id="totalvalue"></a>

**`function totalValue()`**‌

Returns total value of underlying assets and strategies.

| `return` name | Type    | Description                                      |
|:------------- |:------- |:------------------------------------------------ |
| value         | uint256 | total value of underlying assets and strategies. |

### checkBalance\(\) <a id="checkbalance"></a>

**`function checkBalance(address _asset)`**‌

Returns the balance of an asset specified by the`_asset` parameter held in Vault and all strategies represented by `uint256` type.

| Parameter Name | Type    | Description                                                                                                                                        |
|:-------------- |:------- |:-------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset      | address | Address of the [supported](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) stablecoin |

### calculateRedeemOutputs\(\) <a id="calculateredeemoutputs"></a>

**`function calculateRedeemOutputs(uint256 _amount)`**‌

Calculate the mix of stablecoins that a `redeem` function would return when redeeming certain amount of OUSD specified by the `_amount` parameter. Returns an array of stablecoin values.

To attribute the stablecoin values to the correct stablecoin currency this call should be used in conjunction with `getAllAssets` function that returns an array of stablecoin addresses.

The index of an array that is returned by the `calculateRedeemOutputs` corresponds to the stablecoin address with the same index in an array returned by the `getAllAssets` function.

| Parameter Name | Type    | Description                               |
|:-------------- |:------- |:----------------------------------------- |
| \_amount     | uint256 | amount of OUSD expressed in decimal units |

| `return` name | Type          | Description                                                                 |
|:------------- |:------------- |:--------------------------------------------------------------------------- |
| outputs       | uint256\[\] | array of the amount of the stablecoin assets `redeem` function would return |

### getAssetCount\(\) <a id="getassetcount"></a>

**`function getAssetCount()`**‌

Return the number of supported stablecoin assets represented by `uint256` type.‌

### getAllAssets\(\) <a id="getallassets"></a>

**`function getAllAssets()`**‌

Return all assets addresses of supported stablecoin assets in order represented by `uint256` type.‌

### getStrategyCount\(\)‌ <a id="getstrategycount"></a>

**`function getStrategyCount()`**‌

Return the number of strategies active on the Vault represented by `uint256` type.‌

### getAPR\(\) <a id="getapr"></a>

**`function getAPR()`**‌

Return the total annual percentage yield \(APR\) of the Vault and all Strategies represented by `uint256` type. Resulting number has 18 decimal spaces.‌

### isSupportedAsset\(\) <a id="issupportedasset"></a>

**`function isSupportedAsset(address _asset)`**‌

Return the boolean that is true if the asset specified by the `_asset` parameter is supported by the Vault.

| Parameter Name | Type    | Description               |
|:-------------- |:------- |:------------------------- |
| \_asset      | address | Address of the stablecoin |

### priceUSDMint\(\) <a id="issupportedasset-1"></a>

**`function priceUSDMint(string symbol)`**‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal spaces.

| Parameter Name | Type   | Description              |
|:-------------- |:------ |:------------------------ |
| symbol         | string | Symbol of the stablecoin |

### priceUSDRedeem\(\) <a id="issupportedasset-2"></a>

**`function priceUSDRedeem(string symbol)`**‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal spaces.

| Parameter Name | Type   | Description              |
|:-------------- |:------ |:------------------------ |
| symbol         | string | Symbol of the stablecoin |

### priceAssetUSDMint\(\)‌ <a id="issupportedasset-3"></a>

**`function priceAssetUSDMint(address _asset)`**‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal spaces.

| Parameter Name | Type    | Description                |
|:-------------- |:------- |:-------------------------- |
| \_asset      | address | Address of the stablecoin‌ |

### priceAssetUSDRedeem\(\)‌ <a id="issupportedasset-3-1"></a>

**`function priceAssetUSDRedeem(address _asset)`**‌‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal spaces.

| Parameter Name | Type    | Description               |
|:-------------- |:------- |:------------------------- |
| \_asset      | address | Address of the stablecoin |

