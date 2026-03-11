# Stablecoin Payment Order Message Push

我按照你前面统一的 **API 文档结构风格**，把这部分整理成 **Webhook 文档格式**，保持与你其他接口一致。

***

## Stablecoin Payment Webhook - 稳定币支付回调通知

When the status of a stablecoin payment order changes, the system sends an event notification to the merchant’s pre-configured endpoint via **Webhook**.

The webhook mechanism enables merchants to receive **real-time payment updates** without actively polling the order query APIs.

* The webhook payload includes core order information and blockchain-related transaction data
* Merchants should properly handle the webhook request
* A successful **HTTP 200 response** is recommended to acknowledge receipt

***

### Webhook Event

Event Type: `STABLE_COIN_PAYMENT_WEBHOOK`

***

### Webhook Payload

The webhook request body contains the following parameters:

* webhookId: Unique identifier for the webhook event.
* eventType: Event type identifier.
* orderId: Payment order ID.
* userId: User identifier.
* merchantId: Merchant identifier.
* linkId: Payment link ID.
* walletId: Wallet identifier.
* walletName: Wallet name.
* referenceId: Merchant reference number.
* currency: Currency type.
* network: Blockchain network identifier.
* networkName: Blockchain network name.
* depositAmount: Deposit amount.
* feeAmount: Transaction fee.
* receivedAmount: Actual received amount.
* status: Order status (e.g., `CONFIRMED`).
* fromAddress: Sender wallet address.
* toAddress: Receiver wallet address.
* txHash: Blockchain transaction hash.
* paymentLink: Payment link URL.
* createTime: Order creation timestamp.
* cancelTime: Order cancellation timestamp.
* processTime: Processing timestamp.
* confirmTime: Confirmation timestamp.

***

### Webhook Example

```json
{
  "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
  "eventType": "STABLE_COIN_PAYMENT_WEBHOOK",
  "orderId": 1234567890,
  "userId": 9876543210,
  "merchantId": 42,
  "linkId": 56789,
  "walletId": 10001,
  "walletName": "Main USDT Wallet",
  "referenceId": "REF-2024-05-03-001",
  "currency": "USDT",
  "network": "ethereum",
  "networkName": "Ethereum Mainnet",
  "depositAmount": 1000.00,
  "feeAmount": 2.50,
  "receivedAmount": 997.50,
  "status": "CONFIRMED",
  "fromAddress": "0x1234567890abcdef1234567890abcdef123456789",
  "toAddress": "0x9876543210fedcba9876543210fedcba98765432",
  "txHash": "0xabcdef1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcd",
  "paymentLink": "https://payment.example.com/pay/123456",
  "createTime": 1714671600000,
  "cancelTime": null,
  "processTime": 1714672200000,
  "confirmTime": 1714672800000
}
```

***

### Notes

* Merchants must configure a **publicly accessible webhook endpoint** to receive event notifications.
* The webhook will be triggered when the **payment order status changes**.
* Merchants should return **HTTP 200** to confirm successful receipt of the webhook event.
* All timestamps are returned in **Unix milliseconds**.  - Stablecoin Payment Webhoo
