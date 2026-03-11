# Fund Collection

This API is used to consolidate multiple stablecoin payment records generated within the system into the merchant’s **Primary Wallet** for settlement and fund management purposes.

The collection process is an **internal fund operation** and does not involve on-chain transactions or additional blockchain transfers.

* Consolidated funds are reflected in the **Primary Wallet balance**
* Sub wallets are used solely for accounting categorization and do not hold on-chain assets
* Suitable for centralized fund management and settlement scenarios

***

* **Request Header: `X-BH-TOKEN: ******`**
* **Request Header: `Content-Type: application/json`**
* **Request Method: `POST`**
* **Request Path: `/v2/payments/collection`**
* **Authorization Required: Yes**

***

### Request Parameters

The request body should include the following parameters:

* merchantId: Merchant ID.
* currency: Stablecoin type (supported values: `USDT`, `USDC`).
* walletId: Wallet ID.

***

### Request Example

```json
{
  "merchantId": 1,
  "currency": "USDT",
  "walletId": 1
}
```

***

### Response Parameters

The response will contain the following parameters:

* code: Response status code.
* msg: Response message.
* data: No data returned for this operation.

***

### Response Example

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": null
}
```

***

### Notes

* This operation performs **internal balance consolidation** within the platform and does **not trigger any blockchain transaction**.
* Funds recorded under sub wallets are consolidated into the merchant’s **Primary Wallet** for settlement.
* The specified `walletId` must belong to the merchant account.
