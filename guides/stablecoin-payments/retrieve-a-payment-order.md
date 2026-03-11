# Retrieve a Payment Order

This API is used to retrieve detailed information about a specific stablecoin payment order by its order ID.\
Merchants can use this interface to check the current payment status, on-chain transaction details, and relevant timestamps.

Common use cases include:

* Verifying user payment results
* Order status validation
* Financial reconciliation and auditing

***

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header:** `Content-Type: application/json`
* **Request Method:** `GET`
* **Request Path:** `/v2/payments/order`
* **Authorization Required:** Yes

***

### Request Parameters

The request query should include the following parameters:

* orderId: Order ID.

***

### Request Example

```
GET /openapi/v2/payments/order?orderId=1
```

***

### Response Parameters

The response will contain the following parameters:

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
* status: Order status.
* commitTime: Order creation timestamp.
* processTime: Processing timestamp.
* confirmTime: Confirmation timestamp.
* cancelTime: Cancellation timestamp.
* expireTime: Expiration timestamp.
* fromAddress: Sender wallet address.
* toAddress: Receiver wallet address.
* remark: Additional remark.
* payCount: Payment count.
* linkId: Payment link identifier.

***

### Response Example

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
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
    "toAddress": "0x1234567890abcdef",
    "remark": null,
    "payCount": 0,
    "linkId": 1
  }
}
```

***

### Notes

* The `orderId` must correspond to an existing payment order under the merchant account.
* The `status` field reflects the current processing state of the payment order.
* Blockchain-related information such as `txHash`, `fromAddress`, and `toAddress` will be available once the on-chain transaction is detected.
* Timestamps are returned in **Unix milliseconds**.
