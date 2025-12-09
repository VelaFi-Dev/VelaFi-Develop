---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/crypto-transfer
---

# Crypto Transfer

This API allows you to transfer crypto assets internally between merchants.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/assets/internalTransfer`
* **Authorization Required**: Yes



#### **Request Body Parameters**

The request body should include the following fields:

```json
{
  "fromMerchantId": 0,   // (number: ID of the sender merchant)
  "toMerchantId": 0,     // (number: ID of the recipient merchant)
  "tokenId": "",           // (string: token symbol, e.g., USDT,USDC,BTC,MMXN)
  "amount": 0,           // (number: amount to transfer)
  "clientId": ""         // (string: client ID for tracking, optional)
}
```

***

#### **Authorization**

This request requires valid authorization via `X-BH-TOKEN`.

***

#### **Response Structure**

The response will include the following fields:

```json
{
  "code": 0,                // (number: response code)
  "msg": "",                // (string: response message)
  "data": {
    "id": "",               // (string: unique ID of the transfer record)
    "tokenId": "",           // (string: token symbol)
    "amount": "",     // (string: transferred amount, negative means debit)
    "clientId": "",         // (string: client ID)
    "merchantId": "",       // (string: ID of the sender merchant)
    "fromMerchantId": "",   // (string: same as merchantId, sender)
    "toMerchantId": ""      // (string: recipient merchant ID)
  }
}
```

***

#### **Example Request**

```json
{
  "fromMerchantId": 246,
  "toMerchantId": 61,
  "tokenId": "USDT",
  "amount": 10,
  "clientId": "1"
}
```

***

#### **Example Response**

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "id": "4352",
    "tokenId": "USDT",
    "amount": "-10",
    "clientId": "1",
    "merchantId": "246",
    "fromMerchantId": "246",
    "toMerchantId": "61"
  }
}
```

***

✅ **Note:**

* The `amount` is negative on the sender side, indicating a debit.
