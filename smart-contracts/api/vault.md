---
description: >-
  The vault is the main contract of the protocol. The vault is responsible for
  minting/redeeming, rebalancing funds between the various supported strategies,
  and liquidating rewards tokens.
---

# Vault

## Units

All OUSD and OETH amounts passed or returned by the Vault methods use 18 decimal places. For example, 1 OUSD is expressed as 1000000000000000000.

For OUSD's supported [stablecoins](../../core-concepts/supported-stablecoins/), the number of decimal places varies. DAI uses 18 decimal places while USDC and USDT use only 6.

Each of OETH's supported [liquid staking derivatives (LSDs)](../../core-concepts/supported-lsds/) use 18 decimals.

{% hint style="warning" %}
The OUSD protocol was updated in November 2021 to [increase the resolution](https://github.com/OriginProtocol/origin-dollar/issues/590) of rebasing calculations from 18 decimals to 27 decimals. The OUSD token itself retained 18 decimals of precision and user balances were not affected.
{% endhint %}

## Methods‌

### mint() <a href="#mint" id="mint"></a>

\*\*`function mint(address _asset, uint256 _amount, uint256 _minimumOusdAmount)`\*\*‌

Mints OUSD/OETH in exchange for a deposit of a certain `_amount` of assets specified by the `_asset` parameter. The caller receives an amount of OUSD/OETH depending on the **exchange rate**.

| Parameter Name      | Type    | Description                                                                                                            |
| ------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| \_asset             | address | Address of the supported asset token. eg DAI or rETH                                                                   |
| \_amount            | uint256 | Amount of asset tokens to deposit, expressed in decimal units                                                          |
| \_minimumOusdAmount | uint256 | Minimum amount of OUSD or OETH the caller is willing to receive. The call to mint() reverts if the minimum is not met. |

{% hint style="warning" %}
On redemptions, it is the protocol and not the user that decides which asset tokens are returned to the user. This decision of which tokens to return is based on the internal ratios of the assets that are being held in the vault.‌
{% endhint %}

### redeem() <a href="#redeem" id="redeem"></a>

\*\*`function redeem(uint256 _amount)`\*\*‌

Redeems OUSD/OETH in exchange for asset tokens held by the vault or its underlying strategies. The amount of asset tokens received depends on the amount of asset tokens managed by the vault and their exchange rates.

`calculateRedeemOutputs` will return the asset token amounts without doing the actual redeem.

| Parameter Name | Type    | Description                                    |
| -------------- | ------- | ---------------------------------------------- |
| \_amount       | uint256 | amount of OUSD/OETH expressed in decimal units |

### redeemAll()‌ <a href="#redeemall" id="redeemall"></a>

\*\*`function redeemAll()`\*\*‌

Redeem all OUSD/OETH in the user's possession in exchange for one or multiple supported asset tokens. The amount of asset tokens received depends on the amount of asset tokens managed by the vault and their exchange rates.

### rebase() <a href="#rebase" id="rebase"></a>

\*\*`function rebase()`\*\*‌

Updates the balances for all users based on the value of the assets currently stored in the vault. Returns total value of the underlying assets and strategies.‌

### allocate() <a href="#allocate" id="allocate"></a>

\*\*`function allocate()`\*\*‌

Moves assets in the vault into their prescribed [Strategies](https://app.gitbook.com/@originprotocol/s/ousd/\~/drafts/-MHSojsgAcBjyg6RCmpF/architecture/strategies) to maximize yield and diversify risk.‌

### totalValue() <a href="#totalvalue" id="totalvalue"></a>

\*\*`function totalValue()`\*\*‌

Returns total value of underlying assets and strategies in USD for OUSD and ETH for OETH.

| `return` name | Type    | Description                                      |
| ------------- | ------- | ------------------------------------------------ |
| value         | uint256 | total value of underlying assets and strategies. |

### checkBalance() <a href="#checkbalance" id="checkbalance"></a>

\*\*`function checkBalance(address _asset)`\*\*‌

Returns the balance of an asset held in Vault and all its strategies.

| Parameter Name | Type    | Description                                          |
| -------------- | ------- | ---------------------------------------------------- |
| \_asset        | address | Address of the supported asset token. eg DAI or rETH |

### calculateRedeemOutputs() <a href="#calculateredeemoutputs" id="calculateredeemoutputs"></a>

\*\*`function calculateRedeemOutputs(uint256 _amount)`\*\*‌

Calculate the mix of asset tokens that a `redeem` function would return when redeeming certain amount of OUSD or OETH. Returns an array of asset token values.

To attribute the asset token values to the correct asset currency, this call should be used in conjunction with `getAllAssets` function that returns an array of asset token addresses.

The index of an array that is returned by the `calculateRedeemOutputs` corresponds to the asset token address with the same index in an array returned by the `getAllAssets` function.

| Parameter Name | Type    | Description                               |
| -------------- | ------- | ----------------------------------------- |
| \_amount       | uint256 | amount of OUSD expressed in decimal units |

| `return` name | Type       | Description                                                            |
| ------------- | ---------- | ---------------------------------------------------------------------- |
| outputs       | uint256\[] | array of the amount of the asset tokens `redeem` function would return |

### getAssetCount() <a href="#getassetcount" id="getassetcount"></a>

\*\*`function getAssetCount()`\*\*‌

Return the number of supported asset tokens.‌

### getAllAssets() <a href="#getallassets" id="getallassets"></a>

\*\*`function getAllAssets()`\*\*‌

Return all asset token addresses.‌

For OUSD, the assets are [stablecoins](../../core-concepts/supported-stablecoins/).

For OETH, the assets are [liquid staking derivatives (LSD)](../../core-concepts/supported-lsds/).

### getStrategyCount()‌ <a href="#getstrategycount" id="getstrategycount"></a>

\*\*`function getStrategyCount()`\*\*‌

Return the number of strategies active on the Vault.‌

### getAllStrategies()‌ <a href="#getstrategycount" id="getstrategycount"></a>

\*\*`function getAllStrategies()`\*\*‌

Return all the active strategy addresses.

### isSupportedAsset() <a href="#issupportedasset" id="issupportedasset"></a>

\*\*`function isSupportedAsset(address _asset)`\*\*‌

Return true if the asset token specified by the `_asset` parameter is supported by the Vault.

| Parameter Name | Type    | Description                |
| -------------- | ------- | -------------------------- |
| \_asset        | address | Address of the asset token |

### priceUnitMint() <a href="#issupportedasset-1" id="issupportedasset-1"></a>

\*\*`function priceUnitMint(address asset)`\*\*‌‌

Returns the unit price of an asset token used when minting. That is, the exchange rate used to convert the deposited asset tokens to OETH. The exchange is in OETH units so represents the number of OETH for one asset token.

The returned `uint256` unit price has 18 decimal places.

{% hint style="info" %}
Is only on the OETH vault.
{% endhint %}

| Parameter Name | Type    | Description                         |
| -------------- | ------- | ----------------------------------- |
| asset          | address | Address of the asset token. eg rETH |

### priceUnitRedeem() <a href="#issupportedasset-2" id="issupportedasset-2"></a>

\*\*`function priceUnitRedeem(string symbol)`\*\*‌‌

Returns the unit price of an asset token used when redeeming. That is, the exchange rate used to convert the redeeming OETH to asset tokens. The exchange is in OETH units so represents the number of OETH for one asset token.

The returned `uint256` unit price has 18 decimal places.

{% hint style="info" %}
Is only on the OETH vault.
{% endhint %}

| Parameter Name | Type    | Description                         |
| -------------- | ------- | ----------------------------------- |
| asset          | address | Address of the asset token. eg rETH |

