# API

Several data endpoints are used internally and by our partners. These have been created incrementally on an as-needed basis and are not intended for widespread use. This documentation has been added for convenience, but please do not rely on this API for mission-critical data. If you need additional data to use in your application, please [reach out on Discord](https://originprotocol.com/discord).

The are two separate hostnames where different endpoints are hosted. The source code can be found in the [ousd-analytics](https://github.com/OriginProtocol/ousd-analytics/blob/2b16b3af85e90ed85c6375f2a6c0b41848dd8bd8/eagleproject/eagleproject/urls.py#L51-L64) and [origin-website](https://github.com/OriginProtocol/origin-website/blob/master/views/web\_views.py#L291-L324) GitHub repositories.

Some dates are displayed as timestamps or epochs, which can be converted to human-readable dates [here](https://www.epochconverter.com/).

### OUSD/OETH Analytics

{% swagger method="get" path="/api/v2/{symbol}/apr/trailing/{days}" baseUrl="https://analytics.ousd.com" summary="Trailing yield" %}
{% swagger-description %}
The annualized trailing yield for OUSD or OETH over a given number of days

Numbers greater than 365 may produce unexpected results
{% endswagger-description %}

{% swagger-parameter in="path" name="symbol" type="String" required="true" %}
ousd or oeth
{% endswagger-parameter %}

{% swagger-parameter in="path" required="false" type="Number" name="days" %}
Number of days
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "apr": "8.124428550334684695499731787",
  "apy": "8.43"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v2/{symbol}/apr/history" baseUrl="https://analytics.ousd.com" summary="Yield history" %}
{% swagger-description %}
The recent annualized historical yield for OUSD or OETH
{% endswagger-description %}

{% swagger-parameter in="path" name="symbol" type="String" required="true" %}
ousd or oeth
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  // 30-day apr
  "apr": "8.124428550334684695499731787",
  // 30-day apy
  "apy": "8.43",
  // daily apy for the prior 8+ days
  "daily": [
    {
      // today so far
      "apy": "2.757855899964977550381669000"
    },
    {
      // one day ago
      "apy": "5.203087867622041259311806600"
    },
    {
      // two days ago
      "apy": "5.024625361292970831224569500"
    },
    {
      // three days ago
      "apy": "56.33547497366474799228160500"
    },
    {
      // four days ago
      "apy": "3.735047272855167725188208800"
    },
    {
      // five days ago
      "apy": "3.572624475443835457212147200"
    },
    {
      // six days ago
      "apy": "4.959726075089981319735877800"
    },
    {
      // seven days ago
      "apy": "4.907690010865496625532084100"
    },
    {
      // eight days ago
      "apy": "4.643674734037820771919993600"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v2/{symbol}/collateral" baseUrl="https://analytics.ousd.com" summary="Collateral" %}
{% swagger-description %}
A list of backing assets and their balances held by OUSD or OETH
{% endswagger-description %}

{% swagger-parameter in="path" name="symbol" type="String" required="true" %}
ousd or oeth
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "collateral": [
    {
      "name": "dai",
      "total": "18865713.513970309197419331"
    },
    {
      "name": "usdt",
      "total": "10604997.234377000000000000"
    },
    {
      "name": "usdc",
      "total": "15085226.289650000000000000"
    },
    {
      "name": "ousd",
      "total": "8095696.025185597"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/v2/{symbol}/strategies{?structured}" baseUrl="https://analytics.ousd.com" summary="Strategies" %}
{% swagger-description %}
A list of OUSD's or OETH's yield-earning strategies and their token balances
{% endswagger-description %}

{% swagger-parameter in="query" name="structured" required="false" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="symbol" type="String" required="true" %}
ousd or oeth
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="unstructured" %}
```javascript
{
  "strategies": [
    {
      "name": "Vault",
      "total": 7448.884896,
      "dai": 0,
      "usdt": 7448.884896,
      "usdc": 0,
      "ousd": 0,
      "comp": 0
    },
    {
      "name": "Compound Strategy",
      "total": 17398875.172562208,
      "dai": 7269054.303955209,
      "usdt": 870672.787103,
      "usdc": 9259148.081504,
      "ousd": null,
      "comp": 0
    },
    {
      "name": "Convex Strategy",
      "total": 986822.3425206443,
      "dai": 328940.78084064426,
      "usdt": 328940.78084,
      "usdc": 328940.78084,
      "ousd": null,
      "comp": null
    },
    {
      "name": "Aave Strategy",
      "total": 9671353.458348105,
      "dai": 5770579.280891105,
      "usdt": 3900774.177457,
      "usdc": 0,
      "ousd": null,
      "comp": null
    },
    {
      "name": "Morpho Strategy",
      "total": 300046.72524734936,
      "dai": 100009.00572028894,
      "usdt": 100030.335322,
      "usdc": 100007.091334,
      "ousd": null,
      "comp": 0.29287106042538863
    },
    {
      "name": "OUSD MetaStrategy",
      "total": 16191392.352579273,
      "dai": 2698565.3920966364,
      "usdt": 2698565.3920965,
      "usdc": 2698565.3920965,
      "ousd": 8095696.176289637,
      "comp": null
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="structured" %}
```javascript
{
  "strategies": {
    "vault_holding": {
      "name": "Vault",
      "address": "0xe75d77b1865ae93c7eaa3040b038d7aa7bc02f70",
      "icon_file": "ousd-icon.svg",
      "total": 7448.884896,
      "holdings": {
        "DAI": 0,
        "USDT": 7448.884896,
        "USDC": 0,
        "OUSD": 0,
        "COMP": 0
      }
    },
    "compstrat_holding": {
      "name": "Compound Strategy",
      "address": "0x9c459eeb3fa179a40329b81c1635525e9a0ef094",
      "icon_file": "comp-icon.svg",
      "total": 17398876.638909493,
      "holdings": {
        "DAI": 7269054.913390493,
        "USDT": 870672.883321,
        "USDC": 9259148.842198,
        "COMP": 0
      }
    },
    "threepoolstrat_holding": {
      "name": "Convex Strategy",
      "address": "0xea2ef2e2e5a749d4a66b41db9ad85a38aa264cb3",
      "icon_file": "convex.png",
      "total": 986822.4291960566,
      "holdings": {
        "DAI": 328940.8097320566,
        "USDT": 328940.809732,
        "USDC": 328940.809732
      }
    },
    "aavestrat_holding": {
      "name": "Aave Strategy",
      "address": "0x5e3646a1db86993f73e6b74a57d8640b69f7e259",
      "icon_file": "aave-icon.svg",
      "total": 9671354.787477147,
      "holdings": {
        "DAI": 5770579.834380147,
        "USDT": 3900774.953097,
        "USDC": 0
      }
    },
    "morpho_strat": {
      "name": "Morpho Strategy",
      "address": "0x5a4eee58744d1430876d5ca93cab5ccb763c037d",
      "icon_file": "morpho.png",
      "total": 300046.7593402954,
      "holdings": {
        "DAI": 100009.01410501331,
        "USDT": 100030.352537,
        "USDC": 100007.09955,
        "COMP": 0.29314828210923694
      }
    },
    "ousd_metastrat": {
      "name": "OUSD MetaStrategy",
      "address": "0x89eb88fedc50fc77ae8a18aad1ca0ac27f777a90",
      "icon_file": "buffer-icon.svg",
      "total": 16191392.985012937,
      "holdings": {
        "DAI": 2698565.497502468,
        "USDT": 2698565.497502,
        "USDC": 2698565.497502,
        "OUSD": 8095696.492506469
      }
    }
  }
}
```
{% endswagger-response %}
{% endswagger %}

### Origin Protocol

{% swagger method="get" path="/circulating-ogn" baseUrl="https://api.originprotocol.com" summary="OGN circulating supply" %}
{% swagger-description %}
The number of Origin Tokens (OGN) in circulation
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```
503712464
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/circulating-ogv" baseUrl="https://api.originprotocol.com" summary="OGV circulating supply" %}
{% swagger-description %}
The number of Origin Dollar Governance (OGV) tokens in circulation
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```
420803708
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/total-ogn" baseUrl="https://api.originprotocol.com" summary="OGN total supply" %}
{% swagger-description %}
The total number of Origin Tokens (OGN) in existence
{% endswagger-description %}

{% swagger-response status="200: OK" description="OK" %}
```
1000000000
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/total-ogv" baseUrl="https://api.originprotocol.com" summary="OGV total supply" %}
{% swagger-description %}
The total number of Origin Dollar Governance (OGV) tokens in existence
{% endswagger-description %}

{% swagger-response status="200: OK" description="OK" %}
```
3975600118
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/total-ousd" baseUrl="https://api.originprotocol.com" summary="OUSD total supply" %}
{% swagger-description %}
The total number of Origin Dollar (OUSD) tokens in existence
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```
44555185
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/total-oeth" baseUrl="https://api.originprotocol.com" summary="OETH total supply" %}
{% swagger-description %}
The total number of Origin Ether (OETH) tokens in existence
{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

