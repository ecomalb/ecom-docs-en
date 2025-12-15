---
description: POST {{url}}/ecom/execute_request/merchant/ecom_balance/v1/get
---

# Getting a balance

## Output parameters:

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="234">Description</th><th width="160.50000000000003">Data Format</th><th>Example</th></tr></thead><tbody><tr><td>merchantId</td><td>Merchant ID</td><td>string</td><td>235d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>balanceAmount</td><td>Amount on the balance sheet</td><td>string</td><td>47</td></tr><tr><td>balanceLimit</td><td>Merchant overdraft limit amount</td><td>string</td><td>0</td></tr><tr><td>totalAmount</td><td>Total amount</td><td>string</td><td>47</td></tr></tbody></table>

#### Приклади :

<details>

<summary>JWS Payload — тіло запиту перед підписанням</summary>

```
{ }
```

</details>

<details>

<summary>JWS Payload — тіло відповіді перед підписанням</summary>

```
{
    "merchantId": "235d9304-0368-11ed-b939-0242ac120002",
    "balanceAmount": 47,
    "balanceLimit": 0,
    "totalAmount": 47
}
```

</details>
