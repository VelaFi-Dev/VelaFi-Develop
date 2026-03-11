# Retrieve Payment Links

This API is used to retrieve a list of stablecoin payment links created by a merchant, with support for filtering by various conditions.\
The query results are returned in a paginated format, allowing merchants to efficiently manage and analyze payment links.

Typical use cases include:

* Reviewing historical payment links
* Checking payment link status
* Analyzing payment link usage

***

* **Request Header:** X-BH-TOKEN: `******`
* **Request Header:** Content-Type: `application/json`
* **Request Method:** `POST`
* **Request Path:** `/v2/payments/page/links`
* **Authorization:** `Required`

***

### Request Parameters

The request body should include the following parameters:

* currentPage: Current page number (default: 1).
* pageSize: Number of results per page (default: 10, maximum: 1000).
* merchantId: Merchant ID.
* reference: Reference number used for filtering.
* currency: Payment currency.
* status: Link status filter. Possible values: `0` (Active), `1` (Expired).
* startTime: Start time timestamp (Unix milliseconds).
* endTime: End time timestamp (Unix milliseconds).

***

### Request Example

```json
{
  "currentPage": 1,
  "pageSize": 10,
  "merchantId": 1,
  "reference": "INV-123456",
  "currency": "USDT",
  "status": 0,
  "startTime": 1737452292000,
  "endTime": 1737538692000
}
```

***

### Response Parameters

The response will contain the following parameters:

* record: List of payment links.
* linkId: Payment link identifier.
* reference: Reference number.
* paymentLink: Payment URL.
* walletId: Wallet identifier.
* walletName: Wallet name.
* currency: Currency type.
* depositAmount: Deposit amount configured for the link.
* feeAmount: Transaction fee.
* totalDepositAmount: Total deposited amount through this link.
* totalConfirmedOrders: Total number of confirmed orders associated with this link.
* status: Link status (`ACTIVE` or `EXPIRED`).
* createTime: Creation timestamp.
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
        "linkId": 1,
        "reference": "INV-123456",
        "paymentLink": "https://example.com/pay/123456",
        "walletId": 1,
        "walletName": "Primary Wallet",
        "currency": "USDT",
        "depositAmount": 100.00,
        "feeAmount": 0.50,
        "totalDepositAmount": 1000.00,
        "totalConfirmedOrders": 10,
        "status": "ACTIVE",
        "createTime": 1737452292000
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

* This API supports **paginated queries** to efficiently retrieve large numbers of payment links.
* The `reference`, `currency`, and `status` parameters can be used to filter specific payment links.
* Time filters (`startTime`, `endTime`) use **Unix timestamp in milliseconds**.
* The `totalDepositAmount` and `totalConfirmedOrders` fields provide aggregated statistics for each payment link.
