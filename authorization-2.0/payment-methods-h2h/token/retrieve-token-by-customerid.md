---
description: '{{url}}/ecom/jws/token/list/by-customer-id_v1'
---

# Retrieve Token by CustomerId

#### Input parameters of the JWS payload part:

| Parameter  | Description | Data Format | Required | Example |
| ---------- | ----------- | ----------- | -------- | ------- |
| customerId | Customer ID | string(255) | Yes      | 12345   |

#### Output parameters of the JWS payload part:

| Parameter  | Description        | Data Format | Example                              |
| ---------- | ------------------ | ----------- | ------------------------------------ |
| customerId | Customer ID        | string(255) | 12345                                |
| token      | Token ID           | string      | SRrSBe5DOb7lrZ\_FS46fihty            |
| maskedPan  | Masked card number | string      | 516874\*\*\*\*\*\*7753               |
| merchantId | Merchant ID        | string      | 137d9304-0368-11ed-b939-0242ac120002 |
| status     | Token status       | string      | ACTIVE                               |

#### Examples

<details>

<summary>JWS Payload - the request body before signing up</summary>

```
{
    "customerId": "senderCustomerId"
}
```

</details>

<details>

<summary>JWS Payload - the response body before signing up</summary>

```
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

</details>
