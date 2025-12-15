---
description: '{{url}}/ecom/execute_request/token/v1/get'
---

# Retrieve Token Data

#### Request Parameters

| Parameter | Description | Data Format | Required | Example                   |
| --------- | ----------- | ----------- | -------- | ------------------------- |
| token     | Token ID    | string      | Yes      | SRrSBe5DOb7lrZ\_FS46fihty |

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
jsonКопіюватиРедагувати{
    "token": "SRrSBe5DOb7lrZ_FS46fihty"
}
```

#### Example Response Body

```json
jsonКопіюватиРедагувати{
    "result": [
        {
            "token": "-SRrSBe5DOb7lrZ_FS46fihty",
            "status": "ACTIVE",
            "maskedPan": "523244••••••0177",
            "customerId": "senderCustomerId",
            "merchantId": "137d9304-0368-11ed-b939-0242ac120002"
        }
    ]
}
```
