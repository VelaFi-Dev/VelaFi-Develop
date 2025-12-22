---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/payment-method/get-payment-method
---

# Get Payment Method

This API retrieves payment methods based on various query parameters.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/payments`
* **Authorization Required**: Yes

#### Query Parameters

* **country**: (string) The country for which to retrieve payment methods.
* **status**: (int) The status of the payment method \[0: all (default), 1: valid, 2: authenticating, 3: authentication failed].
* **fiat**: (string) The fiat currency.
* **merchantId**: (int) The ID of the merchant id.
* **currentPage**: (int) The current page number.
* **pageSize**: (int) The number of results per page.

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 0,                            // (number: response code)
    "msg": "",                             // (string: message)
    "data": {                              // (object: result data)
        "currentPage": 1,                 // (number: current page number)
        "size": 10,                        // (number: number of results per page)
        "total": 100,                      // (number: total number of results)
        "record": [                        // (array: list of payment methods)
            {
                "id": 1,                  // (number: user payment ID)
                "merchantId": 1,           // (number: ID of the merchant id)
                "country": "Mexico",       // (string: name of the country)
                "fiat": "USD",             // (string: name of the fiat currency)
                "paymentId": 1,            // (number: ID of the payment configuration)
                "paymentMethodName": "Paypal", // (string: name of the payment method)
                "realName": "Bob",         // (string: real name of the account holder)
                "status": 1,                // (number: status of the payment method)
                "hasRefundAccount": 0,     // (number: indicates if a refund account exists)
                "fieldList": {             // (object: field JSON of the payment template)
                    [string]: [string]
                },
                "remark": "",               // (string: remark about the payment method)
                "createTime": 111          // (number: creation time)
            }
        ]
    }
}
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "record": [
            {
                "id": 228,
                "merchantId": 67,
                "country": "Hong Kong",
                "fiat": "USD",
                "paymentId": 529,
                "paymentMethodName": "CHATS",
                "realName": "test",
                "remark": "11",
                "createTime": 0,
                "fieldList": {
                    "Account Owner Type": "Business",
                    "Account Number": "390202731",
                    "Bank Name": "Citibank, N.A., Hong Kong Branch",
                    "Bank Country/Region": "HK",
                    "Bank Identifier": "CITIHKHX",
                    "Remarks": "111",
                    "Street": "UNIT E, 36/F., E-TRADE PLAZA, 24 LEE CHUNG STREET, CHAIWAN, HONG KONG",
                    "City": "Hong Kong",
                    "State": "HK-HK",
                    "Country/Region": "HK",
                    "Postal Code": "00000"
                },
                "status": 1,
                "hasRefundAccount": 0
            }
        ],
        "size": 10,
        "currentPage": 1,
        "total": 1
    }
}
```

#### Notes

* The `record` array contains details about each payment method that matches the query parameters.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
