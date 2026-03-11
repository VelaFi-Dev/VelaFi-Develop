# Retrieve a List of Payment Order

This API is used to retrieve a list of stablecoin payment orders under a merchant account, with support for filtering by payment link and other criteria.\
The results are returned in a paginated format and are suitable for batch order inquiries and financial reconciliation.

***

* **Request Header: `X-BH-TOKEN: ******`**
* **Request Header: `Content-Type: application/json`**
* **Request Method: `POST`**
* **Request Path: `/v2/payments/page/orders`**
* **Authorization Required:** Yes

***

### Request Parameters

The request body should include the following parameters:

* currentPage: Current page number (default: 1).
* pageSize: Number of results per page (default: 10, maximum: 1000).
* merchantId: Merchant ID.
* linkId: Payment link ID used to filter related orders.

***

### Request Example

```json
{
  "currentPage": 1,
  "pageSize": 10,
  "merchantId": 1,
  "linkId": 1
}
```

***

### Response Parameters

The response will contain the following parameters:

* record: List of payment orders.
* userId: User identifier.
* merchantId: Merchant identifier.
* reference: Reference number.
* orderId: Order identifier.
* walletId: Wallet identifier.
* walletName: Wallet name.
* paymentLink: Payment URL.
* depositAmount: Amount to be deposited.
* feeAmount: Transaction fee.
* receivedAmount: Amount actually received.
* currency: Currency type.
* network: Blockchain network.
* txHash: Blockchain transaction hash.
* status: Order status. Possible values include `COMMITTED`, `PROCESSING`, `CONFIRMED`, `CANCELLED`.
* commitTime: Order creation timestamp.
* processTime: Processing timestamp.
* confirmTime: Confirmation timestamp.
* cancelTime: Cancellation timestamp.
* expireTime: Expiration timestamp.
* fromAddress: Sender wallet address.
* toAddress: Receiver wallet address.
* size: Page size.
* currentPage: Current page number.
* total: Total number of records.

***

### Response Example

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "record": [
      {
        "userId": 1,
        "merchantId": 1,
        "reference": "INV-123456",
        "orderId": 1,
        "walletId": 1,
        "walletName": "Primary Wallet",
        "paymentLink": "https://example.com/pay/123456",
        "depositAmount": 100.00,
        "feeAmount": 0.50,
        "receivedAmount": 99.50,
        "currency": "USDT",
        "network": "Polygon (POS)",
        "txHash": "0xabcdef1234567890",
        "status": "CONFIRMED",
        "commitTime": 1737452292000,
        "processTime": 1737452392000,
        "confirmTime": 1737452492000,
        "cancelTime": null,
        "expireTime": 1737538692000,
        "fromAddress": "0x9876543210fedcba",
        "toAddress": "0x1234567890abcdef"
      }
    ],
    "size": 10,
    "currentPage": 1,
    "total": 100
  }
}
```

***

### Notes

* The API supports paginated queries to efficiently retrieve large volumes of payment orders.
* The `linkId` parameter can be used to filter orders generated from a specific payment link.
* The `status` field indicates the current state of the order lifecycle.
* All timestamps are returned in **Unix milliseconds**.
