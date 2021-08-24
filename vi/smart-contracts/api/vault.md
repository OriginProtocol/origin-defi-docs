---
description: >-
  Vault (kho tiền) là điểm cốt lõi của giao thức. Kho tiền chịu trách nhiệm khai tác / hoàn trả OUSD, cân bằng lại quỹ giữa các chiến lược được hỗ trợ khác nhau và thanh lý token thưởng.
---

# Vault

## Đơn vị

Tất cả OUSD được chuyển hoặc trả về theo phương thức Vault đều sử dụng 18 chữ số thập phân. Ví dụ: 1 OUSD được hiển thị 1000000000000000000.

Các đồng stablecoin khác nhau sẽ có số thập phân hiển thị khác nhau. DAI sử dụng 18 chữ số thập phân trong khi USDC và USDT chỉ sử dụng 6.

Efforts are [currently underway](https://github.com/OriginProtocol/origin-dollar/issues/590) to increase the resolution of rebasing calculations from 18 decimals to 27 decimals. The OUSD token itself will still retain 18 decimals of precision and user balances should not change.

## Phương pháp‌

### mint () <a id="mint"></a>

**`function mint(address _asset, uint256 _amount, uint256 _minimumOusdAmount)`**‌

Mints OUSD in exchange for a deposit of a certain `_amount` of stablecoin specified by the `_asset` parameter. The caller receives a certain amount of OUSD depending on the **exchange rate**.

| Tên thông số          | Loại    | Mô tả                                                                                                                                              |
|:--------------------- |:------- |:-------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset             | địa chỉ | Địa chỉ của stablecoin [được hỗ trợ](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets)  |
| \_amount            | uint256 | Số tiền gửi, được biểu thị bằng đơn vị thập phân                                                                                                   |
| \_minimumOusdAmount | uint256 | Số OUSD tối thiểu mà người gọi lệnh chấp nhận. Lệnh gọi mua\(\) sẽ được trả lại nếu số lượng tạo ra ít hơn số lượng mà người gọi lệnh chấp nhận. |

### mintMultiple () <a id="mintmultiple"></a>

**`function mintMultiple(address[] _assets, uint256[] _amounts, uint256 _minimumOusdAmount)`**‌

Mints OUSD in exchange for a deposit of multiple stablecoins in a single call. Stablecoins are specified by the `_assets` array parameter and the amounts by the `_amounts` array parameter. The caller receives a certain amount of OUSD depending on the **exchange rate**.

| Tên thông số          | Loại       | Mô tả                                                                                                                                              |
|:--------------------- |:---------- |:-------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_assets            | địa chỉ [] | Địa chỉ của [stablecoin được hỗ trợ](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets)  |
| \_amounts           | uint256 [] | Số tiền gửi, được biểu thị bằng đơn vị thập phân                                                                                                   |
| \_minimumOusdAmount | uint256    | Số OUSD tối thiểu mà người gọi lệnh chấp nhận. Lệnh gọi mua\(\) sẽ được trả lại nếu số lượng tạo ra ít hơn số lượng mà người gọi lệnh chấp nhận. |

{% hint style="warning" %}
On redemptions, it is the protocol and not the user that decides which stablecoin\(s\) are returned to the user. This decision of which coin\(s\) to return is based on the internal ratios of the assets that are being held in the vault.‌
{% endhint %}

### redeem () <a id="redeem"></a>

**`function redeem(uint256 _amount)`**‌

OUSD specified by the `_amount` parameter is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

| Tên thông số | Loại    | Mô tả                                |
|:------------ |:------- |:------------------------------------ |
| \_amount   | uint256 | lượng OUSD tính tới đơn vị thập phân |

### redeemAll ()‌ <a id="redeemall"></a>

**`function redeemAll()`**‌

All OUSD in user's possession is redeemed in exchange for one or multiple supported stablecoins. Amount of stablecoins received depends on the **exchange rate**.

### rebase () <a id="rebase"></a>

**`function rebase()`**‌

Updates the balances for all users based on the value of the assets currently stored in the vault. Returns total value of the underlying assets and strategies represented by `uint256` type.‌

### allocate () <a id="allocate"></a>

**`function allocate()`**‌

Moves the assets under management into their prescribed [Stategies](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/architecture/strategies) to maximize yield and diversify risk.‌

### totalValue () <a id="totalvalue"></a>

**`function totalValue()`**‌

Returns total value of underlying assets and strategies.

| `return` Tên | Loại    | Mô tả                                                     |
|:------------ |:------- |:--------------------------------------------------------- |
| giá trị      | uint256 | trả về tổng giá trị của các tài sản và chiến lược cơ bản. |

### checkBalance () <a id="checkbalance"></a>

**`function checkBalance(address _asset)`**‌

Returns the balance of an asset specified by the`_asset` parameter held in Vault and all strategies represented by `uint256` type.

| Tên thông số | Loại    | Mô tả                                                                                                                                             |
|:------------ |:------- |:------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_asset    | địa chỉ | Địa chỉ của stablecoin [được hỗ trợ](https://app.gitbook.com/@originprotocol/s/ousd/~/drafts/-MHSojsgAcBjyg6RCmpF/core-concepts/supported-assets) |

### calculateRedeemOutputs () <a id="calculateredeemoutputs"></a>

**`function calculateRedeemOutputs(uint256 _amount)`**‌

Calculate the mix of stablecoins that a `redeem` function would return when redeeming certain amount of OUSD specified by the `_amount` parameter. Returns an array of stablecoin values.

To attribute the stablecoin values to the correct stablecoin currency this call should be used in conjunction with `getAllAssets` function that returns an array of stablecoin addresses.

The index of an array that is returned by the `calculateRedeemOutputs` corresponds to the stablecoin address with the same index in an array returned by the `getAllAssets` function.

| Tên thông số | Loại    | Mô tả                                |
|:------------ |:------- |:------------------------------------ |
| \_amount   | uint256 | lượng OUSD tính tới đơn vị thập phân |

| `return` Tên | Loại       | Mô tả                                                   |
|:------------ |:---------- |:------------------------------------------------------- |
| đầu ra       | uint256 [] | mảng số lượng tài sản stablecoin mà hàm `redeem` trả về |

### getAssetCount () <a id="getassetcount"></a>

**`function getAssetCount()`**‌

Return the number of supported stablecoin assets represented by `uint256` type.‌

### getAllAssets () <a id="getallassets"></a>

**`function getAllAssets()`**‌

Return all assets addresses of supported stablecoin assets in order represented by `uint256` type.‌

### getStrategyCount () <a id="getstrategycount"></a>

**`function getStrategyCount()`**‌

Return the number of strategies active on the Vault represented by `uint256` type.‌

### getAPR () <a id="getapr"></a>

**`function getAPR()`**‌

Return the total annual percentage yield \(APR\) of the Vault and all Strategies represented by `uint256` type. Resulting number has 18 decimal places.‌

### isSupportedAsset (\) <a id="issupportedasset"></a>

**`function isSupportedAsset(address _asset)`**‌

Return the boolean that is true if the asset specified by the `_asset` parameter is supported by the Vault.

| Tên thông số | Loại    | Mô tả                  |
|:------------ |:------- |:---------------------- |
| \_asset    | địa chỉ | Địa chỉ của stablecoin |

### priceUSDMint () <a id="issupportedasset-1"></a>

**`function priceUSDMint(string symbol)`**‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Tên thông số | Loại  | Mô tả                  |
|:------------ |:----- |:---------------------- |
| ký hiệu      | chuỗi | Địa chỉ của stablecoin |

### priceUSDRedeem () <a id="issupportedasset-2"></a>

**`function priceUSDRedeem(string symbol)`**‌‌

Returns the exchange rate price of a stable coin specified by the `symbol` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Tên thông số | Loại  | Mô tả                  |
|:------------ |:----- |:---------------------- |
| ký hiệu      | chuỗi | Địa chỉ của stablecoin |

### priceAssetUSDMint\(\)‌ <a id="issupportedasset-3"></a>

**`function priceAssetUSDMint(address _asset)`**‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when minting OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Tên thông số | Loại    | Mô tả                   |
|:------------ |:------- |:----------------------- |
| \_asset    | địa chỉ | Địa chỉ của stablecoin‌ |

### priceAssetUSDRedeem ()‌ <a id="issupportedasset-3-1"></a>

**`function priceAssetUSDRedeem(address _asset)`**‌‌‌

Returns the exchange rate price of a stable coin specified by the `_asset` parameters used when redeeming OUSD represented by `uint256` type. Resulting number has 18 decimal places.

| Tên thông số | Loại    | Mô tả                  |
|:------------ |:------- |:---------------------- |
| \_asset    | địa chỉ | Địa chỉ của stablecoin |
