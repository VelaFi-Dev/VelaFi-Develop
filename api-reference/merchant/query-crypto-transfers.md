---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/query-crypto-transfers
---

# Query Crypto Transfers

### This API allows you to query internal transfer orders between merchants.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `GET`
* **Request Path**: `/v2/assets/internalTransferOrders`
* **Authorization Required**: Yes



***

#### **Query Parameters**

The request URL may include the following query parameters:

<table><thead><tr><th>Parameter</th><th width="216">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>tokenId</code></td><td>string</td><td>(optional) Token symbol, e.g., <code>USDT</code>.</td></tr><tr><td><code>clientId</code></td><td>string</td><td>(optional) Client ID for filtering.</td></tr><tr><td><code>startTime</code></td><td>number</td><td>(optional) Start timestamp (in ms).</td></tr><tr><td><code>endTime</code></td><td>number</td><td>(optional) End timestamp (in ms).</td></tr><tr><td><code>pageSize</code></td><td>number</td><td>(optional) Number of records per page.</td></tr><tr><td><code>merchantId</code></td><td>number</td><td>(optional) Merchant ID to query records for.</td></tr></tbody></table>

***

#### **Authorization**

This request requires valid authorization via `X-BH-TOKEN`.

***

#### **Response Structure**

The response will include the following fields:

```json
{
  "code": 0,             // (number: response code)
  "msg": "",             // (string: response message)
  "data": [              // (array: list of transfer records)
    {
      "id": "",             // (string: unique ID of the transfer record)
      "tokenId": "",         // (string: token symbol)
      "amount": "",   // (string: transferred amount)
      "clientId": "",       // (string: client ID)
      "merchantId": "",     // (string: merchant ID of this record)
      "fromMerchantId": "", // (string: sender merchant ID)
      "toMerchantId": ""    // (string: recipient merchant ID)
    }
  ]
}
```

***

#### **Example Request**

```
GET /v2/assets/internalTransferOrders?tokenId=&clientId=&startTime=0&endTime=0&pageSize=10&merchantId=
```

***

#### **Example Response**

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": [
    {
      "id": "4355",
      "tokenId": "USDT",
      "amount": "10",
      "clientId": "1",
      "merchantId": "61",
      "fromMerchantId": "246",
      "toMerchantId": "61"
    },
    {
      "id": "4354",
      "tokenId": "USDT",
      "amount": "-10",
      "clientId": "1",
      "merchantId": "246",
      "fromMerchantId": "246",
      "toMerchantId": "61"
    }
  ]
}
```

***

✅ **Note:**

* Positive `amount` indicates credit to the receiving merchant.
* Negative `amount` indicates debit from the sending merchant.
* `merchantId` indicates which merchant the current record belongs to.
