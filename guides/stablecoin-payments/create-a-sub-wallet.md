# Create a Sub-Wallet

This API is used to create a new stablecoin wallet for a specific merchant.\
Once successfully created, the wallet can receive on-chain stablecoin transfers and can be associated with payment links or payment orders.

The platform distinguishes between a **Primary Wallet** and a **Sub Wallet**, which differ in functionality and intended usage.

#### Wallet Types

**Primary Wallet**

* Provides full fund management capabilities, including:
  * Stablecoin on-chain deposits
  * Stablecoin withdrawals
* Typically used for the merchant’s main settlement and fund management purposes

**Sub Wallet**

* Intended for internal accounting and bookkeeping purposes only
* Does not support independent on-chain deposits or withdrawals
* Commonly used for:
  * Business line segregation
  * Financial accounting
  * Payment data tracking and reconciliation

#### Usage Notes

* Each merchant has at least one **Primary Wallet** by default
* Creating sub wallets does not affect the ownership of the merchant’s actual on-chain assets
* Payment links may be associated with sub wallets for accounting categorization purposes, while all on-chain funds are credited to the merchant’s **Primary Wallet**

***

## Create Sub-Wallet

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header:** `Content-Type: application/json`
* **Request Method:** `POST`
* **Request Path:** `/v2/payments/wallet`
* **Authorization Required:** Yes

***

### Request Parameters

The request body should include the following parameters:



* merchantId: Merchant ID.
* walletName: Name of the sub wallet to be created.

***

### Request Example

```json
{
  "merchantId": 1,
  "walletName": "subwallet"
}
```

***

### Response Parameters

The response will contain the following parameters:

* walletId: The identifier of the created wallet.
* walletName: The name of the created wallet.

***

### Response Example

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "walletId": 1,
    "walletName": "New Wallet"
  }
}
```

***

### Notes

* Each merchant must have at least one **Primary Wallet** before creating sub wallets.
* Sub wallets are used for internal accounting purposes and cannot independently receive or withdraw on-chain funds.
* The returned `walletId` can be used for payment link creation, payment order association, and financial categorization.
