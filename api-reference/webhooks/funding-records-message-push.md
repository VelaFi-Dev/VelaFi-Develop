---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/webhooks/funding-records-message-push
---

# Funding Records Message Push

VelaFi uses webhooks to notify merchants of funding-related events in real time, such as deposits, withdrawals, crypto purchases, and refunds. When triggered, a POST request with detailed transaction data is sent to your configured webhook URL.



**Endpoint Information**

* **Request Method:** POST
* **Request Path:** _(Specify the appropriate path for your webhook notifications)_
* **Requesst** **Headers**: Requires signature
  * `signature` (string: To verify that a webhook request is coming from VelaFi, you can use the signature header. The value of the header is a RSA-SHA256 signature of the request body, Use hexadecimal encoding.)

**Request Body Parameters**

The request body should include the following fields:

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",  // (number: ID of the webhook)
    "eventType": "FUNDING_WEBHOOK",                  // (string: event type [FUNDING_WEBHOOK: merchant funding event])
    "txId": "1123123123",                            // (number: ID of the fiat claim)
    "merchantId": "3",                               // (number: ID of the merchant)
    "merchantName": "Rrturo Tellez",                 // (string: name of the merchant)
    "fiat": "ARS",                                   // (string: name of the fiat currency)
    "totalAmount": "22.00",                          // (decimal: total fiat amount)
    "amount": "20.00",                               // (decimal: actual fiat amount)
    "fee": "2.00",                                   // (decimal: amount of the fee)
    "userPaymentId": "91",                           // (number: ID of the user payment method)
    "type": "DEPOSIT",                               // (enum: type [DEPOSIT: The add of the funding record, WITHDRAW: The claim of the funding record, BUY_CRYPTO: The buy crypto of the funding record, REFUND: The refund of the funding record])
    "status": "1",                                   // (enum: status [1: pending, 2: completed, 3: canceled])
    "createTime": "1737452292000",                   // (string: timestamp of the create time in milliseconds)
    "updateTime": "1737452344000",                   // (string: timestamp of the update time in milliseconds)
    "cardNo": "3067212321",                          // (string: id of the entity sending ID number)
    "taxId": "5269328432",                           // (string: id of the entity sending tax)
    "payerName": "Matias Alva",                      // (string: name of the entity sending funds)
    "payerAccount": "CH8508843132556121020",         // (string: bank account of the entity sending funds)
    "bankWebhookInfo": "{}"                          // (json: bank webhook info of the entity sending funds, see Bank Webhook Info Detaials)
}
```

**Response Structure**

The response will include the following fields:

```json
{
    "callbackStatus": "SUCCESS"                      // (string: callback status; if SUCCESS is returned, the message is successfully notified)
}
```

**Example Request**

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
    "eventType": "FUNDING_WEBHOOK",
    "txId": "1123123123",
    "merchantId": "3",
    "merchantName": "Rrturo Tellez",
    "fiat": "ARS",
    "totalAmount": "22.00",
    "amount": "20.00",
    "fee": "2.00",
    "userPaymentId": "91",
    "type": "DEPOSIT",
    "status": "1",
    "createTime": "1737452292000",
    "updateTime": "1737452344000",
    "cardNo": "3067212321",
    "taxId": "5269328432", 
    "payerName": "Matias Alva",
    "payerAccount": "CH8508843132556121020" 
}
```

**Example Response**

```json
{
    "callbackStatus": "SUCCESS"
}
```



**Bank Webhook Info Detaials**

MXN Detail

```json
{
    "sender_account_number": "684180168000000000",  //(the payer cable)
    "description": "Payment",                       //(the description)
    "sender_name": "CENTAURE S.A. DE C.V.",         //(the payer name)
    "tracking_id": "DO1755784299100",               //(the bank tracking id)
    "sender_id": "CCN2203099WA"                     //(the identity id)
}
```

ARS Detail

```json
{	
    "id": "98569107",                                 //id
    "idCoelsa": "86VRPQ2GVJEQE70M2GLY0M",             //bank order id
    "titularOriginante": "Alejandro Samuel Alvarez",  //payer name
    "cuitCvu": "20391896357",                         //payer cuit
    "cuitOriginante": "20391896357",                  //payer cuit
    "cuentaOriginante": "0000003100158708912546",     //payer cvu/cbu
    "titularCvu": "ALVAREZ ALEJANDRO SAMUEL42911|61", //receiver name
    "cuitPsp": "30717909751",                         //receiver cuit
    "cvu": "0000278500000000540634",                  //receiver cvu
    "descripcion": "",                                //remark
    "fechaNegocio": "2025-08-28T00:00:00Z"            //time of payment   
}
```

COP Detail

```json
{
    "sender_name": "SUPEFINE SAS",      //(the payer name)
    "sender_id": "9017343700",          //(the identity id)
    "sender_bank_code": "1013",         //(the bank code)
    "description": "Payment In",        //(the description)
    "r2p_method": "pse",                //(the method)
    "tracking_key": "1714319140"        //(the bank tracking key)
}
```

BRL Detail

```json
{
    "payer_tax_id": "51799311002001",           //(the payer tax id)
    "payer_name": "Tom",                        //(the payer name)
    "payer_bank_account": "570302",             //(the bank last account number)
    "payer_bank_name": "BCO DO BRASIL S.A."     //(the bank name)
}
```

#### Notes

* Ensure that the webhook URL is properly configured to receive and process the notification.
* The `callbackStatus` indicates whether the message was successfully sent to the webhook. If it shows `SUCCESS`, the notification was sent without issues.
