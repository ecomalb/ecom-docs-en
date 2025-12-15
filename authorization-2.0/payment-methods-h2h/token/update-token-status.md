---
description: '{{url}}/ecom/execute_request/token/v1/state/update'
---

# Update Token Status

## Status Transition Rules

* **ACTIVE → SUSPENDED** – An active token can be suspended (e.g., for temporary blocking).
* **SUSPENDED → ACTIVE** – A suspended token can be reactivated (e.g., after unblocking).
* **ACTIVE → DELETED** – An active token can be deleted permanently.
* **SUSPENDED → DELETED** – A suspended token can be deleted if the user does not restore activity.
* **DELETED → any other status** – Not possible.

## Request Parameters

| Parameter | Description      | Data Format | Required | Example                   |
| --------- | ---------------- | ----------- | -------- | ------------------------- |
| token     | Token ID         | string      | Yes      | SRrSBe5DOb7lrZ\_FS46fihty |
| state     | New token status | string      | Yes      | SUSPENDED                 |

## Response Parameters

| Parameter    | Description                                    | Data Format | Example                   |
| ------------ | ---------------------------------------------- | ----------- | ------------------------- |
| tokenUpdated | Indicates whether the token status was updated | boolean     | true / false              |
| customerId   | Customer ID                                    | string(255) | 12345                     |
| token        | Token ID                                       | string      | SRrSBe5DOb7lrZ\_FS46fihty |

#### Приклади :

<details>

<summary>JWS Payload — тіло запиту перед підписанням</summary>

```
{
    "token": "-s9UCfCNN0YMk4ZOyZX8pWAt",
    "state": "SUSPENDED"
}
```

</details>

<details>

<summary>JWS Payload — тіло відповіді перед підписанням</summary>

```
{
    "tokenUpdated": true,
    "customerId": "senderCustomerId",
    "token": "-s9UCfCNN0YMk4ZOyZX8pWAt"
}
```

</details>
