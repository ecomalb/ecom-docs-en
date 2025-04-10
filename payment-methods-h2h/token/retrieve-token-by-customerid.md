---
description: '{{url}}/ecom/execute_request/token/v1/list/by-customer-id'
---

# Retrieve Token by CustomerId

#### Request Parameters

| Parameter  | Description | Data Format | Required | Example |
| ---------- | ----------- | ----------- | -------- | ------- |
| customerId | Customer ID | string(255) | Yes      | 12345   |

#### Response Parameters

| Parameter  | Description        | Data Format | Example                              |
| ---------- | ------------------ | ----------- | ------------------------------------ |
| customerId | Customer ID        | string(255) | 12345                                |
| token      | Token ID           | string      | SRrSBe5DOb7lrZ\_FS46fihty            |
| maskedPan  | Masked card number | string      | 516874\*\*\*\*\*\*7753               |
| merchantId | Merchant ID        | string      | 137d9304-0368-11ed-b939-0242ac120002 |
| status     | Token status       | string      | ACTIVE                               |

#### Example Request Body

```json
{
    "customerId": "senderCustomerId"
}
```

#### Example Response Body

```json
{
    "result": [
        {
            "token": "-s9UCfCNN0YMk4ZOyZX8pWAt",
            "status": "ACTIVE",
            "maskedPan": "523244••••••0177",
            "customerId": "senderCustomerId",
            "merchantId": "137d9304-0368-11ed-b939-0242ac120002"
        }
    ]
}
```
