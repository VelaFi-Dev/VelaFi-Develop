---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/order/retrieve-a-specific-order
---

# Retrieve a Specific Order

This API retrieves the detail of a specific order using its order ID.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/order/detail`
* **Authorization**: Required

**Query Parameters**

* **orderId:** (int)  The id of the order
* **orderType**: (string) The type of the order, `fiat_to_crypto crypto_to_fiat fiat_to_fiat`

<pre class="language-url"><code class="lang-url"><strong>/v2/order/detail?orderId=493829236956962816&#x26;orderType=fiat_to_crypto
</strong></code></pre>

#### Response Structure

When the order type is `fiat_to_crypto` and `crypto_to_fiat`, the response will include the following fields:

* cod&#x65;**:** (number)  response code
* msg: (string) message
* data: (object) order info
* orderId: (int) id of the order
* clientId: (string) a id defined by client
* merchantId: (int)  id of the merchant settings
* paymentId: (int)  id of paymenyId (`fiat_to_crypto`)
* userPaymentId: (int)  id of user paymenyId (`crypto_to_fiat`)
* country: (string) name of the country
* crypto: (string) name of the crypto currency&#x20;
* fiat: (string) name of the fiat currency&#x20;
* orderType: (string) type of the order
* orderPrice: (string) exchange rate when create orden
* cryptoAmount: (string) amount of crypto currency
* fiatAmount: (string) amount of fiat currency
* fiatFee: (string) fee of the order
* orderStatus: (int) status of the order(10: pending, 11: request for information, 12: uploaded RFI Information, 30: approved, 31: support documents pending, 40: pending payment, 50: paid, 60: released, 70: canceled)
* traceNumber: (string) id of the national central bank order
* paymentInfo: (object) info of the payment
* createTime: (string) create time of the order
* completedTime: (string) completed time of the order

<pre class="language-json"><code class="lang-json">{
<strong>    "code": 200,
</strong>    "msg": "SUCCESS",
    "data": {
        "orderId": "493829236956962816",
        "clientId": "f_c_0250222004",
        "merchantId": 3,
        "paymentId": 0,
        "userPaymentId": 0,
        "country": "Mexico",
        "crypto": "USDT",
        "fiat": "MXN",
        "orderType": "fiat_to_crypto",
        "orderPrice": "21.4104",
        "cryptoAmount": "5.1376",
        "fiatAmount": "110",
        "fiatFee": "0",
        "orderStatus": 60,
        "hasRefund": 0,
        "traceNumber": "20241223907069062e51744c4f0e57",
        "paymentInfo": {
            "CLABE number": "",
            "Account number/card": "706180304649761358",
            "Beneficiary Name": ""
        },
        "createTime": "1740214865000",
        "completedTime": "1740214866000"
    }
}
</code></pre>

When the order type is `fiat_to_fiat`, the response will include the following fields:

* cod&#x65;**:** (number)  response code
* msg: (string) message
* data: (object) order info
* orderId: (int) id of the order
* clientId: (string) a id defined by client
* onRampMerchantId: (int)  id of the merchant
* onRampPaymentId: (int)  id of user paymenyId
* onRampCountry: (string) name of the country
* onRampFiat: (string) name of the fiat currency
* onRampFiatAmount: (string) amount of fiat currency
* onRampFiatFee: (string) fee of the order
* offRampMerchantId: (int)  id of the merchant
* offRampPaymentId: (int)  id of user paymenyId
* offRampCountry: (string) name of the country
* offRampFiat: (string) name of the fiat currency
* offRampFiatAmount: (string) amount of fiat currency
* offArriveRampFiatAmount: (string) arrive amount of fiat currency
* offRampFiatFee: (string) fee of the order
* orderPrice: (string) exchange rate when create order
* orderStatus: (int) status of the order(10: pending, 11: request for information, 12: uploaded RFI Information, 30: approved, 31: support documents pending, 41: payin pending, 51: payout pending, 60: released, 71: payin canceled, 72: payout canceled)
* onRampPaymentInfo: (object) info of the payment
* offRampPaymentInfo: (object) info of the payment
* createTime: (string) create time of the order
* completedTime: (string) completed time of the order

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "orderId": "494541042692263936",
        "clientId": "c_f_0250224003",
        "onRampMerchantId": 3,
        "onRampPaymentId": 17,
        "onRampCountry": "Mexico",
        "onRampFiat": "MXN",
        "onRampFiatAmount": "110",
        "onRampFiatFee": "1",
        "offRampCountry": "Argentina",
        "offRampMerchantId": 4,
        "offRampPaymentId": 134,
        "offRampFiat": "ARS",
        "offRampFiatAmount": "6156.3",
        "offArriveRampFiatAmount": "6155.3",
        "offRampFiatFee": "1",
        "orderPrice": "55.9664",
        "orderStatus": 31,
        "onRampPaymentInfo": {
            "CLABE number": "",
            "Account number/card": "706180304649761358",
            "Beneficiary Name": ""
        },
        "offRampPaymentInfo": {
            "CLABE number": "",
            "Account number/card": "706180304649761359",
            "Beneficiary Name": ""
        }
        "createTime": "1740384573000",
        "completedTime": "1740384573000"
    }
}
```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* The `paymentInfo` object will vary based on the country and payment method used.
