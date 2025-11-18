---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/order/retrieve-a-list-of-orders
---

# Retrieve a List of Orders

This API retrieves a list of orders based on specified query parameters.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/orders`
* **Authorization**: Required

Query **Parameters**

* **currentPage**: (number) The current page number (optional, default is 1).
* **pageSize**: (number) The number of results per page (optional, default is 10, max is 100).
* **startTime**: (string) The start time for filtering orders (optional).
* **endTime**: (string) The end time for filtering orders (optional).
* **orderType:** (string)The type of the orders to filter by, `fiat_to_crypto crypto_to_fiat fiat_to_fiat` .
* **orderStatus**: (number) The status of the orders to filter by (optional), status of the `fiat_to_crypto` `crypto_to_fiat` order (10: pending, 30: approved, 31: support documents pending, 40: pending payment, 50: paid, 60: released, 70: canceled); status of the fiat\_to\_fiat order (10: pending, 30: approved, 31: support documents pending, 41: payin pending, 51: payout pending, 60: released, 71: payin canceled, 72: payout canceled).

```url
/v2/orders?currentPage=1&pageSize=10&startTime=100000&endTime=200000
&orderStatus=10&orderType=fiat_to_crypto
```

#### Response Structure

When the order type is `fiat_to_crypto` and `crypto_to_fiat`, the response will include the following fields:

* cod&#x65;**:** (number)  response code
* msg: (string) message
* data: (object) order info
* orderId: (int) id of the order
* clientId: (string) a id defined by client
* merchantId: (int)  id of the merchant
* paymentId: (int)  id of user paymenyId
* country: (string) name of the country
* crypto: (string) name of the crypto currency&#x20;
* fiat: (string) name of the fiat currency&#x20;
* orderType: (string) type of the order
* orderPrice: (string) exchange rate when create orden
* cryptoAmount: (string) amount of crypto currency
* fiatAmount: (string) amount of fiat currency
* fiatFee: (string) fee of the order
* orderStatus: (int) status of the order(10: pending, 30: approved, 31: support documents pending, 40: pending payment, 50: paid, 60: released, 70: canceled)
* createTime: (string) create time of the order
* completedTime: (string) completed time of the order

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "size": 10,
        "currentPage":1,
        "total": 1,
        "record":[
            {
            "orderId": "493829236956962816",
            "clientId": "f_c_0250222004",
            "merchantId": 3,
            "paymentId": 0,
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
            "createTime": "1740214865000",
            "completedTime": "1740214866000"
            }
        ]
    }
}
```

When the order type is `fiat_to_fiat`, the response will include the following fields:

* cod&#x65;**:** (number)  response code
* msg: (string) message
* data: (object) order info
* orderId: (int) id of the order
* clientId: (string) a id defined by client
* onRampMerchantId: (int)  id of the merchant settings
* onRampPaymentId: (int)  id of user paymenyId
* onRampCountry: (string) name of the country
* onRampFiat: (string) name of the fiat currency
* onRampFiatAmount: (string) amount of fiat currency
* onRampFiatFee: (string) fee of the order
* offRampMerchantId: (int)  id of the merchant settings
* offRampPaymentId: (int)  id of user paymenyId
* offRampCountry: (string) name of the country
* offRampFiat: (string) name of the fiat currency
* offRampFiatAmount: (string) amount of fiat currency
* offRampFiatFee: (string) fee of the order
* orderPrice: (string) exchange rate when create order
* orderStatus: (int) status of the order(10: pending, 30: approved, 31: support documents pending, 41: payin pending, 51: payout pending, 60: released, 71: payin canceled, 72: payout canceled)
* onRampPaymentInfo: (object) info of the payment
* offRampPaymentInfo: (object) info of the payment
* createTime: (string) create time of the order
* completedTime: (string) completed time of the order

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "size": 10,
        "currentPage":1,
        "total": 1,
        "record":[
            {
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
                "offRampFiatFee": "1",
                "orderPrice": "55.9664",
                "orderStatus": 31,
                "createTime": "1740384573000",
                "completedTime": "1740384573000"
            }
        ]
    }
}
```

Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* The `record` array contains details about each order that matches the query parameters.
