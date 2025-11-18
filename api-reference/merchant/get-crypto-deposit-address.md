---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/get-crypto-deposit-address
---

# Get Crypto Deposit Address

This API allows you to retrieve the balances of cryptocurrency assets in a user's account.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/assets/depositAddress`
* **Authorization Required**: Yes

#### Query Parameters

* **tokenId**: (String) - ID of the token
* **chainType** (String) - Type of the blockchain (default: "")
* **merchantId**: (int) The ID of the merchant.

| tokenId | ChainType | Chain Full Name |
| ------- | --------- | --------------- |
| USDT    | TRC20     | Tron            |
| USDT    | ERC20     | Ethereum        |
| USDT    | BEP20     | BNB Smart Chain |
| USDT    | POL       | Polygon         |

#### Response Structure

The response will include the following fields:

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "allowDeposit": false, (boolean: whether the deposit is allowed)
    "address": "", (string: address of the deposit)
    "addressExt": "", (string: address tag)
    "minQuantity": "", (string: minimum amount of the deposit)
    "needAddressTag": false, (boolean: whether the address tag is required)
    "requiredConfirmNum": 0, (number: required confirmation number)
    "canWithdrawConfirmNum": 0, (number: maximum confirmation number)
    "tokenType": "" (string: type of the token)
  }
}
```

#### Example Response

tokenId: USDT\
chainType: TRC20

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "allowDeposit": true,
    "address": "TT5PSvrhxXjw2NZNu1S8L5ybwYVxCkQRKC",
    "addressExt": "",
    "minQuantity": "5",
    "needAddressTag": false,
    "requiredConfirmNum": 12,
    "canWithdrawConfirmNum": 20,
    "tokenType": "TRX_TOKEN"
  }
}
```

####
