---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/get-crypto-assets-balance
---

# Get Crypto Assets Balance

This API allows you to retrieve the balances of cryptocurrency assets in a user's account.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/assets/account/assets`
* **Authorization Required**: Yes

#### Query Parameters

* **merchantId**: (int) The ID of the merchant. If `0`, the API will return the **aggregated balances** across all merchants linked to this user.

#### Response Structure

The response will include the following fields:

```json
{
  "code": 200,                      // (number: response code)
  "msg": "SUCCESS",                 // (string: message)
  "data": {                         // (object: account asset details)
    "canDeposit": false,            // (boolean: whether the account can deposit)
    "balances": [                   // (array: list of asset balances)
      {
        "asset": "",                // (string: name of the asset)
        "assetId": "",              // (string: ID of the asset)
        "assetName": "",            // (string: display name of the asset)
        "total": "",                // (string: total amount of the asset)
        "free": "",                 // (string: free amount of the asset)
        "locked": ""                // (string: locked amount of the asset)
      }
    ]
  }
}
```

#### **Example Response (Specific Merchant)**

**Request:**

```
GET /v2/assets/account/assets?merchantId=12345
X-BH-TOKEN: ******
```

**Response:**

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "canDeposit": true,
    "balances": [
      {
        "asset": "USDT",
        "assetId": "USDT",
        "assetName": "USDT",
        "total": "1000",
        "free": "800",
        "locked": "200"
      },
      {
        "asset": "BTC",
        "assetId": "BTC",
        "assetName": "BTC",
        "total": "0.5",
        "free": "0.3",
        "locked": "0.2"
      }
    ]
  }
}
```

***

#### **Example Response (Aggregated Across All Merchants)**

**Request:**

```
GET /v2/assets/account/assets?merchantId=0
X-BH-TOKEN: ******
```

**Response:**

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "canDeposit": true,
    "balances": [
      {
        "asset": "USDT",
        "assetId": "USDT",
        "assetName": "USDT",
        "total": "5000",
        "free": "4000",
        "locked": "1000"
      },
      {
        "asset": "BTC",
        "assetId": "BTC",
        "assetName": "BTC",
        "total": "2",
        "free": "1.5",
        "locked": "0.5"
      }
    ]
  }
}
```

***

#### **Notes**

&#x20;**`canDeposit` field:**\
Indicates whether the account supports deposits at this time.

&#x20;**`merchantId=0` special case:**\
When `merchantId` is `0`, the API aggregates balances across **all merchants** bound to the same account and returns the combined amounts for each asset.
