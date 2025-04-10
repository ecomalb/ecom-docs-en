# Authorization

### **Request Authorization**

To authorize a request, it is necessary to include the following headers:

> x-api\_version:V1
>
> x-device\_id:\{{deviceId\}}
>
> x-refresh\_token:\{{refreshToken\}}

### **Authorization Recovery**

If a request returns an HTTP status **401**, authorization data must be refreshed by executing a **session update request** and then retrying the failed request.

### **Timeout**

Timeout specified in the parameters:&#x20;

* "tokenExpirationDateTime":"2025-02-14 22:45:24.0463 +0000" - UTC&#x20;
* "tokenExpiration":"2025-02-15 00:45:24.463+02:00" - Kyiv, Ukraine time

### **Payments**

A **Payment** is a type of transaction used for purchasing goods, services, or products on websites using a payment card.

For **Payment** transactions, cardholder verification via **3D Secure** is required if the card is enrolled in the program.

### **Testing Data**

* **serviceCode** for device authorization – UUID (e.g., `a51e68aa-c6fa-11ed-afa1-0242ac120005`).
*   In the production environment, this code is generated separately by the **Bank** for each merchant.



### **Authorization Key:**

```json
{
    "kty": "EC",
    "d": "QVwaujXBuM1mdyNSadU5qSjRk5xggY-aX7yzes_qyNQC9nTVO1SmNBHd_fBzZILd",
    "use": "enc",
    "crv": "P-384",
    "x": "lxF9kVkpdTRqd256CO0Q3fOEAPcek-U_Q72UoySdXXZWr9Tf8bSMhc8gwVbgtDC",
    "y": "3aQaGq0Va9OshPr63jZ2KEcfO1jqibz6bKFeJr6K6h4dHFGj298hv7sb6bYaUyD",
    "alg": "ECDH-ES+A256KW"
}
```

### **Payment Key**

```json
{
    "kty": "EC",
    "use": "enc",
    "crv": "P-384",
    "x": "lxF9kVkpdTRqd256CO0Q3fOEgAPcek-U_Q72UoySdXXZWr9Tf8bSMhc8gwVbgtDC",
    "y": "3aQaGq0Va9OsGhPr3jZ2KEcfO1jqibz6bKFeJr6K6h4dHFGj298hv7sb6bYaUyD",
    "alg": "ECDH-ES+A25KW"
}
```

URL - https://api-ecom-prod.bankalliance.ua

### **Request Headers**

| Parameter        | Description                                          | Example                              |
| ---------------- | ---------------------------------------------------- | ------------------------------------ |
| x-api\_version   | API Version                                          | v1                                   |
| x-device\_id     | Generated when requesting authorize\_virtual\_device | f7b244ae-57e7-4fe2-89d7-7d6a02a17048 |
| x-refresh\_token | Generated when requesting authorize\_virtual\_device | 9a64d090-732c-4e28-9c57-609083b8bd56 |

