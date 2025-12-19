---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/merchant/transfer-pending-funds
---

# Transfer Pending Funds

This endpoint allows merchants to transfer funds internally from one merchant account to another within the VelaFi system. It enables seamless movement of balance for operational or accounting purposes.

#### Endpoint Information

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header:** `Content-Type: application/json`
* **Request Method:** POST
* **Request Path:** `/v2/merchant/transfer`
* **Authorization Required:** Yes

#### Request Parameters

The request body must include the following fields:

<pre class="language-json"><code class="lang-json"><strong>{         
</strong>    "clientId": "test01",        // (string: custom client-defined ID for tracking) required  
    "fromMerchantId": 434,       // (number: ID of the sender merchant) required  
    "toMerchantId": 5,           // (number: ID of the recipient merchant) required  
    "fiat": "MXN",               // (string: Name of the fiat currency (e.g., "MXN","ARS")) required  
    "paymentId": 58,             // (number: Payment ID (e.g., 58,63,68,90,95)) required  
    "fiatAmount": 10             // (decimal: amount to transfer) required  
} 
</code></pre>

#### Response Structure

The response will return the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test01",             // (string: client-defined ID for the transaction)
        "fromId": 521006138624569344,     // (number: Funding Records ID)
        "toId": 521006138641346560,       // (number: Funding Records ID)
        "fiat": "MXN",                    // (string: token used in transfer)
        "fiatAmount": "10",               // (string: transferred amount)
        "totalFiatAmount": "12",          // (string: total transferred amount)
        "fee": "2",                       // (string: transferred fee amount)
        "createTime": 1746694343261       // (number: timestamp of transaction creation in milliseconds)
    }
}
```

#### Example Request （MXN）

```json
{         
    "clientId": "test-mxn",
    "fromMerchantId": 434,
    "toMerchantId": 5,
    "fiat": "MXN",
    "paymentId": 58,
    "fiatAmount": 10
} 
```

#### Example Response (MXN)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test-mxn",
        "fromId": 521006138624569344,
        "toId": 521006138641346560,
        "fiat": "MXN",
        "fiatAmount": "10",
        "totalFiatAmount": "10",
        "fee": "0",
        "createTime": 1746694343261
    }
}
```

#### Example Request （ARS）

```json
{         
    "clientId": "test-ars",
    "fromMerchantId": 434,
    "toMerchantId": 5,
    "fiat": "ARS",
    "paymentId": 63,
    "fiatAmount": 10
} 
```

#### Example Response (ARS)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test-ars",
        "fromId": 521006138624569345,
        "toId": 521006138641346561,
        "fiat": "ARS",
        "fiatAmount": "10",
        "totalFiatAmount": "10",
        "fee": "0",
        "createTime": 1746694343261
    }
}
```

#### Example Request （COP）

```json
{         
    "clientId": "test-cop",
    "fromMerchantId": 15127301,
    "toMerchantId": 15127302,
    "fiat": "COP",
    "paymentId": 68,
    "fiatAmount": 10
} 
```

#### Example Response (COP)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test-cop",
        "fromId": 521006138624569346,
        "toId": 521006138624569347,
        "fiat": "COP",
        "fiatAmount": "10",
        "totalFiatAmount": "10",
        "fee": "0",
        "createTime": 1746694343261
    }
}
```

#### Example Request （BRL）

```json
{         
    "clientId": "test-brl",
    "fromMerchantId": 15127301,
    "toMerchantId": 15127302,
    "fiat": "BRL",
    "paymentId": 90,
    "fiatAmount": 10
} 
```

#### Example Response (BRL)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test-brl",
        "fromId": 521006138624569348,
        "toId": 521006138624569349,
        "fiat": "BRL",
        "fiatAmount": "10",
        "totalFiatAmount": "10",
        "fee": "0",
        "createTime": 1746694343261
    }
}
```

#### Example Request （PEN）

```json
{         
    "clientId": "test-pen",
    "fromMerchantId": 15127301,
    "toMerchantId": 15127302,
    "fiat": "PEN",
    "paymentId": 95,
    "fiatAmount": 10
} 
```

#### Example Response (PEN)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "clientId": "test-pen",
        "fromId": 521006138624569350,
        "toId": 521006138624569351,
        "fiat": "PEN",
        "fiatAmount": "10",
        "totalFiatAmount": "10",
        "fee": "0",
        "createTime": 1746694343261
    }
}
```

#### Notes

* Ensure that all provided IDs (merchantId, paymentId) are valid and active.
* The `clientId` can be used by clients to trace or de-duplicate requests.
* This operation is only valid for merchant accounts with sufficient balance.
* Supported fiat currency are:
  * `MXN` (Mexican Peso): use `paymentId = 58`
  * `ARS` (Argentine Peso): use `paymentId = 63`
  * `COP` (Colombia Peso): use `paymentId = 68`
  * `BRL` (Brazil Peso): use `paymentId = 90`
  * `PEN` (Peru Peso): use `paymentId = 95`

