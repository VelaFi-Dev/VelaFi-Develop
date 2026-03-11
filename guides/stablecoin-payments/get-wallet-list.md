# Get Wallet List

This API is used to retrieve a list of available stablecoin wallets under a specific merchant account.\
Merchants can use this interface to obtain wallet information before creating payment links or performing fund management operations.

Typical use cases include:

* Selecting a wallet prior to initiating a payment flow
* Wallet configuration and validation
* Managing multiple wallets under a merchant account

#### Endpoint Information

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header: `Content-Type:`**` ``application/json`
* **Request Method:** `GET`
* **Request Path:** `/v2/payments/wallets`
* **Authorization Required:** Yes

### Request Parameters

The request query should include the following parameters:

* merchantId: The merchant ID.

### Request Example

```
GET /openapi/v2/payments/wallets?merchantId=3
```

### Response Parameters

The response will contain the following parameters:

* wallets: List of wallets under the merchant account.
* walletId: Wallet identifier.
* walletName: Wallet name.

### Response Example

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "wallets": [
      {
        "walletId": 1,
        "walletName": "Primary Wallet"
      }
    ]
  }
}
```

### Notes

* The `merchantId` must correspond to a valid merchant account.
* If multiple wallets are configured for the merchant, all available wallets will be returned in the `wallets` list.
* The returned `walletId` can be used when creating payment links or performing wallet-related operations.
