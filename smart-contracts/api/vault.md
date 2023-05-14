---
description: >-
  The vault is the main contract of the protocol. The vault is responsible for
  minting/redeeming, rebalancing funds between the various supported strategies,
  and liquidating rewards tokens.
---

# Vault

## Units

All OUSD/OETH amounts passed or returned by the Vault methods use 18 decimal places. For example, 1 OUSD is expressed as 1000000000000000000.

For other stablecoins, the number of decimal places varies. DAI uses 18 decimal places while USDC and USDT use only 6.

Each of the supported LSDs all use 18 decimals.

The protocol was updated in November 2021 to [increase the resolution](https://github.com/OriginProtocol/origin-dollar/issues/590) of rebasing calculations from 18 decimals to 27 decimals. The OUSD token itself retained 18 decimals of precision and user balances were not affected.

## Methods‌

### mint() <a href="#mint" id="mint"></a>

\*\*`function mint(address _asset, uint256 _amount, uint256 _minimumOusdAmount)`\*\*‌

Mints OUSD in exchange for a deposit of a certain `_amount` of stablecoin specified by the `_asset` parameter. The caller receives a certain amount of OUSD depending on the **exchange rate**.

| Parameter Name      | Type    | Description                                                                                                                                         |
| ------------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset             | address | Address of the [supported](https://app.gitbook.com/@originprotocol/s/ousd/\~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) stablecoin |
| \_amount            | uint256 | Amount deposited, expressed in decimal units                                                                                                        |
| \_minimumOusdAmount | uint256 | Minimum amount of OUSD the caller is willing to receive. The call to mint() reverts if the minimum is not met.                                      |

{% hint style="warning" %}
On redemptions, it is the protocol and not the user that decides which stablecoin(s) are returned to the user. This decision of which coin(s) to return is based on the internal ratios of the assets that are being held in the vault.‌
{% endhint %}

### redeem() <a href="#redeem" id="redeem"></a>

\*\*`function redeem(uint256 _amount)`\*\*‌

OUSD specified by the `_amount` parameter is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

| Parameter Name | Type    | Description                               |
| -------------- | ------- | ----------------------------------------- |
| \_amount       | uint256 | amount of OUSD expressed in decimal units |

### redeemAll()‌ <a href="#redeemall" id="redeemall"></a>

\*\*`function redeemAll()`\*\*‌

All OUSD in user's possession is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

### rebase() <a href="#rebase" id="rebase"></a>

\*\*`function rebase()`\*\*‌

Updates the balances for all users based on the value of the assets currently stored in the vault. Returns total value of the underlying assets and strategies represented by `uint256` type.‌

### allocate() <a href="#allocate" id="allocate"></a>

\*\*`function allocate()`\*\*‌

Moves the assets under management into their prescribed [Stategies](https://app.gitbook.com/@originprotocol/s/ousd/\~/drafts/-MHSojsgAcBjyg6RCmpF/architecture/strategies) to maximize yield and diversify risk.‌

### totalValue() <a href="#totalvalue" id="totalvalue"></a>

\*\*`function totalValue()`\*\*‌

Returns total value of underlying assets and strategies.

| `return` name | Type    | Description                                      |
| ------------- | ------- | ------------------------------------------------ |
| value         | uint256 | total value of underlying assets and strategies. |

### checkBalance() <a href="#checkbalance" id="checkbalance"></a>

\*\*`function checkBalance(address _asset)`\*\*‌

Returns the balance of an asset specified by the`_asset` parameter held in Vault and all strategies represented by `uint256` type.

| Parameter Name | Type    | Description                                                                                                                                         |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset        | address | Address of the [supported](https://app.gitbook.com/@originprotocol/s/ousd/\~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) stablecoin |

### calculateRedeemOutputs() <a href="#calculateredeemoutputs" id="calculateredeemoutputs"></a>

\*\*`function calculateRedeemOutputs(uint256 _amount)`\*\*‌

Calculate the mix of stablecoins that a `redeem` function would return when redeeming certain amount of OUSD specified by the `_amount` parameter. Returns an array of stablecoin values.

To attribute the stablecoin values to the correct stablecoin currency this call should be used in conjunction with `getAllAssets` function that returns an array of stablecoin addresses.

The index of an array that is returned by the `calculateRedeemOutputs` corresponds to the stablecoin address with the same index in an array returned by the `getAllAssets` function.

| Parameter Name | Type    | Description                               |
| -------------- | ------- | ----------------------------------------- |
| \_amount       | uint256 | amount of OUSD expressed in decimal units |

| `return` name | Type       | Description                                                                 |
| ------------- | ---------- | --------------------------------------------------------------------------- |
| outputs       | uint256\[] | array of the amount of the stablecoin assets `redeem` function would return |

### getAssetCount() <a href="#getassetcount" id="getassetcount"></a>

\*\*`function getAssetCount()`\*\*‌

Return the number of supported stablecoin assets represented by `uint256` type.‌

### getAllAssets() <a href="#getallassets" id="getallassets"></a>

\*\*`function getAllAssets()`\*\*‌

Return all assets addresses of supported stablecoin assets in order represented by `uint256` type.‌

### getStrategyCount()‌ <a href="#getstrategycount" id="getstrategycount"></a>

\*\*`function getStrategyCount()`\*\*‌

Return the number of strategies active on the Vault represented by `uint256` type.‌

### getAPR() <a href="#getapr" id="getapr"></a>

\*\*`function getAPR()`\*\*‌

Return the total annual percentage yield (APR) of the Vault and all Strategies represented by `uint256` type. Resulting number has 18 decimal places.‌

### isSupportedAsset() <a href="#issupportedasset" id="issupportedasset"></a>

\*\*`function isSupportedAsset(address _asset)`\*\*‌

Return the boolean that is true if the asset specified by the `_asset` parameter is supported by the Vault.

| Parameter Name | Type    | Description               |
| -------------- | ------- | ------------------------- |
| \_asset        | address | Address of the stablecoin |

### priceUSDMint() <a href="#issupportedasset-1" id="issupportedasset-1"></a>

\*\*`function priceUSDMint(string symbol)`\*\*‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Parameter Name | Type   | Description              |
| -------------- | ------ | ------------------------ |
| symbol         | string | Symbol of the stablecoin |

### priceUSDRedeem() <a href="#issupportedasset-2" id="issupportedasset-2"></a>

\*\*`function priceUSDRedeem(string symbol)`\*\*‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Parameter Name | Type   | Description              |
| -------------- | ------ | ------------------------ |
| symbol         | string | Symbol of the stablecoin |

### priceAssetUSDMint()‌ <a href="#issupportedasset-3" id="issupportedasset-3"></a>

\*\*`function priceAssetUSDMint(address _asset)`\*\*‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Parameter Name | Type    | Description                |
| -------------- | ------- | -------------------------- |
| \_asset        | address | Address of the stablecoin‌ |

### priceAssetUSDRedeem()‌ <a href="#issupportedasset-3-1" id="issupportedasset-3-1"></a>

\*\*`function priceAssetUSDRedeem(address _asset)`\*\*‌‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Parameter Name | Type    | Description               |
| -------------- | ------- | ------------------------- |
| \_asset        | address | Address of the stablecoin |
